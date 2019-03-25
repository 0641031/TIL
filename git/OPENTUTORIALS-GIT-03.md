## 생활코딩 - [지옥에서 온 git](https://opentutorials.org/course/2708)


### branch의 원리

* git init으로 처음 생성했을 때 HEAD라는 텍스트파일에 refs/heads/branchname이란 파일명(아직 존재하지 않는)이 적혀있음. 
* 커밋하면 해당 파일이 생성되고 commit한 객체의 ID가 기록됨.
* git log를 하면 : HEAD 확인 - 그 안의 경로로 이동 - 커밋아이디 확인하여 객체 확인 - 커밋객체의 parent확인하면 전체 커밋내용 확인 가능.
* br1이라는 브랜치를 생성하면 refs/heads/br1가 생김. 해당 파일을 지우면 git branch했을 때 표시되지 않음.
* git에서 브랜치는 중요하고 강력하지만 텍스트 파일 하나일 뿐.
* branch를 바꾸면(checkout) 해당 브랜치의 최신 commit내용을 가르키기 위해 HEAD 파일이 업데이트 됨.


### reset, checkout의 원리

* git은 웬만하면 정보를 완전히 삭제하지 않음. 그저 사람의 눈에 보이지 않을 뿐...
* reset을 취소하고 싶다면? ORIG_HEAD파일에 삭제한 commit 객체가 있고, logs/refs/heads/master를 확인해보면. reset하면서 commit객체가 어떻게 변경되었는지도 확인 가능.
* git reset --hard ORIG_HEAD 하면 reset취소.
* git reflog : HEAD 변경 이력 확인 가능.
* git checkout commitID : detached HEAD state, git branch하면 커밋아이디를 가르키고 있음. HEAD 파일이 직접 커밋아이디를 가르키고 있음. 


### reset으로 알아보는 working copy, index, repository

* working directory : working tree, working copy
* index : staging area, cache
* repository : history, tree
* git reset 하고 별도의 명령어를 주지 않으면 기본 --mixed로 동작.
![git_reset_img](https://i.imgur.com/zv62NMm.png)
* git diff 로 차이점 확인.


### merge, conflict의 원리

* 충돌이 일어났을 때, git의 내부 : 
	1. index : 커밋아이디 옆에 숫자가 붙음. 커밋한 순서대로.
	2. MERGE_HEAD : 병합이 될 대상의 최신 커밋아이디.
* 병합을 전문적으로 도와주는 프로그램 : kdiff3
	> git config --global merge.tool kdiff3
* base(공통적인 부분), local(checkout된 브랜치), remote(merging을 당하는 쪽), output(자동으로 병합이 불가능한, 충돌이 일어난 부분을 보여줌) 을 한 화면에서 확인하면서 코드수정 가능.


### 3 way merge

	![git_3way_img](https://i.imgur.com/xv9SwWW.png)
* 2 way merge : Base를 확인하지 않고 두 개의 파일을 병합.
* 3 way merge : Base를 참고로 하여 두 개의 파일을 병합. 수정 사항이 있는 쪽을 채택.
