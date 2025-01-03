# 博客搭建教学


## hexo重新部署
### 安装 Node.js 和 Git 必要软件
本文章主要介绍了在重装系统或者更换电脑以后怎样更新自己的博客，经过自己的尝试可行，于是记录分享一下  
Node.js: https://nodejs.org/en    
Git: https://git-scm.com/download/win
- cmd测试命令(检测node安装)
```
node -v
npm -v
git --version
```

### 打开Github，重新配置新的密钥
- 配置SSH,一般位于C:\Users\user_name.ssh(id_rsa.pub)
```
ssh-keygen -t rsa -C"xxxxx@example.com"
```
- 打开GitHub账户,创建新的SSH链接
- 验证链接账户邮箱是否成功
```
ssh -T git@github.com
```
- 此外您还需要如下配置:
```
git config --global user.name “xxx”
git config --golbal user.email"xxxxxx@example.com"
```
Tips: ssh的手动配置
```
/*进入博客目录的“.deploy_git.git”子目录,找到config文件。
手动配置:
[user]
	email = xxxxx@example.com
	name = xxx             */
hexo cl && hexo g -d                /*清除上传指令*/
```

### 安装 hexo 命令
- 在 cmd 下输入下面指令安装 hexo
```
npm install hexo-cli -g
```
- 如果网络被阉，可以使用阿里云镜像源进行安装
```
npm install -g cnpm --registry=https://registry.npmmirror.com
cnpm install -g hexo-cli
```

