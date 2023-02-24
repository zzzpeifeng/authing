!!!include(common/init-js-mngmt-sdk.md)!!!

使用 `OrgManagementClient` 的 `listChildren` 获取子节点列表：

```javascript
// 子节点列表
const children = await managementClient.org.listChildren("ORGID", "NODEID")
```
