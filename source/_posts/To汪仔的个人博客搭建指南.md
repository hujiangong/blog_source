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
5. http://localhost:4000/。打开网址即可看到hexo本地默认页面。
6. 接下里便是将hexo网页发布到你的GitHub上。其他的hexo文档可到hexo官网查看。https://hexo.io/zh-cn/。


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
5. 打开你的项目https地址，例如我的"https://github.com/hujiangong/hujiangong.github.io.git"，正常的稍等几分钟即可看到你的博客啦！！

## 6. 更改博客模板
1. 首先呢，你可以到这个地址挑一个你心仪的博客模板"https://github.com/search?q=hexo+stars%3A%3E1"，我暂用的是"https://github.com/SuperKieran/TKL"，就先拿这个来写了。
2. 到hexo文件夹的themes目录下，这个就是博客模板的目录，在这里右键"Git Bash Here" 执行"git clone https://github.com/SuperKieran/TKL.git"，当然你的地址你看上的那个模板的地址，然后执行就可以将这个模板down下来。
3. 然后修改"_config.yml"文件的theme为刚刚down下来的目录文件名，比方说我的就是"theme: TKL"，保存，退出。执行"hexo clean"、"hexo d -g"，OK，过几分钟重新打开你的博客，就会发现模板变啦！
4. "_config.yml"这个文件可修改的地方，还有你下载的模板可修改的地方还有挺多的，你可以参考官方文档进行修改自定义

> 2018年10月8日 第一阶段教学就到这里啦，虽然写的简单，但是咱售后好呀！