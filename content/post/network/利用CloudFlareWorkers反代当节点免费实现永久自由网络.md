+++
title = '利用CloudFlare Workers反代当节点，免费实现永久自由网络'
date = 2023-11-01T15:40:04+08:00
draft = false

thumbnail = "https://pic.456766.xyz/img/202311020929323.png"

tags = ['CloudflareWorkers','免费vless节点']

categories =  ['网络技术']

series = ['出埃及']

featured = true



+++

你没看错，免费实现永久自由网络！

很不幸，有很多人所处的世界是一个不自由的世界，不但在现实世界不自由，网络上也不能自由活动！好在灵魂是自由的，当然如果你的灵魂也被控制了，那太可怕了……，不过你也不用害怕，让我帮你先实现网络自由，灵魂自由就有希望了！



# 一、配置

## 第一步，注册Cloudflare帐号

打开官网：https://www.cloudflare.com/zh-cn/，注册，登录，这些不就详细介绍了，只要一个邮箱就能实现



## 第二步，创建Workers

![image-20230727110740924](https://pic.456766.xyz/img/202311020922370.png)

在左侧菜单点"Workers和Pages"——创建Workers



## 第三步，部署

![image-20230727111029127](https://pic.456766.xyz/img/202311020924823.png)



## 第四步，修改代码

![image-20230727111103682](https://pic.456766.xyz/img/202311020925656.png)

点“编辑代码”，修改成zizifn大佬的代码：https://github.com/zizifn/edgetunnel/blob/main/src/worker-vless.js

[备用地址](https://4i5i-my.sharepoint.com/:u:/g/personal/sosel_4i5i_onmicrosoft_com/EQr1zW3GUINKptRic9MlSKIBOmUXEukBXOzK6oq-ED0QQQ?e=cTDsBR) （如果你打开不github的话，可以试试从onedrive下载worker-vless.js文件）

![image-20230727111929150](https://pic.456766.xyz/img/202311020925598.png)

删除默认的代码，复制上面链接的代码

![image-20230727114051548](https://pic.456766.xyz/img/202311020926670.png)



注意几个地方：

1，第7行的ID，随便找个UUID替换

2，第9行的IP，可以找前辈们提供的，随便在下面的列表中找一个

```
 cdn-all.xn--b6gac.eu.org
 cdn.xn--b6gac.eu.org
 cdn-b100.xn--b6gac.eu.org
 edgetunnel.anycast.eu.org
 cdn.anycast.eu.org
```



保存并部署

​	修改好之后，点击右上角的“保存并部署”，点击之后没有提示保存成功，但是实际上已经保存并帮你部署好了。

**至此反代已完成**





# 二、使用



## 第一步，找到你的反代地址

## ![image-20230727114615815](https://pic.456766.xyz/img/202311020950740.png)

## 第二步，加上你上面的UUID，得到一个完整的Vless地址

比如我的：https://mailberry.sosel-dfd.workers.dev/868e7e9a-e3fe-407e-bbb9-3d128a9ac51b

![image-20230727114808392](https://pic.456766.xyz/img/202311020950304.png)

## 第三步，得到了V2ray 和clash的节点配置代码，由于workers.dev这个域名已被墙，直接使用是不行的，还要下一步

## 第四步，优选IP

直接使用线上优选

CF在线优选IP：https://vfarid.github.io/cf-ip-scanner/?max=30

![image-20230727123517424](https://pic.456766.xyz/img/202311020950803.png)

这里我随便优选几个IP测试一下

![image-20230727123735605](https://pic.456766.xyz/img/202311020950380.png)

1. 把优选的IP地址填到地址。
2. 把端口改成80，当然，你也可以使用2052，
3. 把TLS改成空，因为我们没有绑定域名，也没有TLS

![image-20230727123946613](https://pic.456766.xyz/img/202311020950821.png)

这样就能正常使用了。

还有一种是有自定议域名的配置，可以使用TLS，也能使用443，更优方案，但不是本文的重点，略过

# 三：进阶

目前使用的反代IP已被滥用，考虑进阶优选一批第三方IP，这些IP太多人在使用，稳定性和速度都不大行，下期介绍第三方优选IP;还有绑定自定义域名，解决官方域名被墙，被污染，很多地方未必能正常长久连接问题。

# 总结

通过利用CF提供的免费workers和借鉴其他专家的智慧，我们不仅仅解决了上外网的难题，还找到了更多创新的方法。这些方法包括使用代理服务器或者云计算等技术手段来实现上外网，让大众用上了免费节点，赞。



参考原文：https://mailberry.com.cn/2023/07/use-cloudflare-workers-to-vless/
