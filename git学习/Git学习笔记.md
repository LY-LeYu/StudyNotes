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

- 使用`git add <filename>`命令将工作区的文件提交到Git的暂存区,或者将`<filename>`改成`.`将所有文件添加到暂存区  
- 使用`git commit -m <summary>`命令将暂存区文件添加到分支(即文件树)
- 如何理解Git的工作区,暂存区和分支,如下图所示:![image-20220907210503966](D:\GitHub\StudyNotes\git学习\image-20220907210503966.png)

- 使用` git status`查看工作区状态以及文件修改的内容

- 使用`git diff`查看文件修改内容

### Git版本控制相关操作

- 使用`git log`来查看Git的提交的历史记录,显示的是最近至最旧的操作记录
  - 在` git log`后面加上条件`--pretty=oneline`,可以详细的看到操作的时间线
  - 显示的一大串数字是`commit id`,十六进制数字组成,方便分布式工作
- Git使用`HEAD`指针控制版本,其中`HEAD`指向当前版本,`HEAD^`表示的是上一个版本,`HEAD^^`表示的是上上个版本,为了方便书写之前的n个版本写成`HEAD~n`
- Git 回退版本使用`Git reset --hard commit id` 命令,这个操作实际就是控制指针指向哪个`commit id`,`commit id`不用全部输入，只需输入前几位数，Git会自动查找
- 当你想要查询某个命令的`commit id`时,使用`git reflog`来查看之前一些操作的命令

### Git撤销修改

- **工作区撤销的作：**使用`git restore <<filename>> `,文件不仅要写文件名还要加上后缀名，该命令相当于将暂存区的文件回退到工作区，回到上一次`git add`
- **提交到暂存区而没有提交到分支的撤销操作：**`git restore --staged <<filename>>`可以把暂存区的修改回退到上一次commit之前，就是把当前HEAD内容回退到暂存区。
  - 更加详细的解释`git restore --source`,该命令可以指定从哪个源恢复内容到文件，例如直接从分支恢复文件到工作区：`git restore --source HEAD <filename>`
- **从分支撤销操作：** 参考上一节回退版本，使用`git reset --hard HEAD^`

### Git删除文件

- `git rm <filename>`命令删除一个文件，并提交到暂存区
  - 当你是误删时，可以使用上一节的`git restore --staged <filename>`恢复，但是未提交的修改会丢失（当然你可以去windows回收站看看🐶）

### Git远程仓库

- 连接远程仓库需要创建SSH key，SSH key是一种加密密钥，用于证明自己的身份，可以在C盘用户目录下看到.ssh目录，其中的`id_ras`和`id_rsa.pub`分别是自己的私钥和公钥。
- 没有SSH Key可以是使用`ssh-keygen -t rsa -C "email"`来创建自己的SSH Key
- 将SSH key中的公钥添加到Github或者Gitee即可将自己的本地分支上传到远程仓库
- **将本地仓库与远程仓库关联:**`git remote add origin git@Github.com:用户名/仓库名.git`
- **关联本地分支和远程分支：**`git push -u origin master` ,当第一次关联仓库后，需要使用本指令，之后可以省略`-u`参数
- **删除本地库与远程库关联：**`git remote rm origin`
- **查看本地库所关联的远程库的信息：**`git remote -v`

### Git分支管理

- 查看分支：`git branch`
- 创建分支：`git branch <name>`
- 切换分支：`git switch <name>`
- 创建并切换到该分支：`git switch -c <name>`
- 合并分支：`git merge <name>`
- 删除分支：`git branch -d <name>`




