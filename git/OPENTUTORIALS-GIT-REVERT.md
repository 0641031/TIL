## [GIT4 - Reset & Revert ](https://opentutorials.org/module/4032)


### HEAD의 이해

* 현재 우리가 작업하고 있는 working directory가 어떤 비전을 기반으로 수정되어있는지를 보여줌. 

### reset

* 해당 커밋 아이디로 checkout : HEAD를 바꿈.
* git reset : HEAD가 브랜치를 가르키고 있을 때, 브랜치가 가르키고 있는 버전을 바꿈. 그렇지 않은 경우에는 checkout처럼 HEAD를 바꿈. 
* reset을 하든 checkout을 하든 같은 로컬 디렉토리의 상태로 갈 수 있으나
* reset은 log의 기록을 확인해보면 커밋아이디가 삭제되지만, checkout의 경우 브랜치를 여전히 최근 커밋아이디를 가르키고 있음.
* HEAD를 브랜치가 아닌 커밋아이디를 가르킬 경우 : 브랜치로부터 detach 된 HEAD라고 경고를 보내줌.

### reset과 revert 차이

* revert는 해당 커밋을 취소한 새로운 버전을 커밋함.
* git reset --hard commitID : 해당 커밋아이디가 최신 커밋이 됨. 삭제하고 싶은 커밋의 이전 커밋아이디를 입력해야함.
* git revert  commitID : 해당 커밋아이디의 변경사항을 취소한 새로운 버전이 생성.
* reset은 해당 커밋이 삭제되지만 revert는 모든 커밋이 확인 가능. 기록이 남아있음.
* 협업을 하는 경우 reset을 통해 기록을 삭제하면 문제가 발생할 수 있음.

### revert해서 충돌이 발생
* 취소하려고 하는 버전의 commitID가 base가 되고, 그 이전버전과 최근버전으로 3 way merge 하는 과정에서 충돌 발생. 
* git mergetool 사용하여 확인하면 수월함.

