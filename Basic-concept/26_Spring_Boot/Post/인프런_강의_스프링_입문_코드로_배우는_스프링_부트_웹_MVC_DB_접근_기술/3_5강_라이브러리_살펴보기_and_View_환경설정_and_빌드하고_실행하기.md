# [3강-5강] 라이브러리 살펴보기 / View 환경설정 / 빌드하고 실행하기

2023년 10월 31일

<br>
<br>

# 1. 3강 라이브러리 살펴보기

- build.gradle 파일 내부의 dependencies에서 설치한 라이브러리를 확인해볼 수 있다.

- 파일 디렉토리 중 External Libraries를 보면 실제 가져온 라이브러리들을 살펴볼 수 있다. build.gradle 파일 내부 dependencies 에 설치한 라이브러리와 차이가 있는데 dependencies 에 설치된 라이브러리 내에서 필요한 패키지들도 모두 포함되어있기 때문에 훨씬 많은 라이브러리들이 포함되어있는 것을 볼 수 있다. 예시에서는 `spring-boot-starter-thymeleaf` 와 `spring-boot-starter-web` 만 설치했음에도 불구하고 External Libraries 디렉토리에는 훨씬 많은 라이브러리가 설치되어있는 것을 볼 수 있다.

  ![spring_boot_inflearn_스프링_입문_3강_01](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/942b5061-46b2-4b7c-a12a-28e933742553)

- gradle과 같은 빌드 툴이 의존 관계를 관리해준다. 즉 `spring-boot-starter-web` 과 같은 라이브러리를 설치할 때 `spring-boot-starter-web` 가 의존 관계를 가지고 있는 필요한 라이브러리들을 알아서 가져와준다. 또한 중복은 알아서 제거해준다.

- 과거에는 웹서버를 띄우기 위해 서버에 톰캣을 설치하고 거기에 자바 코드를 밀어넣는 식으로 작업했다. 이제는 소스 라이브러리에서 이러한 웹서버를 내장(임베디드)하고 있다. 라이브러리 하나 빌드하고 서버에 올리면 끝나는 시대가 되었다.

- system.out.println 같은 경우에는 잘 사용하지 않는다. 실무에서는 로그라는 실무에서는 로깅을 많이 쓴다. 치명적인 에러 로그를 묶어서 관리하거나 로그 파일들을 관리하기 위함이다. 요즘에는 slf4j(인터페이스), logback(실제 로그를 어떤 구현체로 출력할지) 등의 조합을 사용한다.

- 테스트는 junit을 많이 사용한다.

- 정리

  - Gradle은 의존관계가 있는 라이브러리를 함께 다운로드 한다.

  - 스프링 부트 라이브러리

        - spring-boot-starter-web

            - spring-boot-starter-tomcat: 톰캣 (웹서버)

            - spring-webmvc: 스프링 웹 MVC

        - spring-boot-starter-thymeleaf: 타임리프 템플릿 엔진(View)

        - spring-boot-starter(공통): 스프링 부트 + 스프링 코어 + 로깅

            - spring-boot

                - spring-core

            - spring-boot-starter-logging

                - logback, slf4j

  - 테스트 라이브러리

        - spring-boot-starter-test

            - junit: 테스트 프레임워크

            - mockito: 목 라이브러리

            - assertj: 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리

            - spring-test: 스프링 통합 테스트 지원

<br>
<br>

# 2. 4강 View 환경설정

