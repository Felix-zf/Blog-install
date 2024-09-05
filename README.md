# 博客搭建教学


## hexo重新部署

### 首选重新安装Node.js和Git
本文章主要介绍了在重装系统或者更换电脑以后怎样更新自己的博客，经过自己的尝试可行，于是记录分享一下  
Node.js: https://nodejs.org/en    
Git: https://git-scm.com/download/win

- 测试命令(检测node安装)
```
node -v
npm -v
git --version
```
### 打开Git软件，重新配置SSH
- 配置SSH,一般位于C盘用户.ssh(id_rsa.pub)
```
ssh-keygen -t rsa -C"3188221045@qq.com"
ssh -T git@github.com  /*链接测试*/
```
- 链接账户邮箱
```
git config --global user.name “Felix-zf”
git config --golbal user.email"3188221045@qq.com"
```


### 关联github项目
- 配置
```
git init    
git remote add origin https://github.com/felix-zf/felix-zf.github.io.git    
npm install –g hexo     /*安装Hexo*/  
npm install      /*安装项目依赖*/  
hexo g            /*生成并本地预览*/  
hexo s            /*访问本地客户端*/  
hexo d           /*提交到GitHub*/  
```
- 上传
```
/*进入博客目录的“.deploy_git.git”子目录,找到config文件。
手动配置:
[user]
	email=3188221045@qq.com
	name=Felix-zf               */
hexo cl && hexo g -d                /*清除上传指令*/
```


- 图片示例

![](https://github.com/Felix-zf/Picture-Store/blob/master/img/zy.png)

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
2. 下载最新版的WordPress：https://wordpress.org ，把下载好的Wordpress压缩包上传到Fiel manager://domains/felix7200.serv00.net/public_html,解压到public_html中。
3. 新建数据库MySQL
数据库信息：
```
Database name: felix7200gt
User name: felix7200gt
Password: Felix7200gt.

```
4. 进入自己domain,搭建wordpress博客
后台面板管理
```
Name: admin
Password: eYKnTG4u!Z@KP!zyEJ
```
