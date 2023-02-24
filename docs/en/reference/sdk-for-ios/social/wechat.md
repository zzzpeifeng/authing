# Login by wechat

<LastUpdated/>

There are three major steps:
* Configurations on wechat open platform
* Steps at Authing console
* Integrate Authing iOS SDK
<br>

## Configurations on [Wechat open platform](https://open.weixin.qq.com/)

>Note: Developer must be verified before using any service on wechat open platform. Wechat doesn't support personal usage, so developer must be part of some organization, commercial or governmental. And It costs 300 RMB to become a verified developer.

1. Get wechat AppID and AppSecret

![](./images/wechat/1.png)

2. Setup iOS information

![](./images/wechat/2.png)

Wechat requires a callback through [Universal Links](https://developer.apple.com/ios/universal-links/)

<br>

## Steps at Authing console:

1. Click 'Authentication' on the left sidebar and choose 'Social', then click 'Wechat'

![](./images/wechat/3.png)

2. In the list select 'Wechat Mobile'

![](./images/wechat/4.png)

3. Set an ID for this connection. It can be anything as long as being unique across Authing's connections.

4. Enter your wechat AppID and AppSecret
![](./images/wechat/5.png)

6. Hit 'Save' and we are all set

<br>

## Integrate iOS SDK

### Initialize Guard SDK

> Guard-iOS-binary depends on the Guard component (after Version 1.2.4)

- in the swift package search bar enter: https://github.com/Authing/authing-binary

- Dependency rule Select Up to Next Major Version 1.0.0

- Add Package Then select Wechat

<br>

### Add start WeChat whitelist in Info.plist

key: LSApplicationQueriesSchemes

value: weixin, weixinULAPI

![](./images/wechat/6.png)

You can also open Info.plist through Source Code, and then copy and paste the following code:

```xml
<plist version="1.0">
<dict>
    ...
    <key>LSApplicationQueriesSchemes</key>
	<array>
		<string>weixin</string>
		<string>weixinULAPI</string>
	</array>
    ...
</dict>
</plist>
```

<br>

### To set up WeChat when the App starts:

```swift
import Guard
import Wechat
Authing.start(<#Authing AppId#>);
WechatLogin.registerApp(appId: <#your_wechat_appid#>, universalLink: <#your_deep_link#>)
 ```
The first parameter is the WeChat App id; the second parameter is iOS [Universal Link](https://developer.apple.com/ios/universal-links/)

<br>

### Set Associated Domains：

> Replace with the host corresponding to your Universal Link

![](./images/wechat/7.png)

<br>

## Handling Wechat Callbacks

After Alipay returns to the application, if SceneDelegate is used, you need to overload the following functions in SceneDelegate.swift:

```swift
func scene(_ scene: UIScene, continue userActivity: NSUserActivity) {
    NotificationCenter.default.post(name: NSNotification.Name(rawValue: "wechatLoginOK"), object: userActivity)
}
```

If SceneDelegate is not used, you need to be overloaded in AppDelegate

```swift
func application(_ application: UIApplication, continue userActivity: NSUserActivity, restorationHandler: @escaping ([UIUserActivityRestoring]?) -> Void) -> Bool {
    NotificationCenter.default.post(name: NSNotification.Name(rawValue: "wechatLoginOK"), object: userActivity)
    return true
}
```

<br>

### Initiate wechat authorization

#### Wechat Login

```swift
func login(viewController: UIViewController, _ context: String? = nil, completion: @escaping Authing.AuthCompletion) -> Void
``` 

**Parameter**

* *viewController* AuthViewController
* `context` Request context, set here `context` you can get [pipeline context](/guides/pipeline/context-object.md) .

**Example**
```swift
// context is optional Parameters
WechatLogin.login(viewController: <#AuthViewController#>, "context") { code, message, userInfo in
    if (code == 200) {
        // login successful
        // userInfo
    } else if (code == 1640) {
        // Only an existing account can be bound
        // userInfo.socialBindingData return method(login method) and key(intermediate state key)
    } else if (code == 1641) {
        // Allows you to bind existing accounts or create new accounts
        // userInfo.socialBindingData return method(login method) and key(intermediate state key)
    } else if (code == 2921) {
        // Select multiple accounts and bind them
        // userInfo.socialBindingData return accounts(account list) and key(intermediate state key)
    }
}
```

</br>

If you want to obtain only wechat authorization code:
```swift
WechatLogin.getAuthCode(viewController: <#AuthViewController#>) { authCode in
    // authCode: wechat authorization code
}
```

</br>

If you want to implement the whole process by your own, right after you get auth code, please call this API to get Authing user info:

#### Get the data by wechat login

```swift
func getDataByWechatlogin(authData: AuthRequest? = nil, code: String, _ context: String? = nil, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 
**Parameter**

* *code* wechat auth code
* `context` Request context, set here `context` you can get [pipeline context](/guides/pipeline/context-object.md) .

**Example**
```swift
AuthClient().getDataByWechatlogin(code: "Wechat auth code") { code, message, userInfo in
    if (code == 200) {
        // login successful
        // userInfo
    } else if (code == 1640) {
        // Only an existing account can be bound
        // userInfo.socialBindingData return method(login method) and key(intermediate state key)
    } else if (code == 1641) {
        // Allows you to bind existing accounts or create new accounts
        // userInfo.socialBindingData return method(login method) and key(intermediate state key)
    } else if (code == 2921) {
        // Select multiple accounts and bind them
        // userInfo.socialBindingData return accounts(account list) 以及 key(intermediate state key)
    }
}
```

<br>

## Binding API

If you want to ask whether to bind an existing account when you log in with your wechat account, you can enable the query binding function in  [Authing Console](https://authing.cn/)，

**Authentication -> Social -> WeChat -> WeChat Mobile** **-> Bind to Existing Account：**

![](./images/wechat/8.png)

:::hint-info
If using our **AuthFlow** hosting page, after opening the **Bind to Existing Account**, relevant business processes are processed in the hosting page.
:::

If you have selected the  **Login Mode**  and enabled the **Bind to Existing Account** function, use the following API to build the subsequent business process:

### Register a new account and binding to wechat

If **Login Mode** is selected for **Sign in & sign up** and **Bind to Existing Account** is enabled, the Wechat login interface will return `1641` status code and `key`. At this time, this interface can be called to directly create an account.

```swift
func bindWechatWithRegister(key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatWithRegister(key: "key") { code, message, userInfo in
}
```

<br>

### Binding Wechat by account password

If **Login Mode** is selected，the Wechat login interface will return `1640` or`1641` status code, supported binding modes and `key`，If the supported binding modes include `username-password`, `phone-password`, and `email-password,` you can invoke this interface.

```swift
func bindWechatByAccount(account: String, password: String, key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *account* account
* *password* password
* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatByAccount(account: "account", password: "password", key: "key") { code, message, userInfo in
}
```

<br>

### Binding Wechat by mobile verification code

If **Login Mode** is selected，the Wechat login interface will return `1640` or`1641` status code, supported binding modes and `key`，If the supported binding modes include `phone-code`, you can invoke this interface.

```swift
func bindWechatByPhoneCode(phoneCountryCode: String? = nil, phone: String, code: String, key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *phone* phone
* *code* code
* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatByPhoneCode(phone: "188xxxx8888", code: "1234", key: "key") { code, message, userInfo in
}
```

<br>

### Binding Wechat by email verification code

If **Login Mode** is selected，the wechat login interface will return `1640` or`1641` status code, supported binding modes and `key`，If the supported binding modes include `email-code`, you can invoke this interface.

```swift
func bindWechatByEmailCode(email: String, code: String, key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *email* email
* *code* code
* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatByEmailCode(email: "test@example.com", code: "1234", key: "key") { code, message, userInfo in
}
```

<br>


### Bind Wechat by account ID in the accounts list

If **account binding** is enabled, it will return `2921` status code, supported binding account data and `key` when calling wechat login interface.
> Note that this API can only bind the accounts returned by [getDataByWechatlogin](#-get-the-data-by-wechatlogin), and only applies to scenarios where multiple Authing accounts correspond to the same wechat identity source. If you want to directly call the binding API without special scenarios, check this API: [Bind wechat by account ID](#-Bind-wechat-by-account-ID).

```swift
func bindWechatBySelectedAccountId(accountId: String, key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *accountId* account id
* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatBySelectedAccountId(accountId: "AUTHING_ACCOUNT_ID", key: "key") { code, message, userInfo in
}
```

<br>

### Bind Wechat by account ID

If **Login Mode** is selected，this interface can be invoked to bind existing accounts in the user pool.

```swift
func bindWechatByAccountId(accountId: String, key: String, completion: @escaping(Int, String?, UserInfo?) -> Void)
``` 

**Parameter**

* *accountId* account id
* *key* intermediate state key，return by [Wechat Login](#-Get-the-data-by-wechat-login)

**Example**
```swift
AuthClient().bindWechatByAccountId(accountId: "AUTHING_ACCOUNT_ID", key: "key") { code, message, userInfo in
}
```

<br>



