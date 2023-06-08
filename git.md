# Git

## 	1.常用命令

<img src = "https://yqlyq.github.io/problemImages/imgs202306072230827.png">

（第一次使用要设置用户签名 才能提交代码 配置文件在C:\Users\ASUS\ .gitconfig）

```bash
git config --global user.name yql
git config --global user.email 1014796661@qq.com
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072230828.png">

### 1.1初始化

```bash
git init 
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072211096.png"/>

生成.git

<img src = "https://yqlyq.github.io/problemImages/imgs202306072345008.png"/>

### 1.2查看本地库状态

```bash
git status
```

#### 1.2.1首次查看（工作区没有文件）

<img src = "https://yqlyq.github.io/problemImages/imgs202306072212789.png"/>

#### 1.2.2添加文件后（检测到未追踪的文件）

<img src = "https://yqlyq.github.io/problemImages/imgs202306072212996.png"/>

### 1.3添加到暂存区

```bash
git add 文件名
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072214321.png"/>

查看状态（检测到暂存区有新文件）

<img src = "https://yqlyq.github.io/problemImages/imgs202306072221078.png"/>

### 1.4提交本地库

```bash
git commit -m "信息" 文件名
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072226505.png"/>

​									**<u>(33973ac) 是版本号</u>**

查看状态（没有文件需要提交）

<img src = "https://yqlyq.github.io/problemImages/imgs202306072226790.png"/>

查看状态（工作区有更改）

<img src = "https://yqlyq.github.io/problemImages/imgs202306072228913.png"/>

提交暂存区后查看状态

<img src = "https://yqlyq.github.io/problemImages/imgs202306072228291.png"/>

### 1.6历史版本

```bash
git reflog #查看版本信息
git log #查看详细信息
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072228107.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072229914.png"/>

### 1.7 版本穿梭

```bash
git reset --hard 版本号
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072230829.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072250016.png"/>

## 2.Git分支操作

### 2.1常用命令

<img src = "https://yqlyq.github.io/problemImages/imgs202306072231411.png"/>

### 2.2查看分支

```bash
git branch -v 
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072248746.png"/>

### 2.3创建分支

```bash
git branch 分支名
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072233348.png"/>

查看分支

<img src = "https://yqlyq.github.io/problemImages/imgs202306072238193.png"/>

### 2.4切换分支

```bash
git checkout 分支名
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072238235.png"/>

### 2.5合并分支

```bash
git merge 要合并的分支名
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072239359.png"/>

### 2.6合并有冲突

<img src = "https://yqlyq.github.io/problemImages/imgs202306072240159.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072240805.png"/>

手动修改？？？？

提交本地库不要带文件名

<img src = "https://yqlyq.github.io/problemImages/imgs202306072240875.png"/>

# GitHUb

## 1.常用命令

<img src = "https://yqlyq.github.io/problemImages/imgs202306072230830.png"/>

### 1.1 起别名

```bash
git remote add 别名 远程地址
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072257508.png"/>

### 1.2查看当前所有别名

```bash
git remote -v
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072230831.png"/>

### 1.3推送远程仓库

```bash
git push 别名 分支
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072247991.png"/>

### 1.4拉取本地库

``` bash
git pull 别名 分支
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072247246.png"/>

1.5克隆本地库

```bash
git clone 远程库链接
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072248881.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308810.png"/>

## 2.添加合作者

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308617.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308706.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308971.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308640.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308761.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072310888.png"/>

## 3.跨团队协作

<img src = "https://yqlyq.github.io/problemImages/imgs202306072310466.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072310800.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072351970.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072311993.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072311641.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072311512.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072311631.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072355283.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312225.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072359871.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312074.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312096.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312650.png"/>

## 4.SSH免密登录

### 运行命令生成.ssh 秘钥目录

```bash
ssh-keygen -t rsa -C 邮箱号
```

<img src = "https://yqlyq.github.io/problemImages/imgs202306072308451.png"/>

### 生成

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312016.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312106.png"/>

### 查看id_rsa.pub 复制

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312488.png"/>

### 然后在GitHub输入

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312257.png"/>

### 成功效果

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312506.png"/>

# IDEA集成git

## 1.配置GIt忽略文件

### 	1.1 idea特定文件

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312207.png"/>

### 	1.2 maven工程的target目录

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312984.png"/>

​	这些与项目功能运行无关，不参与服务器上部署

### 	1.3 创建忽略规则文件 git.ignore (前缀名可以随意)

​	 建议放在用户名文件夹下

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312953.png"/>

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

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312568.png"/>

# idea 集成gitee

## 	1.如果推送不了

​	<img src = "https://yqlyq.github.io/problemImages/imgs202306072313728.png"/>

但 GitHub可以 可能是在gitee设置了不公开邮箱地址，同时禁止了命令行推送暴露个人邮箱

解决方法：需要设置gitte上找到允许推送的邮箱地址，然后设置在本地的git环境变量中。

1.点开设置

2.点开多邮箱管理

3.取消勾选“禁止命令行推送暴露个人邮箱”，此项默认是勾选状态

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312816.png"/>

修改后成功效果

<img src = "https://yqlyq.github.io/problemImages/imgs202306072312376.png"/>

# github复制迁移到gitee

​	

<img src = "https://yqlyq.github.io/problemImages/imgs202306072313536.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072356935.png"/>

<img src = "https://yqlyq.github.io/problemImages/imgs202306072314865.png"/>



