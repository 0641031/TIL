### git reset head

여러 파일을 수정하고 생각없이 `git add .`했을 때, commit 메세지를 따로 남기기 위해 staging에 올라간 파일들을 되돌리는 방법!

```
git reset HEAD [file]
```
staging에 올라간 파일 중 특정 파일만 제외하고 싶으면 file이름을 적으면 되고, 그렇지 않은 경우에는 add 했던 모든 파일이 취소됨.




###### reference
* [git add 취소하기(파일 상태를 Unstage로 변경하기)](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)
