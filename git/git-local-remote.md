### git local과 remote에서 작업하며 생긴 일

* 로컬에서 작업하고 commit, push한 다음에 pull request는 아직 안한 상태.
* github에서 amend를 했었나...? 정말 기억이 안난다...(저번주)
* 오늘 추가작업 하기 전에, develop 브랜치에 변경사항이 많았기 때문에 pull하고 추가 작업을 한 다음에 push하는데 에러가 발생.
* git push -f 해도 될 거 같은데... 근데 에러가 왜 생기지? pull할 게 없는데 왜 자꾸 pull하라는 거야..?


동료한테 물어봤는데, tree를 보더니 amend했냐고 물어봤다. 근데 정말 기억이 안났다...

![git-local-remote](https://i.imgur.com/CqAPOFy.png)


추가작업을 하기 전, 해당 브랜치의 최신 내용은 remote브랜치에 있는 BBB라는 커밋이기 때문에,
CCC를 push하기 전에 BBB를 pull하라는 거였다. amend도 커밋 아이디를 생성하기 때문에 파일 내용에는 변경사항이 없지만
다른 커밋이 있으니 최신내용 반영한 다음, push하라고 알려주는 것. 안그럼 최신작업내용 다 잃어버리게 되니까.


항상 로컬에서 커밋하고 리모트로 push만 해봤지, 리모트브랜치에서 뭘 해본적이 없어서 몰랐는데
트리에 로컬과 리모트의 브랜치는 다른 브랜치로 나온다. 색깔이 다름...내가 로컬브랜치의 트리 내역만 보다보니까
왜 에러가 나는지도 모르고, git fetch해도 pull할게 없다고만 나왔던 거다. 

bash에서 tree보려면 setting을 하면 되는데,

```
git config --global alias.tree "log --graph --decorate --pretty=oneline --abbrev-commit"
```

하고 `git tree`로 트리확인 가능하다. ~~sourcetree 보겠지만~~


###### reference
* [Git not-fast-forward errors after git commit --amend
](https://stackoverflow.com/questions/21316534/git-not-fast-forward-errors-after-git-commit-amend)