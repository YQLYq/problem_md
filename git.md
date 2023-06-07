# Git

## 	1.常用命令

<img src = "git_img/1.png">

（第一次使用要设置用户签名 才能提交代码 配置文件在C:\Users\ASUS\ .gitconfig）

```bash
git config --global user.name yql
git config --global user.email 1014796661@qq.com
```

<img src = "git_img/2.png">

### 1.1初始化

```bash
git init 
```

![image-20230103202055227](\git_img\image-20230103202055227.png)

生成.git

![image-20230103202153702](\git_img\image-20230103202153702.png)

### 1.2查看本地库状态

```bash
git status
```

#### 1.2.1首次查看（工作区没有文件）

![image-20230103210858440](\git_img\image-20230103210858440.png)

#### 1.2.2添加文件后（检测到未追踪的文件）

![image-20230103211005494](\git_img\image-20230103211005494.png)

### 1.3添加到暂存区

```bash
git add 文件名
```

![image-20230103211656056](\git_img\image-20230103211656056.png)

查看状态（检测到暂存区有新文件）

![image-20230103211707161](\git_img\image-20230103211707161.png)

### 1.4提交本地库

```bash
git commit -m "信息" 文件名
```

![image-20230103212846531](\git_img\image-20230103212846531.png)

​									**<u>(33973ac) 是版本号</u>**

查看状态（没有文件需要提交）

![image-20230103213146286](\git_img\image-20230103213146286.png)

### 1.5修改文件的状态

查看状态（工作区有更改）

![image-20230104160228740](\git_img\image-20230104160228740.png)

提交暂存区后查看状态

![image-20230104160349770](\git_img\image-20230104160349770.png)

### 1.6历史版本

```bash
git reflog #查看版本信息
git log #查看详细信息
```

![image-20230104160838145](\git_img\image-20230104160838145.png)

![image-20230104160916695](\git_img\image-20230104160916695.png)

### 1.7 版本穿梭

```bash
git reset --hard 版本号
```

![image-20230104162004551](\git_img\image-20230104162004551.png)

![image-20230104161931861](\git_img\image-20230104161931861.png)

## 2.Git分支操作

### 2.1常用命令

![image-20230104171454866](\git_img\image-20230104171454866.png)

### 2.2查看分支

```bash
git branch -v 
```

![image-20230104171112749](\git_img\image-20230104171112749.png)

### 2.3创建分支

```bash
git branch 分支名
```

![image-20230104171228115](\git_img\image-20230104171228115.png)

查看分支

![image-20230104171233417](\git_img\image-20230104171233417.png)

### 2.4切换分支

```bash
git checkout 分支名
```

![image-20230104171936412](\git_img\image-20230104171936412.png)

### 2.5合并分支

```bash
git merge 要合并的分支名
```

![image-20230104191553253](\git_img\image-20230104191553253.png)

### 2.6合并有冲突

![image-20230104194409607](\git_img\image-20230104194409607.png)

![image-20230104194448477](\git_img\image-20230104194448477.png)

手动修改？？？？

提交本地库不要带文件名

![image-20230104195129934](\git_img\image-20230104195129934.png)

# GitHUb

## 1.常用命令

![image-20230104203753664](git_img\image-20230104203753664.png)

### 1.1 起别名

```bash
git remote add 别名 远程地址
```

![image-20230104203941208](\git_img\image-20230104203941208.png)

### 1.2查看当前所有别名

```bash
git remote -v
```

![image-20230104204027957](git_img\image-20230104204027957.png)

### 1.3推送远程仓库

```bash
git push 别名 分支
```

![image-20230104204642240](\git_img\image-20230104204642240.png)

### 1.4拉取本地库

``` bash
git pull 别名 分支
```

![image-20230104211102928](\git_img\image-20230104211102928.png)

1.5克隆本地库

```bash
git clone 远程库链接
```

![image-20230104211646019](\git_img\image-20230104211646019.png)

![image-20230104211658609](\git_img\image-20230104211658609.png)

## 2.添加合作者

![image-20230104212536717](\git_img\image-20230104212536717.png)

