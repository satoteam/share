## Git简介
- Git是目前世界上最先进的分布式版本控制系统
- 安装  
linux: >  ```sudo apt-get install git```  
other: >``` sudo pip install git```

## 产生

Linus在1991年创建了开源的Linux，从此，Linux系统不断发展，已经成为最大的服务器系统软件了。Linus虽然创建了Linux，但Linux的壮大是靠全世界热心的志愿者参与的，这么多人在世界各地为Linux编写代码，那Linux的代码是如何管理的呢？事实是，在2002年以前，世界各地的志愿者把源代码文件通过diff的方式发给Linus，然后由Linus本人通过手工方式合并代码！你也许会想，为什么Linus不把Linux代码放到版本控制系统里呢？不是有CVS、SVN这些免费的版本控制系统吗？因为Linus坚定地反对CVS和SVN，这些集中式的版本控制系统不但速度慢，而且必须联网才能使用。有一些商用的版本控制系统，虽然比CVS、SVN好用，但那是付费的，和Linux的开源精神不符。不过，到了2002年，Linux系统已经发展了十年了，代码库之大让Linus很难继续通过手工方式管理了，社区的弟兄们也对这种方式表达了强烈不满，于是Linus选择了一个商业的版本控制系统BitKeeper，BitKeeper的东家BitMover公司出于人道主义精神，授权Linux社区免费使用这个版本控制系统。安定团结的大好局面在2005年就被打破了，原因是Linux社区牛人聚集，不免沾染了一些梁山好汉的江湖习气。开发Samba的Andrew试图破解BitKeeper的协议（这么干的其实也不只他一个），被BitMover公司发现了（监控工作做得不错！），于是BitMover公司怒了，要收回Linux社区的免费使用权。Linus可以向BitMover公司道个歉，保证以后严格管教弟兄们，嗯，这是不可能的。实际情况是这样的：Linus花了两周时间自己用C写了一个分布式版本控制系统，这就是Git！一个月之内，Linux系统的源码已经由Git管理了！牛是怎么定义的呢？大家可以体会一下。Git迅速成为最流行的分布式版本控制系统，尤其是2008年，GitHub网站上线了，它为开源项目免费提供Git存储，无数开源项目开始迁移至GitHub，包括jQuery，PHP，Ruby等等。历史就是这么偶然，如果不是当年BitMover公司威胁Linux社区，可能现在我们就没有免费而超级好用的Git了。


## 远程仓库

- Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上。首先找一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。可以自己搭建这台服务器，也可以使用GitHub网站  

#### 创建github账号  

- 本地Git仓库和GitHub仓库之间的传输是通过SSH加密的

- step1：创建项目的SSH Key(没有安装ssh，自己安装)
```ssh-keygen -t rsa -C "youremail@example.com"```

注：创建完成后，在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人
- step2:* 登录github注册或登录账号，打开“settings”的“SSH Keys”页面，然后，点“New SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容，点“Add Key”，你就应该看到已经添加的Key 

#### 从远程库克隆

- 将github上的项目，克隆到本地一份  
``` git clone git@github.com:账号名/项目名.git ```

#### 与远程库交互

- 从远程库获取到本地  
```git pull```

- 将本地提交远程库  
```git push origin master```  
注意：提示：每次提交前，需要先获取，解决冲突后再次提交 

## 本地仓库  
#### 创建本地仓库  
- 创建空目录在计算机  
```mkdir name```
 ```cd name```

- 在目录下创建本地仓库 
```git init```

- 版本库就是一个目录，这个目录里面的所有文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在将来某个时刻可以“还原”

#### 文件管理
- 本地仓库分为三部分：工作区，暂存区，仓库区，其中暂存区、仓库区是版本库部分
- 三个部分的操作及命令如下图


#### 工作区与暂存区
- 使用IDE打开目录，创建项目，将文件添加到暂存区  
``` git add 文件1 文件2```  
```git add 目录```
- 使用暂时区的内容恢复工作区的内容  
``` git checkout -- 文件名 ```
- 查看暂存区的状态  
``` git status ```

#### 暂存区与仓库区
- 将暂存区的记录添加到仓库区  
```git commit -m '本次提交的说明信息'```  

- 查看仓库区的历史
```当前版本的历史版本：git log```  
```简版显示：git log --pretty=oneline```  
```历史命令：git reflog```   

- 在Git中，用HEAD表示当前版本，也就是最新的提交3628164...882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^， 上上一个版本就是HEAD^^， 当然往上100个版本写100个^ 比较容易数不过来，所以写成HEAD~100

- 对比工作区和仓库区中某版本某文件的不同  
``` git diff HEAD -- 文件名 ```  

- 回退历史版本到暂存区  
```git reset HEAD^或版本号```  

#### 删除文件

- 依次执行如下命令  
```rm 文件名```   
```git rm 文件名```  
```git commit -m '说明信息'```

## 扩展阅读
- 实验楼Git教程
- [最后的中文教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
- [图形化学习git：Learn Git Branching](http://pcottle.github.io/learnGitBranching/)

- [使用git和github进行协同开发流程](http://livoras.com/post/28)

- [Github Help](https://help.github.com/)
- [GitHub秘籍](https://github.com/tiimgreen/github-cheat-sheet/blob/master/README.zh-cn.md)  

- [如何给GitHub项目添加徽章和 wiki的设置](https://github.com/EyreFree/EFArticles/tree/master/Articles/GitHub)


