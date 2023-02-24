# 对用户进行权限管理

<LastUpdated/>

::: hint-info
有关支持「权限管理」功能各项权益的 {{$localeConfig.brandName}} 用户池版本信息，请查看 [官网「价格」页](https://authing.cn/pricing)。如你的版本不支持此权益，且想试用，可开通体验期。有关体验期介绍及开通方式，请查看 [体验期](/guides/basics/trial/README.md)。
::: 

在[上一部分](../authentication/README.md)我们介绍了认证，认证指的是识别请求者身份的过程（比如使用密码、微信、手机号验证码等手段），在成功识别了用户的身份之后，我们接下来要做的就是**管理、分配权限。**

权限管理一般指根据系统设置的安全规则或者安全策略，用户可以访问而且只能访问自己被授权的资源，不多不少。

目前被大家广泛采用的两种权限模型为：[基于角色的访问控制（RBAC）](./choose-the-right-access-control-model.md#什么是基于角色的访问控制-rbac)和[基于属性的访问控制（ABAC）](./choose-the-right-access-control-model.md#什么是基于属性的访问控制-abac)，二者各有优劣：RBAC 模型构建起来更加简单，缺点在于无法做到对资源细粒度地授权（都是授权某一类资源而不是授权某一个具体的资源）；ABAC 模型构建相对比较复杂，学习成本比较高，优点在于细粒度和根据上下文动态执行。

接下来，你可以了解如何[为你的应用系统选择一种合适的权限模型。](./choose-the-right-access-control-model.md)