### 初始化 hexo 框架
- 在 D:\blog 文件夹下,右键打开 Git Bash Here，输入以下命令
```
hexo init    /*进行初始化*/
```
Tips:本步骤为初始搭建hexo框架，如已搭建使用源文件
- 源文件拷贝（重新搭建）
将你原来电脑上个人博客目录下必要文件拷到你的新电脑上（比如D:/Blog目录下），注意无需拷全部，只拷如下几个目录：
```
_config.yml
 package.json
 scaffolds/
 source/
 themes/
```
图片示例:
![](https://github.com/Felix-zf/Picture-Store/blob/master/img/zy.png)

### 安装依赖
在 D:\blog 文件夹下右键打开 Git Bash Here，输入以下命令
```
npm install  // 安装依赖
npm update  // 更新依赖
npm install hexo-deployer-git --save  // 文章部署到 git 的模块
（下面为选择安装）
npm install hexo-generator-feed --save  // 建立 RSS 订阅
npm install hexo-generator-search --save  // 建立文章搜索
npm install hexo-generator-sitemap --save // 建立站点地图
```
Tips: 备用阿里云镜像源cnpm,卡死了可以直接按下 CTRL+C 终止
```
git config --global http.sslVerify false  // 出现SSL错误,可绕过证书验证（仅用于开发环境）
```

### 测试
这时候使用 hexo s 基本可以看到你新添加的文章了。

### 部署发布文章
- 在 D:\blog 文件夹下右键打开 Git Bash Here，输入以下命令
```
hexo clean        /*清除缓存 网页正常情况下可以忽略此条命令*/  
hexo g            /*生成静态网页*/  
hexo s            /*本地部署*/  
```
```
npm install hexo-deployer-git --save    /*安装hexo部署插件*/
hexo d            /*开始部署*/  
```
- 新建deploy.bat文件，快速部署
```
hexo clean && hexo g && hexo d
```

### 更换主题
Oranges：https://github.com/zchengsite/hexo-theme-oranges
- 创建git目录
```
git init
```
- Oranges:
```
git submodule add https://github.com/zchengsite/hexo-theme-oranges.git themes/oranges
```
To update the theme in the future, just execute the "git pull" command in the theme root directory.
- 应用
```
theme: oranges
```
Copy the _config.yml file in the theme folder to the blog root directory and rename it to _config.oranges.yml. Subsequent theme modification operations are performed in _config.oranges.yml

### 网页部署
- Zeabur或者Vercel部署
- Github默认的pages页面部署

### 撰写文章
- Create a new post
```
hexo new "My New Post"
```
- vscode如何预览markdown文件
1. 编写markdown文件时，按" command+k " ，松开后紧着按" v "键，即可在当前窗口右侧打开实时预览
2. 按" command+shift+p "调出命令框，输入" markdown "，选择打开预览，即可新窗口打开实时预览

-------
## serv00搭建wordpress博客
### serv00介绍
Serv00 是一家波兰的免费VPS提供商，成立于2008年，致力于 Web 应用托管市场和 UNIX/Linux 服务器管理

1. 免费提供 3GB 的存储空间
2. 内存：512MB
3. 流量：不限流量 （可以搭建IP节点）
4. 支持PHP、MySQL等网站开发语言和数据库
5. 可以同时搭建100个网站
6. 可自定义开放端口
7. 支持SSH远程访问
8. 免费提供的二级域名，可以自定义绑定
9. 官方要求至少每隔3个月登入一次

### 搭建教程
1. 创建账号，进入后台面板管理
2. 下载最新版的WordPress：https://wordpress.org ，把下载好的Wordpress压缩包上传到Fiel manager://domains/xxx.serv00.net/public_html,解压到public_html中。
3. 新建数据库MySQL
数据库信息：
```
Database name: xxxxx
User name: xxx
Password: _

```
4. 进入自己后台（domain/wp-admin）,搭建wordpress博客
后台面板管理
```
Name: admin
Password: eYKnTG4u!Z@KP!zyEJ
```
Tips: 
1. 安装主题可以选择Astra
2. 新建页面（一级菜单栏）
3. 菜单栏里设置自定义链接（二级菜单）
4. 撰写文章，新建分类，链接到二级菜单
5. Astra主题自定义页眉页脚生成器

## 搭建Discourse论坛社区
1. 第一步，准备好一台VPS，内存最好别低于 1G 
2. 准备好一个域名，收费免费的都可以，比如我使用子域名：bbs.freedidi.com ，将其解析到VPS的ip地址上
3. 连接VPS，进入终端进行安装，安装命Docker
```
sudo apt install docker.io
sudo apt install git
```
4. 安装 Discourse
```
sudo -s
git clone https://github.com/discourse/discourse_docker.git /var/discourse
cd /var/discourse
chmod 700 containers
```
5. 执行安装
```
./discourse-setup
```
6. 安装过程中需要填写的信息
```
Hostname for your Discourse? [discourse.example.com]: 
Email address for admin account(s)? [me@example.com,you@example.com]: 
SMTP server address? [smtp.example.com]: 
SMTP port? [587]: 
SMTP user name? [user@example.com]: 
SMTP password? [pa$$word]: 
Let's Encrypt account email? (ENTER to skip) [me@example.com]: 
Optional Maxmind License key () [xxxxxxxxxxxxxxxx]:
```
7. 如果需要修改配置,只需进入并修改该文件： var/discourse/containers/app.yml,修改后进行重启容器即可：
```
cd /var/discourse
./launcher destroy app
./launcher start app
```

## 鸣谢
- 零度论坛搭建：https://www.freedidi.com/11744.html
- 零度VPS服务器：https://www.freedidi.com/12795.html
- 零度开源论坛搭建： https://www.youtube.com/watch?v=UfFp_akjF8E
- 零度网站搭建视频：https://www.youtube.com/watch?v=vILw9l3c_K4
- 开源论坛discourse：https://github.com/discourse/discourse
- 开源网站建设工具：https://github.com/WordPress/WordPress
- 开源问答社区answer: https://github.com/answerdev/answer
- 开源面板1panel：https://github.com/1Panel-dev/1Panel
- Hexo开源框架：https://github.com/hexojs/hexo
- Hexo博客搭建：https://blog.laogou717.com/2024/07/31/AI%20era/Hexo
- Hexo博客重搭建：https://www.cnblogs.com/study-everyday/p/8902136.html

