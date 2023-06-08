# [Git & GitHub] Git & GitHub 사용법

## Git

Git의 공식 명칭은 분산 버전 관리 시스템 (VCS) 으로써 프로젝트 파일의 변경 사항을 추적하는 시스템이다. 이를 통해 개발자들은 프로젝트의 변경 사항을 기록하고, 특정 시점의 버전으로 언제든 돌아갈 수 있다.

<br>

### #1 Repositories (저장소)

Git repository는 Git으로 관리하는 프로젝트 저장소이다. Git repository 에는 크게 두 가지 종류가 있다.

- Local repository - 본인의 컴퓨터에 저장된 로컬 버전의 프로젝트 저장소
- Remote repository - 로컬 repository 와는 반대로 내 컴퓨터가 아닌 외부 (일반적으로 원격 서버) 버전의 프로젝트 저장소. 팀에서 작업 할 때 특히 유용. 이 곳에서 프로젝트 코드를 공유할 수 있고, 다른 사람의 코드를 확인할 수도 있다. 또, 로컬 버전의 프로젝트와 병합하고, 변경 사항을 적용 할 수 있는 곳.

<br>

### #2 Installation Guide (설치 가이드)

Git은 주로 command-line interface (CLI)를 통해 사용한다.

> Git 다운로드 링크: https://git-scm.com/downloads

본인 컴퓨터에 해당하는 OS를 선택하시고 설치를 진행한다.
설치를 마쳤으면, Git을 사용할 수 있는지 확인하기 위해 터미널을 여시고 아래 커맨드를 입력한다.

> git --version

Git이 정상적으로 설치되었다면, 설치되어 있는 Git 버전이 표시됩니다.

그 후 Git에 본인 정보를 등록하기 위해 터미널에서 아래 커맨드를 입력한다.

> git config --global user.name "이름"
> git config --global user.email "이메일"
> -> "이름" 과 "이메일" 을 실제 본인의 정보로 대체해주세요.

### #3 Initializing a repository

새 저장소(repository) 를 만들고 Git으로 프로젝트 관리를 시작하려면 터미널에서 프로젝트 폴더로 이동 후 다음 명령어를 입력한다.

> git init

이 명령어는 프로젝트 폴더 내에 숨겨진 .git 디렉토리를 생성한다. 이제 Git은 현재 저장소에 대한 모든 변경사항을 추적/관리하게 된다.

<br>

### #4 Staging and committing code

Git에서 commit 이란, 프로젝트의 현재 상태를 나타내는 체크포인트 또는 스냅샷으로 생각할 수 있다. 쉽게 말해, 현재 버전의 코드를 커밋에 저장한다고 생각하면 된다. 커밋 히스토리에 필요한만큼 커밋을 생성 할 수 있으며, 커밋 간 앞뒤로 이동하여 프로젝트 코드의 다른 변경사항을 확인할 수 있다.

> git commit

일반적으로 커밋을 남기는 시점은 특정 내용, 기능을 추가한 후 또는 수정 사항을 적용한 후 이다. 코드를 커밋하려면 우선 코드를 staging area 에 추가해야 한다.

<br>

#### #4-1 Checking the status (상태 확인)

터미널에서 (프로젝트 폴더 내) 다음 명령어를 입력하여 repository의 현재 상태를 확인할 수 있다.

> git status

위 명령어는 Git으로 작업 할 때 굉장히 자주 사용되는 명령어이다. 어떤 파일이 변경되었는지, 어떤 파일이 추가되었는지 등을 전부 보여준다.

git status 명령어를 통해 Git 으로 관리(추적)되고 있지 않던 파일(들)이 있다면 해당 파일들을 staging area 로 추가해줄 수 있다.

모든 파일이 Git으로 관리되고 있는 시점에서는, git status 명령어를 통해 모든 변경사항을 확인할 수 있고, 커밋을 남기기 위해 staging area 로 추가해줘야 한다.

<br>

#### #4-2 Staging files (Staging area에 파일 추가하기)

