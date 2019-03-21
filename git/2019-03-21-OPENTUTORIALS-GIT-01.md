## 생활코딩 - [지옥에서 온 git](https://opentutorials.org/course/2708)


>이 수업을 듣기 전 git을 써본 경험.
>	1. 학원에서 project를 하며 eclipse로 git을 써봤지만 제대로 썼던 건지 확신이 없다. 뭔가 야매로 썼던 느낌...?
>	2. 혼자 jekyll로 블로그를 만들면서 GUI버전으로 commit, push만 하다가 영 찝찝하여 Git Bash를 설치함.
>	3. repository를 local로 복사하기 위해 [블로그](https://wonjerry.tistory.com/6)를 보면서 fetch와 merge를 두어번 써봄.
>	4. git status, git add . , git commit -m "message", git push origin master 로 블로그 포스팅은 가능했음.



### 수업소개

```
이 수업은 Git의 초심자에게는 기본적인 사용법을 중급자는 Git이 동작하는 원리를
소개해드리기 위한 수업입니다. 

이 수업에서는 명령어를 통해서 Git을 다루는 방법을 소개합니다. 
명령어 기반 Git은 많은 시스템에 기본적으로 설치 되어 있기 때문에 
명령어로 Git을 다룰 수 있게 되면 많은 곳에서 특별한 설치 없이 Git을 사용할 수 있습니다. 

명령어로 Git을 다루는 것이 어렵게 느껴지신다면 GUI로 Git을 다루는 수업을 추천드립니다. 
```

* ls -al : 현재 디렉토리의 파일목록을 보여줌
* mkdir : 디렉토리 생성
* stage area : git add를 통해서 파일을 commit 대기상태로 만들어주는 것을 말함.
* repository : commit이 된 파일들이 저장되는 장소.각각의 commit은 고유의 아이디를 가지고 있음


### git log 뒤로 명령어를 붙여서 동작하는 방법을 바꿀 수 있음

* git log -p : 커밋사이 변경사항을 확인할 수 있음 
* git log commitID : 해당 커밋 이전의 메시지만 볼 수 있음
* git diff commitID..commitID : 해당 커밋 사이의 변경사항을 확인할 수 있음
* git diff : 현재와 그 이전 커밋 사이의 변경사항 확인. push하기 전에 커밋사항을 확인할 수 있음. 


### git commit 취소

* git reset commitID --hard : 해당 커밋 이후의 커밋들이 취소됨. (--hard? --soft라는 것도 있는데 나중에 설명해주신다고 넘어가심.)
* 공유한 repository에서는 reset 하면 안됨!


### git의 원리

* 파일의 이름은 index, 파일은 object 아래에 위치
* git에서는 파일의 이름이 달라도 내용이 같다면 같은 object 파일을 가르킨다. 중복이 되지 않음. index에는 파일이름이 추가되지만 같은 object 파일을 가르킴.
* object 파일명 : sh1 hash를 이용
* tree : 커밋할때마다 다른 트리값이 생김. 커밋당시의 파일 내용을 확인할 수 있음.
* commit : 이전 커밋을 말해주는 parent값이 있고, 커밋이 일어난 시점에 디렉토리에 있는 파일의 이름과 내용의 링크를 갖고 있는 tree값이 생성.
* blob : 파일의 내용을 담고 있음.
* object가 갖고있는 값 : tree, blob, commitID
* staging area = index : git add를 하면 index에 등록됨.
* working directory - index or staging area or cache - repository

gistory라는 프로그램을 설치하고 git의 원리를 설명해주셨는데 해당 프로그램을 다운받을 수 있는 상황이 아니어서 강의만 듣다보니 이해가 안가는 부분이 많았다. 그러려니...넘어감. 





