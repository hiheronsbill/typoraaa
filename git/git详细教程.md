# 一、版本控制概要 

## 1.1、什么是版本控制
版本控制（Revision control）是一种在开发的过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的版本的软件工程技术。

- 实现跨区域多人协同开发
- 追踪和记载一个或者多个文件的历史记录
- 组织和保护你的源代码和文档
- 统计工作量
- 并行开发、提高开发效率
- 跟踪记录整个软件的开发过程
- 减轻开发人员的负担，节省时间，同时降低人为错误

简单说就是用于管理多人协同开发项目的技术。
没有进行版本控制或者版本控制本身缺乏正确的流程管理，在软件开发过程中将会引入很多问题，如软件代码的一致性、软件内容的冗余、软件过程的事物性、软件开发过程中的并发性、软件源代码的安全性，以及软件的整合等问题。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071872-c7bffe32-3497-4d46-b32b-ed5d432667ae.png#align=left&display=inline&height=391&margin=%5Bobject%20Object%5D&originHeight=391&originWidth=415&size=0&status=done&style=none&width=415)

## 1.2、常用术语
**1)、仓库（Repository）**
受版本控制的所有文件修订历史的共享数据库
**2)、工作空间（Workspace)**
本地硬盘或Unix 用户帐户上编辑的文件副本
**3)、工作树/区（Working tree）**
工作区中包含了仓库的工作文件。您可以修改的内容和提交更改作为新的提交到仓库。
**4)、暂存区（Staging area）**
暂存区是工作区用来提交更改（commit）前可以暂存工作区的变化。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071754-339f926d-ce8a-4083-a9cb-0d5ce3333c56.png#align=left&display=inline&height=235&margin=%5Bobject%20Object%5D&originHeight=235&originWidth=618&size=0&status=done&style=none&width=618)
**5)、索引（Index）**
索引是暂存区的另一种术语。
**6)、签入（Checkin）**
将新版本复制回仓库
**7)、签出（Checkout）**
从仓库中将文件的最新修订版本复制到工作空间
**8)、提交（Commit）**
对各自文件的工作副本做了更改，并将这些更改提交到仓库
**9)、冲突（Conflict）**
多人对同一文件的工作副本进行更改，并将这些更改提交到仓库
**10)、合并（Merge）**
将某分支上的更改联接到此主干或同为主干的另一个分支
**11)、分支（Branch）**
从主线上分离开的副本，默认分支叫master
**12)、锁（Lock）**
获得修改文件的专有权限。
**13)、头（HEAD）**
头是一个象征性的参考，最常用以指向当前选择的分支。
**14)、修订（Revision）**
表示代码的一个版本状态。Git通过用SHA1 hash算法表示的ID来标识不同的版本。
**15)、标记（Tags）**
标记指的是某个分支某个特定时间点的状态。通过标记，可以很方便的切换到标记时的状态。

## 1.3、常见的版本控制器
主流的版本控制器有如下这些：

- **Git**
- **SVN**（Subversion）
- **CVS**（Concurrent Versions System）
- **VSS**（Micorosoft Visual SourceSafe）
- **TFS**（Team Foundation Server）
- Visual Studio Online

版本控制产品非常的多（Perforce、Rational ClearCase、RCS（GNU Revision Control System）、Serena Dimention、SVK、BitKeeper、Monotone、Bazaar、Mercurial、SourceGear Vault），现在影响力最大且使用最广泛的是Git与SVN

## 1.4、版本控制分类

### **1.4.1、本地版本控制**
记录文件每次的更新，可以对每个版本做一个快照，或是记录补丁文件，适合个人用，如RCS。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071842-a14f4b8f-4f17-433f-9f6a-4e7993082a96.png#align=left&display=inline&height=336&margin=%5Bobject%20Object%5D&originHeight=336&originWidth=400&size=0&status=done&style=none&width=400)

### **1.4.2、集中版本控制**
所有的版本数据都保存在服务器上，协同开发者从服务器上同步更新或上传自己的修改
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071753-d1638155-1505-4548-b786-8a6e8fc1326f.png#align=left&display=inline&height=392&margin=%5Bobject%20Object%5D&originHeight=392&originWidth=500&size=0&status=done&style=none&width=500)
所有的版本数据都存在服务器上，用户的本地只有自己以前所同步的版本，如果不连网的话，用户就看不到历史版本，也无法切换版本验证问题，或在不同分支工作。而且，所有数据都保存在单一的服务器上，有很大的风险这个服务器会损坏，这样就会丢失所有的数据，当然可以定期备份。代表产品：SVN、CVS、VSS

### 1.4.3、分布式版本控制
所有版本信息仓库全部同步到本地的每个用户，这样就可以在本地查看所有版本历史，可以离线在本地提交，只需在连网时push到相应的服务器或其他用户那里。由于每个用户那里保存的都是所有的版本数据，只要有一个用户的设备没有问题就可以恢复所有的数据，但这增加了本地存储空间的占用。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071851-0663ac52-d435-4cc7-8f4d-d3aed1909662.png#align=left&display=inline&height=563&margin=%5Bobject%20Object%5D&originHeight=563&originWidth=500&size=0&status=done&style=none&width=500)

## 1.5、Git与SVN最主要区别
SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把自己做完的活推送到中央服务器。集中式版本控制系统是必须联网才能工作，对网络带宽要求较高。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071784-4f5a3ce2-31e4-45d0-90bb-9b682c8585f0.png#align=left&display=inline&height=83&margin=%5Bobject%20Object%5D&originHeight=83&originWidth=406&size=0&status=done&style=none&width=406)![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071806-dba85130-5f6d-4bf8-84c9-00084521a69f.png#align=left&display=inline&height=87&margin=%5Bobject%20Object%5D&originHeight=87&originWidth=222&size=0&status=done&style=none&width=222)![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071840-b6b45479-c235-4e49-8b6f-c86626b62fbb.png#align=left&display=inline&height=88&margin=%5Bobject%20Object%5D&originHeight=158&originWidth=227&size=0&status=done&style=none&width=126)

Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整的版本库，工作的时候不需要联网了，因为版本都在自己电脑上。协同的方法是这样的：比如说自己在电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需把各自的修改推送给对方，就可以互相看到对方的修改了。

# 二、Git安装与配置
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071835-8190b1a1-310f-425e-87ac-fd2ec16895b8.png#align=left&display=inline&height=92&margin=%5Bobject%20Object%5D&originHeight=92&originWidth=220&size=0&status=done&style=none&width=220)

## 2.1、什么是Git
Git是目前世界上最先进的分布式版本控制系统。
Git是免费、开源的
最初Git是为辅助 Linux 内核开发的，来替代 BitKeeper
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071897-f9b8a58d-0388-4682-bd30-5b3324068e7b.png#align=left&display=inline&height=201&margin=%5Bobject%20Object%5D&originHeight=201&originWidth=371&size=0&status=done&style=none&width=371)
**作者**：Linux和Git之父李纳斯·托沃兹（Linus Benedic Torvalds）1969、芬兰
**优点：**

- 适合分布式开发，强调个体。
- 公共服务器压力和数据量都不会太大。
- 速度快、灵活。
- 任意两个开发者之间可以很容易的解决冲突。
- 离线工作。

**缺点：**

- 模式上比SVN更加复杂。
- 不符合常规思维。
- 代码保密性差，一旦开发者把整个库克隆下来就可以完全公开所有代码和版本信息。

