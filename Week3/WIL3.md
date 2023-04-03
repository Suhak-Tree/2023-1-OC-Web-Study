<복습>
GIT - 컴퓨터 파일의 변경상 을 추적하고 여러 명의 사용자들 간의 해당 파일들의 작업을 조율하기 위한 스냅샷 스트림, 사진을 찍어서 코드들을 보관하는 어떤 프로그램. 파일의 변경사항을 추적하고 작업하고 조율한( 닥터스트레인지)
코드의 분기를 만들 수 있다. 코드의 다양한 분기들을 만들어서 또 다른 버전의 코드를 만들 수가 있고 그걸로 이제 다양한 시도도 해볼 수 있고 문제가 생겼을 때 과거로 돌아가서 빠르게 고치는 것이 가능. 분기를 나눌 수도 있음.
파일에 네 가지 상태 - untracked(추적 아예X), unmodified(추적중, 변화X or 커밋한 파일-변화가 초기화되어서 새로운 기준점이 됨), modified(파일 수정O), staged(commit하면 unmodified가 됨 - 새로운 기준점이 되니까)
working directory(내가 일하는 공간) -> (add - commit에 추가할 변경사항 추가) -> Staging Area(변경사항을 쌓아두는 공간, ex. 뒤로하기 누를 시 페이지 이탈 동의 모달구현 - 팀원들도 무엇을 했는지 알아보기 쉬움) -> commit(이름 지어줄 수 O, ex) git commit -m "feat. ~~~~") -> local repository(.git directory - git으로 관리하는 코드를 입력하면 ,git 폴더가 생김) // 여기까지가 내 컴퓨터 // -> push-> remote repository(서버 역할 외부 저장소. ex)GitHub) -팀원들 모두 공유 가능(pull or fetch or clone) => 협업에 유용 (빨간거=없어짐, 파란거=추가됨
<내용>
브랜치(Git Branch)란? 분기들을 관리해줌, 실체는 포인터, 헤드 - 하나하나의 commit
HEAD(내가 보고 있는 공간을 가리킴) -> master -> f30ab -> 34ac2 : 하나하나가 포인터
$ git branch testing testing이라는 포인터가 하나 생김. testing -> f30ab를 가르킴(내 맨 끝) - 가장 마지막 commit을 가리키는 포인터
if ) testing branch에서 commit을 하나 더함. -> commit이 하나 더 생김, testing만 한 칸 넘어옴, 마스터는 그자리
if) 마스터 commit으로 헤드를 옮기고, 하나를 추가하면 HEAD -> master -> 86ab2 0> f30ab, testing -> c279e -> f30ab로 바뀜
$ git checkout testing : HEAD를 testing으로 branch를 옮길 수 있음. testing 브랜치로 옮김
$ git branch testing : testing 이라는 이름의 branch를 만듦
$ git branch : 현재 있는 브랜치들을 모두 볼 수 있음
git status - 내가 어느 branch에 있나, 변화가 있나 볼 수 있음
폴더에 branchTest.md라는 파일을 만듦 -> checkout 넘어가는 것 -> commit 한번 함(변경사항 저장용) -> testing – HEAD 이어짐

<실습>

1. 깃허브에서 레포 만들기
2. 폴더 하나 정해서 git clone 명령어로 클론
3. 받아서 브랜치 만들기
   git branch <브랜치 이름>
   git branch => 브랜치 목록 띄워서 잘 만들어졌는지 확인
4. 깃허브 사이트 메인 레포에서 add file 해서 아무 파일 만들기
5. git pull로 메인 브랜치에서 파일 받아오기
   git pull origin master 혹은 git pull origin main (자기 설정에 맞게)
   -> add file로 홈페이지에서 만든 파일이 당겨서 받아짐
6. 깃 체크아웃으로 앞서 만든 브랜치에 파일이 없는 것을 확인
   git checkout <만든 브랜치 이름>
7. 새 브랜치와 메인 브랜치를 병합 -> main 브랜치의 파일이 새 브랜치에도 보임
   git merge <메인 브런치>

origin : 처음만들어질 때 주어진 이름, romote repository의 별명

