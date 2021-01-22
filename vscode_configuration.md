[toc]

### 一、插件

#### **1. settings sync** : 保存配置与环境，不同电脑实现同步

**旧设备**

1. Github-> 右settings-> Developer settings -> Personal access tokens-> Generate new token ->Token(vscode_sync) + √gist Generate token -> 保存生成的token值:

```shell
Token Id:
c4b2ba541eddcf9fa387a1d81cebeac313fcc799
```

2. vscode-> (crtl+shift+p)->
   sync:Advanced Options--Sync:Edit Extension Local Settings--crtl+f:“token”,paste Token id
3. vscode-> (crtl+shift+p)->
   **Sync:Update/Uplaod Settings**上传设置，(若报错：令牌无效或过期：搜索：syn重置扩展设置，重新执行上一步)-> 保存！在控制台输出Github Token 和Github Gist

```shell
GitHub Gist: 
e495946166765c13382c133fa4d523c9
```

**新设备**：

1. 登录Github
2. 安装 Settings Sync 插件
3. 重复步骤2. 输入token_id
   sync:Advanced Options--Sync:Edit Extension Local Settings
4. **Sync: Download Settings（下载配置）**:点击界面中**Edit Configuration**输入Gist_id
   ![](image/extention/1611240838722.png)

**以后的更新**
旧电脑：**Sync:Update/Uplaod Settings（上传设置）**
新电脑：**Sync: Download Settings（下载配置）**

---

#### **2.1 EverMonkey**：vscode中markdown上传到evernote

