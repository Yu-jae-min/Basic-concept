## # Git & Github

<br>

### # **git flow(process)**

<br>

- git으로 어떻게 일했는지 프로세스 설명

  (0) 기본적으로 커맨드(CLI, Command-Line Interface)를 사용하여 git을 사용하였다.

  (1) 기능 개발을 위한 feature 브랜치 생성하였다.

  (2) 기능 단위로 작업 완료 후 add -> commit -> PR을 날렸다.

  (3) 팀원들에게 리뷰받은 뒤 수정 후 직접 스쿼시 머지 (커밋을 하나로 합쳐 머지)

<br>

- git branch 종류

  (1) Master Branch : 제품으로 출시될 수 있는 브랜치

  (2) Develop Branch : 다음 출시 버전을 개발하는 브랜치

  (3) Feature branch : 기능을 개발하는 브랜치

  (4) Release Branch : 이번 출시 버전을 준비하는 브랜치

  (5) Hotfix Branch : 출시 버전에서 발생한 버그를 수정 하는 브랜치

<br>

- git merge, git rebase, git squash 차이

  (1) git merge : merge는 일반적인 병합 방법이다. 모든 커밋이 시간 순서대로 병합된다. 충돌이 일어났을 경우 맨 마지막 커밋에 머지 커밋을 추가하여 해결한다.

  (2) git squash : squash 병합은 여러 개의 커밋을 하나의 커밋으로 합친 후 merge하는 방식이다. 충돌이 일어났을 경우 충돌 해결 후 squash 병합을 진행하므로 마지막에 머지 커밋이 추가되지 않는다.

  (3) git rebase : rebase는 커밋의 시간에 관계없이 마지막에 merge 되는 branch의 commit을 가장 뒤로 병합된다. 충돌이 연쇄적으로 발생할 수 있기 때문에 주의해서 병합해야한다. 또한 브랜치 병합 시 머지 커밋 기록이 남지 않는다. 따라서 마치 하나의 브랜치에서 작업한 것처럼 보여진다.

<br>

- 커밋 메시지 종류

  (1) feat : 새로운 기능 추가

  (2) fix : 버그 수정

  (3) docs : 문서의 수정

  (4) style : (코드의 수정 없이) 스타일(style)만 변경(들여쓰기 같은 포맷이나 세미콜론을 빼먹은 경우)

  (5) refactor : 코드를 리펙토링

  (6) test : Test 관련한 코드의 추가, 수정

  (7) chore : (코드의 수정 없이) 설정을 변경

<br>