merge(병합)
fast-forward 전략 : c2- master가 있고, c4에 hotfix가 있는데 merge => master의 포인터를 hotfix로 이동
3ways merge : c2 <- c4 <- master, c2(공통 조상) <- c3 <- c5 <- iss53 : 변화 기준
변화 – 기준이 있어야함 공통 조상을 기준으로 삼음 -> 둘 중에 무엇이 변한거고 안 변한것인지를 쉽게 파악할 수 있음 -> git은 기준 확인해서 합침!
새로운 commit이 만들어짐. c4 <- c6 <- master, c3<- c5 <- iss53, c5<- c6 <- master(새로운 commit이 생김)

conflict(충돌)

제가 어떤 기능을 올렸는데 사장님께서 이제 빠르게 뭔가를 합쳐버렸어요. 제가 합치기 전에 신속하게 그러면 이제 이 충돌을 제가 해결해야 되거든요. 뭐 그런 의도는 아니셨겠지만, 제가 홈버튼 추가를 했는데 싱크를 맞춰 달라 했잖요 이게 그거예요. 내가 수정한 부분을 사장님이 수정했으니까. 좀 맞춰 달라 좀 해결해 달라 네 그래서 이거를 두 코드가 충돌 났다고 해서 confict 부릅니다.

<상황>
master, mergeTest1, mergeTest2 모두 입력된 내용 다름 -> mergeTest1(head를 여기로 옮김)에서 megeTest2와 병합 시도 ->

current change(mergeTest1 - 기준), incoming change(mergeTest2) - IncomingChange누르면 Incoming change로 내용 변경됨 -> commit을 해줘야함 -> 꼭지점이 동그란 ㅅ모양 (알아서 staging은 되어있음, 개발자 개입으로 commit이 꼭 필요) ->

VSC – Resolve in Merge Editor -> Incoming, current가 바로 뜸 -> result에 결과가 바로 뜸 -> conflict merge -> commit 해줌 // but, master는 그대로
git stash : 지금까지 작업 중 커밋 못 해둔거 있으면 스택에 임시 보관
git checkout develop : develop으로 checkout
git pull orgin develop : develop 변경 내용들 pull
git checkout <> : 작업중이던 브랜치로 다시 이동
git merge develop : develop이랑 merge
//conflict 있으면 해결
git stash pop : 스택에 임시 보관한거 다시 불러오기
git add .
git commit –m “남길 메시지”
git push origin feature/niceCoolFeature : remote 서버의 feature/niceCoolFeature에 올림

깃 플로우 : 브랜치들을 관리하는 하나의 전략, develop – 메인 개발 branch(여기서 개발은X, feature branches - 검사한 괜찮은 코드만 develop에 합침, realese branch – 버전 관리할 때 사용. develop 모은 거 합친 것을 realese에 넣음, hotfix – 에러 관리)
github commit message convention : feat- 새로운 기능 추가, fix – 버그 수정, docs – 문서 수정, style – 코드 포맷팅, 세미콜론 누락, 코드 변경이 없는 경우, refactor – 코드 리펙토링, test – 테스트 코드, 리펙토링 테스트 코드 추가, chore – 빌드 업무 수정, 패키지 매니저 수정

<과제> - Pull Request 날리기
강사님의 repository fork -> 내 repository 저장 -> git clone 명령어로 내 컴퓨터에 받기(저는 git Desktop을 이용했습니다) -> 내 컴퓨터에서 작업 -> local에 내 github로 된 branch 만들기 (git branch Suhak-Tree) -> Suhak-Tree 폴더 작성 -> readmd.md 작성 -> 자기소개 추가 -> commit message를 convention에 맞게 두기(새로운 기능이 추가된 것은 아니고 문서를 추가한 것이디 docs가 맞지 않을까라는 생각으로 docs로 올림) -> romote repository에 새로운 내용을 push(단, Suhak-Tree로 된 branch에 push) -> 원본 리포지토리에 pull request 보냄 (base, head, compare 잘 설정할 것.) -> 끝

구글링을 조금씩 하면서 모르는 단어를 찾아보고 최대한 올려진 글에 맞게 따라할 수 있을 만큼 따라 했다고 생각했는데, 제대로 되었는지 아닌지를 잘 모르겠습니다. 아직 완벽하게 이해를 하고 있지는 않은 것 같은 느낌입니다.
