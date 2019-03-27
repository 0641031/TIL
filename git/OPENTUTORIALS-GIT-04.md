## 생활코딩 - [지옥에서 온 git](https://opentutorials.org/course/2708)


### Remote Repository

* git init --bare directoryname : 원격저장소를 만들 때 사용. 작업은 할 수 없고, 저장소로서의 역할만 수행함.
* 현재 저장소에 원격 저장소를 추가.
	> git remote add 원격 저장소 경로
* local -> remote로 push
	


### github에 있는 프로젝트를 local로 가져오기

* git clone
	> git clone 복사할 repository 주소
* git log --reverse : log를 거꾸로 볼 수 있다.


### local저장소를 github 원격저장소에 연결

* 로컬저장소에 해당 주소의 원격저장소를 origin이란 이름을 붙여서 연결
	> git remote add origin remote저장소의 주소
* git remote 라는 명령어로 원격 저장소 확인 가능
* 로컬저장소의 내용을 원격 저장소로 push. -u를 한번쓰면 다음부터 git push까지만 써도 됨.
	> git push -u origin master 


### github 원격저장소를 로컬저장소로 clone

* remote주소 뒤에 .은 현재 디렉토리라는 뜻. 현자 디렉토리가 아닐경우 디렉토리 이름을 적으면 됨.
	> git clone remote주소 .
* 마지막 commit 메세지 변경가능
	> git commit --amend 
* git pull : 원격저장소의 내용을 로컬저장소로 땡겨온다. 작업을 하기전에 git pull, 작업완료하고 git push 하는 것을 생활화
	


### SSH (Secure Shell)

* 운영체제 상관없이 $ ssh-keygen (경로체크)
* command line에서 \~는 홈디렉토리
* 해당명령어로 public key, private key가 생성됨. public key 파일을 접속을 원하는 컴퓨터 서버의 특정 디렉토리에 복사. 로컬에 private key가 있기 때문에 public key가 저장되어있는 컴퓨터에 접속할 때 안전하게 자동로그인.


### git remote의 원리

* 원격저장소 생성 시 : .git/config 파일이 변경됨. 원격저장소의 이름, url, fetch정보가 등록.
* 로컬저장소와 연결 시 : .git/config 파일에 연결 정보가 등록. refs/remotes/origin(원격저장소이름)/master(원격저장소에 push한 branch)에 push한 커밋에 대한 정보가 등록. 
* 로컬저장소에서 commit을 할 경우, refs/heads/master의 내용만 변경되므로, ref 하위의 파일의 내용에 따라 로컬저장소와 원격저장소의 차이를 알 수 있음. 


### difference between git pull and git fetch

* 모든 브랜치의 로그 확인
	> git log --all
* git pull 했을 때 : refs 하위의 master와 origin/master가 같은 커밋을 가르키고 있음. ORIG_HEAD는 직전의 커밋을 가르키고 있기 때문에, 병합하기 이전 상태로 되돌릴 수 있음.
* git fetch 했을 때 : refs 하위의 origin/master 파일만 최신 커밋을 가르키는 상태로 수정됨. 로컬저장소에는 아무런 변화가 없음. (직전의 커밋을 가르키는 상태)
* 해당 명령어로 병합 전에 HEAD(로컬저장소의 브랜치, 여기선 master)와 origin(원격저장소)의 차이점을 확인할 수 있음.
	> git diff HEAD origin
* 병합을 하면 git pull 했을 때 처럼 refs/heads/master도 최신 커밋을 가르키는 상태가 됨.
	> git merge origin/master
* git fetch는 원격 저장소로부터 필요한 파일을 다운로드만 받은 상태. 그렇기 때문에 바로 병합을 해줘야 함. git pull은 다운로드 받고 병합까지 완료한 상태. 