[参考文章](https://blog.csdn.net/qq_27637587/article/details/83308601)

1. 安装插件EverMonkey
2. Ever Token: Open developer page to get API token -> 保存生成的Token和NoteStore URL

```shell
token
S=s34:U=1d7e48a:E=1774cee4584:C=17728e1be78:P=1cd:A=en-devtoken:V=2:H=7e09dff2d5b8f26c8bebe5b0e97e1106

url
https://app.yinxiang.com/shard/s34/notestore
```

**以后只需要**
3. 新建markdown文件：Ever New: Create a new empty note with markdown supported
4. 同步笔记：Ever publish: Publish current editting note to Evernote server

注意：无法将图片保存到evernote

---

##### **2.2 markdown PDF**：将md保存为PDF

* 在preview界面上右键--Chrome--PDF

---

#####  **2.3 Paste Image** : 粘贴截图到markdown

* 默认保存图片到当前目录[设置](https://blog.csdn.net/javahighness/article/details/90454136)
---

#### **3. office viewer** ：可以打开office文件

* 中文乱码设置：文件-首选项-设置-文件-用户设置"files.auto.Guess"改为TRUE

---

#### **4. python环境搭建**

##### **4.1 插件**

* code runner(设置：save before run \ run in Terminal)
* python
* python preview(右上角)
* python Extendon Pack\anacond
* extension pack**

##### **4.2 环境**

* 左下角是python运行环境，点击可切换
* 镜像

```shell
#Win全局镜像
cd C:\Users\Administrator
mkdir pip
vi pip.ini
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
#其他镜像
阿里：https://mirrors.aliyun.com/pypi/simple
豆瓣：http://pypi.douban.com/simple
http://pypi.mirrors.ustc.edu.cn/simple/
#测试(terminal)
python -m  pip install jedi
```

##### **4.3 pip**

```python
#pip版本
pip -V
#列出所有包
pip list
#升级pip
pip install -U pip
pip install pkg/pip install pkg -i 镜像
pip uninstall pkg
pip install -U pkg
```

##### **4.4 conda**

```python
conda -V
conda info -e
conda list
conda create -n env_name python=3.4.0 anaconda
activate env_name
conda install -n env_name [package]
deactivate env_name
conda remove -n env_name --all
conda remove --name env_name [package]
```

* conda与pip之间的区别:
conda=包管理器+环境管理器,python+R
pip=包管理器，python，pip中的包更多

* 注意： base conda 既能使用pip安装的包，也可以使用conda 安装的包

### 二、Git

1. **[安装](https://www.jianshu.com/p/bebba0d8038e)**
   从分享小图标下载git，注意：

* 使用Vscode作为默认编辑器
  ![](image/extention/1611148665479.png)
* 将git添加到系统环境变量，以在cmd/powerShell可用
* 打开cmd/powerShell/vscodeTerminal 输入git 验证是否安装正确,注意！要打开新窗口！！！

#### 1. 打开target_folder几种方式
* 右键git bash(linux)-> cd target_folder-> code .
* vscode->open target_folder
* 右键-通过code打开（安装时必须勾选上下文）

#### 2. 配置

```shell
################################ 初始配置 ###########################
#1. github账号:
ywu19,3140575572@qq.com,berry2012Wule

#（一台电脑一次）
#设置用户名
git config --global  user.name 'ywu19'  
#设置用户邮箱
git config --global  user.email '3140575572@qq.com'
#验证设置
git config --list

##############################################################
######################## 添加SSH公钥 ###################
##############################################################
cd target_folder
右键-git bash
#################### 2.1 本地创建ssh key，一路回车
ssh-keygen -t rsa -C "3140575572@qq.com"
#################### 2.2 复制key到剪贴板
clip < ~/.ssh/id_rsa.pub
#################### 2.3 GitHub
右上角setting--SSH and GPG keys--New SSH key--title随意，下方粘贴ssh key
#################### 2.4 验证
ssh -T git@github.com
```

![](image/extention/1611164554786.png)

#### 3. 本地上传/vscode上传

* 不管是上传还是下载，第一步一定在目标文件夹内
* [参考文章](https://blog.csdn.net/loner_fang/article/details/80488385?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.control)

```shell

##############################################################
######################## 方法一：git clone ###################
##############################################################
### 不需要本地初始化
### 不需要关联，直接推送到GitHub
### 有与GitHub仓库同样的文件
############################################################## 
cd target_folder
右键-git bash
# 从远程主机克隆一个版本库到本地,会生成与GitHub重名文件夹test-github
git clone git@github.com:ywu019/test-github.git
cd test-github
1. new action                               #(code .)
2. git add .                                #(target_files--+)
3. git commit -m "seconde_time"             #(√--message)
4. git push origin master                   #(...--推送到)

##############################################################
######################## 方法二：git push ###################
##############################################################
### 需要初始化
### 需要先关联才能推送
### 无与GitHub仓库同样的文件
##############################################################

##############################################################
######################## 一个文件夹 配置一次  ###################
##############################################################
cd target_folder
右键-git bash
########################## 1. 初始化为本地仓库,生成.git
git init   
#分享符--初始化存储库
########################## 2. 本地仓库与GitHub仓库关联
git remote add origin git@github.com:ywu019/test-github.git
#...--远程--添加远程仓库位置--↑--名字--origin

########################## 3. pull down到本地仓库，两者保持一致（同步远程仓库）
###########################当两个不同文件夹上传，即版本不同会冲突，该参数会解决问题
git pull origin master --allow-unrelated-histories
#Terminal--↑

################################################################
###############  配置后文件夹内任何修改执行下边即可 ###############
################################################################

# 1. 工作区：必须有新的修改文件等动作
# 2. 暂存区：暂存已修改的文件
# 3. Git仓库：最终确定的文件存到仓库
# 4. 上传
1. new action-save #code .
2. git add abc.py
3. git commit -m "seconde_time"
4. git push origin master
```

<font color = red size=4>**In vscode git 界面**</font>

1. [认识界面](https://blog.csdn.net/weixin_39874202/article/details/107978289)
   ![](image/extention/1611200173889.png)

* 文件按钮
  打开文件：显示修改的地方
  + == git add
  √ == git commit
  ... 拉取 git pull 推送 git push
* 三种文件状态
  M modify 文件存在修改
  D delete 文件被删除了
  U Update 文件是新添加

### 三、SSH

[参考文章](https://blog.csdn.net/weixin_40373708/article/details/90376258)

1. 下载vscode \ssh \ **Remote Development**扩展
2. ctrl+shift+P--Remote-ssh: connect to host选项
3. 初次使用，Configure SSH Hosts
4. 直接选择用户名下的config进行配置， 填入远程电脑的ip地址和用户名
   ![](image/extention/1611144978914.png)
5. 保存后--再次Remote-ssh: connect to host选项
   ![](image/extention/1611145021290.png)
6. 多次输入密码
7. open foler打开的就都是远程电脑的文件，默认在~/路径。打开文件夹时候也要输很多次密码。
   ![](image/extention/1611145075795.png)
8. 打开terminal

#### 免密码登陆ssh

[教程](https://blog.csdn.net/qq_33384402/article/details/104575475?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control)

1. 打开cmd/cd .ssh/ls,若没有私钥(id_rsa)和公钥(id_rsa.pub)：

```bash
ssh-keygen -t rsa number（number处随便填数字）
```

![](image/extention/1611146692782.png)
2. 用scp命令把目录下的id_rsa.pub放到服务器中

```bash
scp .\id_rsa.pub zpzhou@211.69.141.147:~/.ssh/id_rsa.pub
```

![](image/extention/1611146199623.png)
3. 在服务器中操作：把id_rsa.pub的内容添加到authorized_keys的文件尾，最后删除id_rsa.pub

```bash
cat id_rsa.pub >> authorized_keys
rm id_rsa.pub
```

![](image/extention/1611146329761.png)
4. 以后不需要输入密码
![](image/extention/1611147603185.png)
![](image/extention/1611147647145.png)
![](image/extention/1611147686406.png)


### 四、错误
#### * **import pkg**
[python环境错误](https://blog.csdn.net/yitanjiong4414/article/details/106485708?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromBaidu-1.control)
![](img/2021-01-20-16-34-51.png)

查看当前环境
![](img/2021-01-20-16-36-20.png)

conda list发现openpyxl是由pip安装的，
![](image/extention/1611131835521.png)

选择python解析器的时候选择conda base版本的就OK了。在这个解析器下，即使是pip安装的模块也可以照常使用
![](image/extention/1611132120418.png)
