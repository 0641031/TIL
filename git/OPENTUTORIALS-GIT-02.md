## 생활코딩 - [지옥에서 온 git](https://opentutorials.org/course/2708)


### git log 뒤로 명령어를 붙여서 동작하는 방법을 바꿀 수 있음

* git log -p : 커밋사이 변경사항을 확인할 수 있음 
* git log commitID : 해당 커밋 이전의 메시지만 볼 수 있음
* git diff commitID..commitID : 해당 커밋 사이의 변경사항을 확인할 수 있음
* git diff : 현재와 그 이전 커밋 사이의 변경사항 확인. push하기 전에 커밋사항을 확인할 수 있음. 


### git branch

* git branch : branch의 이름이 나와있고 해당 브랜치 이름 앞에 ‘\*’가 붙음.
* git brach brachname : 브랜치 생성
* git checkout branchname : 브랜치 변경
* 브랜치를 생성하면 현재 속해있는 브랜치의 상태를 그대로 갖게 된다.
* 브랜치들의 log를 한 번에 볼 수있고, HEAD -> 현재 체크아웃 된 브랜치이름이 나옴. --decorate를 추가함으로써 브랜치별로 구분이 가능.
	> git log --branches --decorate
* 브랜치들의 log를 시각적으로 보여줌.
	> git log --branches --decorate --graph
* sourcetree라는 GUI 툴로도 확인 가능. (회사에서 써봤는데 좀 무거운 것 같다.)
* br1과 br2브랜치들의 차이를 말해줌. br1에는 있고 br2에는 없는 것들 보여줌. 2에는 있고 br1에는 없는 것을 확인하기 위해서는 순서를 바꾸면 됨. 
	> git log br1..br2
* source code까지 확인하고 싶다면
	> git log -p br1..br2
* 각각의 브랜치들의 현재 상태를 비교할 수 있음
	> git diff br1 br2


### branch 병합

* 병합 하고싶은 브랜치로 체크아웃 (br1) 
* git merge br2(병합의 대상이 되는 브랜치)하면 해당 액션을 커밋하는 창이 나옴. 
* git branch -d branchname : 브랜치 삭제
* git branch -D branchname : 브랜치 강제 삭제


### [Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

* br3이란 브랜치를 만들면서 동시에 체크아웃
	> git checkout -b br3
* master가 브랜치를 만든 시점 이후에 다른 브랜치와 병함한 경우 fast forward가 불가능함 : recursive strategy라는 메세지가 출력. 
* 공통의 조상을 찾아서 three-way merge 사용 : 공통의 조상 이후에 생긴 변화에 대하여 브랜치들을 병합하는 별도의 커밋을 생성. 
* fast forward는 커밋을 생성하지 않음.


### Conflict while merging

* 같은 부분 수정할 때 충돌함
* 충돌하는 파일을 확인
* ======== 구분자를 중심으로 위쪽의 <<<<<<<HEAD 부분이 현재 브랜치의 내용이고 하단의 >>>>>>branch 내용이 branch의 내용
* 해당 파일을 수정하고 위의 기호들을 삭제하고 커밋하면 충돌했던 내역을 보여주고 병합이 되면서 커밋됨.


### stash

* 감추다, 숨겨 두다.
* 브랜치에서 하던 일이 끝나지 않았는데 다른 브랜치로 체크아웃 해야되는 경우, 하던 작업을 커밋할 수는 없기 때문에 stach로 하던 작업을 숨겨두고 다른 브런치로 체크아웃 할 수 있게 하는 것. 브런치를 사용하지 않을 경우, 굳이 공부하지 않아도 됨.
* 파일을 공유하고 있기 때문에 브랜치에서 하는 작업이 다른 브랜치에도 영향을 줌.
* working derectory와 index에 저장됨.
	> git stash (save)
* git status 하면 nothing to commit
* 하던 작업을 불러옴.
	> git stash apply
* stash한 리스트가 나옴.
	> git stash list
* stash list를 명시적으로 삭제하지 않는 이상 항상 살아있음. reset을 해도 stash list는 사라지지 않으므로 불러올 수 있음.
* 가장 최신 stash를 삭제
	> git stash drop
* git stash pop : git stash apply + git stash drop
* stash는 버전관리가 되고있는 파일에 대해서만 사용 가능. 