- src → main → resources → static 디렉토리 내부에 `index.html`을 작성해주면 웰컴 페이지([참고 URL](https://docs.spring.io/spring-boot/docs/current/reference/html/web.html#web.servlet.spring-mvc.welcome-page))를 만들 수 있다. 해당 페이지는 정적 페이지이다.

- 템플릿 엔진을 사용하면 원하는 형태로 바꿔줄 수 있다. 예제에서는 타임리프를 사용한다. ([참고 URL](https://www.thymeleaf.org/))

- 웹 MVC의 첫번째 진입점은 컨트롤러이다.

- 컨트롤러를 활용한 동적 페이지 작성 예시

  - 컨트롤러를 작성

    ```java
    // src/main/java/hello/hellospring/controller
    package hello.hellospring.controller;
    import org.springframework.stereotype.Controller;
    import org.springframework.ui.Model;
    import org.springframework.web.bind.annotation.GetMapping;

    @Controller
    public class HelloController {
        @GetMapping("hello")
        public String hello(Model model){
            model.addAttribute("data", "hello!!");
            return "hello";
        }
    }
    ```

  - 동적 html을 작성

    ```html
    <!-- // src/main/resources/templates/hello.html -->
    <!DOCTYPE html>
    <html xmlns:th="http://www.thymeleaf.org">
      <head>
        <title>Hello</title>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
      </head>
      <body>
        <p th:text="'안녕하세요. ' + ${data}">안녕하세요. 손님</p>
      </body>
    </html>
    ```

    - 타임리프 템플릿 엔진이 xmlsn에 선언되어있다. (html 태그의 `xmlns:th="http://www.thymeleaf.org"`)

    - th는 타임리프에 th이다.

  - 결과를 확인해보면 `안녕하세요. hello!!`가 찍히는 것을 볼 수 있다. p 태그의 `th:text="'안녕하세요. ' + ${data}"` 부분 중 `${data}`가 컨트롤러 내부의 `hello!!`로 치환되는 것이다.

- 위 동적 페이지가 가능한 이유

  ![spring_boot_inflearn_스프링_입문_3강_02](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/8e588804-8dbb-43c7-b5ab-9fc053026bf1)

  (1) 먼저 웹브라우저에서 [localhost:8080/hello](http://localhost:8080/hello라고) 로 접속한다.

  (2) 스프링은 톰캣이라는 서버를 내장하고 있는데 톰캣은 브라우저에서 URL을 전달받아 스프링으로 전달한다.

  (3) 스프링은 컨트롤러 내부 GetMapping을 통해 전달받은 URL의 Path와 매핑시킨다. 이 때 위 예시에서는 `@GetMapping("hello")` 통해 매핑시키는 것이다.

  (4) 매핑이 완료되면 해당 컨트롤러 내부에 있는 메소드를 실행시킨다. 이 때 model을 전달받는 것을 볼 수 있는데 스프링이 model을 만들어서 전달하는 것이다. 위 예시에서 html 내부 p 태그의 data는 모델이 key이다.

  (5) 메소드 내부의 return은 `“hello”`를 리턴하고 있는데 이 hello는 templates 디렉토리에 작성된 `hello.index`를 가리키는 것이다.

  (6) 컨트롤러에서 리턴 값으로 문자를 반환(위에서 hello)하면 뷰 리졸버(viewResolver)가 화면을 찾아서 처리하고 브라우저에 처리한 html을 넘겨준다.

- 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰 리졸버(viewResolver)가 화면을 찾아서 처리한다.

  - 스프링 부트 템플릿엔진 기본 viewName 매핑

  - `resources:templates/` + {ViewName} + `.html`

- 참고: spring-boot-devtools 라이브러리를 추가하면, html 파일을 컴파일만 해주면 서버 재시작 없이
  View 파일 변경이 가능하다. - 인텔리J 컴파일 방법: 메뉴 build → Recompile

<br>
<br>

# 3. 5강 빌드하고 실행하기

- 프로젝트 빌드

  - (1) 터미널 열고 프로젝트 디렉토리로 이동

  - (2) `./gradlew build`

    ![spring_boot_inflearn_스프링_입문_3강_03](https://github.com/Yu-jae-min/Basic-concept/assets/85284246/bb179b44-29b9-433a-85e8-5f64df410dfd)

  - (3) cd build → cd libs

  - (4) `java -jar hello-spring-0.0.1-SNAPSHOT.jar`을 통해 자바 실행

  - (5) http://localhost:8080/ 으로 접속하여 실행확인, 이 때 인텔리J에서 이미 서버를 실행 중인 경우 에러가 발생할 수 있기 때문에 미리 종료해주고 실행해야한다.

- 서버 배포 시에는 `hello-spring-0.0.1-SNAPSHOT.jar` 이 파일을 복사해서 넣어준 후 실행시켜주면 된다.

- `./gradlwe clean build`를 통해 이미 빌드된 디렉토리를 제거하고 다시 빌드를 시도할 수 있다.

<br>
