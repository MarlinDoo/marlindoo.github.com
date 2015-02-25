---
layout: page
title : Git最常见的16个问题
header : Post Archive
---
## How to edit an incorrect commit message in Git
## 问题一：Git的commit message写错了，如何修改呢？

If the commit is the last one:
最后一次提交如下：

    git commit --amend -m "New commit message"

You can also use rebase to edit the commit messages – choose ‘reword’ for the commits you wish to edit.
这时可以使用rebase命令编辑提交的信息 - 选择“改写”你要编辑的commits。

    git rebase -i HEAD~5  # Rebase the last 5 commits

    git rebase -i HEAD~5  # 重置最后5次提交

Warning: Doing a rebase does change the commit history – it changes the SHA of commits – so do not rebase a commit that has already been published otherwise you will end up with duplicated commits when your team merges your branch with their own branch.

注意：使用rebase会修改提交的历史 - 也会改变提交的SHA值 - 因此不要对已经发布的提交做rebase操作，否则当你的团队合并你的分支到他们的分支时，同时会合并入你的重复提交。（译注：同样变更有了不同的版本）

Protip: You can ignore that rule if you are working on a feature branch and you are about to merge your work with master and you just want to clean up things. Since you are going to be merging to master and then deleting the feature branch nobody is going to be affected. It is actually a good practice to do that in such a case.

提示：如果你正在使用功能分支开发，这个分支将被合并到master分支，并且你只是想清理提交的信息，这时你完全可以忽略上面的规则。因为功能分支终将合并到master分支，然后会被删除，这不会影响到任何人。在这种情况下，这实际上是一种很好的做法。

Trivia: You can’t rebase the first commit of a repository, unless you pass the --root option.
其它：除非传入--root参数，否则不可以对仓库的第一次提交进行rebase操作。

## How to undo the last Git commit
## 问题二：如何取消最后一次提交

    git reset --soft 'HEAD^'

Protip:
提示：为该命令分派一个别名

    git config --global alias.undo-commit 'reset --soft HEAD^'
    git undo-commit

## How to delete a git branch both locally and remotely:
## 问题三：如何同时删除本地和远程的git分支

    git push origin --delete <branchName>

## What is the difference between ‘git pull’ and ‘git fetch’
## 问题四：'git pull'和'git fetch'的区别

git fetch: Updates your local repository with the data from remote.
git pull: Updates your working copy with the changes in the remote.

git fetch: 将远程仓库数据更新到本地仓库。
git pull: 将远程仓库变化部分更新到当前工作目录。