![image-20230104213147499](\git_img\image-20230104213147499.png)

![image-20230104213152568](\git_img\image-20230104213152568.png)

![image-20230104213202704](\git_img\image-20230104213202704.png)

![image-20230104213209626](\git_img\image-20230104213209626.png)

![image-20230104213218273](\git_img\image-20230104213218273.png)

## 3.跨团队协作

![image-20230104213359197](\git_img\image-20230104213359197.png)

![image-20230104213407721](\git_img\image-20230104213407721.png)

![image-20230104213412577](\git_img\image-20230104213412577.png)

![image-20230104213418064](\git_img\image-20230104213418064.png)

![image-20230104213425237](\git_img\image-20230104213425237.png)

![image-20230104213430918](\git_img\image-20230104213430918.png)

![image-20230104213435842](\git_img\image-20230104213435842.png)

![image-20230104213442669](\git_img\image-20230104213442669.png)

![image-20230104213503815](\git_img\image-20230104213503815.png)

![image-20230104213512699](\git_img\image-20230104213512699.png)

![image-20230104213551447](\git_img\image-20230104213551447.png)

![image-20230104213558582](\git_img\image-20230104213558582.png)

![image-20230104213605891](\git_img\image-20230104213605891.png)

## 4.SSH免密登录

### 运行命令生成.ssh 秘钥目录

```bash
ssh-keygen -t rsa -C 邮箱号
```

![image-20230105112827625](\git_img\image-20230105112827625.png)

### 生成

![image-20230105113128947](\git_img\image-20230105113128947.png)

![image-20230105113126202](\git_img\image-20230105113126202.png)

### 查看id_rsa.pub 复制

![image-20230105113105360](\git_img\image-20230105113105360.png)

### 然后在GitHub输入

![image-20230105112756357](\git_img\image-20230105112756357.png)

### 成功效果

![image-20230105113216371](\git_img\image-20230105113216371.png)

# IDEA集成git

## 1.配置GIt忽略文件

### 	1.1 idea特定文件

![image-20230105114513908](\git_img\image-20230105114513908.png)

### 	1.2 maven工程的target目录

![image-20230105114519705](\git_img\image-20230105114519705.png)

​	这些与项目功能运行无关，不参与服务器上部署

### 	1.3 创建忽略规则文件 git.ignore (前缀名可以随意)

​	 建议放在用户名文件夹下

![image-20230105115133476](\git_img\image-20230105115133476.png)

#### 		git.ignore 模板		

```bash
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
*.nar
*.ear
*.zip
*.tar.gz
*.rar

# virtual machine crash logs, see 
http://www.java.com/en/download/help/error_hotspot.xml
hs_err_pid*

.classpath
.project
.settings
target
.idea
*.iml
```

#### 在"C:\Users\ASUS\.gitconfig" 下输入引用忽略配置文件 （注意使用的是/）

```bash
[user]
	name = yql
	email = 1014796661@qq.com
[core]
	excludesfile = C:/Users/ASUS/git.ignore
	#注意：这里要使用“正斜线（/）”，不要使用“反斜线（\）”
```

![image-20230105115554600](\git_img\image-20230105115554600.png)

# idea 集成gitee

## 	1.如果推送不了

​	![image-20230105231603789](\git_img\image-20230105231603789.png)

但 GitHub可以 可能是在gitee设置了不公开邮箱地址，同时禁止了命令行推送暴露个人邮箱

解决方法：需要设置gitte上找到允许推送的邮箱地址，然后设置在本地的git环境变量中。

1.点开设置

2.点开多邮箱管理

3.取消勾选“禁止命令行推送暴露个人邮箱”，此项默认是勾选状态

![image-20230105231656616](\git_img\image-20230105231656616.png)

修改后成功效果

![image-20230105231751980](\git_img\image-20230105231751980.png)

# github复制迁移到gitee

​	

![image-20230105232323559](\git_img\image-20230105232323559.png)

![image-20230105232700567](\git_img\image-20230105232700567.png)

![image-20230105232715403](\git_img\image-20230105232715403.png)
