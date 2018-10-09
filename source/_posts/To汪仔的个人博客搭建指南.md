---
title: To汪仔的个人博客搭建指南
---
## 1. 说明 ##

简单来说，通过GitHub免费搭建个人博客是基于其GIthub Pages功能，也就是将你存储在GitHub上的静态网页文件展示出来。So，你需要有一个GitHub账号，注册和使用GitHub问题就不在这里阐述了。你肯定会的。

官方推荐使用GitHub+jekyll（简单的免费的Blog生成工具），我们使用教程更加丰富的GitHub+Hexo+Markdown。
	
## 2. 准备 ##

1. **git**：这个安装和使用对你来说应该也不是什么问题。
2. **Note.js**：一个Javascript运行环境，猜测JavaScript能在静态页面正常运行就是基于这个。https://nodejs.org 官网下载，使用默认安装即可。
3. **Hexo**：如果Note.js正常安装并且加入了环境变量中，直接在Windows命令窗口输入“npm install hexo-cli -g”即可安装。之后在命令窗口输入“hexo -v”正常显示即安装成功。
4. **MarkdownPad 2**：一款Markdown编辑器，我目前也是根据网上的评价下载安装，你也可以使用别的markdown编辑器，比方说CSDN博客或者有道云笔记的。（附赠一个注册码，嘘...  **email**: Soar360@live.com **lience**：GBPduHjWfJU1mZqcPM3BikjYKF6xKhlKIys3i1MU2eJHqWGImDHzWdD6xhMNLGVpbP2M5SN6bnxn2kSE8qHqNY5QaaRxmO3YSMHxlv2EYpjdwLcPwfeTG7kUdnhKE0vVy4RidP6Y2wZ0q74f47fzsZo45JE2hfQBFi2O9Jldjp1mW8HUpTtLA2a5/sQytXJUQl/QKO0jUQY4pa5CCx20sV1ClOTZtAGngSOJtIOFXK599sBr5aIEFyH0K7H4BoNMiiDMnxt1rD8Vb/ikJdhGMMQr0R4B+L3nWU97eaVPTRKfWGDE8/eAgKzpGwrQQoDh+nzX1xoVQ8NAuH+s4UcSeQ==）
5. 如果在使用MarkdownPad的时候出现“This view has crashed”错误，安装“Awesomium 1.6.6 SDK.”即可，参考官方文档：http://markdownpad.com/faq.html#livepreview-directx

## 3. 创建GitHub博客仓库 ##
就按照正常的GitHub创建仓库的步骤就可以，唯一需要注意的一点就是创建的GitHub仓库格式必须是username.github.io（username是你的账号名)，这个地址也就是最后的访问域名，之后Create repository即可。![创建实例](https://i.imgur.com/B3PgNqq.png)

## 4. 创建本地博客文件 ##
1. 找一个目录，根据经验来说，最好是全英文路径，中文不知道以后会有什么奇怪的问题出现。新建一个hexo文件夹(名字随意)，在文件夹上右键git bash here.
2. hexo init。初始化目录结构
3. hexo g。生成静态文件
4. hexo s。启动服务。
5. http://localhost:4000/ 。打开网址即可看到hexo本地默认页面。
6. 接下里便是将hexo网页发布到你的GitHub上。其他的hexo文档可到hexo官网查看。https://hexo.io/zh-cn/ 。


## 5. 上传本地博客文件到GitHub上 ##
1. 首先，默认你会并且已经将你电脑上git和你的GitHub账号绑定，即push代码到你的GitHub木有问题了！
2. 然后将你Hexo文件夹下的"_config.yml"文件打开，将其中deploy部分改成如下格式。其中repo是你的上面新建的仓库的ssh地址。

```
deploy:
  type: git
  repo: git@github.com:hujiangong/hujiangong.github.io.git
  branch: master
```

![repo地址](https://i.imgur.com/Ric2yeI.png)
3. 执行"npm install hexo-deployer-git --save"命令安装一些必要的插件
4. 执行"hexo d -g"部署代码并且上传到你的GitHub地址上。
5. 打开你的项目https地址，例如我的" https://github.com/hujiangong/hujiangong.github.io.git "，正常的稍等几分钟即可看到你的博客啦！！

## 6. 更改博客主题
1. 首先呢，你可以到这个地址挑一个你心仪的博客主题" https://github.com/search?q=hexo+stars%3A%3E1 "（GitHub上有关hexo内容的star排行）或者到hexo的官方主题站" https://hexo.io/themes/ "，我暂用的是" https://github.com/SuperKieran/TKL "，就先拿这个来写了。
2. 到hexo文件夹的themes目录下，这个就是博客主题的目录，在这里右键"Git Bash Here" 执行"git clone https://github.com/SuperKieran/TKL.git"，当然你的地址你看上的那个主题的地址，然后执行就可以将这个主题down下来。
3. 然后修改"_config.yml"文件的theme为刚刚down下来的目录文件名，比方说我的就是"theme: TKL"，保存，退出。执行"hexo clean"、"hexo d -g"，OK，过几分钟重新打开你的博客，就会发现主题变啦！
4. "_config.yml"这个文件可修改的地方，还有你下载的主题可修改的地方还有挺多的，你可以参考官方文档进行修改自定义

> 2018年10月8日 第一阶段教学就到这里啦，虽然写的简单，但是咱售后好呀！

----------
***------------------------------------- 2018年10月9日更新 ----------------------------------------*** 
## 7. 同时上传静态代码和hexo源码 ##
首先呢，问题发生在今天打算在公司的时候进行一些小的修改（我才不会承认是不想干活），才发现GitHub的这个仓库里面只有静态网页文件，没有hexo源码，这样也不可能直接修改静态文件啊，所以只能先好好工作了。嘘... 这样既不便于多台电脑同时修改，而且如果存hexo文件的电脑出现什么无法修复的数据丢失问题，也会把原始文件都丢了，所以解决办法当然就是再上传一份源码到GitHub上。解决办法有两种：
### 1.新建一个仓库 ###
1. 第一步不用说就是在GitHub新建一个仓库，我的就叫blog_source了。
2. 然后将你下载的hexo文件夹下themes目录的博客主题文件夹中的.git文件夹删除。比方说目前用的是TKL主题，在我的themes/TKL/.git这个文件夹删除。因为我们需要把hexo文件夹里面的内容当做一个git文件上传到GitHub库中。git的正常运作是通过.git文件夹中的内容进行更新。TKL文件中的.git目录说明TKL文件中的内容本身就是一个git仓库（我们是从GitHub上直接clone下来的，方便以后博客主题更新以后，我们也可以同步更新），有自己的版本，如果你将它的母目录也当做git仓库去操作就会产生冲突。一种解决办法是把它当做git的子模块处理，但是比较麻烦，暂先直接当做普通文件夹处理，主题以后的更新另想它法。
3. 在hexo文件夹中右键git bash here，然后执行
```
git init 														## 将hexo文件夹初始化成git文件夹
git add . 														## 新增所有文件
git commit -m "first commit"									## commit add 操作
git remote add origin git@github.com:hujiangong/blog_source.git	## 将本地库和GitHub库关联
git push -u origin master										## push 本地origin分支的内容到远程master分支，首次需要使用-u参数，以后的更新只需要git push origin master即可
```
4. 之后就可以在别的电脑上克隆下载代码，然后同步更新了。但是别忘了在不同电脑更新以后，在其他电脑上更新的时候先更新一下本地的代码。git pull 操作。