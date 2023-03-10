
# 社会化身份源

<LastUpdated/>

::: hint-info
有关支持「社会化身份源」功能权益的 {{$localeConfig.brandName}} 用户池版本信息，请查看 [官网「价格」页](https://authing.cn/pricing)。如你的版本不支持此权益，且想试用，可开通体验期。有关体验期介绍及开通方式，请查看 [体验期](/guides/basics/trial/README.md)。
::: 

社会化身份源登录，是指用户使用第三方社交平台的身份认证信息在当前网址进行认证登录的流程。社会化登录不仅有助于简化用户的登录体验，同时也为用户提供了一种更为简单便捷的注册登录方式。在 [{{$localeConfig.brandName}} 控制台](https://authing.cn/) ，目前一共支持国内外将近 20 余种社会化登录，比如个人微信、腾讯 QQ、Facebook、Google、Twitter 等。

![](./images/add_social.png)


## 社会化登录列表

以下是目前平台支持的社会化登录完整列表及相关使用文档：

!!!include(common/social-connections-table.md)!!!

## 社会化登录关联方式

使用「身份源连接的账号关联」功能，让你的用户在使用你所配置的社会化身份源登录时，能够直接登录到已有账号。

当 **未开启「账号身份关联」** 时，用户首次通过身份源登录时默认在用户池中创建新用户。开启 **「账号身份关联」** 后，你可以对用户的「身份源账号关联方式」进行选择，可以允许用户通过「字段匹配」或「询问绑定」的方式直接绑定且登录到已有的账号。

以下是目前平台支持的社会化登录支持关联账号的方式：

!!!include(common/social-connections-associated.md)!!!