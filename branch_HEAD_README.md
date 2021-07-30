# branch_HEAD_guideline (Korean Ver)
branch와 HEAD와 관련된 내용 정리

---

## HEAD
* HEAD는 어떤 커밋 하나를 가리킴  
* deafult) 가장 최근에 한 커밋을 가리킴
* HEAD가 가리키는 커밋을 변경할 수 있음; 이에 따라 working directory가 구성됨
  -> git reset --hard/mixed/soft 커밋번호  
  -> git reset --hard/mixed/soft HEAD^ ; HEAD 직전으로 이동
  -> git reset --hard/mixed/soft HEAD~2 ; HEAD보다 2단계 전으로 이동
  
|option|working directory|staging area|repository|
|------|---|---|---|
|--soft|X|X|O|
|--mixed|X|O|O|
|--hard|O|O|O|  
- O: 변경 / X : 변경되지 않음  


---


## Branch
### [Branch]
* 하나의 코드 관리 흐름 
 ex) free version branch (usually master branch) & premium version branch
 
 * master branch : 가장 처음 commit을 하면 자동으로 생성되는 branch  
 
 |명령어|설명|
|------|---|
|**git branch** branch이름|branch 만들기|
|**git checkout** branch이름|해당 branch로 이동하기|
|**git checkout** -b branch이름|해당 branch 생성 + 그 branch로 이동|
|**git branch** -d branch 이름|해당 branch 삭제|
|**git branch**|branch 리스트|


---


### [HEAD와 Branch 간 관계]
   * branch : commit을 가리키는 포인터  
   * HEAD : branch를 통해 commit을 가리키는 포인터  
   : HEAD -> Branch -> Commit  
   ![head&branch](https://i.stack.imgur.com/eAo7u.png)
   
   #### exercise 1
   1. git branch premium  
   2. git checkout premium  
   3. commit  
   4. git checkout master  
   5. commit  
   6. git merge premium  
   
 ![image](https://user-images.githubusercontent.com/48611663/127634379-806c4eea-ba54-4baa-88e2-1633ef966525.png)


---


 ### [Deatched HEAD]
   : branch에서 떨어진 HEAD  
   : 과거의 특정 커밋에서 새로운 branch를 만들고 싶을 때 사용  
   
   (exercise)
   1. git checkout a  (detached HEAD)
   2. git branch premium  
   3. git checkout premium  
   4. git commit  
   
   ![image](https://user-images.githubusercontent.com/48611663/127618683-c7069244-1ee2-46dd-9766-7385b78979c3.png)


---


### [Branch Merge 1]
 - 하나의 branch 기능을 다른 branch에서 모두 반영  
 - HEAD가 가리키던 커밋에 다른 branch가 가리키던 commit을 합쳐서 새로운 commit을 만드는 작업

 ex) premium version이 free version(master)이 제공하는 모든 기능을 포함해야할 때
 1. git checkout premium
 2. git merge master


```
   [주의사항] 
   CONFLICT : Merge 시 나타날 수 있는 충돌 현상 / Merge하는 branch 내 파일들에 차이가 있을 때 발생  
  ```

```
   [해결방법 1]  
  1. 해당 파일에 가서, 문제 부분을 해결
  2. git add .
  3. git commit -m ""
```

```
   [해결방법 2] Merge 취소
  git merge --abort
```  
  
* Merge 종류  
   1. fastforward merge  
    : branch가 안 갈라져 있을 때  
    
   2. 3-way merge  
    : base branch를 기준으로 변화가 많은 쪽으로 merge   
   cf) 만약 두 branch 모두 base와 다른 때로 변화한다면, CONFLICT가 일어남  


  ### [Branch 명령어 예시]
  - git remote add origin remote_repository_주소  
   : remote repository의 주소를 origin이라는 이름으로 등록함 (origin remote repository)  
   : origin이란; remote resitory를 최초로 추가할 때  
   
  - git push -u origin master  
   : 현재 local repository에 있는 master branch의 내용을 origin remote repository에 보냄

  ** git reset --option 커밋번호 : branch를 움직이는 명령어
  ** git checkout 커밋번호 : HEAD를 움직이는 명령어


---


  ### [Branch rebase]
  - git rebase branch이름
  ex) git rebase premium
  - Merge가 아닌, branch 자체를 옮김  
  - Merge와 달리 새로운 커밋을 만드는 것이 아니기 때문에, 더 간단하다는 장점이 있음  
  
---