**官网**： [https://git-scm.com/](https://git-scm.com/)
**源码：** [https://github.com/git/git/](https://github.com/git/git/)

## 2.2、搭建Git工作环境

### 2.2.1、下载Git
打开 [git官网](https://git-scm.com/)，下载git对应操作系统的版本。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071842-1a86785c-1421-4063-b7d5-71dffa46c09d.png#align=left&display=inline&height=731&margin=%5Bobject%20Object%5D&originHeight=731&originWidth=1126&size=0&status=done&style=none&width=1126)
选择版本：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071872-e55979b1-ea5a-41a5-9d0f-10fd9848651c.png#align=left&display=inline&height=735&margin=%5Bobject%20Object%5D&originHeight=735&originWidth=1123&size=0&status=done&style=none&width=1123)
这里我选择下载**[64-bit Git for Windows Setup](https://github.com/git-for-windows/git/releases/download/v2.14.1.windows.1/Git-2.14.1-64-bit.exe)**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071839-ff15edec-caa7-4585-87d1-2388dfd96809.png#align=left&display=inline&height=70&margin=%5Bobject%20Object%5D&originHeight=70&originWidth=263&size=0&status=done&style=none&width=263)

### **2.2.2、安装Git**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071800-0db41dca-3a63-454b-a462-5e1152e175da.png#align=left&display=inline&height=392&margin=%5Bobject%20Object%5D&originHeight=392&originWidth=507&size=0&status=done&style=none&width=507)
选择安装配置信息
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071817-73d5df48-7372-491c-bca8-cb09ede10522.png#align=left&display=inline&height=389&margin=%5Bobject%20Object%5D&originHeight=389&originWidth=506&size=0&status=done&style=none&width=506)
一直Next默认就好了，如果需要设置就要仔细读一下安装界面上的选项。

### 2.2.3、启动Git
安装成功后在开始菜单中会有Git项，菜单下有3个程序：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071873-11eb398c-2ce9-4936-8629-cda34218ab04.png#align=left&display=inline&height=87&margin=%5Bobject%20Object%5D&originHeight=87&originWidth=174&size=0&status=done&style=none&width=174)
**Git Bash：**Unix与Linux风格的命令行，使用最多，推荐最多
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071971-8271cb1f-57c2-4973-b21b-f84cf4b43e4e.png#align=left&display=inline&height=342&margin=%5Bobject%20Object%5D&originHeight=342&originWidth=624&size=0&status=done&style=none&width=624)
与DOS风格的命令有些区别，不习惯可以选择Git CMD
**Git CMD：**Windows风格的命令行
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072030-89873c26-1e37-4341-a330-2ecbc5ffcd2e.png#align=left&display=inline&height=389&margin=%5Bobject%20Object%5D&originHeight=389&originWidth=673&size=0&status=done&style=none&width=673)
**Git GUI**：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072004-ecbfa41d-72ea-4da8-95c3-30cf4ba8d79c.png#align=left&display=inline&height=331&margin=%5Bobject%20Object%5D&originHeight=331&originWidth=681&size=0&status=done&style=none&width=681)
点击Create New Repository可以直接创建一个新的仓库。

### 2.2.4、Linux与Mac OS安装Git
Linux安装Git：sudo apt-get install git 命令行就可以安装了。
Mac OS安装Git： [https://git-scm.com/download/mac](https://git-scm.com/download/mac)，下载双击.pkg安装

### 2.2.5、Bash基本操作命令
~就是home
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072149-9baf60ad-e825-44af-af2a-c9301b6d3d2e.png#align=left&display=inline&height=364&margin=%5Bobject%20Object%5D&originHeight=364&originWidth=734&size=0&status=done&style=none&width=734)
进入Bash默认位置，注意标题栏
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072223-f370e586-7532-48d1-9960-ccc3efbe736d.png#align=left&display=inline&height=136&margin=%5Bobject%20Object%5D&originHeight=136&originWidth=731&size=0&status=done&style=none&width=731)
1）、cd : 改变目录。
　　cd ~ 回Home（windows是当前用户所在目录）
　　![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072202-da30f126-01f3-46ff-afb0-30a050148c1b.png#align=left&display=inline&height=225&margin=%5Bobject%20Object%5D&originHeight=225&originWidth=727&size=0&status=done&style=none&width=727)
2）、cd . . 回退到上一个目录，直接cd进入默认目录
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072156-e025b0d6-76e8-42cb-bd4d-c2d1439365b4.png#align=left&display=inline&height=184&margin=%5Bobject%20Object%5D&originHeight=184&originWidth=731&size=0&status=done&style=none&width=731)
3）、pwd : 显示当前所在的目录路径。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991071991-0ae5fceb-e0f4-4098-a635-347565d43008.png#align=left&display=inline&height=227&margin=%5Bobject%20Object%5D&originHeight=227&originWidth=732&size=0&status=done&style=none&width=732)
4）、ls(ll): 都是列出当前目录中的所有文件，只不过ll(两个ll)列出的内容更为详细。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072183-d956425b-9b52-44a5-a1c1-edd090bb9476.png#align=left&display=inline&height=242&margin=%5Bobject%20Object%5D&originHeight=242&originWidth=730&size=0&status=done&style=none&width=730)
5）、touch : 新建一个文件 如 touch index.js 就会在当前目录下新建一个index.js文件。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072124-acac9aab-f66d-4c6c-ae4e-68c9efbf8c9e.png#align=left&display=inline&height=357&margin=%5Bobject%20Object%5D&originHeight=357&originWidth=730&size=0&status=done&style=none&width=730)
6）、rm: 删除一个文件, rm index.js 就会把index.js文件删除。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072009-462717a5-cd98-46b7-8d0d-3c65e7d5c6e2.png#align=left&display=inline&height=362&margin=%5Bobject%20Object%5D&originHeight=362&originWidth=734&size=0&status=done&style=none&width=734)
7）、mkdir: 新建一个目录,就是新建一个文件夹。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072074-9d5f221a-a7ed-46ac-92bb-82d0b46b64f2.png#align=left&display=inline&height=305&margin=%5Bobject%20Object%5D&originHeight=305&originWidth=730&size=0&status=done&style=none&width=730)
8）、rm -r : 删除一个文件夹, rm -r src 删除src目录， 好像不能用通配符。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072150-a2635dd0-4a2a-41a7-ad81-606286a0a4c6.png#align=left&display=inline&height=415&margin=%5Bobject%20Object%5D&originHeight=415&originWidth=731&size=0&status=done&style=none&width=731)
9）、mv 移动文件, mv index.html src index.html 是我们要移动的文件, src 是目标文件夹,当然, 这样写,必须保证文件和目标文件夹在同一目录下。
10）、reset 重新初始化终端/清屏。
11）、clear 清屏。
12）、history 查看命令历史。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072177-8b43d758-0482-412d-8fee-4e41d04a00da.png#align=left&display=inline&height=355&margin=%5Bobject%20Object%5D&originHeight=355&originWidth=727&size=0&status=done&style=none&width=727)
13）、help 帮助。
14）、exit 退出。
15）、#表示注释
16）、输出与注释
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072194-6ae7db7e-e4c3-487b-8714-0b0655ece7f2.png#align=left&display=inline&height=306&margin=%5Bobject%20Object%5D&originHeight=306&originWidth=731&size=0&status=done&style=none&width=731)
17）、创建文件
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072052-fc3aec94-a186-43ee-a082-9a629e7c9688.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
小于号：命令默认从键盘获得的输入，改成从文件，或者其它打开文件以及设备输入

>> 是追加内容

> 是覆盖原有内容
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072036-47c5cd49-d1a8-4f20-b9e7-9a257bea51ad.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072238-31911a26-dec4-4837-8cc7-1261758b1de1.png#align=left&display=inline&height=358&margin=%5Bobject%20Object%5D&originHeight=358&originWidth=725&size=0&status=done&style=none&width=725)
 18、显示文件内容 cat
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072009-c66a4ac0-75af-4e2e-9708-6b511cd4fd9d.png#align=left&display=inline&height=205&margin=%5Bobject%20Object%5D&originHeight=205&originWidth=808&size=0&status=done&style=none&width=808)

## 2.3、Git配置 - git config

### 2.3.1、查看配置 - git config -l
使用git config -l 可以查看现在的git环境详细配置
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072040-24423d1f-2294-4832-bfdf-ebde8e8c03c2.png#align=left&display=inline&height=579&margin=%5Bobject%20Object%5D&originHeight=579&originWidth=958&size=0&status=done&style=none&width=958)
查看不同级别的配置文件：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072111-da2f6b7e-ae51-427d-a968-d4a7d3d6257e.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#查看系统config
git config --system --list

#查看当前用户（global）配置
git config --global  --list

#查看当前仓库配置信息
git config --local  --list
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072069-e2df6fd5-81a0-4a01-b2f9-6b243e01c7cf.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)

### 2.3.2、Git配置文件分类
在Windows系统中，Git在$HOME目录中查找.gitconfig文件（一般位于C:\Documents and Settings$USER下）
**Git相关的配置文件有三个：**
1）、 /etc/gitconfig：包含了适用于系统所有用户和所有项目的值。(Win：C:\Program Files\Git\mingw64\etc\gitconfig) --system 系统级
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072043-0432639a-215f-4cdd-bbe1-a9280ec1ef9c.png#align=left&display=inline&height=342&margin=%5Bobject%20Object%5D&originHeight=342&originWidth=949&size=0&status=done&style=none&width=949)

2）、~/.gitconfig：只适用于当前登录用户的配置。(Win：C:\Users\Administrator\.gitconfig)  --global 全局
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072110-3fa9f425-139e-4d9d-885e-7d910cda6b88.png#align=left&display=inline&height=630&margin=%5Bobject%20Object%5D&originHeight=630&originWidth=1005&size=0&status=done&style=none&width=1005)
3）、位于git项目目录中的.git/config：适用于特定git项目的配置。(Win：C:\gitProject) --local当前项目
注意：对于同一配置项，三个配置文件的优先级是1<2<3
这里可以直接编辑配置文件，通过命令设置后会响应到这里。

### 2.3.3、设置用户名与邮箱（用户标识，必要）
当你安装Git后首先要做的事情是设置你的用户名称和e-mail地址。这是非常重要的，因为每次Git提交都会使用该信息。它被永远的嵌入到了你的提交中：
   $ git config --global user.name **"zhangguo"**  #名称
   $ git config --global user.email zhangguo@qq.com   #邮箱
只需要做一次这个设置，如果你传递了--global 选项，因为Git将总是会使用该信息来处理你在系统中所做的一切操作。如果你希望在一个特定的项目中使用不同的名称或e-mail地址，你可以在该项目中运行该命令而不要--global选项。 总之--global为全局配置，不加为某个项目的特定配置。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072105-b6af894f-5841-4284-9be6-551232600abf.png#align=left&display=inline&height=542&margin=%5Bobject%20Object%5D&originHeight=542&originWidth=1012&size=0&status=done&style=none&width=1012)

### 2.3.4、添加或删除配置项
**1）、添加配置项 **
git config [--local|--global|--system]  section.key value
[--local|--global|--system]  #可选的，对应本地，全局，系统不同级别的设置，请看2.3.2
section.key #区域下的键
value #对应的值
--local 项目级
--global 当前用户级
--system 系统级 
例如我们要在student区域下添加一个名称为height值为198的配置项，执行结果如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072050-7df7e364-0919-4099-961c-7887c863fe8c.png#align=left&display=inline&height=593&margin=%5Bobject%20Object%5D&originHeight=593&originWidth=1074&size=0&status=done&style=none&width=1074)
**2）、删除配置项 **
git config [--local|--global|--system] --unset section.key
 将系统级的height配置项移除
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072048-0d214554-ad4e-439e-9f30-33f565b459a0.png#align=left&display=inline&height=269&margin=%5Bobject%20Object%5D&originHeight=269&originWidth=472&size=0&status=done&style=none&width=472)

### 2.3.5、更多配置项
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072151-31a4b4ef-1a3f-4ff4-8b77-042e07a8ea33.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
git config --global color.ui true   #打开所有的默认终端着色
git config --global alias.ci commit   #别名 ci 是commit的别名
[alias]  
co = checkout  
ci = commit  
st = status  
pl = pull  
ps = push  
dt = difftool  
l = log --stat  
cp = cherry-pick  
ca = commit -a  
b = branch 

user.name  #用户名
user.email  #邮箱
core.editor  #文本编辑器  
merge.tool  #差异分析工具  
core.paper **"less -N"**  #配置显示方式  
color.diff true  #diff颜色配置  
alias.co checkout  #设置别名
git config user.name  #获得用户名
git config core.filemode false  #忽略修改权限的文件  
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072201-51fd9657-847b-43bd-8627-a0b6dfebc9b0.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
所有config命令参数
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072168-36c192c4-0150-4630-99f5-55ba4cd07098.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
语法: git config [<options>]        
        
文件位置        
    --global                  #use global config file 使用全局配置文件
    --system                  #use system config file 使用系统配置文件
    --local                   #use repository config file    使用存储库配置文件
    -f, --file <file>         #use given config file    使用给定的配置文件
    --blob <blob-id>          #read config from given blob object    从给定的对象中读取配置
        
动作        
    --get                     #get value: name [value-regex]    获得值：[值]名[正则表达式]
    --get-all                 #get all values: key [value-regex]    获得所有值：[值]名[正则表达式]
    --get-regexp          #get values for regexp: name-regex [value-regex]    得到的值根据正则
    --get-urlmatch            #get value specific for the URL: section[.var] URL    为URL获取特定的值
    --replace-all             #replace all matching variables: name value [value_regex]    替换所有匹配的变量：名称值[ value_regex ]
    --add                     #add a new variable: name value    添加一个新变量：name值
    --unset                   #remove a variable: name [value-regex]    删除一个变量名[值]：正则表达式
    --unset-all               #remove all matches: name [value-regex]    删除所有匹配的正则表达式：名称[值]
    --rename-section          #rename section: old-name new-name    重命名部分：旧名称 新名称
    --remove-section          #remove a section: name    删除部分：名称
    -l, --list                #list all    列出所有
    -e, --edit            #open an editor    打开一个编辑器
    --get-color               #find the color configured: slot [default]    找到配置的颜色：插槽[默认]
    --get-colorbool           #find the color setting: slot [stdout-is-tty]    发现颜色设置：槽[ stdout是TTY ]
        
类型        
    --bool                    #value is "true" or "false"    值是“真”或“假”。
    --int                     #value is decimal number    值是十进制数。
    --bool-or-int             #value is --bool or --int    值--布尔或int
    --path                    #value is a path (file or directory name)    值是路径（文件或目录名）
        
其它        
    -z, --null                #terminate values with NUL byte    终止值与null字节
    --name-only               #show variable names only    只显示变量名
    --includes                #respect include directives on lookup    尊重包括查找指令
    --show-origin             #show origin of config (file, standard input, blob, command line)    显示配置（文件、标准输入、数据块、命令行）的来源
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072176-1477a7ba-544d-422d-b8c8-d92a00461346.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)

# 三、Git理论基础

## 3.1、工作区域
Git本地有三个工作区域：工作目录（Working Directory）、暂存区(Stage/Index)、资源库(Repository或Git Directory)。如果在加上远程的git仓库(Remote Directory)就可以分为四个工作区域。文件在这四个区域之间的转换关系如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072208-7f0569b6-0b33-4732-bc8a-89c3c4abcccf.png#align=left&display=inline&height=305&margin=%5Bobject%20Object%5D&originHeight=305&originWidth=318&size=0&status=done&style=none&width=318)

- Workspace：工作区，就是你平时存放项目代码的地方
- Index / Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息
- Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本
- Remote：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换

本地的三个区域确切的说应该是git仓库中HEAD指向的版本
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072217-3cb0cd7c-0620-4a9e-bd76-639da9584f8d.png#align=left&display=inline&height=539&margin=%5Bobject%20Object%5D&originHeight=539&originWidth=818&size=0&status=done&style=none&width=818)

- Directory：使用Git管理的一个目录，也就是一个仓库，包含我们的工作空间和Git的管理空间。
- WorkSpace：需要通过Git进行版本控制的目录和文件，这些目录和文件组成了工作空间。
- .git：存放Git管理信息的目录，初始化仓库的时候自动创建。
- Index/Stage：暂存区，或者叫待提交更新区，在提交进入repo之前，我们可以把所有的更新放在暂存区。
- Local Repo：本地仓库，一个存放在本地的版本库；HEAD会只是当前的开发分支（branch）。
- Stash：隐藏，是一个工作状态保存栈，用于保存/恢复WorkSpace中的临时状态。


## 3.2、工作流程
git的工作流程一般是这样的：
１、在工作目录中添加、修改文件；
２、将需要进行版本管理的文件放入暂存区域；
３、将暂存区域的文件提交到git仓库。
因此，git管理的文件有三种状态：已修改（modified）,已暂存（staged）,已提交(committed)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072182-80d038c6-e773-4f6a-81b6-04bfa35d8732.png#align=left&display=inline&height=574&margin=%5Bobject%20Object%5D&originHeight=905&originWidth=1157&size=0&status=done&style=none&width=734)

## 3.3、图解教程
个人认为Git的原理相比别的版本控制器还是复杂一些的，有一份图解教程比较直观：
[图解教程英文原版](https://github.com/MarkLodato/visual-git-guide)
[图解教程中文版](http://www.cnblogs.com/yaozhongxiao/p/3811130.html)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072206-b2885302-f8df-4b9d-8bd5-841a3ecfee66.png#align=left&display=inline&height=287&margin=%5Bobject%20Object%5D&originHeight=339&originWidth=746&size=0&status=done&style=none&width=632)

# 四、Git操作

## 4.1、创建工作目录与常用指令
工作目录（WorkSpace)一般就是你希望Git帮助你管理的文件夹，可以是你项目的目录，也可以是一个空目录，建议不要有中文。
日常使用只要记住下图6个命令：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072248-9c68e900-2f05-4a98-9394-0b5c6b40fa71.png#align=left&display=inline&height=330&margin=%5Bobject%20Object%5D&originHeight=340&originWidth=1172&size=0&status=done&style=none&width=1138)

## 4.2、获得GIT仓库
创建本地仓库的方法有两种：一种是创建全新的仓库，另一种是克隆远程仓库。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072252-c2426d33-ebc9-4cd8-afd1-9e38e6af8e23.png#align=left&display=inline&height=133&margin=%5Bobject%20Object%5D&originHeight=133&originWidth=448&size=0&status=done&style=none&width=448)

### 4.2.1、创建全新仓库
需要用GIT管理的项目的根目录执行：
# 在当前目录新建一个Git代码库
$ git init
**执行：**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072188-a9a4a096-9fab-4e1f-9c62-ca3820c2f9ae.png#align=left&display=inline&height=558&margin=%5Bobject%20Object%5D&originHeight=558&originWidth=1006&size=0&status=done&style=none&width=1006)
**结果：**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072226-139c46da-8ece-442d-bf3d-5396b5cf3dd0.png#align=left&display=inline&height=393&margin=%5Bobject%20Object%5D&originHeight=393&originWidth=872&size=0&status=done&style=none&width=872)
执行后可以看到，仅仅在项目目录多出了一个.git目录，关于版本等的所有信息都在这个目录里面。
当然如果使用如下命令，可以把创建目录与仓库一起完成：
# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]
 执行命令与运行结果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072235-b3ebef76-44a1-4eb8-b933-9daa7d46a783.png#align=left&display=inline&height=574&margin=%5Bobject%20Object%5D&originHeight=574&originWidth=946&size=0&status=done&style=none&width=946)

### 4.2.2、克隆远程仓库
 另一种方式是克隆远程目录，由于是将远程服务器上的仓库完全镜像一份至本地，而不是取某一个特定版本，所以用clone而不是checkout，语法格式如下：
# 克隆一个项目和它的整个代码历史(版本信息)
$ git clone [url]
**执行：**
比如我们要从克隆的远程仓库托管在github上，地址为：[https://github.com/zhangguo5/SuperPlus.git](https://github.com/zhangguo5/SuperPlus.git)，这是一个公开的项目
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072201-d9a5be53-15c2-4977-a3ea-e17a3623a703.png#align=left&display=inline&height=700&margin=%5Bobject%20Object%5D&originHeight=700&originWidth=1099&size=0&status=done&style=none&width=1099)
**![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072223-6f5b6891-ffe9-4109-ae07-567b33d674ed.png#align=left&display=inline&height=245&margin=%5Bobject%20Object%5D&originHeight=245&originWidth=911&size=0&status=done&style=none&width=911)**
**结果：**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072255-dd56c905-2fae-4b1b-bebe-5d8ad13ae49e.png#align=left&display=inline&height=433&margin=%5Bobject%20Object%5D&originHeight=433&originWidth=832&size=0&status=done&style=none&width=832)

## 4.3、GIT文件操作
版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。GIT不关心文件两个版本之间的具体差别，而是关心文件的整体是否有改变，若文件被改变，在添加提交时就生成文件新版本的快照，而判断文件整体是否改变的方法就是用SHA-1算法计算文件的校验和。

### 4.3.1、文件4种状态
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072808-04db77b4-0583-4519-8c61-7f05e01e0659.png#align=left&display=inline&height=330&margin=%5Bobject%20Object%5D&originHeight=330&originWidth=800&size=0&status=done&style=none&width=800)

- **Untracked**: 未跟踪, 此文件在文件夹中, 但并没有加入到git库, 不参与版本控制. 通过`git add` 状态变为`Staged`.

- **Unmodify**: 文件已经入库, 未修改, 即版本库中的文件快照内容与文件夹中完全一致. 这种类型的文件有两种去处, 如果它被修改, 而变为`Modified`. 如果使用`git rm`移出版本库, 则成为`Untracked`文件

- **Modified**: 文件已修改, 仅仅是修改, 并没有进行其他的操作. 这个文件也有两个去处, 通过`git add`可进入暂存`staged`状态, 使用`git checkout` 则丢弃修改过, 返回到`unmodify`状态, 这个`git checkout`即从库中取出文件, 覆盖当前修改

- **Staged**: 暂存状态. 执行`git commit`则将修改同步到库中, 这时库中的文件和本地文件又变为一致, 文件为`Unmodify`状态. 执行`git reset HEAD filename`取消暂存, 文件状态为`Modified`


![](https://cdn.nlark.com/yuque/0/2020/jpeg/322438/1604991072202-dc7cc161-9e8f-4613-b92d-207185b8e381.jpeg#align=left&display=inline&height=728&margin=%5Bobject%20Object%5D&originHeight=728&originWidth=1047&size=0&status=done&style=none&width=1047)

### 4.3.2、查看文件状态
上面说文件有4种状态，通过如下命令可以查看到文件的状态：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072261-e3099272-3e39-4bc4-9969-5115b83f9af1.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#查看指定文件状态
git status [filename]

#查看所有文件状态
git status
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072305-8d05e3e3-69bc-450c-914d-ba300c2df1f4.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
命令：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072258-0adac1b9-c20c-4fa5-9c6f-5d3668083a75.png#align=left&display=inline&height=647&margin=%5Bobject%20Object%5D&originHeight=647&originWidth=915&size=0&status=done&style=none&width=915)
结果：
foo.htm文件的状态为untracked（未跟踪），提示通过git add可以暂存
GIT在这一点做得很好，在输出每个文件状态的同时还说明了怎么操作，像上图就有怎么暂存、怎么跟踪文件、怎么取消暂存的说明。

### 4.3.3、添加文件与目录
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072258-d6b133e9-d06f-4eaa-9ab4-f718576a7795.png#align=left&display=inline&height=234&margin=%5Bobject%20Object%5D&originHeight=234&originWidth=458&size=0&status=done&style=none&width=458)
工作区（Working Directory）就是你在电脑里能看到的目录。
版本库（Repository）工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。
Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。
将untracked状态的文件添加到暂存区，语法格式如下：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072277-d828eb89-c7f9-4c18-befa-1c82e4f6130e.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072339-9952d6d2-e00c-4c01-86f0-3e896ed4fa9b.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
执行：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072410-a5b06bb1-b6a9-4013-8328-7a99de0b22bf.png#align=left&display=inline&height=627&margin=%5Bobject%20Object%5D&originHeight=627&originWidth=912&size=0&status=done&style=none&width=912)

### 4.3.4、移除文件与目录（撤销add）
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072438-2e9db504-b12e-4c83-857c-b941641191fc.png#align=left&display=inline&height=387&margin=%5Bobject%20Object%5D&originHeight=387&originWidth=775&size=0&status=done&style=none&width=775)
当执行如下命令时，会直接从暂存区删除文件，工作区则不做出改变
#直接从暂存区删除文件，工作区则不做出改变
git rm --cached <file>
执行命令
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072386-71d390c6-434c-4bbd-a7d4-4144f4dc7a9e.png#align=left&display=inline&height=431&margin=%5Bobject%20Object%5D&originHeight=431&originWidth=1009&size=0&status=done&style=none&width=1009)
通过重写目录树移除add文件：
#如果已经用add 命令把文件加入stage了，就先需要从stage中撤销
git reset HEAD <file>...
当执行 “git reset HEAD” 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
示例：把f1.txt文件从暂存区撤回工作区
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072397-b8a08635-19f6-4b70-90a5-a249ca673a30.png#align=left&display=inline&height=619&margin=%5Bobject%20Object%5D&originHeight=619&originWidth=733&size=0&status=done&style=none&width=733)
移除所有未跟踪文件
#移除所有未跟踪文件
#一般会加上参数-df，-d表示包含目录，-f表示强制清除。
git clean [options] 
示例：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072378-d2dba9c4-6ae6-4c92-844f-6cc4bcf758b5.png#align=left&display=inline&height=217&margin=%5Bobject%20Object%5D&originHeight=217&originWidth=863&size=0&status=done&style=none&width=863)
移除前：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072425-06ae2ab5-fa14-4b69-a8da-ee55913b0609.png#align=left&display=inline&height=240&margin=%5Bobject%20Object%5D&originHeight=240&originWidth=858&size=0&status=done&style=none&width=858)
执行移除：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072390-f7cb6f59-97ff-40de-a47c-448f24b32975.png#align=left&display=inline&height=66&margin=%5Bobject%20Object%5D&originHeight=66&originWidth=859&size=0&status=done&style=none&width=859)
移除后：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072459-d7882519-02e7-4054-ae54-0a4cea7cea2b.png#align=left&display=inline&height=216&margin=%5Bobject%20Object%5D&originHeight=216&originWidth=859&size=0&status=done&style=none&width=859)
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072397-79b81df8-4849-448b-b230-c0dd5911213a.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#只从stage中删除，保留物理文件
git rm --cached readme.txt 

#不但从stage中删除，同时删除物理文件
git rm readme.txt 

#把a.txt改名为b.txt
git mv a.txt b.txt 
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072386-23180a16-9b8d-4bef-a12a-1f94eea5663b.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
当执行提交操作（git commit）时，暂存区的目录树写到版本库（对象库）中，master 分支会做相应的更新。即 master 指向的目录树就是提交时暂存区的目录树。
当执行 “git reset HEAD” 命令时，暂存区的目录树会被重写，被 master 分支指向的目录树所替换，但是工作区不受影响。
当执行 “git rm –cached <file>” 命令时，会直接从暂存区删除文件，工作区则不做出改变。
当执行 “git checkout .” 或者 “git checkout — <file>” 命令时，会用暂存区全部或指定的文件替换工作区的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。
当执行 “git checkout HEAD .” 或者 “git checkout HEAD <file>” 命令时，会用 HEAD 指向的 master 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改 动。

### 4.3.5、查看文件修改后的差异
git diff用于显示WorkSpace中的文件和暂存区文件的差异
用"git status"只能查看对哪些文件做了改动，如果要看改动了什么，可以用：
#查看文件修改后的差异
git diff [files]
命令：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072442-629b5482-f78c-43b3-a900-0bdac35af7e3.png#align=left&display=inline&height=582&margin=%5Bobject%20Object%5D&originHeight=582&originWidth=1109&size=0&status=done&style=none&width=1109)
 ---a表示修改之前的文件，+++b表示修改后的文件
#比较暂存区的文件与之前已经提交过的文件
git diff --cached
也可以把WorkSpace中的状态和repo中的状态进行diff，命令如下:
#比较repo与工作空间中的文件差异
git diff HEAD~n
**![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072409-27052529-b121-4148-9ff4-23c864d03735.png#align=left&display=inline&height=346&margin=%5Bobject%20Object%5D&originHeight=451&originWidth=821&size=0&status=done&style=none&width=629)**

### **4.3.6、签出**
如果仓库中已经存在文件f4.txt，在工作区中对f4修改了，如果想撤销可以使用checkout，签出覆盖
检出命令git checkout是git最常用的命令之一，同时也是一个很危险的命令，因为这条命令会重写工作区
语法：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072439-47ba6f77-ed1b-40c1-b0a6-60e41ba83eca.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#用法一
git checkout [-q] [<commit>] [--] <paths>...
#用法二
git checkout [<branch>]
#用法三
git checkout [-m] [[-b]--orphan] <new_branch>] [<start_point>]
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072476-241dbf03-b480-4cc1-b91f-41e9c1642010.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
<commit>是可选项，如果省略则相当于从暂存区（index）进行检出
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072463-429d6d53-d62f-4dc2-94cf-36c948279fad.png#align=left&display=inline&height=229&margin=%5Bobject%20Object%5D&originHeight=229&originWidth=529&size=0&status=done&style=none&width=529)
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072828-9caeb6cd-f798-4bdf-9d3a-0f3774aa7990.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
$ git checkout branch
#检出branch分支。要完成图中的三个步骤，更新HEAD以指向branch分支，以及用branch  指向的树更新暂存区和工作区。

$ git checkout
#汇总显示工作区、暂存区与HEAD的差异。

$ git checkout HEAD
#同上

$ git checkout -- filename
#用暂存区中filename文件来覆盖工作区中的filename文件。相当于取消自上次执行git add filename以来（如果执行过）的本地修改。

$ git checkout branch -- filename
#维持HEAD的指向不变。用branch所指向的提交中filename替换暂存区和工作区中相   应的文件。注意会将暂存区和工作区中的filename文件直接覆盖。

$ git checkout -- . 或写作 git checkout .
#注意git checkout 命令后的参数为一个点（“.”）。这条命令最危险！会取消所有本地的  #修改（相对于暂存区）。相当于用暂存区的所有文件直接覆盖本地文件，不给用户任何确认的机会！

$ git checkout commit_id -- file_name
#如果不加commit_id，那么git checkout -- file_name 表示恢复文件到本地版本库中最新的状态。
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072621-75123eb9-7c4f-4a0c-9dea-e726a3697deb.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
示例： 
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072595-9bc855d8-84c4-45ca-baa2-c89bc633256a.png#align=left&display=inline&height=417&margin=%5Bobject%20Object%5D&originHeight=417&originWidth=787&size=0&status=done&style=none&width=787)

### 4.3.6、忽略文件
有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等
在主目录下建立".gitignore"文件，此文件有如下规则：

1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
1. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等。
1. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略。
1. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
1. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

如：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072597-31b3ba3d-ebef-4817-826e-75f7e9f715a7.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#为注释
*.txt #忽略所有 .txt结尾的文件
!lib.txt #但lib.txt除外
/temp #仅忽略项目根目录下的TODO文件,不包括其它目录temp
build/ #忽略build/目录下的所有文件
doc/*.txt #会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072558-f2890551-413c-45b6-960f-88fbeeb3b38d.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
[更多规则请点这里](http://www.cnblogs.com/kevingrace/p/5690241.html)
示例：
创建一个.gitignore文件忽视所有的日志文件
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072584-36df4bad-849b-41cc-8452-de8abf283667.png#align=left&display=inline&height=319&margin=%5Bobject%20Object%5D&originHeight=319&originWidth=893&size=0&status=done&style=none&width=893)
查看状态：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072570-64069c7a-18d2-4437-8545-7a03953e475c.png#align=left&display=inline&height=333&margin=%5Bobject%20Object%5D&originHeight=333&originWidth=867&size=0&status=done&style=none&width=867)
从上图中可以看出2个日志文件并没有添加到暂存区，直接被忽视了。
针对各种语言与项目的Git忽视文件： [https://github.com/kaedei/gitignore](https://github.com/kaedei/gitignore)   [https://github.com/github/gitignore](https://github.com/github/gitignore)
通用的java忽视文件：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072564-dbc3b64d-ad04-4a23-b1fa-1108cf8a54ec.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
# Compiled class file
*.class

# Log file
*.log

# BlueJ files
*.ctxt

# Mobile Tools for Java (J2ME)
.mtj.tmp/

# Package Files #
*.jar
*.war
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see [http://www.java.com/en/download/help/error_hotspot.xml](http://www.java.com/en/download/help/error_hotspot.xml)
hs_err_pid*
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072673-ded79da2-a7ed-4159-947c-37b3c835c59d.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
通用的Visual Studio开发项目忽视文件：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072664-bfe2cd99-f9bc-49ed-a0ae-1cda67f8170f.gif#align=left&display=inline&height=16&margin=%5Bobject%20Object%5D&originHeight=16&originWidth=11&size=0&status=done&style=none&width=11) View Code
idea忽视文件：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072578-d1a85283-ce11-47b3-aa30-b26691da19de.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
.idea/
*.iml
out/
gen/
idea-gitignore.jar
resources/templates.list
resources/gitignore/*
build/
build.properties
junit*.properties
IgnoreLexer.java~
.gradle

/verification
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072613-d9166083-22ed-408f-a402-e956d7ea7d4d.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)


### 4.3.7、提交
通过add只是将文件或目录添加到了index暂存区，使用commit可以实现将暂存区的文件提交到本地仓库。
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072548-0f81f39d-1461-456d-a1b9-b5048de5e8cb.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区，跳过了add,对新文件无效
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072708-00ba73b4-8a17-4cab-bd36-7728a7d3ff74.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
示例：
提交前的状态
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072561-f506d948-d1e4-4172-a279-f90c3a05b787.png#align=left&display=inline&height=305&margin=%5Bobject%20Object%5D&originHeight=305&originWidth=608&size=0&status=done&style=none&width=608)
提交：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072695-561959df-0654-432d-bfba-6b709eb5480e.png#align=left&display=inline&height=158&margin=%5Bobject%20Object%5D&originHeight=158&originWidth=945&size=0&status=done&style=none&width=945)
提交后的状态：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072564-91a917d5-7f09-4cac-988c-48774b901f4e.png#align=left&display=inline&height=234&margin=%5Bobject%20Object%5D&originHeight=234&originWidth=859&size=0&status=done&style=none&width=859)
从上图中可以看出暂存区中没有了bar.htm
**修订提交**
如果我们提交过后发现有个文件改错了，或者只是想修改提交说明，这时可以对相应文件做出修改，将修改过的文件通过"git add"添加到暂存区，然后执行以下命令：
#修订提交
git commit --amend
**撤销提交（commit）**
原理就是放弃工作区和index的改动，同时HEAD指针指向前一个commit对象
#撤销上一次的提交
git reset --hard HEAD~1
 要通过git log查看提交日志，也可直接指定提交编号或序号
示例：
**![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072562-9d1d1d1d-b5e9-4ba3-a3f1-4a5fea233124.png#align=left&display=inline&height=493&margin=%5Bobject%20Object%5D&originHeight=493&originWidth=814&size=0&status=done&style=none&width=814)**
撤销提交
git revert <commit-id>
这条命令会把指定的提交的所有修改回滚，并同时生成一个新的提交。

### 4.3.8、日志与历史
查看提交日志可以使用git log指令，语法格式如下：
#查看提交日志
git log [<options>] [<revision range>] [[\--] <path>…?]
示例：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072561-fa10bd0a-5266-4842-bd32-434e46edaa9b.png#align=left&display=inline&height=330&margin=%5Bobject%20Object%5D&originHeight=330&originWidth=861&size=0&status=done&style=none&width=861)
"git log --graph"以图形化的方式显示提交历史的关系，这就可以方便地查看提交历史的分支信息，当然是控制台用字符画出来的图形。
"git log -1"则表示显示1行。
使用history可以查看您在bash下输入过的指令：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072560-18df223a-bcbb-4379-a55b-2652a5401f45.png#align=left&display=inline&height=379&margin=%5Bobject%20Object%5D&originHeight=379&originWidth=868&size=0&status=done&style=none&width=868)
几乎所有输入过的都被记录下来的，不愧是做版本控制的。
**查看所有分支日志**
"git reflog"中会记录这个仓库中所有的分支的所有更新记录，包括已经撤销的更新。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072579-7b324190-8041-44fa-939e-024262740e38.png#align=left&display=inline&height=345&margin=%5Bobject%20Object%5D&originHeight=345&originWidth=919&size=0&status=done&style=none&width=919)

### 4.3.9、查看文件列表
使用git ls-files指令可以查看指定状态的文件列表，格式如下：
#查看指定状态的文件
git ls-files [-z] [-t] [-v] (--[cached|deleted|others|ignored|stage|unmerged|killed|modified])* (-[c|d|o|i|s|u|k|m])*
示例：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072579-8f5854a1-2c91-4a3d-874e-3fbf6695703a.png#align=left&display=inline&height=443&margin=%5Bobject%20Object%5D&originHeight=443&originWidth=762&size=0&status=done&style=none&width=762)

### 4.3.10、撤销更新
**1）、撤销暂存区更新**
使用"git add"把更新提交到了暂存区。这时"git status"的输出中提示我们可以通过"git reset HEAD <file>..."把暂存区的更新移出到WorkSpace中
示例：f6已经提交，工作区修改，暂存区修改，撤销
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072607-57f78b91-b522-4f88-bf6c-fe378c1bda07.png#align=left&display=inline&height=473&margin=%5Bobject%20Object%5D&originHeight=473&originWidth=823&size=0&status=done&style=none&width=823)
**2)、撤销本地仓库更新**
使用git log查看提交日志
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072805-0eb6e815-4c4d-4843-bba9-2cd5f6976a89.png#align=left&display=inline&height=406&margin=%5Bobject%20Object%5D&originHeight=406&originWidth=726&size=0&status=done&style=none&width=726)
撤销提交有两种方式：**使用HEAD指针**和**使用commit id**
在Git中，有一个HEAD指针指向当前分支中最新的提交。当前版本，我们使用"HEAD^"，那么再钱一个版本可以使用"HEAD^^"，如果想回退到更早的提交，可以使用"HEAD~n"。（也就是，HEAD^=HEAD~1，HEAD^^=HEAD~2）
git reset --hard HEAD^
git reset --hard HEAD~1
git reset --59cf9334cf957535cb328f22a1579b84db0911e5
示例：回退到添加f6
回退前：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072708-beb98838-dad4-4e3e-959a-9c2efaba7810.png#align=left&display=inline&height=67&margin=%5Bobject%20Object%5D&originHeight=67&originWidth=733&size=0&status=done&style=none&width=733)
回退后：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072726-f47c0cc3-39a9-4aee-ae53-40079f8638de.png#align=left&display=inline&height=142&margin=%5Bobject%20Object%5D&originHeight=142&originWidth=731&size=0&status=done&style=none&width=731)
现在又想恢复被撤销的提交可用"git reflog"查看仓库中所有的分支的所有更新记录，包括已经撤销的更新，撤销方法与前面一样。
git reset --hard HEAD@{7}
git reset --hard e0e79d7
--hard：撤销并删除相应的更新
--soft：撤销相应的更新，把这些更新的内容放到Stage中

### 4.3.11、删除文件
**1）、删除未跟踪文件**
如果文件还是未跟踪状态，直接删除文件就可了，bash中使用rm可以删除文件，示例如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072717-9a07d6e6-f190-4476-b099-126936f2d9a4.png#align=left&display=inline&height=324&margin=%5Bobject%20Object%5D&originHeight=324&originWidth=932&size=0&status=done&style=none&width=932)
**2）、删除已提交文件**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072719-c5414752-a71f-4219-b5db-7224a82e0d6d.png#align=left&display=inline&height=548&margin=%5Bobject%20Object%5D&originHeight=548&originWidth=1069&size=0&status=done&style=none&width=1069)
-f 强制删除，物理删除了，同时删除工作区和暂存区中的文件
**撤销删除：**
#to discard changes in working directory
git checkout -- <file>...
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072717-015c158b-c0c6-4d9d-8ff1-afa65be385ee.png#align=left&display=inline&height=459&margin=%5Bobject%20Object%5D&originHeight=459&originWidth=1050&size=0&status=done&style=none&width=1050)
**3）、删除暂存区的文件，不删除工作区的文件**
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072725-4acf9c58-1e16-43d4-a4d1-798f4a03111d.png#align=left&display=inline&height=495&margin=%5Bobject%20Object%5D&originHeight=495&originWidth=919&size=0&status=done&style=none&width=919)
使用git reset HEAD <file>...同样可以实现上面的功能

### 4.3.12、文件操作小结
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072810-8d4f0bd7-9ec2-405a-b0ca-ffa5984facb3.png#align=left&display=inline&height=614&margin=%5Bobject%20Object%5D&originHeight=614&originWidth=529&size=0&status=done&style=none&width=529)
 Git很强大，很灵活，这是毋庸置疑的。但也正因为它的强大造成了它的复杂，因此会有很多奇奇怪怪的问题出现，多用就好了。

## 4.4、GIT分支
分支在GIT中相对较难
分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。
如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN！
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072856-01212855-e619-4f72-be1d-c240834b8b78.png#align=left&display=inline&height=179&margin=%5Bobject%20Object%5D&originHeight=179&originWidth=561&size=0&status=done&style=none&width=561)
分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。
现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。
Git分支的速度非常快。
截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072771-d1c08ead-9937-4f36-a38f-592c34dda539.png#align=left&display=inline&height=310&margin=%5Bobject%20Object%5D&originHeight=310&originWidth=445&size=0&status=done&style=none&width=445)
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072704-ac8c7c41-f372-4485-b4f7-2dd1ee864ee9.gif#align=left&display=inline&height=799&margin=%5Bobject%20Object%5D&originHeight=768&originWidth=575&size=0&status=done&style=none&width=598)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072773-d00cf252-bfac-446b-9334-fdbed7de14a0.png#align=left&display=inline&height=259&margin=%5Bobject%20Object%5D&originHeight=259&originWidth=577&size=0&status=done&style=none&width=577)
git分支中常用指令：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072838-371b13f3-f913-4c00-9cbf-923b8c499f8b.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072762-7723d4a3-5f26-4d8b-8746-fea8b34bb295.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)

### 4.4.1、新建分支与切换分支
每次提交，Git都把它们串成一条时间线，这条时间线就是一个分支。截止到目前，只有一条时间线，在Git里，这个分支叫主分支，即master分支。HEAD严格来说不是指向提交，而是指向master，master才是指向提交的，所以，HEAD指向的就是当前分支。
一开始的时候，master分支是一条线，Git用master指向最新的提交，再用HEAD指向master，就能确定当前分支，以及当前分支的提交点：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072930-9722a477-de8c-4c88-bdb1-973aa6fed6a4.png#align=left&display=inline&height=159&margin=%5Bobject%20Object%5D&originHeight=159&originWidth=300&size=0&status=done&style=none&width=300)
每次提交，master分支都会向前移动一步，这样，随着你不断提交，master分支的线也越来越长：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072854-570f1a72-c6f7-454a-b428-704ec5063e23.gif#align=left&display=inline&height=600&margin=%5Bobject%20Object%5D&originHeight=600&originWidth=800&size=0&status=done&style=none&width=800)
默认分支是这样的，master是主分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072928-d2c678e7-5273-4678-a775-c8d5529a5491.png#align=left&display=inline&height=151&margin=%5Bobject%20Object%5D&originHeight=151&originWidth=301&size=0&status=done&style=none&width=301)
1）、新建一个分支，但依然停留在当前分支，使用：$ git branch [branch-name]
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072747-a738bda4-2ef7-4183-9e2b-bab2d678aa91.png#align=left&display=inline&height=381&margin=%5Bobject%20Object%5D&originHeight=381&originWidth=968&size=0&status=done&style=none&width=968)
切换分支到dev1后的结果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072724-ae6761a3-7a88-4069-829b-b566bfc02864.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&originHeight=192&originWidth=818&size=0&status=done&style=none&width=818)
[关于分支廖雪峰解释的比较清楚，我们引用一下](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840038939c291467cc7c747b1810aab2fb8863508000)。
当我们创建新的分支，例如`dev`时，Git新建了一个指针叫`dev`，指向`master`相同的提交，再把`HEAD`指向`dev`，就表示当前分支在`dev`上：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073107-0d014017-8b27-48c9-8bb1-1a40e6406f13.png#align=left&display=inline&height=233&margin=%5Bobject%20Object%5D&originHeight=233&originWidth=367&size=0&status=done&style=none&width=367)
你看，Git创建一个分支很快，因为除了增加一个`dev`指针，改改`HEAD`的指向，工作区的文件都没有任何变化！
不过，从现在开始，对工作区的修改和提交就是针对`dev`分支了，比如新提交一次后，`dev`指针往前移动一步，而`master`指针不变：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072865-f9c57f19-17bb-4cb4-99df-88571023bed8.png#align=left&display=inline&height=233&margin=%5Bobject%20Object%5D&originHeight=233&originWidth=494&size=0&status=done&style=none&width=494)
假如我们在`dev`上的工作完成了，就可以把`dev`合并到`master`上。Git怎么合并呢？最简单的方法，就是直接把`master`指向`dev`的当前提交，就完成了合并：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072945-ad2ccbd2-3275-48a0-869a-5dd50c4748fc.png#align=left&display=inline&height=222&margin=%5Bobject%20Object%5D&originHeight=222&originWidth=423&size=0&status=done&style=none&width=423)
所以Git合并分支也很快！就改改指针，工作区内容也不变！
合并完分支后，甚至可以删除`dev`分支。删除`dev`分支就是把`dev`指针给删掉，删掉后，我们就剩下了一条`master`分支：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073059-4c45996e-729d-49cb-bb34-3b12cc1d7cbd.png#align=left&display=inline&height=159&margin=%5Bobject%20Object%5D&originHeight=159&originWidth=423&size=0&status=done&style=none&width=423)
动画演示：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991072752-9b78f97c-14c6-41c1-a538-07c7f342d60f.gif#align=left&display=inline&height=600&margin=%5Bobject%20Object%5D&originHeight=600&originWidth=800&size=0&status=done&style=none&width=800)
2）、切换分支，git branch <name>，如果name为-则为上一个分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072714-bc3ed518-64a7-4550-b375-1cd2563445fd.png#align=left&display=inline&height=192&margin=%5Bobject%20Object%5D&originHeight=192&originWidth=739&size=0&status=done&style=none&width=739)
切换为上一个分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072773-b725a34c-4638-449d-99d0-9fa158470ab2.png#align=left&display=inline&height=113&margin=%5Bobject%20Object%5D&originHeight=113&originWidth=752&size=0&status=done&style=none&width=752)
3）、新建一个分支，并切换到该分支，$ git checkout -b [branch]
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072779-b7b0dbc3-49d3-44a5-a867-36850461ae93.png#align=left&display=inline&height=173&margin=%5Bobject%20Object%5D&originHeight=173&originWidth=705&size=0&status=done&style=none&width=705)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072908-975c00ce-cf93-4852-a934-fad98485b5cd.png#align=left&display=inline&height=139&margin=%5Bobject%20Object%5D&originHeight=139&originWidth=812&size=0&status=done&style=none&width=812)
4）、新建一个分支，指向指定commit使用命令：$ git branch [branch] [commit]
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072945-ba381f69-c4d6-44dc-b14a-7c2624b6ee9d.png#align=left&display=inline&height=313&margin=%5Bobject%20Object%5D&originHeight=313&originWidth=736&size=0&status=done&style=none&width=736)
上面创建了dev3分支且指向了master中首次提交的位置，切换到dev3查看日志如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072892-84246b4e-b265-445d-9adf-67424eb3d862.png#align=left&display=inline&height=270&margin=%5Bobject%20Object%5D&originHeight=270&originWidth=724&size=0&status=done&style=none&width=724)
master上本来有两个提交记录的，此时的dev3指向的是第1次提交的位置
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072915-1656585c-c448-4e90-b790-f7ba7fa9bdf5.png#align=left&display=inline&height=302&margin=%5Bobject%20Object%5D&originHeight=302&originWidth=816&size=0&status=done&style=none&width=816)
 5）、新建一个分支，与指定的远程分支建立追踪关系使用命令：$ git branch --track [branch] [remote-branch]
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072872-2fc1cbc3-5703-4a0a-be99-3a28356e9056.png#align=left&display=inline&height=575&margin=%5Bobject%20Object%5D&originHeight=575&originWidth=738&size=0&status=done&style=none&width=738)

### 4.4.2、查看分支
1）、列出所有本地分支使用$ git branch
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072900-da22979a-181b-43be-afe6-e8c3866d0bba.png#align=left&display=inline&height=139&margin=%5Bobject%20Object%5D&originHeight=139&originWidth=723&size=0&status=done&style=none&width=723)
2）、列表所有远程分支使用$ git branch -r
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072869-f0ffa085-7daa-4514-8a95-49408e16d8a8.png#align=left&display=inline&height=88&margin=%5Bobject%20Object%5D&originHeight=88&originWidth=718&size=0&status=done&style=none&width=718)
3)、列出所有本地分支和远程分支使用$ git branch -a
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072872-4511050e-51e7-4f8b-a23e-7e3c2de26380.png#align=left&display=inline&height=184&margin=%5Bobject%20Object%5D&originHeight=184&originWidth=722&size=0&status=done&style=none&width=722)

### 4.4.3、分支合并
合并指定分支到当前分支使用指令$ git merge [branch]
这里的合并分支就是对分支的指针操作，我们先创建一个分支再合并到主分支：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073193-def84ae8-206a-43a9-947d-068d0d8c39e9.png#align=left&display=inline&height=637&margin=%5Bobject%20Object%5D&originHeight=637&originWidth=733&size=0&status=done&style=none&width=733)
这里的file11.txt主分支与dev6的内容现在是不同的，因为在dev6中已被修改过，我们可以使用指令查看：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072892-628f868d-fe52-4882-8832-0a3e77f1f124.png#align=left&display=inline&height=239&margin=%5Bobject%20Object%5D&originHeight=239&originWidth=665&size=0&status=done&style=none&width=665)
现在我们将dev6合并到主分支中去，从下图中可以看出dev6中有一次提交，而master并没有
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072879-1326640f-3f1d-4ac0-bf8d-e1811149e88d.png#align=left&display=inline&height=314&margin=%5Bobject%20Object%5D&originHeight=314&originWidth=816&size=0&status=done&style=none&width=816)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072887-f3acea83-3e21-4e91-b419-b4b2bda483a5.png#align=left&display=inline&height=248&margin=%5Bobject%20Object%5D&originHeight=248&originWidth=698&size=0&status=done&style=none&width=698)
合并后在master上查看file11.txt文件内容与dev6上的内容就一样了，合并后dev6中多出的提交在master也拥有了。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072927-2c48c489-b08e-4a7e-a970-885086d140ad.png#align=left&display=inline&height=304&margin=%5Bobject%20Object%5D&originHeight=304&originWidth=821&size=0&status=done&style=none&width=821)

### 4.4.4、解决冲突
如果同一个文件在合并分支时都被修改了则会引起冲突，如下所示：
提交前两个分支的状态
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072898-8cb4d07b-fa5c-4594-9dec-674e9c954bad.png#align=left&display=inline&height=164&margin=%5Bobject%20Object%5D&originHeight=164&originWidth=714&size=0&status=done&style=none&width=714)
在dev6分支中同样修改file11.txt
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072935-fa43c0fc-c189-4170-b805-a28bb5ab45d1.png#align=left&display=inline&height=290&margin=%5Bobject%20Object%5D&originHeight=290&originWidth=733&size=0&status=done&style=none&width=733)
dev6与master分支中file11.txt文件都被修改且提交了，现在合并分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072928-df8d4413-75d6-4ea4-9521-76ee3bc0dcf1.png#align=left&display=inline&height=437&margin=%5Bobject%20Object%5D&originHeight=437&originWidth=760&size=0&status=done&style=none&width=760)
提示冲突，现在我们看看file11.txt在master分支中的状态
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072890-a1f545f5-403d-400d-bdf9-5c1960501efe.png#align=left&display=inline&height=153&margin=%5Bobject%20Object%5D&originHeight=153&originWidth=764&size=0&status=done&style=none&width=764)
Git用<<<<<<<，=======，>>>>>>>标记出不同分支的内容，其中<<<HEAD是指主分支修改的内容，>>>>>dev6 是指dev6上修改的内容
解决的办法是我们可以修改冲突文件后重新提交，请注意当前的状态产master | MERGING：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072930-321f28c2-5b1f-47eb-b620-c3fd26443c33.png#align=left&display=inline&height=101&margin=%5Bobject%20Object%5D&originHeight=101&originWidth=744&size=0&status=done&style=none&width=744)
重新提交后冲突解决：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072975-5e31a551-b041-401e-8e6b-7231afdca574.png#align=left&display=inline&height=250&margin=%5Bobject%20Object%5D&originHeight=250&originWidth=750&size=0&status=done&style=none&width=750)
手动解决完冲突后就可以把此文件添 加到索引(index)中去，用git commit命令来提交，就像平时修改了一个文件 一样。
用_git log --graph_命令可以看到分支合并图。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072956-51672cd1-2f11-4607-be1a-d3dbdbe26fb4.png#align=left&display=inline&height=318&margin=%5Bobject%20Object%5D&originHeight=318&originWidth=703&size=0&status=done&style=none&width=703)
**分支策略**
master主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的dev分支上工作，工作完后，比如上要发布，或者说dev分支代码稳定后可以合并到主分支master上来。

### 4.4.5、删除分支
删除本地分支可以使用命令：$ git branch -d [branch-name]，-D（大写）强制删除
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072954-f5ee0fdd-9d67-46cc-adaa-90e39ca571d3.png#align=left&display=inline&height=532&margin=%5Bobject%20Object%5D&originHeight=532&originWidth=700&size=0&status=done&style=none&width=700)
删除远程分支可以使用如下指令：
$ git push origin --delete [branch-name]

$ git branch -dr [remote/branch]
-d表示删除分支。分支必须完全合并在其上游分支，或者在HEAD上没有设置上游
-r表示远程的意思remotes，如果-dr则表示删除远程分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072968-90c5b719-ce25-487e-96e8-32e84558cce1.png#align=left&display=inline&height=442&margin=%5Bobject%20Object%5D&originHeight=442&originWidth=683&size=0&status=done&style=none&width=683)

## 4.5、Git GUI 操作
通过命令行可以深刻的理解Git，Git GUI或IDE插件却可以更加直观操作Git，常用的Git GUI有如下这些：

### 4.5.1、GitHub for Desktop
全球开发人员交友俱乐部提供的强大工具，功能完善，使用方便。对于使用GitHub的开发人员来说是非常便捷的工具。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072995-82333357-2515-4471-a2c1-07afc6d297f9.png#align=left&display=inline&height=810&margin=%5Bobject%20Object%5D&originHeight=810&originWidth=1234&size=0&status=done&style=none&width=1234)
GitHub for Desktop不带三方合并工具，你必须自己手动解决冲突才可以。
– 免费
– 同时支持 Windows 和 Mac：对于需要经常在不同的操作系统间切换的开发人员来说非常方便。
– 漂亮的界面：作为每天盯着看的工具，颜值是非常重要的
– 支持Pull Request：直接从客户端提交PR，很方便
– Timeline 支持：直接在时间线上显示每次提交的时间点和大小
– 支持git LFS：存储大文件更加节省空间和高效
– 不支持三方合并：需要借助第三方工具才行

### 4.5.2、Source Tree
SourceTree是老牌的Git GUI管理工具了，也号称是最好用的Git GUI工具。强大，功能丰富，基本操作和高级操作都设计得非常流畅，适合初学者上手，支持Git Flow。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073017-daf4c3d5-a50d-4daa-8ef7-5143c61e3dbb.png#align=left&display=inline&height=704&margin=%5Bobject%20Object%5D&originHeight=704&originWidth=1050&size=0&status=done&style=none&width=1050)
– 免费
– 功能强大：无论你是新手还是重度用户，SourceTree 都会让你觉得很顺手。对于非常重度用户，Source Tree还支持自定义脚本的执行。
– 同时支持 Windows 和 Mac 操作系统
– 同时支持 Git 和 Mercurial 两种 VCS
– 内置GitHub, BitBucket 和 Stash 的支持：直接绑定帐号即可操作远程repo

### 4.5.3、TortoiseGit
小乌龟，SVN的超广泛使用也使得这个超好用的Svn客户端成了几乎每个开发人员的桌面必备软件。小乌龟只提供Windows版本，提供中文版支持的。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072957-9555434c-d2a8-403a-95c6-f2e2c8094f83.png#align=left&display=inline&height=759&margin=%5Bobject%20Object%5D&originHeight=759&originWidth=925&size=0&status=done&style=none&width=925)
– 免费
– 只支持Windows操作系统：与文件管理器的良好集成
– 中文界面
– 与TortoiseSVN一脉相承的操作体验

### 4.5.4、Git集成Gui工具
安装Git时会集成安装Gui工具，在Git菜单下可以找到，特点是：免费、简单、不需要额外安装
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073018-621f5675-d6ba-414b-91c6-72a3d96daf14.png#align=left&display=inline&height=532&margin=%5Bobject%20Object%5D&originHeight=532&originWidth=942&size=0&status=done&style=none&width=942)

## 4.6、IDE集成的Git客户端
对于使用IDE进行开发的程序员来说，可以不离开常用的IDE就直接操作源代码管理系统是最好的选择，以下是我对几个常见的IDE集成的git客户端：

### 4.6.1、Eclipse – Egit
作为Java集成开发环境的代表，Eclipse内置了egit这个插件来提供git的集成支持。实话实说，这个插件的功能非常丰富，无论是普通的clone, commit, pull/push操作；还是复杂一些的git flow都有支持。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072967-245b6142-db55-4e25-aff0-c6148df60328.png#align=left&display=inline&height=771&margin=%5Bobject%20Object%5D&originHeight=771&originWidth=1140&size=0&status=done&style=none&width=1140)

### 4.6.2、Visual Studio – Git Integration & GitHub Extension
VS里面的Git支持已经相当的完善。直接克隆github上的repo
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072977-9ce35911-3435-40a8-aeb1-afd0507096a8.png#align=left&display=inline&height=519&margin=%5Bobject%20Object%5D&originHeight=519&originWidth=939&size=0&status=done&style=none&width=939)

![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072977-641e737a-055e-47bc-962e-0d138248f0e4.png#align=left&display=inline&height=781&margin=%5Bobject%20Object%5D&originHeight=781&originWidth=980&size=0&status=done&style=none&width=980)

### 4.6.3、IntelliJ IDEA
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991072997-cc81e2b0-e3fc-45e5-93fa-6cb253b0c8db.png#align=left&display=inline&height=738&margin=%5Bobject%20Object%5D&originHeight=738&originWidth=1361&size=0&status=done&style=none&width=1361)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073017-e7f9d08f-d7f8-456e-ac49-f7084115fef6.png#align=left&display=inline&height=736&margin=%5Bobject%20Object%5D&originHeight=736&originWidth=873&size=0&status=done&style=none&width=873)

## 4.7、帮助与代码统计
**1）、帮助文档**
完整的安装了Git后有一个官方帮助，这是最权威的资料，方法如下：
比如我们要查看git commit的使用
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073036-101667b5-89d1-4540-9f48-b6f4fda0e146.png#align=left&display=inline&height=528&margin=%5Bobject%20Object%5D&originHeight=528&originWidth=1061&size=0&status=done&style=none&width=1061)
执行时会打开对应的git帮助文档，其实就在本地，当然您也可以去官网在线搜索，地址是： [https://git-scm.com/docs](https://git-scm.com/docs)。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073026-7ffda569-05f0-4de8-b000-8cb352aa7ca6.png#align=left&display=inline&height=634&margin=%5Bobject%20Object%5D&originHeight=634&originWidth=975&size=0&status=done&style=none&width=975)
**2）、信息查看与统计命令**
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073163-fac6a80e-c36d-439c-a4f1-d686ee02dcf6.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#统计某人的代码提交量，包括增加，删除：
git log --author=**"$(git config --get user.name)"** --pretty=tformat: --numstat | gawk **'{ add += $1 ; subs += $2 ; loc += $1 - $2 } END { printf **
"added lines: %s removed lines : %s total lines: %s\n",add,subs,loc }**'** -

#仓库提交者排名前 5（如果看全部，去掉 head 管道即可）：
git log --pretty=**'%aN'** | sort | uniq -c | sort -k1 -n -r | head -n 5

#仓库提交者（邮箱）排名前 5：这个统计可能不会太准，因为很多人有不同的邮箱，但会使用相同的名字
git log --pretty=format:%ae | gawk -- **'{ ++c[$0]; } END { for(cc in c) printf "%5d %s\n",c[cc],cc; }'** | sort -u -n -r | head -n 5

#贡献者统计：
git log --pretty=**'%aN'** | sort -u | wc -l

#提交数统计：
git log --oneline | wc -l 

# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat **"@{0 day ago}"**

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073164-6592539c-ed06-40ec-8ef3-f79e78f5fea4.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
示例：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073056-a1298f7c-357e-4b8f-b415-1a3fa8d8b0cb.png#align=left&display=inline&height=419&margin=%5Bobject%20Object%5D&originHeight=419&originWidth=938&size=0&status=done&style=none&width=938)

# 五、远程仓库
Git是分布式版本控制系统，同一个Git仓库，可以分布到不同的机器上，但开发参与者必须在同一个网络中，且必须有一个项目的原始版本，通常的办法是让一台电脑充当服务器的角色，每天24小时开机，其他每个人都从这个“服务器”仓库克隆一份到自己的电脑上，并且各自把各自的提交推送到服务器仓库里，也从服务器仓库中拉取别人的提交。完全可以自己搭建一台运行Git的服务器但现在更适合的做法是使用免费的托管平台。
同时相较于传统的代码都是管理到本机或者内网。 一旦本机或者内网机器出问题，代码可能会丢失，使用远端代码仓库将永远存在一个备份。同时也免去了搭建本地代码版本控制服务的繁琐。 云计算时代 Git 以其强大的分支和克隆功能，更加方便了开发者远程协作。

## 5.1、托管平台
Git代码托管平台，首先推荐的是GitHub，好多好的开源项目都来自GitHub，但是GitHub只能新建公开的Git仓库，私有仓库要收费，有时候访问比较卡，如果你做的是一个开源项目，可以首选GitHub。下面推荐几个比较好的Git代码托管平台：

### **5.1.1、GitHub**
关于GItHub相信大家都有耳闻，我就不详细介绍了。GitHub地址： [https://github.com/](https://github.com/)，其首页如图：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073031-bacc46c7-9c8f-4f28-8d51-f8fc447cbe2b.png#align=left&display=inline&height=734&margin=%5Bobject%20Object%5D&originHeight=734&originWidth=1072&size=0&status=done&style=none&width=1072)

### **5.1.2、Gitlab**
对于有些人，提到GitHub就会自然的想到Gitlab,Gitlab支持无限的公有项目和私有项目。Gitlab地址： [https://about.gitlab.com/](https://about.gitlab.com/)，其首页截图如图：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073070-b927e7b5-332b-472a-97b8-365e20083811.png#align=left&display=inline&height=682&margin=%5Bobject%20Object%5D&originHeight=682&originWidth=1239&size=0&status=done&style=none&width=1239)

### **5.1.3、Bitbucket**
bitbucket**免费支持5个开发成员的团队创建无限私有代码托管库**。bitbucket地址：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073081-47a5b809-06ac-48c3-827a-37bf0b567993.png#align=left&display=inline&height=716&margin=%5Bobject%20Object%5D&originHeight=716&originWidth=1216&size=0&status=done&style=none&width=1216)

### **5.1.4、开源中国代码托管**
开源中国一个账号最多可以创建1000个项目，包含公有和私有，开源中国代码托管地址： [http://git.oschina.net/](https://bitbucket.org/)，其首页如图：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073108-bc469e20-c642-4398-b51f-1bf65839219f.png#align=left&display=inline&height=724&margin=%5Bobject%20Object%5D&originHeight=724&originWidth=1123&size=0&status=done&style=none&width=1123)

### 5.1.5、(推荐)coding.net
谈到coding.net,首先必须提的是速度快，功能与开源中国相似，同样一个账号最多可以创建1000个项目(5个私有)，也支持任务的创建等。coding.net地址： [https://coding.net/](https://coding.net/)：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073088-b126c7c8-b8b3-41ac-bcef-e7314a8cb126.png#align=left&display=inline&height=685&margin=%5Bobject%20Object%5D&originHeight=685&originWidth=1133&size=0&status=done&style=none&width=1133)
我个人比较推荐Coding.net、GItHub。
当然还有许多，如CSDN，百度，阿里等，欢迎大家比较后推荐。
选择国外的主机请考虑网速，选择国内的主机请考虑稳定与安全性。

## 5.2、申请帐号与设置
因为coding.net免费，可以创建私有项目，且速度不错，这里我们以coding.net为托管平台完成远程仓库的帐号申请与操作。

### 5.2.1、申请帐号
1）、打开 [https://coding.net/](https://coding.net/)，点击右上角的注册按钮：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073090-313395bf-8f96-47ab-b960-8fd13a660e9e.png#align=left&display=inline&height=663&margin=%5Bobject%20Object%5D&originHeight=663&originWidth=921&size=0&status=done&style=none&width=921)
 2)、填写好注册信息通过邮箱或手机验证后注册就成功了。登录到个人首页。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073110-9c2ce5b0-fb04-421a-a228-da8dda3d25fd.png#align=left&display=inline&height=696&margin=%5Bobject%20Object%5D&originHeight=696&originWidth=965&size=0&status=done&style=none&width=965)
如果是QQ邮箱请注意激活邮件可能会被当着垃圾邮件，到垃圾箱中可以找到。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073124-014f0d5e-263b-4dad-90f8-c0d79e212a8a.png#align=left&display=inline&height=612&margin=%5Bobject%20Object%5D&originHeight=612&originWidth=1027&size=0&status=done&style=none&width=1027)

### 5.2.2、创建项目
登录成功后，点击左侧菜单项目，点击加号新建项目，这里创建的是一个公开项目，没有Readme.md、许可证与忽视文件，原因是如果你本地已经有一个项目了，想提交到远程仓库而新创建的3个文件本地没有，当然有办法但初学避免麻烦这里我就不添加这三个文件了，输入相关信息后点击创建就成功了。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073133-435c92b7-a9f2-4a26-b121-e1d8bb0d8a9d.png#align=left&display=inline&height=664&margin=%5Bobject%20Object%5D&originHeight=664&originWidth=1146&size=0&status=done&style=none&width=1146)

### 5.2.3、提交源代码到远程仓库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073136-7202a2be-a45b-4f35-a097-8002f0bd1043.png#align=left&display=inline&height=677&margin=%5Bobject%20Object%5D&originHeight=677&originWidth=719&size=0&status=done&style=none&width=719)
从上图可以看出创建地址有两种：
https 类型的：[https://git.coding.net/zhangguoGit/project7.git](https://git.coding.net/zhangguoGit/project7.git)
SSH类型的：git@git.coding.net:zhangguoGit/project7.git
#### HTTPS（推荐轻量级用户使用）
使用加密的网页访问通道读写仓库，使用用户名及密码进行鉴权。 避免重复输入密码，查看 [怎样在每次 Push 时不用重复输入密码](https://coding.net/help/faq/git/git.html#push-)？
> 提示：Git 用户名为 Coding 的账户邮箱或者个性后缀，密码为 Coding 的账户密码。
> 注意：HTTPS 方式 push 大文件可能引发错误，查看  [Push 出错怎么办](https://coding.net/help/faq/git/git.html)？

#### SSH（推荐资深用户或经常推送大型文件用户使用）
SSH全称(Secure SHell)是一种网络协议，顾名思义就是非常安全的shell，主要用于计算机间加密传输。
使用加密通道读写仓库，无单次上传限制，需先设置 [“账户 SSH 公钥”](https://coding.net/help/doc/git/ssh-key.html#ssh-)，完成配对验证。
导入仓库可以将已存在的Git项目或SVN项目直接导入。
在命令行创建项目：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073201-d2cb1f92-a137-4fc6-a8c9-1a7e573d15de.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#1、创建目录
mkdir project7

#2、进入目录
cd project7

#3、初始化目录为git项目
git init

#4、创建md文件追加内容# project7(一级标题)
echo **"# project7"** >> README.md

#5、添加说明文件到暂存区
git add README.md

#6、提交到本地仓库并写日志
git commit -m **"first commit"**

#7、添加远程主机，主机名为origin 地址为[https://git.coding.net/zhangguoGit/project7.git](https://git.coding.net/zhangguoGit/project7.git)
git remote add origin [https://git.coding.net/zhangguoGit/project7.](https://git.coding.net/zhangguoGit/project7.)git

#8、本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了，-u 参数指定一个默认主机
git push -u origin master
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073165-f30fc98e-a64c-4403-8223-8ae5afb10581.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
如果创建已经创建则只需要第7步与第8步就好了。

### 5.2.4、Markdown文件（.md文件）
Markdown 是一种轻量级标记语言,它允许人们“使用易读易写的纯文本格式编写文档,然后转换成有效的XHTML(或者HTML)文档。
Markdown 语法的目标是：成为一种适用于网络的书写语言。
#### 1.标题
`# 一级标题`
`## 二级标题`
`### 三级标题`
`#### 四级标题`
`##### 五级标题`
`###### 六级标题`
####### 七级标题
效果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073265-964c9a6d-9163-4065-b4a4-4e66dbceb271.png#align=left&display=inline&height=284&margin=%5Bobject%20Object%5D&originHeight=461&originWidth=716&size=0&status=done&style=none&width=441)
#### 2.列表
分为有序列表和无序列表。
**有序列表**
`1. 1`
`2. 2`
`3. 3`
**无序列表**
`* 1`
`* 2`
`* 3`
#### 3.引用
`> 这是引用`
#### 4.图片和链接
两者格式区别在于“ ! ”。
`![图片描述](图片链接)`
`[链接描述](链接地址)`
#### 5.粗体和斜体
`**这是粗体**`
`*这是斜体*`
#### 6.表格
`| Tables | Are | Cool |`
`| ------------ |:------------:| -----:|`
`| col 3 is | right-aligned| $1600 |`
`| col 2 is | centered | $12 |`
`| zebra stripes| are neat | &1 |`
#### 7.代码框
`用``这个把代码包裹起来`
#### 8.分割线
输入`***`即可。
示例：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073187-4ceec0df-1b89-4b5c-a5e5-dacb18a458d5.gif#align=left&display=inline&height=16&margin=%5Bobject%20Object%5D&originHeight=16&originWidth=11&size=0&status=done&style=none&width=11) View Code
对应的HTML:
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073162-0630166c-eb38-4f24-a5cc-6745bcb568b1.gif#align=left&display=inline&height=16&margin=%5Bobject%20Object%5D&originHeight=16&originWidth=11&size=0&status=done&style=none&width=11) View Code
结果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073194-1389091f-d2a7-4337-8716-7fba35c468f5.png#align=left&display=inline&height=562&margin=%5Bobject%20Object%5D&originHeight=562&originWidth=974&size=0&status=done&style=none&width=974)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073188-1baaadad-0aa2-4046-afab-347dae7ac16a.png#align=left&display=inline&height=162&margin=%5Bobject%20Object%5D&originHeight=162&originWidth=928&size=0&status=done&style=none&width=928)
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073186-c101c016-d466-46f3-9849-e934e3217fa1.png#align=left&display=inline&height=650&margin=%5Bobject%20Object%5D&originHeight=650&originWidth=867&size=0&status=done&style=none&width=867)
[在线实时预览](http://tool.oschina.net/markdown/)工具
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073483-f3f905dc-8265-4639-b898-2dc1d241ec2b.png#align=left&display=inline&height=522&margin=%5Bobject%20Object%5D&originHeight=522&originWidth=800&size=0&status=done&style=none&width=800)

## 5.3、远程仓库操作
申请到了Git远程仓库的帐号并创建了一个空的远程仓库现在我们就可以结合本地的仓库与远程仓库一起协同工作了，模拟多人协同开发，这里我们全部使用命令完成。

### 5.3.1、常用操作指令
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073462-b291a42b-acfa-43d6-88fc-fad8c459a190.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all

#简单查看远程---所有仓库
git remote  （只能查看远程仓库的名字）#查看单个仓库
git  remote show [remote-branch-name]

#新建远程仓库
git remote add [branchname]  [url]

#修改远程仓库
git remote rename [oldname] [newname]

#删除远程仓库
git remote rm [remote-name]

#获取远程仓库数据
git fetch [remote-name] (获取仓库所有更新，但不自动合并当前分支)
git pull (获取仓库所有更新，并自动合并到当前分支)

#上传数据，如git push origin master
git push [remote-name] [branch]
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073326-21ebb478-bf73-4a8b-9a04-78b805fe9b20.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)

### 5.3.2、git clone 克隆
远程操作的第一步，通常是从远程主机克隆一个版本库，这时就要用到`git clone`命令。
$ git clone <版本库的网址>
比如，克隆一个上课示例的版本库。
$ git clone [https://github.com/zhangguo5/AngularJS04_BookStore.git](https://github.com/zhangguo5/AngularJS04_BookStore.git)
该命令会在本地主机生成一个目录，与远程主机的版本库同名。如果要指定不同的目录名，可以将目录名作为`git clone`命令的第二个参数。
$ git clone <版本库的网址> <本地目录名>
`git clone`支持多种协议，除了HTTP(s)以外，还支持SSH、Git、本地文件协议等，下面是一些例子。
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073207-965775f6-4c25-49d4-a13b-61f56e45fc79.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
$ git clone http[s]://example.com/path/to/repo.git/
$ git clone ssh://example.com/path/to/repo.git/
$ git clone git://example.com/path/to/repo.git/
$ git clone /opt/git/project.git 
$ git clone file:///opt/git/project.git
$ git clone ftp[s]://example.com/path/to/repo.git/
$ git clone rsync://example.com/path/to/repo.git/
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073241-da60fbbb-0a68-4031-bb53-66065c1fd957.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
SSH协议还有另一种写法。
$ git clone [user@]example.com:path/to/repo.git/
通常来说，Git协议下载速度最快，SSH协议用于需要用户认证的场合。各种协议优劣的详细讨论请参考 [官方文档](http://git-scm.com/book/en/Git-on-the-Server-The-Protocols)。
示例：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073230-873baad6-2cba-4b3e-b05a-a2782bd2d8d2.png#align=left&display=inline&height=379&margin=%5Bobject%20Object%5D&originHeight=379&originWidth=800&size=0&status=done&style=none&width=800)
结果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073337-43b61226-44a4-4ca8-a829-23776efb036c.png#align=left&display=inline&height=535&margin=%5Bobject%20Object%5D&originHeight=535&originWidth=980&size=0&status=done&style=none&width=980)

### 5.3.3、git remote
为了便于管理，Git要求每个远程主机都必须指定一个主机名。`git remote`命令就用于管理主机名。
不带选项的时候，`git remote`命令列出所有远程主机。
$ git remote
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073278-2c28e547-89bc-491f-a7bf-68c00ae1b7d7.png#align=left&display=inline&height=59&margin=%5Bobject%20Object%5D&originHeight=59&originWidth=666&size=0&status=done&style=none&width=666)
使用`-v`选项，可以参看远程主机的网址。
$ git remote -v
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073287-32a52eeb-8ab3-481f-b439-77241ad276f7.png#align=left&display=inline&height=77&margin=%5Bobject%20Object%5D&originHeight=77&originWidth=665&size=0&status=done&style=none&width=665)
上面命令表示，当前只有一台远程主机，叫做origin，以及它的网址。
克隆版本库的时候，所使用的远程主机自动被Git命名为`origin`。如果想用其他的主机名，需要用`git clone`命令的`-o`选项指定。
$ git clone -o WeUI [https://github.com/Tencent/weui.git](https://github.com/Tencent/weui.git)
$ git remote
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073264-b368e40f-2a43-496f-b4c4-87e696168be7.png#align=left&display=inline&height=300&margin=%5Bobject%20Object%5D&originHeight=300&originWidth=696&size=0&status=done&style=none&width=696)
上面命令表示，克隆的时候，指定远程主机叫做WeUI。
`git remote show`命令加上主机名，可以查看该主机的详细信息。
$ git remote show <主机名>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073276-c65383da-216a-4260-b254-033d5471ac0d.png#align=left&display=inline&height=259&margin=%5Bobject%20Object%5D&originHeight=259&originWidth=623&size=0&status=done&style=none&width=623)
`git remote add`命令用于添加远程主机。
$ git remote add <主机名> <网址>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073293-a15bf0a6-79f8-4d8e-9550-b9bb95f7c18b.png#align=left&display=inline&height=117&margin=%5Bobject%20Object%5D&originHeight=117&originWidth=639&size=0&status=done&style=none&width=639)
`git remote rm`命令用于删除远程主机。
$ git remote rm <主机名>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073302-4c1022de-b3bf-4ddf-b954-3736693f058e.png#align=left&display=inline&height=187&margin=%5Bobject%20Object%5D&originHeight=187&originWidth=641&size=0&status=done&style=none&width=641)
`git remote rename`命令用于远程主机的改名。
$ git remote rename <原主机名> <新主机名>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073330-f0a25b16-4e24-4844-a590-0cb0dd9cc4da.png#align=left&display=inline&height=207&margin=%5Bobject%20Object%5D&originHeight=207&originWidth=651&size=0&status=done&style=none&width=651)

### 5.3.4、git fetch
一旦远程主机的版本库有了更新（Git术语叫做commit），需要将这些更新取回本地，这时就要用到`git fetch`命令。
$ git fetch <远程主机名>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073339-11397777-8b72-437e-bd73-00f858f980dd.png#align=left&display=inline&height=46&margin=%5Bobject%20Object%5D&originHeight=46&originWidth=625&size=0&status=done&style=none&width=625)
上面命令将某个远程主机的更新，全部取回本地。
`git fetch`命令通常用来查看其他人的进程，因为它取回的代码对你本地的开发代码没有影响。
默认情况下，`git fetch`取回所有分支（branch）的更新。如果只想取回特定分支的更新，可以指定分支名。
$ git fetch <远程主机名> <分支名>
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073347-781674a9-0dd8-4459-a8a2-d38de3d91417.png#align=left&display=inline&height=376&margin=%5Bobject%20Object%5D&originHeight=376&originWidth=641&size=0&status=done&style=none&width=641)
比如，取回`origin`主机的`master`分支。
$ git fetch origin master
所取回的更新，在本地主机上要用"远程主机名/分支名"的形式读取。比如`origin`主机的`master`，就要用`origin/master`读取。
`git branch`命令的`-r`选项，可以用来查看远程分支，`-a`选项查看所有分支。
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073378-1b76b2ba-1aa5-4fda-9ee0-2192f9fdbc05.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
$ git branch -r
origin/master

$ git branch -a
* master
  remotes/origin/master
  ![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073373-6e37e15a-5e52-4573-b1e3-4f17f7242fd1.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
  上面命令表示，本地主机的当前分支是`master`，远程分支是`origin/master`。
  取回远程主机的更新以后，可以在它的基础上，使用`git checkout`命令创建一个新的分支。
  $ git checkout -b newBrach origin/master
  上面命令表示，在`origin/master`的基础上，创建一个新分支。
  此外，也可以使用`git merge`命令或者`git rebase`命令，在本地分支上合并远程分支。
  $ git merge origin/master
# 或者
$ git rebase origin/master
上面命令表示在当前分支上，合并`origin/master`。

### 5.3.5、git pull
`git pull`命令的作用是，取回远程主机某个分支的更新，再与本地的指定分支合并。它的完整格式稍稍有点复杂。
$ git pull <远程主机名> <远程分支名>:<本地分支名>
比如，取回`origin`主机的`next`分支，与本地的`master`分支合并，需要写成下面这样。
$ git pull origin next:master
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073352-824dff2d-5e09-4ff0-a4a8-8dff37049cee.png#align=left&display=inline&height=61&margin=%5Bobject%20Object%5D&originHeight=61&originWidth=631&size=0&status=done&style=none&width=631)
如果远程分支是与当前分支合并，则冒号后面的部分可以省略。
$ git pull origin next
上面命令表示，取回`origin/next`分支，再与当前分支合并。实质上，这等同于先做`git fetch`，再做`git merge`。
$ git fetch origin
$ git merge origin/next
在某些场合，Git会自动在本地分支与远程分支之间，建立一种追踪关系（tracking）。比如，在`git clone`的时候，所有本地分支默认与远程主机的同名分支，建立追踪关系，也就是说，本地的`master`分支自动"追踪"`origin/master`分支。
Git也允许手动建立追踪关系。
git branch --set-upstream master origin/next
上面命令指定`master`分支追踪`origin/next`分支。
如果当前分支与远程分支存在追踪关系，`git pull`就可以省略远程分支名。
$ git pull origin
上面命令表示，本地的当前分支自动与对应的`origin`主机"追踪分支"（remote-tracking branch）进行合并。
如果当前分支只有一个追踪分支，连远程主机名都可以省略。
$ git pull
上面命令表示，当前分支自动与唯一一个追踪分支进行合并。
如果合并需要采用rebase模式，可以使用`--rebase`选项。
$ git pull --rebase <远程主机名> <远程分支名>:<本地分支名>
如果远程主机删除了某个分支，默认情况下，`git pull` 不会在拉取远程分支的时候，删除对应的本地分支。这是为了防止，由于其他人操作了远程主机，导致`git pull`不知不觉删除了本地分支。
但是，你可以改变这个行为，加上参数 `-p` 就会在本地删除远程已经删除的分支。
$ git pull -p
# 等同于下面的命令
$ git fetch --prune origin 
$ git fetch -p

### 5.3.6、git push
`git push`命令用于将本地分支的更新，推送到远程主机。它的格式与`git pull`命令相仿。
$ git push <远程主机名> <本地分支名>:<远程分支名>
注意，分支推送顺序的写法是<来源地>:<目的地>，所以`git pull`是<远程分支>:<本地分支>，而`git push`是<本地分支>:<远程分支>。
如果省略远程分支名，则表示将本地分支推送与之存在"追踪关系"的远程分支（通常两者同名），如果该远程分支不存在，则会被新建。
$ git push origin master
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073394-5c9e2ec5-99af-40b5-ab00-91a4a0e9c96c.png#align=left&display=inline&height=224&margin=%5Bobject%20Object%5D&originHeight=224&originWidth=666&size=0&status=done&style=none&width=666)
上面命令表示，将本地的`master`分支推送到`origin`主机的`master`分支。如果后者不存在，则会被新建。
如果省略本地分支名，则表示删除指定的远程分支，因为这等同于推送一个空的本地分支到远程分支。
$ git push origin :master
# 等同于
$ git push origin --delete master
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073381-fb6ff4e5-0069-4e0a-a2c0-d0d06adf17df.png#align=left&display=inline&height=245&margin=%5Bobject%20Object%5D&originHeight=245&originWidth=825&size=0&status=done&style=none&width=825)
上面命令表示删除`origin`主机的`master`分支。
如果当前分支与远程分支之间存在追踪关系，则本地分支和远程分支都可以省略。
$ git push origin
上面命令表示，将当前分支推送到`origin`主机的对应分支。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073411-689cbb18-c43e-4967-aa98-566d5e5bd69b.png#align=left&display=inline&height=365&margin=%5Bobject%20Object%5D&originHeight=365&originWidth=691&size=0&status=done&style=none&width=691)
如果是新建分支第一次push，会提示：
　　fatal: The current branch dev1 has no upstream branch.
　　To push the current branch and set the remote as upstream, use
　　git push --set-upstream origin dev1
　　输入这行命令，然后输入用户名和密码，就push成功了。
　　以后的push就只需要输入git push origin
原因是：
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073443-562f6c69-0598-40de-a4bb-c7400a800631.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
#因为在git的全局配置中，有一个push.default属性，其决定了git push操作的默认行为。在Git 2.0之前，这个属性的默认被设为'matching'，2.0之后则被更改为了'simple'。

#我们可以通过git version确定当前的git版本（如果小于2.0，更新是个更好的选择），通过git config --global push.default 'option'改变push.default的默认行为（或者也可直接编辑~/.gitconfig文件）。

push.default 有以下几个可选值：
nothing, current, upstream, simple, matching

其用途分别为：
nothing - push操作无效，除非显式指定远程分支，例如git push origin develop（我觉得。。。可以给那些不愿学git的同事配上此项）。
current - push当前分支到远程同名分支，如果远程同名分支不存在则自动创建同名分支。
upstream - push当前分支到它的upstream分支上（这一项其实用于经常从本地分支push/pull到同一远程仓库的情景，这种模式叫做central workflow）。
simple - simple和upstream是相似的，只有一点不同，simple必须保证本地分支和它的远程
upstream分支同名，否则会拒绝push操作。
matching - push所有本地和远程两端都存在的同名分支。

因此如果我们使用了git2.0之前的版本，push.default = matching，git push后则会推送当前分支代码到远程分支，而2.0之后，push.default = simple，如果没有指定当前分支的upstream分支，就会收到上文的fatal提示。
![](https://cdn.nlark.com/yuque/0/2020/gif/322438/1604991073427-1446bd30-33cd-4268-b3bd-da564b13776d.gif#align=left&display=inline&height=20&margin=%5Bobject%20Object%5D&originHeight=20&originWidth=20&size=0&status=done&style=none&width=20)
如果当前分支只有一个追踪分支，那么主机名都可以省略。
$ git push
如果当前分支与多个主机存在追踪关系，则可以使用`-u`选项指定一个默认主机，这样后面就可以不加任何参数使用`git push`。
$ git push -u origin master
上面命令将本地的`master`分支推送到`origin`主机，同时指定`origin`为默认主机，后面就可以不加任何参数使用`git push`了。
不带任何参数的`git push`，默认只推送当前分支，这叫做simple方式。此外，还有一种matching方式，会推送所有有对应的远程分支的本地分支。Git 2.0版本之前，默认采用matching方法，现在改为默认采用simple方式。如果要修改这个设置，可以采用`git config`命令。
$ git config --global push.default matching
# 或者
$ git config --global push.default simple
还有一种情况，就是不管是否存在对应的远程分支，将本地的所有分支都推送到远程主机，这时需要使用`--all`选项。
$ git push --all origin
上面命令表示，将所有本地分支都推送到`origin`主机。
如果远程主机的版本比本地版本更新，推送时Git会报错，要求先在本地做`git pull`合并差异，然后再推送到远程主机。这时，如果你一定要推送，可以使用`--force`选项。
$ git push --force origin 
上面命令使用`--force`选项，结果导致远程主机上更新的版本被覆盖。除非你很确定要这样做，否则应该尽量避免使用`--force`选项。
最后，`git push`不会推送标签（tag），除非使用`--tags`选项。
$ git push origin --tags

## 5.4、在命令行中同步本地仓库示例
假定我们创建好了一个远程仓库地址为：[https://coding.net/u/zhangguo5/p/project7/git](https://coding.net/u/zhangguo5/p/project7/git)，现在我们在本地创建一个项目并同步到远程仓库中。
1）、创建文件添加到暂存区
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073395-20d77f7b-77d1-48ea-a06d-06815a882f4d.png#align=left&display=inline&height=489&margin=%5Bobject%20Object%5D&originHeight=489&originWidth=719&size=0&status=done&style=none&width=719)
2）、提交到本地仓库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073407-1ce6e2f3-e6d1-40b7-ad52-7c4ac685d4af.png#align=left&display=inline&height=217&margin=%5Bobject%20Object%5D&originHeight=217&originWidth=715&size=0&status=done&style=none&width=715)
3）、提交到远程仓库
添加远程主机地址：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073424-1257efe8-51c8-44c1-83e2-d69f595ad9bd.png#align=left&display=inline&height=47&margin=%5Bobject%20Object%5D&originHeight=47&originWidth=708&size=0&status=done&style=none&width=708)
推送文件：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073397-79044dae-0e8d-490e-b5c6-432aa57560a3.png#align=left&display=inline&height=168&margin=%5Bobject%20Object%5D&originHeight=168&originWidth=709&size=0&status=done&style=none&width=709)
结果：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073404-a767126c-d137-46d2-a2f3-d137c514764b.png#align=left&display=inline&height=569&margin=%5Bobject%20Object%5D&originHeight=569&originWidth=1212&size=0&status=done&style=none&width=1212)
说明：这里我使用的是SSH方式提交的，所有并没有让我输入用户名与密码，如果你使用https方式提交则要配置用户名与邮箱，还要输入密码。

## 5.5、IDEA中Git的使用
工作中多人使用版本控制软件协作开发，常见的应用场景归纳如下：
假设小组中有两个人，组长盖茨，组员艾伦
场景一：盖茨创建项目并提交到远程Git仓库
场景二：艾伦从远程Git仓库上获取项目源码
场景三：艾伦修改了部分源码，提交到远程仓库
场景四：盖茨从远程仓库获取艾伦的提交
场景五：艾伦接受了一个新功能的任务，创建了一个分支并在分支上开发
场景六：艾伦把分支提交到远程Git仓库
场景七：盖茨获取艾伦提交的分支
场景八：盖茨把分支合并到主干
下面来看以上各场景在IDEA中对应的操作。
### 场景一：盖茨创建项目并提交到远程Git仓库
在IDEA中配置Git
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073527-96cfc10d-d889-4854-b68f-549bee7b990f.png#align=left&display=inline&height=519&margin=%5Bobject%20Object%5D&originHeight=519&originWidth=789&size=0&status=done&style=none&width=789)
测试环境是否正常
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073473-20b709d5-65c6-45c1-aa41-aae524e78a47.png#align=left&display=inline&height=661&margin=%5Bobject%20Object%5D&originHeight=661&originWidth=920&size=0&status=done&style=none&width=920)
创建好项目，这里创建了一个Maven项目，结构如下，当然可以是任意项目：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073602-81c8837b-6c9e-4ee9-91c5-17b03f02f481.png#align=left&display=inline&height=345&margin=%5Bobject%20Object%5D&originHeight=345&originWidth=261&size=0&status=done&style=none&width=261)
选择VCS - > Enable Version Control Integration，允许将项目集成到版本控制器中
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073550-43c9159f-d735-4f40-958e-fb2bcf35903c.png#align=left&display=inline&height=302&margin=%5Bobject%20Object%5D&originHeight=302&originWidth=933&size=0&status=done&style=none&width=933)
选择版本控制器类型
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073524-99b4598d-c096-428e-a3fc-b2eedbe332c8.png#align=left&display=inline&height=259&margin=%5Bobject%20Object%5D&originHeight=259&originWidth=657&size=0&status=done&style=none&width=657)
完成后当前项目就变成一个Git项目，是工作空间
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073584-0cac58f6-3ca5-4e29-8f34-a92598c5cf50.png#align=left&display=inline&height=465&margin=%5Bobject%20Object%5D&originHeight=465&originWidth=919&size=0&status=done&style=none&width=919)
点击OK后创建完成本地仓库，注意，这里仅仅是本地的。下面把项目源码添加到本地仓库。
下图是Git与提交有关的三个命令对应的操作，Add命令是把文件从IDE的工作目录添加到本地仓库的stage区，Commit命令把stage区的暂存文件提交到当前分支的仓库，并清空stage区。Push命令把本地仓库的提交同步到远程仓库。
![](https://cdn.nlark.com/yuque/0/2020/jpeg/322438/1604991073731-b546768e-39cb-49d3-83f0-f8847ac20d9a.jpeg#align=left&display=inline&height=349&margin=%5Bobject%20Object%5D&originHeight=349&originWidth=708&size=0&status=done&style=none&width=708)
IDEA中对操作做了一定的简化，Commit和Push可以在一步中完成。
具体操作，在项目上点击右键，选择Git菜单，如果使用Add则将文件从工作空间提交到暂存库，Commit Directory则是同时完成提交到暂存与本地仓库。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073915-d9b5e612-0bd6-4acd-86c9-d02b44b1c6d2.png#align=left&display=inline&height=552&margin=%5Bobject%20Object%5D&originHeight=552&originWidth=833&size=0&status=done&style=none&width=833)
 选择要提交的文件，填写消息
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073566-2c0b17cb-3cea-47ea-b8f3-31e7e83b7a5c.png#align=left&display=inline&height=728&margin=%5Bobject%20Object%5D&originHeight=728&originWidth=804&size=0&status=done&style=none&width=804)
将本地仓库的内容提交到远程仓库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073608-43adc473-0380-4209-9a40-4e76cc6047c1.png#align=left&display=inline&height=552&margin=%5Bobject%20Object%5D&originHeight=552&originWidth=1017&size=0&status=done&style=none&width=1017)
 定义远程地址的别名
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073527-316d00d9-b16a-47ca-8da8-53fd73527f08.png#align=left&display=inline&height=583&margin=%5Bobject%20Object%5D&originHeight=583&originWidth=642&size=0&status=done&style=none&width=642)
 输入名称与URL
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073702-01b57f90-a1f1-460d-abba-ddb5b19c0307.png#align=left&display=inline&height=195&margin=%5Bobject%20Object%5D&originHeight=195&originWidth=416&size=0&status=done&style=none&width=416)
 点击push将本地仓库的内容推送到远程服务器
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073550-e41f2651-fbc1-4ebc-a50c-aa821e380ff7.png#align=left&display=inline&height=582&margin=%5Bobject%20Object%5D&originHeight=582&originWidth=641&size=0&status=done&style=none&width=641)
 提示Push Successful就成功了
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073686-1cac0ff7-8b3e-4408-8672-45701c26f103.png#align=left&display=inline&height=332&margin=%5Bobject%20Object%5D&originHeight=332&originWidth=1021&size=0&status=done&style=none&width=1021)
 提交后的远程库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073646-197a528f-cb4a-4b72-b659-c11277f06064.png#align=left&display=inline&height=538&margin=%5Bobject%20Object%5D&originHeight=538&originWidth=862&size=0&status=done&style=none&width=862)
### 场景二：艾伦从远程Git仓库上获取项目源码
即克隆项目，操作如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073680-b9def45c-3ac7-477e-88c0-82d3bf6165c4.png#align=left&display=inline&height=510&margin=%5Bobject%20Object%5D&originHeight=510&originWidth=799&size=0&status=done&style=none&width=799)
输入盖茨Push时填写的远程仓库地址
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073653-37e9549a-de24-42b1-86b2-ccd38e8475af.png#align=left&display=inline&height=177&margin=%5Bobject%20Object%5D&originHeight=177&originWidth=641&size=0&status=done&style=none&width=641)
填写仓库地址、要克隆到的父目录与项目目录
接下来按向导操作，即可把项目从远程仓艾伦隆到本地仓库和IDE工作区。
当提示签出成功点击打开就可以看到项目了
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073698-bb8d779e-1ec0-4b93-9f38-ad086db5989d.png#align=left&display=inline&height=338&margin=%5Bobject%20Object%5D&originHeight=338&originWidth=221&size=0&status=done&style=none&width=221)
下载到本地的文件
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073662-0b515101-a616-4433-be67-96c2e98cd252.png#align=left&display=inline&height=257&margin=%5Bobject%20Object%5D&originHeight=257&originWidth=750&size=0&status=done&style=none&width=750)
其它方法
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073769-17b73691-b41b-4932-86ae-dfd18f048eb9.png#align=left&display=inline&height=677&margin=%5Bobject%20Object%5D&originHeight=677&originWidth=976&size=0&status=done&style=none&width=976)
### 场景三：艾伦修改了部分源码，提交到远程仓库
这个操作和首次提交的流程基本一致，分别是 Add -> Commit -> Push。请参考场景一

 添加一个类，并提交
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073654-44e8d1d7-efd7-439e-9af5-b62b6b8ef2b6.png#align=left&display=inline&height=488&margin=%5Bobject%20Object%5D&originHeight=488&originWidth=924&size=0&status=done&style=none&width=924)

提交到本地仓库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073645-cb12ccf6-c3c3-47fd-918d-737f39aa1428.png#align=left&display=inline&height=734&margin=%5Bobject%20Object%5D&originHeight=734&originWidth=873&size=0&status=done&style=none&width=873)
提交到远程仓库
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073739-f3bd0adb-943e-401c-8128-e88be71c8675.png#align=left&display=inline&height=527&margin=%5Bobject%20Object%5D&originHeight=527&originWidth=993&size=0&status=done&style=none&width=993)
### 场景四：盖茨从远程仓库获取艾伦的提交
获取更新有两个命令：Fetch和Pull，Fetch是从远程仓库下载文件到本地的origin/master，然后可以手动对比修改决定是否合并到本地的master库。Pull则是直接下载并合并。如果各成员在工作中都执行修改前先更新的规范，则可以直接使用Pull方式以简化操作。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073696-869d65c2-addf-423f-bcac-fab32e1ca22d.png#align=left&display=inline&height=459&margin=%5Bobject%20Object%5D&originHeight=459&originWidth=914&size=0&status=done&style=none&width=914)
选择分支
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073633-907e0910-7f84-42a7-b86d-16f9eb67bb10.png#align=left&display=inline&height=411&margin=%5Bobject%20Object%5D&originHeight=411&originWidth=630&size=0&status=done&style=none&width=630)
### 场景五：艾伦接受了一个新功能的任务，创建了一个分支并在分支上开发
建分支也是一个常用的操作，例如临时修改bug、开发不确定是否加入的功能等，都可以创建一个分支，再等待合适的时机合并到主干。
创建流程如下：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073677-6ae30817-1efa-4ba7-a878-51260450968b.png#align=left&display=inline&height=529&margin=%5Bobject%20Object%5D&originHeight=529&originWidth=982&size=0&status=done&style=none&width=982)
选择New Branch并输入一个分支的名称
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073816-2761ae7b-f0a8-4f05-8ff1-47baddab7c9f.png#align=left&display=inline&height=301&margin=%5Bobject%20Object%5D&originHeight=301&originWidth=265&size=0&status=done&style=none&width=265)
创建完成后注意IDEA的右下角，如下图，Git: dev表示已经自动切换到dev分支，当前工作在这个分支上。
点击后弹出一个小窗口，在Local Branches中有其他可用的本地分支选项，点击后选择Checkout即可切换当前工作的分支(见场景7操作切换其他分支)。
如下图，点击Checkout
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073860-3abfd34e-1cc2-4ddc-b63a-90c2c858452b.png#align=left&display=inline&height=392&margin=%5Bobject%20Object%5D&originHeight=392&originWidth=603&size=0&status=done&style=none&width=603)
注意，这里创建的分支仅仅在本地仓库，如果想让组长盖茨获取到这个分支，还需要提交到远程仓库。
### 场景六：艾伦把分支提交到远程Git仓库
切换到新建的分支，使用Push功能
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073707-0f9037a1-0f57-4432-8237-49685febda00.png#align=left&display=inline&height=296&margin=%5Bobject%20Object%5D&originHeight=296&originWidth=965&size=0&status=done&style=none&width=965)
提交到远程
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073796-19242f80-8c2f-401a-96dc-b36270ecc7f0.png#align=left&display=inline&height=584&margin=%5Bobject%20Object%5D&originHeight=584&originWidth=643&size=0&status=done&style=none&width=643)
艾伦将新开发的功能提交到远程
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073907-909db114-5f1c-4b98-8906-ffd06bd22841.png#align=left&display=inline&height=734&margin=%5Bobject%20Object%5D&originHeight=734&originWidth=789&size=0&status=done&style=none&width=789)
提交到远程
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073725-58b77649-f29d-4230-9474-6ccd1c795d34.png#align=left&display=inline&height=578&margin=%5Bobject%20Object%5D&originHeight=578&originWidth=645&size=0&status=done&style=none&width=645)
### 场景七：盖茨获取艾伦提交的分支
使用Pull功能打开更新窗口，点击Remote栏后面的刷新按钮，会在Branches to merge栏中刷新出新的分支。这里并不想做合并，所以不要选中任何分支，直接点击Pull按钮完成操作。
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073771-d33c80a5-bcdd-4b4c-8cbb-ce48a1feecd4.png#align=left&display=inline&height=412&margin=%5Bobject%20Object%5D&originHeight=412&originWidth=635&size=0&status=done&style=none&width=635)
更新后，再点击右下角，可以看到在Remote Branches区已经有了新的分支，点击后在弹出的子菜单中选择Checkout as new local branch，在本地仓库中创建该分支。完成后在Local Branches区也会出现该分支的选项，可以按上面的方法，点击后选择Checkout切换。
切换远程分支：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073805-335a432c-4c07-49ed-80ff-308e36d605e2.png#align=left&display=inline&height=287&margin=%5Bobject%20Object%5D&originHeight=287&originWidth=624&size=0&status=done&style=none&width=624)
切换本地分支：
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073713-4493e074-78f6-4227-80a5-264adfa48bbe.png#align=left&display=inline&height=222&margin=%5Bobject%20Object%5D&originHeight=222&originWidth=461&size=0&status=done&style=none&width=461)
### 场景八：盖茨把分支合并到主干
新功能开发完成，体验很好，项目组决定把该功能合并到主干上。
切换到master分支，选择Merge Changes
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073889-41967353-6b34-4522-8387-6b6bbb865e3b.png#align=left&display=inline&height=481&margin=%5Bobject%20Object%5D&originHeight=481&originWidth=867&size=0&status=done&style=none&width=867)
选择要合并的分支，点击Merge完成
![](https://cdn.nlark.com/yuque/0/2020/png/322438/1604991073848-7c8b33db-49c9-4c4a-91e1-1de7d15d09fc.png#align=left&display=inline&height=421&margin=%5Bobject%20Object%5D&originHeight=421&originWidth=548&size=0&status=done&style=none&width=548)

# 六、资源与资料下载

- 权威Git书籍 [ ProGit（中文版）](http://git.oschina.net/progit/)
- git官网： [http://git-scm.com](http://git-scm.com/)
- git手册： [http://git-scm.com/docs](http://git-scm.com/docs)
- 网友整理的Git@osc教程，请 [点击这里](http://git.oschina.net/oschina/git-osc/wikis/%E5%B8%AE%E5%8A%A9#%E7%BB%A7%E7%BB%AD%E9%98%85%E8%AF%BB)；
- 一份很好的 Git 入门教程，请 [点击这里](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001373962845513aefd77a99f4145f0a2c7a7ca057e7570000)；
- [Git图解教程](http://www.cnblogs.com/yaozhongxiao/p/3811130.html)

资料链接: [https://pan.baidu.com/s/1c20DVOW](https://pan.baidu.com/s/1c20DVOW)  密码: p9ri
[Git教程下载_王亮（大神）](https://pan.baidu.com/s/1qYlw2YS)

# 七、视频
[https://www.bilibili.com/video/av14813510/](https://www.bilibili.com/video/av14813510/)

