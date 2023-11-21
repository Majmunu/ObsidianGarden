# master

> master 分支始终是最稳定的代码分支，我们每一次迭代开发完后发布到市场版本的代码分支，一个项目的master 分支只能有一个

**注意：** master 分支只能从其他分支合并进来，严格禁止在master分支修改代码

# develop

> develop 分支是我们的主要开发分支，我们每一次的需求迭代开发都是从这个develop 分支上来拉一个新的feature 分支来进行开发，develop 分支是从master 分支上拉去的

**注意：** 一个项目也是只能有一个 develop 分支，develop 分支上也是不允许直接进行代码的修改

# feature

> feature 分支就是我们每一次需求迭代开发的分支，每一个需求迭代，我们可以在develop 分支上拉去多个 feature 分支，也可以在别人的 feature 分支上拉去 另一个feature 分支，等feature 分支开发完成后，我们需要将feature 分支 合回到 develop 分支上

# release

> release 分支是类似于预生产的分支，当我们的一个迭代的需求开发完成后，开发分支 feature 已经合并回了 develop 分支上后，我们需要拉取 release 分支，也可以理解为当我们开始提测的时候，我们来拉去 release 分支，在这个分支上进行修改bug

**注意：**

- 当我们的 release 分支开发完后，我们需要将 release 分支合回 develop 分支 和master 分支
- 当release 分支合并到 master 分支上后，我们记得在 master 分支上打一个 tag

# hotfix

> hotfix 分支是当我们线上应用出现了重大的bug，这时我们需要发布一个紧急修复版本，这时我们需要在 master 分支上拉去 一个 hotfix分支

**注意：**

- hotfix分支 开发完后，我们同样是需要合并回 master 分支 和 develop 分支
- 当hotfix 分支合并到 master 分支上后，我们记得在 master 分支上打一个 tag
# Bugfix 

> 线上出现故障的时候，但是并不需要立刻修复
    新功能开发完毕，合到 develop 分支之后发现有 bug




  
