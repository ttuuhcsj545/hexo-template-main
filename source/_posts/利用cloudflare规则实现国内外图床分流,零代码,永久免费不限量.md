---
title: 利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量
date: 2025-07-31 16:40:00
updated: 2025-07-31 18:16:00
tags: [零代码, 不限量, 分流, 图床]
description: 利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量,
index_img: 利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/封面.webp
---
>本教程实现了利用cloudflare的规则来实现图床分流，因为cloudflare的规则功能并没有说明使用限量，所以为不限量，只需要添加几个规则即可
## 前提条件  
1.一个cloudflare账号  
2.一个已托管到cloudflare的域名  
3.已经准备好国内外的图床链接  
## 分流至国内
登录cloudflare点击进入你的域名
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20164505.webp)
在左侧菜单点击规则  
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20164920.webp)
在右侧点击创建规则选择重定向规则
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20165153.webp)
在输入框输入名称，选择自定义筛选表达式
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20165711.webp)
在值里面填写你的域名`https://子域.你的主域名/*`子域名可有可不有(域名后面必须有`/*`)，然后点击and添加一个筛选,然后在选项框选择国家与地区,在国家选项框搜索`china`,然后点击china
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20170845.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20170912.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20170932.webp)
将保留查询字符串勾选上，再将类型切换为动态，在表达式里输入`concat("你的国内图床链接", http.request.uri.path)`(如果你的国内图床链接为`https://cn.123.com/123/123.webp`,那你填入的图床链接为`https://cn.123.com/123`,注意最后没有`/`)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172033.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172042.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172239.webp)  
最后点击部署，如果遇到`此规则可能不适用于您的流量`点击部署规则(注意：还没有完)
### 最后一步(国内分流)
如果你只进行国内分流就[进入最后一步](#最后一步)  

## 分流至国外
分流至国外和分流至国内差不多
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20164920.webp)
在右侧点击创建规则选择重定向规则
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20165153.webp)
在输入框输入名称，选择自定义筛选表达式
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20165711.webp)
在值里面填写你的域名(刚刚在分流至中国里面填写的域名(注意：两个域名要一模一样))，然后点击and添加一个筛选,然后在选项框选择国家与地区,将等于切换为不等于,在国家选项框搜索`china`,然后点击china
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20170845.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20170912.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20173847.webp)

将保留查询字符串勾选上，再将类型切换为动态，在表达式里输入`concat("你的国外图床链接", http.request.uri.path)`(如果你的国外图床链接为`https://gw.123.com/123/123.webp`,那你填入的图床链接为`https://gw.123.com/123`,注意最后没有`/`)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172033.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172042.webp)

![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20172239.webp)  
最后点击部署，如果遇到`此规则可能不适用于您的流量`点击部署规则(注意：还没有完)
### 最后一步(国外分流)
如果你只进行国外分流就[进入最后一步](#最后一步)  

## 最后一步
点击右上角黄云回到注意点击`计算（worke）`点击创建，选择`从hello world开始`，点击部署，完成后来到worker的设置，在域和路由里面点击添加，选择自定义域名，输入你在规则里面输入的域名（去掉/*）点击添加域，就完成了
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174552.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174613.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174631.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174640.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174715.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174720.webp)
![dianji](利用cloudflare规则实现国内外图床分流,零代码,永久免费不限量/屏幕截图%202025-07-31%20174746.webp)
## 使用
比方说你的原始图片链接为`https://cn.123.com/123/123.webp`，在要使用这个图片的时候，填入你在规则里面设置的域名后面加`/123.webp`
## 解决问题
如果遇到网站无法跟进重定向，来到域名的规则里面点击添加规则，选择响应头转换规则，选择自定义筛选表达式，在`当传入请求匹配时...`里面的值填写你在规则里面填写的域名（加上/*）,然后在`则...`里面选择添加静态标头名称为`Access-Control-Allow-Origin`值为`*`点击部署，完成