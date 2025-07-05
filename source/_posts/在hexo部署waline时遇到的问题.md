---
title: 在hexo部署waline时遇到的问题
date: 2025-07-05 14:43:00
tags: [hexo, 个人博客,waline,评论系统]
---

## 前言
最近Edgeone非常的火，大家都在在抢兑换码,我刚好抢了一个，试了一下他的pages部署了一个hexo博客使用Fluid主题，速度还可以，今天准备加上评论系统waline,我的部署方式为LeanCloud+Vercel
## 问题
- 在本地测试评论没有问题但部署完成后但无法显示评论系统  
解决办法：在项目的themes/fluid/_conflg.yml配置文件中翻到最后将  
`waline: https://registry.npmmirror.com/@waline/client/2.15.8/files/dist/`  
修改为  
  `waline: https://cdn.jsdelivr.net/npm/@waline/client@2.15.8/dist/`
- Vercel部署完成的链接无法访问  
解决办法：添加自定义域名详情看[Vercel配置自定义域名](https://blog.csdn.net/weixin_67658096/article/details/135540102)配置完成后如果太慢可以用Edgeone加速一下详情看[Edgeone加速教程](https://cloud.tencent.com/document/product/1552/87601)
## 结束
我总共就遇到这两个问题，大家还有什么问题可以在评论区讨论