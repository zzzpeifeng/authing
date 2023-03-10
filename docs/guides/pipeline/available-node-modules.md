---
meta:
  - name: description
    content: 可用的 Node Modules
---

# 可用的 Node Modules

<LastUpdated/>


目前 {{$localeConfig.brandName}} Pipeline 中可以使用以下 Node Modules:

* [Authing SDK for Node.js](https://github.com/Authing/authing.js)
* 网络请求库 [axios](https://github.com/axios/axios)
* lodash
* {{$localeConfig.brandName}} 内置工具集函数 utils

## {{$localeConfig.brandName}} SDK for Node.js

::: hint-danger
出于安全考虑， {{$localeConfig.brandName}} 会通过特殊方式，使用你的用户池 ID（userPoolId） 和用户池密钥（secret） 初始化 authing-js-sdk，此过程不会将你的用户池密钥发送到公网。你可以使用使用全局变量 **authing**，**请勿再次初始化 SDK！**
:::

开发者可以直接使用[初始化](/reference/sdk-for-node/README.md)过后的 authing 实例，**无需手动初始化**！{{$localeConfig.brandName}} Pipeline 会自动帮助开发者  take care 初始化过程。

如下所示：

```js
async function pipe(user, context, callback) {
  //判断用户邮箱是否已 @authing.cn 结尾
  if (!user.email.endsWith('@authing.cn')) {
    return callback(null, user, context)
  }

  try {
    //调用 API 给用户添加角色
    await authing.roles.addUsers('ROLE', [user.id])
  } catch (error) { }

  callback(null, user, context)
}
```

在 addUsers() 中我们使用了 env.ROOT\_GROUP\_ID 通过环境变量来获取组 ID，这样可以避免硬编码。关于如何在 Pipeline 函数中使用环境变量，请见[使用环境变量](env.md)。
关于如何使用 callback 以及 Pipeline 函数的完整 API，请见 [Pipeline 函数 API 文档](pipeline-function-api-doc.md)。

## 网络请求库

目前 {{$localeConfig.brandName}} 支持使用 `axios`，且支持 async/await 语法 🚀！

axios 详细文档请移步[其官方文档](https://github.com/axios/axios)。

## lodash

需要开发者手动导入：

```js
const lodash = require("lodash")
```

详细文档请移步[其官方文档](https://lodash.com/docs/)。

## 内置工具集 utils

{{$localeConfig.brandName}} 内置封装了一些实用的函数，供开发者直接调用。

需要开发者手动导入：

```js
const utils = require("./utils")
```

### 检查 IP 是否位于 IP 段内 <a id="iprangecheck"></a>

使用方法：

```js
utils.ipRangeCheck(IP, [start, end])
```

返回值为 boolean。

示例：以下 Pipeline 函数实现注册 IP 段白名单功能。

```js
async function pipe(context, callback) {
  const utils = require("./utils")
  const ip = context.ip
  if (ip && utils.ipRangeCheck(ip, ["110.53.254.1", "110.53.254.255"])) {
    return callback(null, context)
  }
  return callback(new Error('Access Denied!'))
}

```

## 其他 Node 自带 Module

 {{$localeConfig.brandName}} Pipeline 使用 node8 引擎，[node8 的所有内置模块](https://nodejs.org/dist/v8.17.0/docs/api/documentation.html)均可使用，如 `querystring` 等。

