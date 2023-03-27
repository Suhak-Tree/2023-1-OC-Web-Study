<1주차> : www.hongik.ac.kr을 입력했을 뿐인데

URI : Uniform Resource Identifier. 리소스를 식별하는 통일된 방식 ex)URL, URN
URL : Uniform Resource Location. 리소스의 위치를 알려줌. 프로토콜(http등 통신 규약) + DNS 주소 ex) 교촌치킨 신촌점
URN : Uniform Resource Name. 리소스를 이름으로 찾음 ex)도서 출판번호 ISBN -> 책 쉽게 찾으려고 책에 고유 번호 부여
문제점 : IP주소 암기 및 관리 어려움, IP주소가 사정에 따라 변겨될 수 있음 -> DNS 서버의 등장 (서버 = 컴퓨터, 리소스 = 자료)
DNS : Domain Name System. 사이트들의 이름을 지어주자.
DNS 서버 : 지어준 이름들을 한 곳에다가 저장해둔 서버 -> IP주소 변경될 경우 변경된 IP주소를 연결해줌
Resource : html(자료, 뼈대역할), css(UI, 살과 옷 역할), js(제어) 파일들
랜더링 : html, css, js를 재료삼아 브라우저가 그림을 그려줌(js끄면 배너 이동x, 사진 변경x. js, css 끄면 렉 걸렸을 때처럼 앙상한 모습)
브라우저(프로그램)의 주소창에 URL 입력 -> DNS 서버에서 홍익대학교의 주소임을 확인 후 리소스를 브라우저에 전송 -> 브라우저가 html, css, js를 이용해서 페이지를 그려줌

정리 : www.hongik.ac.kr을 입력하면 무슨 일이 생기는가? -> 브라우저가 URL이 들어왔으니 DNS서버에 리소스를 요청함 -> 승인하면 DNS 서버가 홍익대학교 서버로 연결해줌 -> 브라우저가 홍익대학교 서버로부터 리소스를 받아서 웹 페이지를 그려줌

<2주차> : GIT – The Information From The Hell

GIT : 컴퓨터 파일의 변경사항을 추적하고 여러명의 사용자들간에 해당 파일들의 작업을 조율하기 위한 스냅샷 스트림 made by 리누스(linux 제작자)

GIT 장점 - 1. 코드의 수많은 분기(branch)를 만들어낼 수 O -> 코드의 수많은 버전을 만들 수 O 2. 분기를 나눌 수 O -> 원래 버전에서 새로운 버전으로 갈라져서 만들 수 O 3. 분기를 합칠 수 O -> 새로 만든 코드가 괜찮을 경우 합칠 수 O 4. 변화 추적(버전 관리) -> 새로 만들어진 것이 이상할 경우 특정 시점으로 되돌릴 수 O

기본 동작 방식 : untracked(추적X, 관심 없어서 추적을 하지 X), unmodified(변경X, github가 감시하는 상태) -> modified (. 명령어 입력시)-> staged

*내 작업공간
-working directory(작업 폴더) : 내 작업 공간. 코드를 합치고 보는 등 변화를 만들 수 있음. (ex. A라는 기능을 만들기 위해 A,B,C,D 코드를 짬) git add 명령어를 통해 staging area에 보낼 수 있음(stage fixes)
-staging area : 잠깐 대기시키는 공긴. 코드, 기능, 변화 조금씩 모아두고 쌓아두는 곳(ex. A,B,C,D를 통해 A 기능을 완성 시킨 것을 대기) git commit 명령어를 통해 이름을 붙이고 하나의 commit이 되어 local repository로 전달.(변화들 중 다음 커밋에 포함시킬 변화들을 모아두기)
-local repository(.git directory) : GIT에서 관리하는 어떤 저장소.(단, 우리 컴퓨터에서만 사용 O), push 명령어를 통해 remote repository로 전송 가능
*서버. 외부 저장소
-remote repository(서버 역할) : 외부 저장소. GIT의 변화 데이터들을 모아둘 수 있는 곳. 공통의 외부 저장소 역할을 하기에 팀원들이 자료를 공유하고 협업할 수 있음. (ex.GitHub) fetch, pull 명령어를 이용해서 코드를 내 컴퓨터로 받을 수 있음 -> 변화 추적 + 작업 조율의 역할

_실습 내용 복습_ GitHub remote repository와 내 프로젝트 local repository 연결하기

echo “# I love you” >> readme.md - readme.md 파일을 만드는 것
git init – git 시작함. 폴더를 git으로 관리하자. -> 내 프로젝트에 빈 Git Repository가 만들어짐(.git 폴더가 생성됨)
git add <파일명> - 변경 내용 파일 올림
git add . - 폴더에 있는 변경 내용 전부를 올림
git status – 상태확인
git commit –m “first commit” - “” 안의 내용 변경 O, m=message, staging 영역에서 local repository로 옮기며 명명
git branch –M main – branch 이름이 master에서 main으로 변경 -> 수많은 코드의 분기를 만들 수 O
git remote add origin “https://github........ 주소/.git) - origin이라는 이름을 붙여줌. local repository와 remote repository의 연관성 만듦
git push –u origin main. - local repository의 내용을 remote repository에 올림

<필수과제>
git add : 작업 디렉토리 상의 변경 내용을 staging area에 추가하기 위해 사용하는 명령어. 다음 변경(commit) 기록 전까지 변경분을 모아두기 위해 사용됨 => git commit 명령 전까지는 Git 저장소에 변경 이력 영향X
git commit : staging Area의 모든 파일을 local repository에 commit 한다.
git push : local repository의 commit 내역을 remote repository에 전송한다. -u 옵션은 upstream repository 설정해줌 -> 한번 설정 후 push, pull만 간단히 사용 O
git fetch : 로컬 저장소에 있는 것을 뺀 remote repository의 모든 것을 가져옴
git pull : remote repository의 commit을 가져오고 병합 -> =git fetch 후 git merge 실행
fetch와 pull의 차이점 : git fetch는 로컬 Git에게 원격 저장소에서 최신 메타데이터 정보를 확인하라는 명령을 전달. 단, 원격 저장소에 변경 사항이 있는지 확인만하고 변경된 데이터를 로컬 Git에서 실제로 가져오지 X. git pull은 원격 저장소에서 변경된 메타 데이터 정보를 확인할 뿐만 아니라 최신 데이터를 복사하여 로컬 Git에 가져옴

선택 과제 링크 : https://github.com/Suhak-Tree/create-react-app-homework.git
