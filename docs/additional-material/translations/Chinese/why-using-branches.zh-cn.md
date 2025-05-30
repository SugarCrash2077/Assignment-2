# 为什么在贡献时要使用分支

## 什么是分支？

分支（Branch）本质上是指向某个提交（commit）的指针。

当你创建分支时，Git 会基于你当前的代码状态生成一个新的快照，你可以在这个分支上自由修改，而不会影响主代码（通常是 master 分支）。

当你对实验结果满意并希望将其合并进主代码时，只需运行：
<branch name> master.
这会告诉 Git：将你在实验分支上的更改合并到 master 主分支中。

在多人参与的开源项目中，使用分支可以让每位贡献者独立开发，不影响主分支，从而更方便地合并最合适的代码。

## 它是如何工作的？

分支代表了一条独立的开发路径。  
分支是编辑/暂存/提交流程的抽象表现。你可以将其想象为：为你开辟了一套新的工作目录、暂存区和项目历史。

新提交会被记录在当前分支的历史中，从而在项目历史中形成一个“分叉”。

`git branch` 命令可用于创建、列出、重命名和删除分支。  
但它并不能用于切换分支或合并历史记录。因此，它通常与 `git checkout` 和 `git merge` 命令一起使用。

## 为什么要使用分支？

如果你仍然在思考“为什么我们要在版本控制中使用分支？”，那这里有一个简单的例子可以说明：

假设某款量产汽车在正式发布前需要喷漆，原定默认颜色为“橄榄绿”，但制造团队的一些成员想展示“红色”版本。

为了避免混乱，“红色喷漆”就像是主项目（汽车）的一个分支。  
如果将该分支合并进主项目，那么最终的颜色就是红色；如果不合并，则继续使用橄榄绿。

是否将某个贡献者的分支合并进主分支，通常由项目负责人决定。

## 举个例子

Alice 在开发功能 A，Bob 在开发功能 B。  
Alice 完成功能 A 一半后，提交了几次；但功能 A 实在太复杂，于是她决定先去开发功能 C，并继续在同一分支（alice）提交。

与此同时，Bob 完成功能 B 后，打算接手功能 A，于是他把 alice 分支合并到了自己的 bob 分支中。

等 Bob 完成功能 A 后，准备将 bob 分支合并进 master。  
但 bob 分支此时包含了功能 A、功能 B 和部分功能 C，而功能 C 还没完成！

这就很容易在合并时引发混乱的冲突。

解决办法是：不要用“人名分支”，而应该使用“功能分支”。  
Alice 应该为功能 A 和功能 C 分别创建分支；Bob 应该为功能 B 和功能 A 分别创建分支。  
这样，他们就能并行开发各自的功能，互不干扰。

## 如何创建分支？

#### 创建分支

```
git branch 任意分支名
```

这将新建一个名为“任意分支名”的分支。  
在这个分支上进行的更改不会影响主分支。
详细教程请参考： [如何创建分支](https://www.atlassian.com/git/tutorials/using-branches)

#### 删除分支

```
git branch -d 任意分支名
```

此命令会从 Git 仓库中删除名为“任意分支名”的分支。
参考： [如何从仓库中移除分支](https://github.com/jashnimje/first-contributions/blob/7dcae72208e4b42fcf834b4f189fa8ee78238077/additional-material/git_workflow_scenarios/removing-branch-from-your-repository.md)
