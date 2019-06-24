# 本地仓库
## 切换并且创建一个分支
### `git checkout -b <分支名>`
---
## rebase合并分支，更加干净的提交历史
### 合并分支：当前项目有两个分支，master，bugFix，当我们需要把bugFix合并在master里时，在bugFix分支时输入`git rebase master`然后切换分支到master，然后再次执行`git rebase bugFix`，分支合并完成。
### `git rebase <分支名>`
### demo:
### git rebase master
```
graph BT
bar*-->c1
master-->c1
bar'-->master
```
### git rebase side1 side2
### git rebase side2 side3

```
graph BT
side2-->side1
side3-->side2
```
#### 参数2要在参数1上面
---
## 将其他分支的内容拷贝到当前分支
### `git cherry-pick <提交号>`
---
## 撤销变更
### `git reset HEAD~1`向上移动分支，相当于没有提交过，当然在reset后，所做的变更还在，但是还是处于暂存区状态。
### `git revert HEAD~1`向下会增加一个新的提交，新的提交是用来撤销之前的提交的，但是revert有一个好处可以把我的更改推送到远程仓库与别人分享

# 远程仓库
## 远程分支只有在远程仓库中更新了以后才会更新
## git远程跟踪
### `git checkout -b 分支名 远程仓库/远程仓库的分支`
### `git branch -u 远程仓库/远程仓库名 分支名`
#### 注：如果远程仓库里没有分支名是不能被跟踪的
---
## Git Push的参数
### git push origin master
#### 翻译：切到本地仓库中的master分支，获取所有提交，再到远程仓库origin中找到master分支，将远程分支中没有的提交记录都添加上去
### git push origin bar:tangdy
#### 翻译：把本地的bar分支推送到origin的远程仓库中的tangdy分支，如果没有tangdy分支，则会创建tangdy分支
### git push origin :foo
#### 翻译：通过给push传空值，成功删除了远程仓库的foo分支
### git push origin master:foo
#### 翻译：在本地创建一个foo的分支，从远程仓库中的master分支中下载提交记录，并且合并到foo，然后再merge到我们当前检出的分支上
---