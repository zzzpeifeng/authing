# 添加用户自定义字段

<LastUpdated/>

用户自定义字段是除了[基础用户字段](/guides/user/user-profile.md)之外，可以给用户对象添加的额外字段。开发者可以通过设置自定义字段，存储**少量**业务相关的数据。

你可以在 **设置->字段管理->用户字段管理** 页面配置自定义用户字段。

可以定义以下几种类型的自定义字段：

- 字符串
- 数值
- 日期
- 布尔值
- Object 对象

![](../images/extend-column.png)

在给新创建的自定义字段命名时，你可以编辑该字段在多种语言环境下的显示名称：

- 直接在「显示名称」下的输入框中编辑，得到默认展示的字段名称
- 勾选「中文」，并编辑中文环境下的字段显示名称
- 勾选「English」，并编辑英文环境下的字段显示名称
- 勾选「繁體」，并编辑繁体中文环境下的字段显示名称
- 勾选「日本語」，并编辑日语环境下的字段显示名称

特别的，如果该字段的显示环境未包含在上述四种语言环境的范围内，将会采用你配置的「默认展示的字段名称」进行显示。

![](../images/extend-column-i18n.jpg)

配置自定义字段之后，你可以开启应用的注册信息补全页面，让用户补全这些自定义字段的信息。

在 **应用详情** - **高级配置** 页，开启 **自定义本应用的登录框**

![](../images/extend-column-supplement-1.png)

然后切换到 **品牌化**，勾上 **开启注册信息补全** 开关，然后选择刚刚添加的自定义字段：

![](../images/extend-column-supplement-2.png)

![](../images/extend-column-supplement-3.png)

输入类型可以选择文本、密码、数字、日期、颜色、Email 和图片，这会决定页面最终的展示样式。

点击保存，之后访问应用的登录页面。

用户点击注册之后将跳转到下面这个注册信息补全页面：

![](../images/extend-column-supplement-4.png)

用户成功注册之后，你可以在用户详情页面看到用户刚刚输入的自定义字段值：

![](../images/extend-column-supplement-5.png)