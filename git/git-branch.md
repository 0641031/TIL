### git branch

상황은,
1. feature아래 a 브랜치에서 작업을 하다가 다른 작업요청이 들어왔다. 기억은 나지 않는데… 아마 stash를 하고 feature아래 b를 만들고 작업을 하고 commit - push 했다. 
2. pr을 하려고 보니… a 브랜치의 커밋이 내가 b에서 한 commit 아래로… 보이는 것이다.

검색어 뭐라고 하지... 이것저것 시도하다가 `git checkout to another branch and pushed i found former commit log`으로 해답을 찾았다.:stuck_out_tongue_closed_eyes: ~~문법 신경쓰지 말고 때려넣다보면 나온다...~~

[https://stackoverflow.com/questions/37010110/git-pushes-old-commit-in-different-branch-to-new-branch](https://stackoverflow.com/questions/37010110/git-pushes-old-commit-in-different-branch-to-new-branch)

---


처음 git을 접한 건, 학원에서 세미 프로젝트를 할 때였는데 하다가 때려쳤었다. 그때는 브랜치를 사람? 계정?이라고 생각했던 것 같다. 각자 한 작업을 브랜치를 통해서 업데이트하는… 

branch는 작업의 라벨정도라고 생각하면 가장 적합할 것 같다. 


기본적으로 HEAD가 브랜치를 가르키고, 브랜치가 커밋을 가르킨다. HEAD를 보면 내가 현재 작업하고 있는 working directory가 어떤 버전을 기반으로 되어있는지 알 수 있다. 

![git-branch-01](https://i.imgur.com/xdo6gmK.png)

work1에서 작업하고 commit하고 work2로 브랜치 생성하여 체크아웃하고 git log를 찍었을 때 화면이다. HEAD는 현재 체크아웃 된 work2 브랜치를 가르키고, work1을 기반으로 하고 있음을 확인 할 수 있다.


위와 같은 상황이 발행하게 된 원인은 나의 착각인데, 그림으로 그려보자면 

![git-branch-02](https://i.imgur.com/9B9eZsu.png)

이러하다. 나는 상단의 그림처럼 test_feature의 하부에 브랜치를 만들었으니까 당연히 test를 기반으로 하는 브랜치를 만들었다고 착각을 한거다. 실제로는 하단의 그림과 같은 흐름으로 작업을 했고. 만약 내가 생각한대로 상단의 그림처럼 하고 싶었다면 다시 test브랜치로 체크아웃을 하고 거기서 test_feature/work2 브랜치를 만들었어야 한다. 


내가 했던 방식으로 작업하고 pr을 하려고 할 때 나오는 모습인데,

![git-branch-03](https://i.imgur.com/sjgGDJT.png)

develop브랜치에서 test브랜치를 만들어서 체크아웃 했기때문에 둘의 버전이 같다. 그리고 test브랜치에서 work1를 만들었기 때문에, 그 이후에 pr하려는 브랜치(위 그림에선 develop) 에 반영되지 않은 커밋내용이 전부 나오는거다. 
(new pull request해서 브랜치를 임의로 선택하고 pr대상을 master로 해보니 적용안된 commit아이디가 엄청 뜨는거 보고 알았다.)

결국은 브랜치의 문제이기 보단 브랜치 상태(버전)의 문제다. 

그래서 해결은.. cherry pick으로 했다. develop에서 새로운 브랜치를 만들고, work2에서 작업한 커밋을 가져와서 push를 했다.
위의 stackoverflow에서는

```
git rebase --onto master feature/feature1 chore/update-framework
```

이 방법을 가르쳐주는데… rebase를 아직 이해를 못했다… 역시 경험해보지 않으면 이해가 힘들다…