프로젝트 폴더에서, git add 라는 명령어를 통해 우리가 원하는 파일들을 staging area 로 추가해줄 수 있다.
아래와 같이 특정 파일만 추가할 수 있다.

> git add file.js

여러개의 파일들을 추가하고 싶다면 아래와 같이 할 수 있다.

> git add file.js file2.js file3.js

파일을 각각 추가하지 않고, 아래와 같이 모든 파일을 한번에 추가할 수도 있다.

> git add .

위 명령어는 프로젝트 폴더 내의 모든 파일과 폴더를 staging area 에 추가하고 커밋을 남길 수 있게 해준다.

<br>

#### #4-3 Making commits (커밋 남기기)

커밋은 특정 시간의 코드 스냅샷의 형태로 해당 repository의 커밋 기록에 남게된다. git add 명령어를 사용하여 모든 파일을 staging area에 추가 해주었다면 이제 커밋을 남길 준비가 된 것이다.

아래 명령어를 통해 staging area에 있는 파일들을 커밋할 수 있다.

> git commit -m "Commit message"

식별을 위해 큰 따옴표안에 커밋 메세지를 작성해야 한다. 커밋 메시지는 repository에 커밋하는 변경 사항을 설명하는 짧은 summary 여야 한다.
위 명령어를 실행하면, 터미널에 방금 남긴 커밋에 대한 세부 내용이 보여지게 된다.

#### #4-4 Commit history

프로젝트의 모든 커밋 내역을 보려면 다음 명령어를 입력하면 된다.

> git log

git log 명령어를 통해 보여지는 log는 각 커밋에 대한 자세한 정보를 담고 있다. (작성자, hash 값, 날짜와 시간, 그리고 커밋 메세지)

만약 특정 커밋 시점의 코드로 되돌리고 싶다면, 아래 명령어를 사용할 수 있다.

> git checkout `<commit-hash>`
> -> `<commit-hash>` 를 git log 에서 보이는 커밋의 실제 hash 값으로 대체

<br>

#### #4-5 Ignoring files

staging area 에 추가하고 싶지 않거나, git 에서 관리하지 않아도 되는 파일이 있다면, .gitignore 파일을 프로젝트 폴더에 생성해주시면 된다.

.gitignore 파일 안에, 해당하는 파일명과 폴더명을 나열하면 된다. (각 파일, 폴더가 새로운 줄에 입력되어야 한다.)

> // example
> .DS\_\*
> _.log
> logs
> \*\*/_.backup._
> \*\*/_.back.\*
> node_modules
> bower_components

### #5 Branches

브랜치란 독립적으로 어떤 작업을 진행하기 위한 개념이다. 필요에 의해 만들어지는 각각의 브랜치는 다른 브랜치의 영향을 받지 않기 때문에, 여러 작업을 동시에 진행할 수 있다.

여러 명이서 동시에 작업을 할 때에 다른 사람의 작업에 영향을 주거나 받지 않도록, 먼저 메인 브랜치에서 자신의 작업 전용 브랜치를 만든다. 그리고 각자 작업을 진행한 후, 작업이 끝난 사람은 메인 브랜치에 자신의 브랜치의 변경 사항을 적용한다.

이렇게 함으로써 다른 사람의 작업에 영향을 받지 않고 독립적으로 특정 작업을 수행하고 그 결과를 하나로 모아 나가게 된다. 이러한 방식으로 작업할 경우 '작업 단위', 즉 브랜치로 그 작업의 기록을 중간 중간에 남기게 되므로 문제가 발생했을 경우 원인이 되는 작업을 찾아내거나 그에 따른 대책을 세우기 쉬워진다.

저장소를 처음 만들면, Git은 바로 'master'라는 이름의 브랜치를 만들어 둔다. 이 새로운 저장소에 새로운 파일을 추가 한다거나 추가한 파일의 내용을 변경하여 그 내용을 저장(커밋, Commit)하는 것은 모두 'master' 라는 이름의 브랜치를 통해 처리할 수 있는 일이 된다.

