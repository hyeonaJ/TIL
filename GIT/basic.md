## 개념 ##
- Committed란 데이터가 로컬 데이터베이스에 안전하게 저장됐다는 것을 의미한다.

- Modified는 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않은 것을 말한다.

- Staged란 현재 수정한 파일을 곧 커밋할 것이라고 표시한 상태를 의미한다.
이 세 가지 상태는 Git 프로젝트의 세 가지 단계와 연결돼 있다. Git 디렉토리, 워킹 트리, Staging Area 이렇게 세 가지 단계를 이해하고 넘어가자.
# 1. GIT 명령어
## 프로젝트 가져오기와 생성하기 ##
- git init: git 저장소가 새로 만들어지고 프로젝트 버전을 관리할 수 있다.
- git clone: 디렉토리를 만들고 디렉토리로 들어가고 나서 git init 명령으로 빈 git 저장소를 만든다.

## 스냅샷 다루기 ##
- git status: 파일의 상태 확인
- git diff: 두 트리의 차이를 보고 싶을 때 ex) Staged와 Unstaged 상태의 변경 내용을 보기에서 처음 설명
- git commit: git add 로 Staging Area에 넣은 모든 파일을 커밋한다. 데이터베이스에는 하나의 스냅샷으로 기록된다. 그리고 현 브랜치가 새 커밋을 가리키게 한다. 커밋에 대한 기본적인 내용은 변경사항 커밋하기에서 다룬다. -a 플래그를 주고 git add 를 건너뛰고 바로 커밋하는 것과 -m 으로 커밋 메시지를 파라미터로 넘기는 방법도 보여준다. 가장 최근 커밋을 수정하는 --amend 옵션은 되돌리기에서 설명한다. -S 플래그로 커밋에 서명하는 방법은 커밋에 서명하기에서 설명한다.
- git reset: 되돌리는(Undo) 명령
- git rm:  Staging Area나 워킹 디렉토리에 있는 파일을 삭제하는 데 사용
- git mv: 일을 옮기고(이름을 변경하고) 나서 새 파일에 git add 명령을 실행하고 이전 파일에는 git rm 을 실행시켜주는 명령
- git clean: 필요없는 파일을 삭제하는 명령
git init
init : .git directory를 생성하기 위한 명령어
이미 .git 폴더가 있다면 입력하지 않아도 된다.
git add <filename>
git add <foldername>
git add .
add : working Directory 에서 Staging Area(Index)로 추가
.은 현재폴더의 모든 폴더, 파일을 의미
git commit -m "message"
commit : Staging Area에 올라간 파일들의 스냅샷을 찍어 .git directory에 저장
일반적으로 -m 옵션을 이용하여 커밋메세지를 같이 등록
git remote add origin https://github.com/sample.git
remote : 원격저장소주소를 추가한다 origin이라는 별명으로, 실제주소는 https://....이다.
이미 원격저장소를 추가했다면 입력하지 않아도 된다.
git push origin master
push : 업로드한다 origin이라는 원격저장소로 master를 보낸다.

## 공유하고 업데이트하기 ##
- git push: 프로젝트에 기여하기에서는 git push 를 주구장창 사용한다. 리모트를 여러 개 사용해서 브랜치에 작업한 내용을 공유하는 것을 보여준다.
- git remote:  git remote add <name> <url> 형식으로 사용

## 보기와 비교 ##
- git show:  Git 개체를 사람이 읽을 수 있도록 요약해서 보여준다. 태그나 커밋 정보를 보고 싶을 때 이 명령을 사용한다.
- git shortlog: git log 명령의 결과를 요약해서 보여 준다고 생각하면 된다. 옵션도 git log 명령의 것과 매우 비슷하다. 이 명령은 Author 별로 커밋을 묶어서 보여준다.
- git describ: 명령은 커밋과 관련된 정보를 잘 조합해서 사람이 읽을 수 있는 스트링을 만들어 준다. 커밋 SHA-1처럼 식별 가능하고 사람이 이해할 수 있는 정보가 필요할 때 사용한다.

## - 단축키##
$ git add -h
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --ignore-removal      ignore paths removed in the working tree (same as --no-all)
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
    --chmod <(+/-)x>      override the executable bit of the listed files