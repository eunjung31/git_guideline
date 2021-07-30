# github_guideline (Korean Ver)
some useful command lines for github users

---


## 기본

### [Notations]
 * local repository : 내 컴퓨터의 repository
 * remote repository : github repository


### [local repository를 remote repository에 올리기 (처음)]
 1. git remote add origin 웹페이지주소
 2. git push -u origin master


### [local repository의 변경사항을 remote repository에 반영하기]
 1. git add .
 2. git commit -m "현재 커밋하는 메세지 내용"
 3. git push


### [remote repository 변경사항을 local repository에 반영하기]
 1. git pull

- git pull, git push는 그 작업 단위가 branch임. 예를 들어, master branch에서 git push를 하면 master branch의 내용만 remote repository의 master branch로 전송됨
   
---
 
 ## Git 실무지식
  ### Local Repository와 Remote Repository의 내용이 다를 경우    
   1. git pull  => error 발생 ; local이 remote의 내용을 덮어쓰지 않게 하기 위함  
   2. 문제 해결 (CONFLICT 해결방법처럼)  
   3. git push  

   |명령어|설명|
|------|---|
|**git fetch**|데이터를 가져오되, merge는 하지 않음; git pull은 데이터를 가져온 후, merge|
|**git diff** 커밋번호A 커밋번호B|A와 B 내용 차이를 살펴보기; ex) git diff premium origin/premium; origin/premium은 remote repository를 의미|



  ### 이 코드는 누가 작성했을까?  
|명령어|설명|
|------|---|
|**git blame**|코드 작성 정보; 작성자, 작성일시 등|
|**git show** 커밋아이디|해당 커밋의 자세한 내용 제시|


 ### git revert   
 
   |명령어|설명|
|------|---|
|git revert 커밋번호|remote에 올라간 해당 커밋번호를 되돌림|
|git revert A..B|여러 개의 커밋번호를 취소하기|
|git reflog|코드 작성 정보; 작성자, 작성일시 등|
|git reset 커밋번호|만약 git reset을 하고 난 후, 해당 커밋으로 다시 돌아가고 싶을 때|
