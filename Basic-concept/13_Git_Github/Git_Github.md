## # Git & Github

<br>

### # git branch 종류

1. Master Branch : 제품으로 출시될 수 있는 브랜치

2. Develop Branch : 다음 출시 버전을 개발하는 브랜치

3. Feature branch : 기능을 개발하는 브랜치

4. Release Branch : 이번 출시 버전을 준비하는 브랜치

5. Hotfix Branch : 출시 버전에서 발생한 버그를 수정 하는 브랜치

<br>

### # git merge, git rebase, git squash 차이

- git merge

  merge는 일반적인 병합 방법이다. 모든 커밋이 시간 순서대로 한꺼번에 병합된다. 충돌이 일어났을 경우 맨 마지막 커밋에 머지 커밋을 추가하여 해결한다.

- git squash

  squash 병합은 여러 개의 커밋을 하나의 커밋으로 합친 후 merge 하는 방식이다. 충돌이 일어났을 경우 충돌 해결 후 squash 병합을 진행하므로 마지막에 머지 커밋이 추가되지 않는다.
  이러한 방식은 feature branch에서 develop branch로 머지할 때 적합하다. 기능 단위로 개발된 feature의 commit을 하나로 모아줌으로써 기능 단위의 commit을 만들어
  develop branch에 머지하는 것이다. 이러한 방식을 통해 이슈를 추적하기가 용이해진다.

- git rebase

  rebase는 커밋의 시간과 상관없이, 병합 대상 브랜치(예: main)의 마지막 커밋 뒤에 현재 브랜치(예: develop)의 커밋들을 하나씩 순서대로 붙이는 방식이다. (쉽게 말해 rebase는 이름과 같이 base commit을 재정의하는데 병합 대상 브랜치의 마지막 커밋으로 재정의하는 것)
  이 과정에서 커밋을 하나씩 이어붙이기 때문에, 각 커밋마다 충돌이 발생할 수 있어 연쇄적으로 충돌이 발생할 가능성이 높다. (일반 merge는 여러 커밋을 한꺼번에 병합하기 때문에, 충돌이 연쇄적으로 발생하지 않는다.)
  또한 rebase는 병합 시 머지 커밋 기록이 남지 않아, 마치 하나의 브랜치에서 작업한 것처럼 깔끔한 히스토리를 보여준다. 이 방식은 보통 develop 브랜치를 main 브랜치에 병합할 때 적합하다.
  main 브랜치의 마지막 커밋 뒤에 develop 브랜치의 커밋들이 순차적으로 이어붙여지기 때문에 커밋 단위의 이력을 유지하면서 히스토리를 깔끔하게 관리할 수 있다.
  반면에 이 상황에서 squash를 사용하면 develop 브랜치의 여러 커밋들이 하나로 합쳐져서 커밋 단위의 상세 이력을 추적하기 어려워질 수 있다. 따라서 관련 기능별 커밋들을 rebase하여 main 브랜치 히스토리에 나란히 정리하는 것이 더 적합합니다.
  (ex git squash를 통해 feature에서 develop에 merge 된 기능별 커밋들을 그대로 살려 main 브랜치 맨 뒤 커밋에 순차적으로 병합하는 것)

<br>

### # 커밋 메시지 종류

(1) feat : 새로운 기능 추가

(2) fix : 버그 수정

(3) docs : 문서의 수정

(4) style : (코드의 수정 없이) 스타일(style)만 변경(들여쓰기 같은 포맷이나 세미콜론을 빼먹은 경우)

(5) refactor : 코드를 리펙토링

(6) test : Test 관련한 코드의 추가, 수정

(7) chore : (코드의 수정 없이) 설정을 변경

<br><br><br>
