# git_guideline (Korean Ver)
some useful command lines for git users

---

### git 개본 개념
 * repository  
  : 프로젝트의 여러 버전을 저장하는 장소 (현 상황을 사진 찍듯이 저장)
  : .git 파일 생성
  
 * commit  
  : commit 당시의 프로젝트 디렉토리의 특정 모습을 하나의 버전으로 남기는 행위 & 결과물 


### git의 세 가지 저장소  
* working directory  
  : 작업하는 프로젝트 디렉토리  
  
* staging area  
  : repository에 올릴 파일들이 존재하는 영역 (working memory와 같은 영역)  
  
* repository 
  : 프로젝트의 여러 버전을 저장하는 장소 (현 상황을 사진 찍듯이 저장)
  : .git 파일 생성
  : working directory의 변경 이력이 저장되어 있는 영역


### git의 workflow
**working directory** --> (git add .) --> **staging area** --> (git commit -m "message") --> **repository **

* git add 파일이름  
  : working directory에서 변경사항이 생긴 파일들을 staging area에 올리는 명령어
* git commit -m "현재 커밋하는 메세지 내용"  
  : staging area에 있는 파일들을 repository에 저장하는 명령어

---

## git 시작하기

### 과정
(초기 설정)
1. git bash에서 로컬 디렉토리로 이동
2. git init : .git 파일 생성
3. git config user.name "사용자이름"
4. git config user.email "사용자이메일"

(commit까지의 과정)
5. git add .
6. (git reset 파일이름)
7. git commit -m "현재 커밋하는 메세지 내용"  
 : 커밋 메세지 내용은 어떤 기능을 추가했는지, 기존에 어떤 문제가 있었는지, 이 기능을 추가함으로써 어떤 효과가 있는지 등으로 구성  


### git 기본 명령어 (commit까지의 과정)
 |명령어|설명|
|------|---|
|**git add** 파일이름|해당 파일을 git add|
|**git add** .|현재 디렉토리 내에서 변경사항이 생긴 모든 파일을 git add|
|**git status**|현 상황을 제시|
|**git reset** 파일이름|staging area에서 해당 파일을 제거|


---


## git 기본 명령어 (commit 이후의 과정)
### [commit 다루기 1 : git log]
 |명령어|설명|
|------|---|
|**git log**|커밋 히스토리|
|**git log --pretty=oneline**|깔끔하게 커밋 히스토리|
|**git log --pretty=oneline** --all|깔끔하게 커밋 히스토리 + 다른 branch의 커밋 모두 제시|
|**git log --pretty=oneline** --all --graph|깔끔하게 커밋 히스토리 + 다른 branch의 커밋 모두 제시 +  graph 그|
|**git show** 커밋번호|해당 커밋에서 어떤 변화가 있었는지 확인|


### [commit 다루기 2 : commit 수정]
 |명령어|설명|
|------|---|
|**git commit --amend**|최신 커밋내용 수정; 파일 수정, git add., git commit --amend|
|**git diff** old_커밋번호 new_커밋번호|두 커밋 간의 차이 보기|
|**git reset** --option 커밋번호|해당 커밋 상태로 가기|


|option|working directory|staging area|repository|
|------|---|---|---|
|--soft|X|X|O|
|--mixed|X|O|O|
|--hard|O|O|O|  

* O: 변경 / X : 변경되지 않음

### [commit 다루기 3 : 기타]
 |명령어|설명|
|------|---|
|**git config alias**.이름|바로가기 명령어 ex) git config alias.history 'log--pretty=oneline'|
|**git tag** 태그이름 커밋번호|커밋에 태그 달기|

---

## git 기타 명령어

### branch 간 이동 시 임시저장 (git stash) 
- 어떤 일을 하던 도중, 다른 branch로 가야할 때
- 잘못된 branch에서 작업하고 있었을 때
 

 |명령어|설명|
|------|---|
|**git stash**|stack에 임시 저장; working directory는 이전으로 돌아감|
|**git stash list**|임시 저장한 파일 리스트 보기|
|**git stash apply** stash@{번호}|임시 저장한 파일 다시 가져오기|
|**git stash drop** stash@{번호}|임시 저장한 파일 리스트에서 지우기|
|**git stash pop** stash@{번호}|임사 저장 파일 다시 가져오면서 리스트에서 지우기 (apply + drop)|


### git cherry-pick
- 필요한 커밋만 가져오기  

### 여러 commit을 하나의 commit으로 만들기
- 마음에 들지 않는 commit을 없애고 싶을 때  
 1. git reset --soft 커밋번호
   : 마음에 들지 않는 커밋의 지전 커밋 번호
   : working directory의 파일을 살려두고, 불필요한 commit들은 지우는 방식 
 2. git add .
 3. git commit

---





