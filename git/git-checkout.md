### git checkout


1. 브랜치를 변경할 때

```
git checkout [변경하고자 하는 브랜치 이름]
```

브랜치 작성과 변경을 동시에 하려면

```
git checkout -b [브랜치 이름]
```


2. 변경사항 폐기할 떄

브랜치를 변경할 때만 쓰는 명령어인 줄 알았는데, staging에 올리지 않은 파일의 변경사항을 폐기하는 명령어로도 쓰인다.

```
git checkout [파일 이름]
```

레포지토리 전체의 변경사항을 폐기하려면 `.` 특정 디렉토리 이하의 모든 변경사항을 폐기하려면 디렉토리 이름을 입력하면 된다.


###### reference
* [http://hochulshin.com/git-revert-changes/](http://hochulshin.com/git-revert-changes/)