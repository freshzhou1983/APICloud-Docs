/*
Title: 支付宝支付平台接入
Description: 调用支付宝前期准备
Sort: 11
*/


接入前期准备工作包括商户签约和密钥配置。

- 注册账户

 商户需要在 https://ms.alipay.com 进行注册,并签约安全支付服务。签约成功

![图片说明](/img/docImage/276.png)  
 签约过程中需要任何帮助请致电: 0571-88158090(支付宝商户服务专线)

- 密钥配置

 签约成功后,商户可登陆 https://ms.alipay.com 获取商户账号对应的支付宝公钥(具体步骤见RSA详解),接着,商户生成商户公钥和商户私钥（具体见RSA详解）,并登录 https://ms.alipay.com,上传商户公钥（RSA详解）。 至此,接入前期准备工作完成.

##RSA详解

- RSA 和 OpenSSL 介绍

  RSA 是一种非对称的签名算法,即签名密钥(私钥)与验签密钥(公钥)是不一样的, 私钥用于签名,公钥用于验签。在与支付宝交易中,会有 2 对公私钥,即商户公私钥,支付宝公私钥。使用这种算法可以起到防止数据被篡改的功能,保证支付订单和支付结果不可抵赖(商户私钥只有商户知道)。
  
  OpenSSL 是基于众多的密码算法、公钥基础设施标准以及 SSL 协议安全开 发包。通过 OpenSSL 生成的签名和内置的算法可以做到跨平台,这样在不同的开发语言中均可以签名和验签 
  
###RSA 密钥详解

(1) 生成原始RSA商户私钥文件

![图片说明](/img/docImage/277.png)  
(2) 将原始RSA商户私钥转换为pkcs8格式

![图片说明](/img/docImage/278.png) 

(3) 生成RSA商户公钥

![图片说明](/img/docImage/279.png) 

(4) 上传商户公钥至支付宝 产品”,右侧点击“密钥管理”,见下图红色框内

![图片说明](/img/docImage/280.png) 

点击“上传”,选择步骤(3)生成的“public_key.txt”并完成上传。

(5) 获取RSA支付宝公钥 成功上传公钥至支付宝后,页面显示如下:

![图片说明](/img/docImage/281.png) 

其中红色框内部分即支付宝公钥,请复制至新建 txt 文档,去掉换行和空格,妥善保存(用