'master'가 아닌 또 다른 새로운 브랜치를 만들어서 '이제부터 이 브랜치를 사용할거야!'라고 선언(체크아웃, checkout)하지 않는 이상, 이 때의 모든 작업은 'master' 브랜치에서 이루어 진다.

#### #5-1 Creating a new branch (브랜치 생성하기)

아래 명령어를 통해 새로운 브랜치를 생성할 수 있다.

> git branch `<new-branch-name>`
> -> 새로 만들어진 브랜치는 현재 프로젝트의 코드를 그대로 반영하여 생성된다. 또한 작업 도중 추가로 브랜치를 생성할 때는 master로 이동 후 생성해야 한다.

보통 코드를 개선하고 새로운 실험 기능을 추가하는 등의 작업을 할 수있는 development 브랜치를 만드는 것이 좋다. 새로운 기능을 개발하고 테스트 한 후 버그가 없고, 사용할 준비가 되어있는지 확인한 후 최종적으로 master 브랜치에 병합할 수 있다.

<br>

#### #5-2 Changing branches (브랜치 전환하기)

아래 명령어를 통해 다른 브랜치로 이동할 수 있다.

> git checkout `<branch-name>`

원하는 브랜치로 이동하면, 해당 브랜치 안에 있는 마지막 커밋 내용이 작업 트리에 펼쳐진다. 브랜치가 전환 되었으므로 이후에 남기는 커밋은 전환한 브랜치에 추가된다. 해당 브랜치에만 영향을 주게 되는 것이다. 그런 다음 다른 브랜치로 이동하여 작업 할 수 있으며, 이전 브랜치의 변경 사항 및 커밋의 영향을 받지 않는다.

브랜치 생성과 동시에 생성된 브랜치로 이동하고 싶다면 기존 checkout 명령어에 -b 라는 flag 를 추가해주면 된다.

> git checkout -b `<new-branch-name>`

프로젝트에 존재하는 모든 브랜치를 확인하고 싶다면 아래와 같은 명령어를 입력하면 된다.

> git branch

<br>

#### #5-3 Merging branches (브랜치 병합하기)

A 라는 브랜치에서 작업한 내용을 B 라는 브랜치에 적용하고 싶을 때, 브랜치 A 와 브랜치 B 를 병합(merge) 할 수 있다. 예를 들어, 특정 브랜치에서 새로운 기능을 완벽하게 구현하고 테스트까지 완료한 시점이면, 기준이 되는 master 브랜치에 구현내용을 적용시켜야 할 때 merge 를 사용한다.
아래 명령어를 통해 다른 브랜치를 현재 브랜치와 병합할 수 있다.

> git merge `<branch-name>`

<br>

#### #5-4 Deleting a branch (브랜치 삭제하기)

아래 명령어를 통해, 브랜치를 삭제할 수 있다.

> git branch -d `<branch-name>`

<br>

## Git Hub

GitHub은 Git repository를 위한 호스팅 플랫폼이다. GitHub (및 기타 유사한 플랫폼) 없이도 Git을 사용할 수 있지만 다른 개발자와 같은 프로젝트를 두고 협업하거나 내 코드를 공유하기는 어렵다.

> - Git은 버전 관리 시스템으로, 시간이 지남에 따라 파일의 변경 사항을 추적하는 도구.

- GitHub은 Git을 사용하는 프로젝트를 위한 호스팅 서비스.

<br>

### #1 Using GitHub

Common Workflow: 내 로컬 Repository를 GitHub 에 push 하기

> (1) 로컬에서 add / commit 한다.
> (2) Github 으로 이동 후 새 repository를 생성한다.
> (3) 나의 로컬 repository 를 GitHub repository 와 연결한다. (remote 추가)
> (4) 새 remote 를 이용하여 코드를 Push 한다.

<br>

#### #1-1 repository 생성하기

GitHub repository 를 생성하려면, github.com 으로 이동 후 우측 상단 + 버튼을 누른 뒤 'New repository' 라는 옵션을 선택한다. 그 후 repository 를 생성하는 페이지에서 제일 먼저 Repository name 을 설정해야한다.

