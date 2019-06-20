### git amend

commit message를 수정할 때, 사용함.

```
git commit --amend
```
라는 명령어를 입력하면 수정할 수 있는 화면이 나온다.
git bash에서는 기본 텍스트편집기로 vi라는 것을 사용하는데, 처음에는 이 화면이 편집기인지도 몰랐고 사용방법도 몰라서 엄청 헤매다가
생활코딩 git 강의를 듣고나서야 사용할 수 있게 되었다. :

i를 누르면 edit mode가 된다. 수정을 하고나서 esc를 눌러 edit mode를 종료하고 :을 입력하여 명령어를 입력할 수 있는 상태로 변경. 
그 후에 저장을 의미하는 w와 종료를 의미하는 q를 같이쓰면 수정 끝!

바로 수정하고 싶을 때는,
```
git commit --amend -m "commit message"
```



###### reference
* [Git에 Commit 메시지를 다시 수정하는 방법](https://webisfree.com/2017-02-15/git%EC%97%90-commit-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%EC%88%98%EC%A0%95%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95)