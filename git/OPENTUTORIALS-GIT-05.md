## 생활코딩 - [지옥에서 온 git](https://opentutorials.org/course/2708)


### git flow

* master에서는 개발을 하지 않고 master에서 파생된 develop이란 브랜치에서 실질적인 개발을 함. 특정 기능을 개발해야 될 때는 feature라는 브랜치를 만들어서 작업을 하다가 develop으로 병합함. 
* 서버에 업로드 하기 위해 release 브랜치를 만든다. 배포 하기 전에 버그의 수정, 문서의 업데이트등도 release브랜치에서 이루어지고 개발을 계속해서 해야하기 떄문에 develop브랜치로 병합함. 
* release브랜치에서 master브랜치로 병합한 내용을 배포. (tag기능 이용) master브랜치는 사용자에게 제공되었던 버전들만 모아놓은 브랜치가 됨.
* hotfixes : 사용자에게 배포후에, 급한 버그 수정 등이 있을 때 사용하는 브랜치. 해당내용은 배포하기 위해 master브랜치로 병합되고, 수정사항 반영을 위해 develop브랜치로 병합함.
* branch를 만들기 전에 pull 해서 최신버전으로 맞춰야함. feature브랜치에서 작업할 때는 develop브랜치의 내용을 수시로 pull해줘야 함. feature브랜치에서 작업이 끝나면 그 때 develop에서 병합.

![git-flow](https://nvie.com/img/git-model@2x.png)


### [.gitignore](https://opentutorials.org/course/1492/8124) 
(해당 부분만 Git GUI에서 따로 수강)

* 버전관리에서 제외하도록 설정.
* 특정 파일, 특정 확장자 설정 가능.
* glob을 이용하여 파일 설정.
* gitignore.io : 개발환경, 에디터 등에 따른 설정 파일 제공 :eyes:




:grey_exclamation: 후에 Git GUI에서 수강한 내용 추가 가능성 있음.