<br>

#### #1-2 repository 에 코드 push 하기

'Create repository' 버튼을 누르게 되면 새로 만든 GitHub repository 의 스타팅 페이지로 이동하게 된다.

로컬환경에 이미 Git repository 가 있다면 아래 ...or push an existing repository from the command line 부분에 나와있는 순서대로 진행하면 된다.

git remote add origin 명령어는 내 컴퓨터에 있는 로컬 repository 와 방금 만든 GitHub repository 를 연결해준다. 쉽게 설명하면, 로컬 Git repository 에게 이름이 origin 이라는 어떤 URL을 알려주는 것과 같다. 이름이 꼭 origin 이어야 하지는 않지만 보통 remote 주소가 한개라면 origin 이라고 지어주게 된다.

git push 명령어는 로컬 Git repository 의 코드를 GitHub repository 로 업로드 해준다.

> git remote add origin https://github.com/<`your-username`>/<`your-repo-name`>.git
> git push -u origin master

git push 명령어를 실행하면 GitHub 유저네임과 비밀번호를 입력하라는 prompt 가 뜨게 된다.

repository 가 성공적으로 push 되었다면, 전에 만든 GitHub repo 페이지로 가서 새로고침하면 로컬에서 push 한 코드가 해당 remote repository 로 업로드 된 것을 확인할 수 있다.

<br>

#### #1-3 repository 에 변경사항 남기기

로컬 Git repo를 GitHub remote repo 와 연결 후 push 까지 했다고 로컬에서 작업한 내용들이 자동으로 remote 에 반영되는 것은 아니다. 그래서 변경사항이 있으면 다시 push 를 해줘야 GitHub repo 가 업데이트 된다.

예를 들어, "console.log("안녕하세요!")" 와 같이 콘솔로그문을 이미 가지고 있는 js 파일에 추가해주거나, 해당 내용을 담고 있는 새로운 js 파일을 생성해준다. 저장 후 커밋을 위해 add 후 커밋메세지를 남겨준다.

> git add .
> git commit -m "Change greeting"

커밋을 한 뒤, 아래 명령어를 입력해서 업데이트 된 로컬 repo를 GitHub repo로 push 해준다.

> git push origin master

브랜치를 push하는 경우 git push origin <브랜치명>으로 push한다.

<br>

#### #1-4 repository 클론하기 (clone)

지금까지는 로컬에서 Git repo 를 생성한 뒤 리모트 GitHub repo 를 생성해 연결해주는 예시를 보았다. 다른 방법으로, GitHub repo 를 먼저 생성한 뒤 clone 을 받아 내 로컬환경에 다운로드 후 프로젝트를 시작하는 방법도 있다.

2.1 에서와 같이 GitHub repo 를 생성해준다.

repository 를 clone 하기 위해서 'Clone or download' 라는 초록색 버튼을 누른 뒤 아래 복사 아이콘을 클릭한다. (repository 주소를 복사해준다.)

그 다음 해당 remote repository 를 내 컴퓨터로 받아오기 위해, 해당 repo 를 다운로드 받고 싶은 경로로 이동한 뒤 git clone 명령어에 방금 복사해준 URL 을 붙여주고 실행해준다.

> git clone <`github-repo-link`>

이렇게 하면 해당 경로에 clone 받은 GitHub repository 의 이름을 그대로 딴 폴더가 생성되고 cd 명령어를 사용해 해당 폴더로 이동하면, clone 시점에 remote repository에 존재했던 모든 폴더 및 파일들이 그대로 복제되어 있는것을 확인할 수 있다.

이렇게 다른 개발자들의 public repository 를 클론받아 작업할 수도 있다.

<br>

### #2 Branching and merging

일반적으로 GitHub repository 의 master 브랜치는 항상 잘 작동하고 안정적인 버전의 코드를 포함하고 있어야 한다. 하지만, 테스트를 아직 해보지 않았거나, 새로 추가한 기능을 GitHub repo 에 push 하고 싶다면 어떻게 해야할까?

