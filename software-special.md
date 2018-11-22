# 2018 년 10 월 18 일 소프트웨어 공학 특강 - 최우영 강사님.

- (git for windows)[gitforwindows.org]

## GIT

- workspace :
- => add .
- index : 변경사항이 올라간다.
- => commit : 변경사항이 어떤 연유로 어떤 시점에 바뀌었다
- local repository : commit 한 내용이 라벨이 달려서 여기 저장된다.
- => commit
- remote repository : git server

## 1. git ignore 가 필요하지 않을때의 레포 등록 방식

```js
mkdir react-sample
ls
cd react-sample
ls
git --version // git 버전 확인
git init
git status // git initialized가 잘 되었는지 확인
touch README.md // 파일 생성
vi READMD.md // vim으로 해당 파일 오픈

// vim editor 에서
i // insert 단축키. 글쓰기
: // 콜론 후 저장,종료, 저장및 종료 등등 사용가능
: 4 // 4번 줄로 이동하라
: w // 저장
: q // 나가기
: wq // 저장하고 나가기
: q! // 저장하지않고 나가기

cat README.md // 쓴 글 확인

git status // workspace에서 수정된 내용이 있는것을 확인
git add README.md

// github에서  repo 생성
// 연결을 위해 SSH 소스 따옴
git remote add origin git@github.com:bbgrams/react-sample.git
// 이후에 나올 깃 주소를 origin이라는 이름으로 부르겠다.

git remote get-url origin // 오리진이라는 이름을 붙인 깃 url을 가져와라
git remote remove origin // 오리진이라는 이름을 삭제한다.

git remeote origin
git config --global core.editor "vim" // 앞으로 vim이라는 에디터를 쓰겟다. 이후에 git commit을 하면 vim으로 넘어감.
git config --list // 여러가지 정보를 확인할수있음. user.name, user.email 등

git commit // commit하면 vim이 뜸.
// insert모드로 가서 commit 메세지를 자세하게 작성하고 :wq하여 나옴.

// 혹시 git repo를 잘못 연결했다면 해당 폴더에서 `rm -rf .git`을 하면 된다


git push origin master // push
```

## 2. git ignore

- 레포를 만들 때 `Initialize this repository with a README` 에 체크를 해주면 READMD.md 와 gitignore 파일이 만들어진다.
- Add.gitignore 에 Node 로 체크
- license
  - appach : 자유롭게 써도 되지만 내꺼라는 표시
  - GPL : 저작권?처럼 소유권 등록. 이 코드를 몇줄이라도 갖다 썼다간 수익의 일부를 줘야할수있음..
  - MIT : 아주 자유

```js
// 레포를 만들고 git clone 주소를 복사해서
**dev** 폴더로 꼭 들어간다!!
git status
git clone git@github.com:bbgrams/ignore-practice.git // git 연결 완료
git status

vi .gitignore // .gitignore 파일을 vim에서 읽는다.

// gitignore 파일안에서
# Custom // #은 주석
hidden/
*.py    // py확장자의 모든 파일 무시


mkdir hidden // hidden 폴더 생성
mkdir hiddens // hiddens 폴더 생성

touch hidden/index.js // hidden파일 안에 index.js 파일 생성
touch hiddens/main.py // hidden파일 안에 main.py 파일 생성
touch index.js // index.js파일 생성

git status // 2개의 파일이 확인될 것.

// 두 개의 파일은 따로따로 짤라서 커밋해야함.
// 내가 어느 시점에 어떤 이유로 수정을 했는지 , 다른 목적으로 수정을 했기 떄문에 따로따로 커밋해야함

git add .gitignore
git commit -m " git commit -m Conf: edit .gitignore
 I edited .gitignore to ignore hidden/ and *.py"
 // 쌍따옴표가 닫힐때까지 적을 수있다. 줄바꿈도 가능.

git add .index.js
git commit -m " Feat : create index.js
create index.js for init project"
```

```js
git branch // 생성되어있는 브랜치 확인
git branch -r
git branch -a

git branch stem // stem이라는 브렌치 생성
git branch // 하이라이트가 현재 위치

git checkout stem //  stem으로 현재 위치 변경
git branch // 바뀐 하이라이트 확인

vi index.js // vim에서 insert모드 수정 :wq

git checkout master // 마스터로 변경
git branch

vi index.js // 빈공간인걸 확인. stem에서 수정한거랑은 다른 내용

git merge stem // stem에서 수정한 내역을 현재위치에서 합친다

vi index.js // stemㅇ서 수정한 내용을 merge해서 master에서도 동일한 수정내용이 확인된다.

git branch -D stem // stam이라는 브랜치를 지운다

// 항상 작업할때는.
// 서브브랜치를 만들어서 수정하고 완성되면 master에 merge하고 서브브랜치를 삭제하는 방식으로 작업.
```

## git flow 다른 사람의 레포에 기여를 하려면 !

```js
// merge
```

### commit 메세지 쓸때 :

- Docs : 문서
- Conf : 환경설정
- Feat : 기능

* 헥소 라는 깃헙블로그 테마가 있다. hexo

# 2018-10-19

```js
fork -> clone
git init
git flow init -> enter enter
git flow feature start addcontents
git branch //확인
ls
vi README.md
git  status
git add README.md
git commit -m "~~"
git push origin addcontents
git flow feature finish addcontents
git branch // addcontents라는 브랜치가 없어졌는지 확인
git push origin develop //develp에 푸쉬

repo에 와서 develop 확인 후
리퀘를 날림.

merge가 되면
pull을 받는다

// pull 받는 방법
git remote add pmorigin 깃주소~ // 깃주소에 pmorigin이라는 이름을 저장한다

git remote get-url pmorigin //pmorigin에 저장된 주소 확인

git pull pmorigin develop // pmorigin의 develop 브랜치의 수정사항을  pull

vi README.md // 변경된것 확인
```

```js
// pm이 할일
// master 브랜치에 합칠 때
git branch
git flow release start v1.0.1.20181019
// 버전1.0.1~ 의 test 진행
git flow release finish v.1.0.1.20181019
```

## HEXO

```js
npm install hexo-cli -g // hexo install
hexo init my-first-hexo // my-first-hexo라는 폴더생성
cd my-first-hexo
npm install
hexo server
//hexo 설치 완료

hexo new post "포스트제목"//post 생성
hexo new page //독립된 page 생성
```

```js
// 헥소
hexo clean && hexo generate
hexo deploy
```



# git 협업하기 10-25

```js
git branch feature
git checkout feature 
-작업-
git add, commit 진행
git push origin feature
git checkout develop
git merge feature
git push origin develop
git checkout master
git merge develop
git push origin master
```