In practice: If you want to get the changes from remote without immediately changing your working copy then use git fetch. Otherwise use git pull. git pull does a git fetch followed by a `git merge.

实践：如果你需要获取远程仓库的变化并且不需要立刻更新工作目录，则使用git fetch。否则，使用git pull。git pull相当于git fetch后再执行git merge。


## How to undo ‘git add’ before having commited
## 问题五：在提交前，如何取消'git add'操作

    git reset <file>
    git reset # omit the file in order to reset all of them

Protip:
提示：可以这样为reset HEAD -- 分派别名

    git config --global alias.unstage 'reset HEAD --'
    git unstage <file>

## How to merge a Git conflict
## 问题六：如何合并冲突

A conflict in Git occurs when two branches happen to modify the same area of code. Say you have a branch A:
同时在两个分支中修改同一区域的代码，会产生冲突。假设你有一个分支A：

    # John renamed this method to:
    def john_is_the_best
    end

…while branch B have this code in the same line:
...同时分支B在同一行有这样一段代码：

    # Jaime renamed this method to:
    def jaime_is_the_best
    end

In such case Git is not capable of merging both changes because Git can’t possibly know which one to choose. Your manual intervention is necessary and that is what we call a Git conflict. Git merging tools will markup areas in your code with conflict markers.
在这种情况下，Git不知道该选择哪一个代码，因此Git不能合并这些变化。这种情况我们称之为Git冲突，需要我们手工干预解决。Git合并工具将在你的代码中使用冲突标志标示出冲突区域。

After seeing a conflict, you can do two things:
当发现有冲突，你可以做两件事：
Decide not to merge. git merge --abort can be used for this.
决定不做合并。git merge --abort可以被用来放弃合并。

Resolve the conflicts. Git will mark the conflicts in the working tree. Edit the files into shape and git add them to the index. Use git commit to seal the deal.
解决冲突。Git将在工作树上标示冲突。编辑这些文件恢复正常，最后像往常的提交一样先add再commit即可。

    Protip:
    git config merge.conflictstyle diff3 # Uses diff3 conflict markers.

    提示：
    git config merge.conflictstyle diff3 # 使用diff3来标记冲突。

Anatomy of a conflict marker:
冲突标记剖析：

    <<<<<<<
    Changes made on the branch that is being merged into. In most cases,
    this is the branch that I have currently checked out (i.e. HEAD).
    |||||||
    The common ancestor version. This is what the common ancestor looked like. This is useful because you can compare it to the top and bottom versions to get a better sense of what was changed on each branch, which gives you a better idea for what the purpose of each change was.
    =======
    Changes made on the branch that is being merged in. This is often a
    feature/topic branch.
    >>>>>>>

    <<<<<<<
    已经合并分支中的变化内容。在大多数情况下，这就是我们当前签出的分支（即HEAD）。
    |||||||
    共同的父级版本。这是共同的先前版本看起来的样子。你可以通过将其与上面的和下面的版本进行比较，从而更明了每一个分支中的变化，这也将让你了解每个变化的目的。
    =======
    要合并过来的分支上的变化部分。这常常是一个功能/主题分支。
    >>>>>>>

Following the example, if we try to merge John’s branch in Jaime’s branch we would have had:
下面的例子中，如果我们尝试合并John的分支到Jaime得分支，我们不得不进行下面的判断：

    <<<<<<< HEAD
    def jaime_is_the_best
    ||||||| merged common ancestors
    def who_is_the_best?
    =======
    def john_is_the_best
    >>>>>>> john

    <<<<<<< HEAD
    def jaime分支是最好的
    ||||||| 合并后的共同父级
    def 哪一个分支是最好的?
    =======
    def john分支是最好的
    >>>>>>> john

Understanding the intention behind each diff block is generally very helpful for understanding where a conflict came from and how to handle it.
了解了每个区块差异的目的，对于理解冲突的产生以及如何处理冲突非常有帮助。

This shows all of the commits that touched that file, considering just changes in between the common ancestor and the two heads you are merging, so it doesn’t include commits that already exist in both branches before merging. This helps you ignore diff blocks that clearly are not a factor in your current conflict.
这显示了所有有关这个文件的提交，考虑共同父级与两个正在合并的头之间的变化，这里没有包含两个分支合并前就已经存在的提交。？？？这将帮助你忽略掉明显不是当前冲突原因的差异代码块。

    git log --merge -p <name of file>

After resolving the conflicts, it is a very good practice to test that you didn’t broke anything. Run your automated test suite.
解决冲突之后，这里有一个非常好的方法来确认你没有搞砸。运行你的自动化测试工具。

The easiest conflicts to solve are the ones that never happened:
最容易解决的冲突之一是不发生冲突：

Talk to your team and if you anticipate that some of you are going to be doing extensive modifications to a single file consider instead working sequentially – one of you make your changes first, and the other can work on the top of said changes. No conflicts.
如果预期团队成员会有多人对一个程序文件做大量修改，这种情况下需要告诉团队成员按照先后顺序工作 - 一个成员先修改，其他成员在这次修改的基础上在进行修改。这样就不会产生冲突。

If working in parallel is a must, then merge assiduously; that way you will catch conflicts sooner than later – and so will be smaller and fresher in the memory of both parties involved.
如果并行工作是必须的，那就需要认真的合并；在这种方式下，遇到冲突越早解决越好 - 趁着冲突规模很小，并且双方当事人的记忆还很清楚。
If there is something worse than a difficult merge is a merge that went wrong but got commited anyways. If you find yourself unable to resolve the conflicts with confidence, do not merge, instead abort the merge with git merge abort and talk to your team on how to best tackle it.
如果有比难以合并还糟糕的事情，那么归并错误并且还提交了算是一个。如果你发现自己没能力解决冲突，那么就不要做归并，通过"git merge abort"放弃归并，然后与团队商量如何能更好的解决冲突。

## How to clone all remote branches with Git
## 问题七：如何使用Git克隆所有远程分支

    git remote update
    git pull --all

## How to remove all untracked files in Git
## 问题八：如何在Git中删除所有未跟踪的文件

    git clean -f # Remove all untracked files.
    git clean -f -d # Remove all untracked files and directories.
    git clean -f -X # Remove just ignored files.
    git clean -f -x # Remove all untracked and ignored files.
    Protip:
    Use the --dry-run option in order to preview changes.

    git clean -f    # 删除所有未跟踪的文件。
    git clean -f -d # 删除所有未跟踪的文件和目录。
    git clean -f -X # 仅删除忽略的文件
    git clean -f -x # 删除所有未跟踪及忽略的文件
    Protip:
    使用 --dry-run 参数可以预览变化。

## How to remove a git submodule
## 问题九：如何删除一个git子模块

    git submodule deinit <name>

## How to make an existing Git branch track a remote branch
## 问题十：如何使现有Git分支跟踪远程分支

    git branch -u upstream/foo foo # you can omit the last 'foo' if you are already in that branch.

    git branch -u upstream/foo foo # 如果已经在分支中，你可以忽略最后的'foo'

## How to do a “git export” (like “svn export”)
## 问题十一：如何像svn导出一样导出git

    git archive --format zip --output name.zip master

## How to rename a local Git branch
## 问题十二：如何给本地Git分支重命名

    git branch -m <oldname> <newname> # You can skip oldname if you want to rename the current branch.

    git branch -m <oldname> <newname> # 如果给当前分支重命名，可以忽略旧分支名称

## How to add an empty directory to a git repository
## 问题十三：如何给git仓库添加一个空目录

Currently the design of the git index (staging area) only permits files to be listed. Directories are added automatically when adding files inside them. That is, directories never have to be added to the repository, and are not tracked on their own.

目前，gix索引（暂存区）被设计为只允许查看文件列表。当添加文件到目录中时，目录才被自动添加。也就是说，目录本身不会被添加到仓库，并不会被跟踪。（？？）

If you really need a directory to exist in checkouts you should create a file in it. For example a .gitignore file; you can leave it empty.

在签出工程时，如果真的需要生成一个目录，则必须在目录中创建一个文件。例如，创建一个.gitignore文件；这样可以保持目录为空。

## How to checkout a remote branch
## 问题十四：如何签出远程分支

Checkouts a branch named my_branch that exists in any of the remotes.
签出远程存在的任何一个分支，并命名为my_branch。

    git checkout my_branch

If multiple remotes have branches with the same name you will get an error – in which case you need to use the next form.
如果多个远程仓库中有相同名字的分支，则会git会报错 - 在这种情况下，需要使用下面的命令。

Protip:
Use the next form to checkout a branch named my_branch that exists in the remote named 'origin'
提示：
使用下面的命令将远程一个叫做“origin”的分支签出，并命名为my_branch分支。

    git checkout origin/my_branch

## How to revert to previous Git commit
## 问题十五：如何恢复到上一次提交状态

There are two cases:
有下面两个场景：

If you have published it already:
如果你已经发布：

    git revert commit_sha
    git revert commit_sha1 commit_sha2 commit_sha3 # Three commits are reverted in 3 separate commits
    git revert HEAD~2..HEAD # Revert a range of commits. Each commit will have is own revert commit.

    git revert commit_sha
    git revert commit_sha1 commit_sha2 commit_sha3 # 三次提交将被恢复为三次独立的提交
    git revert HEAD~2..HEAD # 还原一系列提交。每次提交都有其还原提交。

If you haven’t publish it already
如果你还没有发布：

    git reset commit_sha # The one you want to revert to.
    Protip:
    If you have staged changed and you don't want to keep them use the `--hard` option.
    git reset --hard commit_sha

    git reset commit_sha # 需要恢复的提交SHA
    提示：
    如果你不想保留变化部分的内容，可以使用 `--hard`参数
    git reset --hard commit_sha

## How to force git to overwrite local files on pull
## 问题十六：如何使用pull强制覆盖本地文件

Update from remote.
从远程更新。

    git fetch --all

Reset the master branch to what you just fetched. The --hard option changes all the files in your working tree to match the files in origin/master, so if you have any local changes, they will be lost. With or without --hard, any local commits that haven’t been pushed will be lost.
把你刚刚获取的分支使用主分支重置。 使用 --hard 选项将你的工作树中所有的文件更新，与 origin/master一致，这样本地的修改将丢失。有无 --hard选项，本地没有发布的提交豆浆丢失。

    git reset --hard origin/master

## How to stash only one file out of multiple files that have changed
## 问题十七：当多个文件都被修改时，如何忽略其中一个文件
This will stash everything that you haven’t previously added. Just git add the things you want to keep, then run it.
这个操作将忽略所有你没有添加的文件。使用git add添加需要提交的文件之后，执行下面的命令：

    git stash --keep-index

文章翻译自http://nerian.es/，[原文地址](http://nerian.es/articles/2014/04/30/the-16-most-common-questions-about-git/)

明明是十七个问题，结果大标题居然

词汇表
working copy    工作目录
repository      仓库
merge           合并
conflict        冲突
checkout        签出

参考 [Git Community Book 中文版 术语表](http://gitbook.liuhui998.com/7_8.html)