이럴 때 Branch 가 필요하다. 브랜치를 사용해서 현재 프로젝트의 코드를 그대로 복제하여 작업 환경을 만들 수 있다. 그렇게 된다면, master 브랜치를 건드릴 필요없이 작업환경에서 기능을 추가하거나 테스트를 진행할 수 있게 되는것이다. 나중에 전부 완료가 된다면, 그 때 master 브랜치와 merge (병합) 해줄 수 있다.

<br>

#### #2-1 GitHub 에 브랜치 push 하기

예를 들어, 아까 생성 한 hello-wecoders 프로젝트에 새로운 파일을 추가하고 싶다면, 우선 아래 명령어를 통해 새로운 브랜치를 생성하고 이동해야 한다.

> git checkout -b feature/greetings
> -> <feature/greetings> 부분을 원하시는 브랜치 이름으로 대체

그런 다음, example.js 라는 파일을 만들고, 아래 코드를 삽입해준다.

> console.log("Hello!");

그런 뒤, 커밋 절차를 거쳐 변경사항을 커밋해준다.

> git add .
> git commit -m "Add: greetings"

이제 push를 통해 feature/greetings 브랜치를 remote 로 올려줄 차례이다.

> git push origin feature/greetings

이렇게하면, GitHub repository 에 내가 방금 push 한 branch가 추가되는 것을 확인할 수 있다.

<br>

#### #2-2 Pull Request (PR) 생성하기

커스텀 브랜치를 push 하고 master 브랜치에 적용될 준비가 되었다면, Pull Request (PR) 라는 것을 통해 프로젝트 오너 (혹은 팀 리더) 에게 내가 작업한 브랜치의 작업내용을 master 브랜치에 반영해달라는 요청을 보낼 수 있다.

Pull Request 에서는 해당 repository 를 열람할 수 있는 권한이 있는 개발자들이 작업내용에 대한 리뷰를 해주거나, 변경 사항을 확인할 수 있다. (master 브랜치로 합쳐지기 전에 확인해야하기 때문에)

해당 링크를 클릭하면, Pull Request 를 생성할 수 있는 페이지로 이동하게 됩니다. 거기서 해당 PR의 제목과 어떤 내용을 담고 있는지 설명하는 Description을 작성할 수 있다.

작성을 완료했다면, 하단에 'Create pull request' 버튼을 눌러 마무리한다.

이때부터는 함께 협업하는 개발자들이 방금 만든 PR을 리뷰, 분석하고 댓글까지 달아줄 수 있다.

모든 리뷰 내용이 반영된 후 master 브랜치와 충돌이 발생하지 않았다면, 해당 PR은 master 브랜치로 merge 될 준비가 완료된다.

<br>

#### #2-3 Conflicts (충돌)

항상 이렇게 순조롭게 merge 까지 진행되면 너무 좋겠지만, merge 하기 전 conflicts (충돌) 가 발생할 수도 있다. 충돌은 어떤 파일의 변경사항이 기준이 되는 master 브랜치의 파일과 겹쳐, Git 에서 어떤 버전의 코드를 선택해야하는지 모를 때 발생한다. 이런 상황에서는, 개발자가 직접 코드를 비교해 충돌을 해결하고 merge 를 마무리 해야한다.

<br>

#### #2-4 GitHub 으로부터 변경사항 pull 하기

Pull Request 를 통해 master 브랜치를 업데이트했다면, 이제 로컬 repository 는 GitHub 에 있는 master 와 서로 다른 내용을 가지고 있게 된다. 이 때 git pull 명령어를 통해 remote 의 최신화된 코드를 내 로컬 repo 에 반영할 수 있다.

우리는 GitHub remote repo 링크에 origin 이라는 이름을 붙여줬었기 때문에 아래 명령어를 통해 GitHub repo 의 master 브랜치 내용을 받아올 수 있다.

> git pull origin master
