# 什么是用户池

<LastUpdated/>

当你开始要构建一个激动人心的应用程序的时候，往往第一件事情是搭建一个用户系统，而搭建用户系统又总是牵扯到复杂的认证流程和安全问题，使用 {{$localeConfig.brandName}} 可以解除你这些烦恼。

在使用 {{$localeConfig.brandName}} 的第一步是创建一个用户池。用户池是你用户系统的隔离的最小单位，你可以把不同场景的用户划分在不同的用户池。每个用户池下拥有自己的用户和应用程序，不同用户池之间的权限、应用、组织是完全隔离的。

<!-- （建议此处加一个用户池和多应用的架构图） -->

<img src="~@imagesZhCn/concepts/userpool.png" alt="drawing"/>

你可以在 {{$localeConfig.brandName}} 的用户池中创建用户，通过目录集成导入用户，或通过应用程序集成导入用户。用户池下的应用程序是与公共应用程序（例如 Office365）或专有应用程序（例如你自己的应用程序）的连接。通过这样的连接，你的用户可以通过一个身份在不同的应用之间快速高效的完成认证和授权。

## 用户池的 URL 地址

在创建 {{$localeConfig.brandName}} 的用户池的时候，会为每个用户池分配了一个 URL（即进入用户池后浏览器地址栏地址）。典型的组织 URL 是租户名称（子域），然后是域名（如 `you-tenant-domain.authing.cn`）。你可以通过使用自己的域名替换 {{$localeConfig.brandName}} 域名来自定义 {{$localeConfig.brandName}} 用户池的 URL，[详情请查看此文档](/guides/deployment/custom-domain.md)。

## 管理员控制台

管理员控制台（或管理控制台）是你用来管理 {{$localeConfig.brandName}} 用户池的地方。作为管理员你需要通过 [https://console.authing.cn](https://console.authing.cn) 这个域名登录管理员控制台，在管理员控制台，你可以创建新的用户池或者在不同的用户池之间切换。

在管理控制台中进入某个用户池可以管理用户池内的用户数据和应用连接信息。

## 跨用户池

用户池是用户或者应用资源的硬性分界，因此无法在用户池之间共享用户和应用数据。你可以使用[联邦认证](/guides/federation/)的方式，以允许用户跨用户池登录，但是用户仍然分别存在于每个组织中。

## 多个用户池

在大多数情况下，你的公司或项目只有一个用户池。单个用户池为整个用户群提供了一个标准资源管理入口，为应用程序提供了一个集成点，并且具有较低的复杂性。
但是，在更复杂的情况下，你可能需要多个用户池。例如，你的公司是一个大型组织，员工数大于一万人，有很多的上游和下游供应商，你需要将员工和供应商在某个 ERP 应用中配合完成某项业务流程。这时候可以建立两个用户池，内部员工属于一个用户池，外部供应商属于另一个用户池。通过连接外部身份源的方式，允许供应商访问内部的 ERP 应用，实现公司内外部组织的分割管理和协同工作。
多个用户池允许内部和外部用户的完全隔离，并且内部或外部组织的应用程序和更改不会相互影响。但是，多个用户池在要管理的环境数量方面增加了复杂性。我们推荐尽可能减少用户池的数量降低系统复杂度。

## 什么是用户池场景

在 {{$localeConfig.brandName}} 中我们将用户池分为不同使用场景以便更好地为你服务，每个场景都有独立的服务计划，分为「B2C」「B2B」和 「B2E」, 在创建用户池之前必须选择场景，对应的选项分别为：B2C - 我想为我的 C 端用户提供更好地身份认证体验；B2B - 我想为我的 B 端客户提供更好地身份认证体验；B2E -  我想为企业管理员工身份。

<img src="./images/userpool_02.png" alt="drawing"/>

## 费用收取

在 {{$localeConfig.brandName}} 中，不同的用户池场景收费不同，除 B2E 外每个场景都分为「免费版」「基础版」「高级版」和「企业版」。

不同场景下「免费版」「基础版」「高级版」和「企业版」功能与服务的详细对比，详情请见  [官网「价格」页](https://authing.cn/pricing)。

## 接下来

了解了用户池的概念之后，接下来你可以了解一下[应用](./application.md)的概念。
