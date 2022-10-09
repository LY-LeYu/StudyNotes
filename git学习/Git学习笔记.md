# 写在开头

**熟悉Linux的一些语法，有助与git的操作，在下面列出一些常用的Linux语法**

```
mkdir xxx //创建一个文件夹
touch xxx.txt //创建一个文件,以创建txt文件为例
cd file folde route    //进入某个文件夹下
cd ..   //退回上一个路径
ls //查看文件列表
ll //比ls更加详细的查看列表信息
```

# Git学习笔记

## 初始化git仓库

- 在本地创建文件夹并进入，输入` git init`指令初始化你的git仓库
- 将GitHub、Gitee等远程仓库上的仓库克隆到本地，使用`git clone`命令

## 添加文件至Git仓库相关操作

- 使用`git add`命令将工作区的文件提交到Git的暂存区
- 使用`git commit -m <summary>`命令将暂存区文件添加到分支(即文件树)
- 如何理解Git的工作区,暂存区和分支,如下图所示:![image-20220907210503966](D:\GitHub\study\git学习\image-20220907210503966.png)

- 使用` git status`查看工作区状态以及文件修改的内容

- 使用`git diff`查看文件修改内容

### Git版本控制相关操作

- 使用`git log`来查看Git的提交的历史记录,显示的是最近至最旧的操作记录
  - 在` git log`后面加上条件`--pretty=oneline`,可以详细的看到操作的时间线
  - 显示的一大串数字是`commit id`,十六进制数字组成,方便分布式工作

- Git使用`HEAD`指针控制版本,其中`HEAD`指向当前版本,`HEAD^`表示的是上一个版本,`HEAD^^`表示的是上上个版本,为了方便书写之前的n个版本写成`HEAD~n`
- Git 回退版本使用`Git reset --hard`命令,这个操作实际就是控制指针指向哪个`commit id`
- 当你想要查询某个命令的`commit id`时,使用`git reflog`来查看之前一些操作的命令
- 