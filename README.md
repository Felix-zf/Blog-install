# Hexo-IS
hexo install

# 重新部署hexo
## 重新安装Node.js和Git
本文章主要介绍了在重装系统或者更换电脑以后怎样更新自己的博客，经过自己的尝试可行，于是记录分享一下
Node.js: ![1](https://nodejs.org/en)
Git: ![2](https://git-scm.com/download/win)
- 测试命令(检测node安装)
```
node -v
npm -v
git --version
```
## 打开Git软件，重新配置SSH
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


## 关联github项目
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


