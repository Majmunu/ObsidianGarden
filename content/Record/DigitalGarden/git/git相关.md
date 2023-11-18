![[Pasted image 20230128180704.png]]

```ad-note
title:查看当前用户名和修改
1. 查看当前登录账号：
git config user.name

2. 查看当前登录邮箱：
git config user.email

3. 修改用户名和邮箱：
git config --global user.name "Your_username"
git config --global user.email "Your_email"

```
```ad-note
title:在命令行上创建新的存储库
echo "# IndividualExerciseProgram" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/chenchen2692/IndividualExerciseProgram.git
git push -u origin main
```



```ad-note
title:从命令行推送现有存储库
git remote add origin https://github.com/chenchen2692/IndividualExerciseProgram.git
git branch -M main
git push -u origin main
```

## Git 分支命令

-   git branch– 显示 Git 存储库中[本地分支的列表](https://www.gitkraken.com/learn/git/problems/git-branch-list)。
-   git branch -a– 在 Git 存储库中显示本地分支和远程分支的列表。
-   git branch -c– 复制一个 Git 分支。
-   git branch -d <branch-name>– [删除本地 GIT 分支](https://www.gitkraken.com/learn/git/problems/delete-local-git-branch)。如果您尝试删除的分支具有未合并的更改，则此命令将不起作用。
-   git branch -D <branch-name>– 删除具有未合并更改的本地 Git 分支。
-   git branch -m <branch-name> <new-branch-name>– [重命名 GIT 分支](https://www.gitkraken.com/learn/git/problems/rename-git-branch)。
-   git branch -r– 显示 Git 存储库中远程分支的列表。
-   git push <remote> --delete <remote-branch-name>– [删除远程 GIT 分支](https://www.gitkraken.com/learn/git/problems/delete-remote-git-branch)。
-   git push --set-upstream <remote> <branch>– [设置上游分支](https://www.gitkraken.com/learn/git/problems/git-set-upstream-branch)。运行此命令会将本地分支推送到新的远程分支。

---

## Git 签出命令

-   git checkout <branch-name>– [切换到不同的 GIT 分支](https://www.gitkraken.com/learn/git/problems/switch-git-branch)。
-   git checkout -b <branch-name>– [创建一个新分支](https://www.gitkraken.com/learn/git/problems/create-git-branch)并切换到它。
-   git checkout -b <branch-name><remote-name>/<branch-name>– 从远程 Git 分支创建一个本地分支并签出该分支。
-   git checkout <commit hash>– [签出以前的 GIT 提交](https://www.gitkraken.com/learn/git/problems/git-checkout-commit)。
-   git checkout <tag name>– 签出处于分离 HEAD 状态的 Git 标签。
-   git checkout -b <branch-name><tag-name>– [签出 GIT 标签](https://www.gitkraken.com/learn/git/problems/git-checkout-tag)作为分支。

---

## Git 樱桃选择命令

-   git cherry-pick [insert commit reference]– [将提交的更改应用到](https://www.gitkraken.com/learn/git/cherry-pick#cherry-pick-example-cli)不同的分支上。

---

## Git 克隆命令

-   git clone <repository-url>– 克隆指定的远程存储库。请参阅 [GIT-SCM 的远程 URL 格式最佳实践](https://git-scm.com/docs/git-clone#_git_urls)。
-   git clone <repository-url> <directory-name>– 克隆存储库并命名本地目录。
-   git clone <repository-url> --origin <name>– [克隆存储库](https://www.gitkraken.com/learn/git/git-clone)并命名远程 （）。如果您不想命名远程，Git 将提供默认名称。`<name>``origin`
-   git clone <repository-url> --branch <branch-name>– 克隆存储库并签出特定分支。
-   git clone <repository-url> --depth <depth>– 克隆具有指定提交次数的存储库 （）。`<depth>`
-   git clone <repository-url> --no-tags– 克隆存储库而不复制存储库的标记。

---

## Git 提交命令

-   git status– 显示暂存目录中的文件列表以及随附的文件状态。
-   git add– 暂存文件更改。使用关联的文件名运行此命令会将文件更改暂存到暂存目录。
-   git commit– 将更改保存到您的 Git 存储库。使用关联的文件名运行此命令会将文件更改保存到存储库。
-   git commit -a– 将工作目录中所有修改和删除的文件添加到当前提交中。
-   git commit --amend– [修改 GIT 提交](https://www.gitkraken.com/learn/git/problems/git-commit-amend)。通过在命令后添加引号消息来编辑 Git 提交消息。
-   git commit -m– 添加 Git 提交消息。在命令后面用引号引起来添加消息。

---

## Git 配置命令

-   `git config --global`– 自定义存储在主目录中的配置，并且可以覆盖 Git 配置系统设置。
-   `git config --email`– 设置与您的 Git 提交和其他 Git 操作关联的电子邮件。
-   `git config --system`– 自定义操作系统的配置设置。
-   `git --config user.name`– 设置与您的 Git 提交和其他 Git 操作关联的用户名。
-   `git config --list`– 查看所有 Git 配置设置，包括本地、全局和系统级别。
-   `git config --local`– 自定义特定于 Git 存储库的设置，并在全局和系统级别覆盖 Git 配置。

---

## Git 合并命令

-   git merge– 将两个或多个开发历史组合在一起。与 fetch 结合使用，这会将从远程分支获取的历史记录合并到当前签出的本地分支中。
-   git merge <branch-name>– [将一个分支中的更改合并](https://www.gitkraken.com/learn/git/problems/merge-git-branch)到您当前已签出的分支中。
-   git merge --abort– 中止合并过程并将项目的状态还原到尝试合并之前的状态。当发生冲突时，这可以作为故障保护。
-   git merge --continue– [在解决合并冲突后](https://www.gitkraken.com/learn/git/tutorials/how-to-resolve-merge-conflict-in-git)，尝试完成因文件冲突而停止的合并。
-   git merge --squash– 将分支中的所有更改合并到单个提交中，而不是将它们保留为单个提交。
-   git merge --no-commit– 将分支合并到当前分支中，但不要进行新的提交。
-   git merge --no-ff– 创建合并提交，而不是尝试快进。

---

## Git 拉取命令

-   git pull– 这将执行后跟 ，并允许您从另一个存储库或本地分支获取并与之集成。`git fetch``git merge FETCH_HEAD`
-   git pull --quiet– 在 和 之后禁止输出文本。`git fetch``git merge`
-   git pull --verbose– 在两者和之后展开输出文本。`git fetch``git merge`

#### 与合并相关的 Git 拉取命令

-   git pull --squash– 将分支中的所有更改合并到单个提交中，而不是保留单个提交。
-   git pull --no-commit– 将当前签出的分支与远程上游分支合并。
-   git pull --no-ff– 在所有情况下创建合并提交，即使合并可以作为快进解析。

#### 与 fetch 相关的 Git pull 命令

-   git pull --all– 获取所有遥控器。
-   git pull --depth=<depth>– 获取有限数量的提交。
-   git pull --dry-run– 显示无需实际更改存储库即可完成的操作。
-   git pull --prune– 删除远程上不再存在的所有远程引用。
-   git pull --no-tags– 不要获取标签。

---

## Git 推送命令

-   git push– 将当前签出的分支推送到默认远程。`origin`
-   git push <remote><branch>– 将指定的分支及其所有必要的提交推送到目标远程仓库。
-   git push <remote> --force– 在非快进合并中强制 Git 推送。此选项强制更新远程引用，即使该远程引用不是本地引用的祖先。这可能会导致远程仓库丢失提交，因此请谨慎使用。
-   git push <remote> --all– 将所有本地分支推送到指定的远程。
-   git push <remote> --tags– 将所有本地标签推送到指定的远程。使用 时不会自动发送标记。`--all`

---

## Git 变基命令

-   git rebase <target branch name>– 将当前签出的分支重新定位到目标分支。这会从源分支重写提交并将其应用于目标分支的顶部。
-   git rebase --continue– 解决文件之间的冲突后继续执行 [GIT 变基](https://www.gitkraken.com/learn/git/git-rebase)。
-   git rebase --skip– 跳过导致冲突的操作以继续执行 Git 变基。
-   git rebase --abort– 取消 Git 变基。您的分支将恢复到您开始变基之前的状态。
-   git rebase <target branch name> -i– 从当前签出的分支启动[交互式变基](https://www.gitkraken.com/learn/git/problems/git-interactive-rebase)到目标分支。

---

## Git 存储命令

-   git stash– 创建一个包含本地修改的存储，并恢复到头部提交。
-   git stash list– 显示存储库中所有存储的列表。
-   git stash show– 查看您最近藏匿的内容。这会将存储的更改显示为存储内容与创建存储时提交的提交之间的差异。
-   git stash drop <stash>– 从存储库的存储列表中删除存储。
-   git stash pop <stash>– 将存储应用到当前工作树的顶部，并将其从存储列表中删除。
-   git stash apply <stash>– 在当前工作树的顶部应用一个藏匿处。该存储不会从您的存储列表中删除。
-   git stash clear– 从存储库中删除所有藏匿处。