---
meta:
  - name: description
    content: SDK for React Native
---

# SDK for React Native

<LastUpdated/>

#### ð  [Homepage](https://github.com/Authing/authing-rn-sdk)

<!-- Authing æ¯æ React Native ç§»å¨ç«¯å¼åç§»å¨ç«¯ï¼ä½¿å¾å¼åèå¯ä»¥å¿«éæ¥å¥æ¯ä»å®ãå¾®ä¿¡ç­ APP ç»å½ï¼ä»¥ååä»£ç å¼åæ¯æé®ç®±å¯ç ãç¨æ·åå¯ç ãææºéªè¯ç ç»å½ã

<img height="500px" src="http://lcjim-img.oss-cn-beijing.aliyuncs.com/2019-12-03-150521.jpg" alt="" style="display:block;margin: 0 auto;"/>

[ç¹å»æ­¤æ¥çæ¼ç¤ºè§é¢](https://cdn.authing.cn/authing-rn-sdk.mp4)ã

ä»¥ä¸æ¯æä¾çå®æ´åè½åè¡¨ï¼

- é®ç®±å¯ç ç»å½æ³¨å
- ææºéªè¯ç ç»å½
- ç¨æ·åå¯ç ç»å½
- å¿è®°å¯ç ä»¥åéç½®å¯ç 
- ç§»å¨ç«¯ APP ç¤¾ä¼åç»å½

ç®åæ¯æçç¤¾ä¼åç»å½æï¼

- [x] æ¯ä»å®
- [ ] å¾®ä¿¡ -->

<img height="500px" src="https://authing-files.oss-cn-zhangjiakou.aliyuncs.com/authing-blog/rn-demo.jpeg" alt="" style="display:block;margin: 0 auto;"/>


## GitHub ä¸è½½å°å

| æ¡ç®     | è¯´æ                                        |
| -------- | ------------------------------------------- |
| æ¯æçæ¬ | ææçæ¬                                    |
| ä»åºå°å | [https://github.com/Authing/authing-rn-sdk](https://github.com/Authing/authing-rn-sdk) |


## å®è£

> æ³¨ï¼authing-rn-sdk ç npm ååç§°ä¸º @authing/rn

```bash
yarn add react-native-gesture-handler react-native-webview
yarn add @authing/rn
```

å¦ææ¯ iOSï¼éè¦æ§è¡ï¼

```bash
cd ios && pod install
```

> æ³¨ï¼ä» react-native 0.60 çæ¬å¼å§ï¼ä¸åéè¦æå¨æ§è¡ react-native link æä»¤ã

å¦æä¸åé¡ºå©ï¼ä½ ä¼çå°ï¼

![](https://cdn.authing.cn/blog/image%20%28224%29.png)

> ç±äºå¹³å°éå¶ï¼å¦æéè¦æ¥å¥ç¤¾ä¼åç»å½ï¼è¿éè¦è¿è¡ä¸äºé¢å¤éç½®ï¼è¯¦æè§ä¸æã

ç°å¨ä¸åå°±ç»ªï¼å¯ä»¥å¼å§ä½¿ç¨ authing-rn-sdk å¿«éæ¥å¥ Authing å¼ºå¤§çèº«ä»½è§£å³æ¹æ¡å¦ï¼

## å¿«éæ¥å¥

æ¥å¥ AuthingGuard éå¸¸ç®åï¼æç®æåµä¸ï¼ä½ åªéè¦æå®[åºç¨ ID (appId)](/guides/faqs/get-app-id-and-secret.md) åæåç»å½äºä»¶çåè°å½æ°å³å¯ï¼ï¼å®æ´çäºä»¶åè¡¨è§ä¸æãï¼

```js
import { AuthingGuard } from '@authing/rn';
```

```js
const onLogin = userInfo => {
	// deal with userInfo
};
```

```javascript
<AuthingGuard appId="{appId}" onLogin="{onLogin}" />
```

ä¸é¢æ¯ä¸ä¸ªç®åçå®æ´ç¤ºä¾ï¼

```js
import React from 'react';
import { SafeAreaView, StatusBar } from 'react-native';
import { AuthingGuard } from '@authing/rn';

const App = () => {
	const appId = '5dd77e6efa26f000d18101ca';
	const options = {
		title: 'Authing Guard SDK',
		forceLogin: true // å°æ³¨ååç»å½åå¹¶ï¼å½ç¨æ·ä¸å­å¨çæ¶åä¸ºå¶èªå¨æ³¨å
	};
	const onLogin = (loginMethod, userInfo) => {
		alert(JSON.stringify(userInfo));
	};
	return (
		<>
			<StatusBar barStyle="dark-content" />
			<SafeAreaView style={{ flex: 1 }}>
				<AuthingGuard appId={appId} options={options} onLogin={onLogin} />
			</SafeAreaView>
		</>
	);
};

export default App;
```

éè¿ä»¥ä¸æä»¤è¿è¡ï¼ iOSï¼

```bash
npx react-native run-ios
```

Android:

```bash
npx react-native run-android
```

ç¨æ·æåç»å½ä¹å authing-rn-sdk ä¼å°ç¨æ·ä¿¡æ¯ `userInfo` åè°ç»ä¼ å¥ç `onLogin` å½æ°ï¼`userInfo` æ¯æ°ç»ç±»åï¼ç¬¬ä¸é¡¹æ¯ç¨æ·ä¿¡æ¯ï¼ç¨æ·ä¿¡æ¯ä¸­åå«äº Authing ç¨æ· IDãå¤´åãæµç§°ç­ï¼è¿åæ¬ç»å½å­è¯ `token`ã`userInfo` ç¤ºä¾å¦ä¸ï¼

```json
[
	{
		"id": "5dc10bcb6f94c178c6ffffb9",
		"email": null,
		"emailVerified": false,
		"unionid": "oiPbDuG4S7msrKHPKDc8MECSe8jM",
		"openid": "oiPbDuG4S7msrKHPKDc8MECSe8jM",
		"oauth": "{\"openid\":\"oiPbDuG4S7msrKHPKDc8MECSe8jM\",\"nickname\":\"å¼ ä¸\",\"sex\":1,\"language\":\"zh_CN\",\"city\":\"æµ·æ·\",\"province\":\"åäº¬\",\"country\":\"ä¸­å½\",\"headimgurl\":\"http://thirdwx.qlogo.cn/mmopen/vi_32/GkxYERPDdTMk7bOk3BgBmEEYul8oMcOoLgNHLoibZn5ibe4EulWBp1xo6uN4az59eoSBYBW0QmXB9TrsJEM0EoPw/132\",\"privilege\":[]}",
		"registerMethod": "oauth:wxmp",
		"username": "å¼ ä¸",
		"nickname": "å¼ ä¸",
		"company": "",
		"photo": "https://usercontents.authing.cn/avatar-5dc10bcb6f94c178c6ffffb9-1572932555337",
		"token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjp7InVuaW9uaWQiOiJvaVBiRHVHNFM3bXNyS0hQS0RjOE1FQ1NlOGpNIiwiaWQiOiI1ZGMxMGJjYjZmOTRjMTc4YzZmZmZmYjkiLCJjbGllbnRJZCI6IjVkYTdlZGFiNTAzOTZjMWFkOTYyMzc4YSJ9LCJpYXQiOjE1NzI5NTY0MjUsImV4cCI6MTU3NDI1MjQyNX0.OTgl72WZS8So3R5DbWCJ7I_Bd0LaZa4S0TAVMg9qaYQ",
		"tokenExpiredAt": "11/20/2019, 8:20:25 PM",
		"loginsCount": 43,
		"lastLogin": "11/5/2019, 8:20:25 PM",
		"lastIP": "127.0.0.1",
		"signedUp": "11/5/2019, 1:42:35 PM",
		"blocked": false,
		"isDeleted": false
	}
]
```

### å¦ä½æºå¸¦ token

å° `Authorization` è¯·æ±å¤´è®¾ç½®ä¸º "Bearer " + tokenï¼ä¾å¦ï¼

> æ³¨æ Bearer å token ä¹é´çç©ºæ ¼

```js
Authorization: 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJkYXRhIjp7InVuaW9uaWQiOiJvaVBiRHVHNFM3bXNyS0hQS0RjOE1FQ1NlOGpNIiwiaWQiOiI1ZGMxMGJjYjZmOTRjMTc4YzZmZmZmYjkiLCJjbGllbnRJZCI6IjVkYTdlZGFiNTAzOTZjMWFkOTYyMzc4YSJ9LCJpYXQiOjE1NzI5NTY0MjUsImV4cCI6MTU3NDI1MjQyNX0.OTgl72WZS8So3R5DbWCJ7I_Bd0LaZa4S0TAVMg9qaYQ';
```

å¦æä½ ä½¿ç¨çæ¯ axiosï¼å¯ä»¥è¿æ ·åï¼

```js
axios.get('https://mywebsite.com/endpoint/', {
	headers: {
		Authorization: `Bearer ${userInfo[0].token}`
	}
});
```

å¦æä½ ä½¿ç¨çæ¯ fetchï¼å¯ä»¥è¿æ ·åï¼

```js
fetch('https://mywebsite.com/endpoint/', {
	method: 'POST',
	headers: {
		Authorization: `Bearer ${userInfo[0].token}`
	},
	body: JSON.stringify({
		firstParam: 'yourValue',
		secondParam: 'yourOtherValue'
	})
});
```

### å¦ä½å¨åç«¯æ£éª Token

Authing æä¾äºå ç§æ¹æ³å¸®å©æ£éª token çåæ³æ§åå¯¹åºç¨æ·çç»å½ç¶æï¼[ææ¡£ç¹è¿é](https://docs.authing.cn/v2/guides/faqs/how-to-validate-user-token.html)ã

å¼åèå¯ä»¥æè¿ä¸ªæ¹æ³å°è£æä¸ä¸ªå½æ°ï¼æ¯å¦è¯´ check_authing_token_statusï¼ä¸ºäºæ¹ä¾¿æä½¿ç¨äº Python ï¼ï¼

> å¼åèä¸ç¨å¨åç«¯å­å¨è¯¥ tokenï¼åªéè¦è°ç¨ Authing æä¾çæ¥å£ã

```python
def check_authing_token_status(token: str) -> bool:
    """
    :param token: Authing è¿åç¨æ·ä¿¡æ¯ä¸­æºå¸¦ç token
    :return: å¸å°å¼ï¼è¡¨ç¤ºæ¯å¦å¤äºç»å½ç¶æ
    """
    # è°ç¨ Authing æä¾çæ¹æ³ï¼å·ä½å®ç°æ¹æ³çç¥ï¼è¯·åè§ä¸ææå°çææ¡£
    pass
```

ç¶åå°±å¯ä»¥éè¿ç»å½ç¶æåèªå·±çä¸å¡é»è¾å¯¹è¯·æ±è¿è¡ååºäºï¼æ¯å¦ï¼

```python
logged_in = check_authing_token_status(token)
if not logged_in:
    # è¿åéè¯¯æç¤º
# æ­£å¸¸ç»§ç»­ä¸é¢çé»è¾
```

### å¦ä½éè¿ç¨æ·è§è²æ§å¶ç¨æ·è®¿é®

ææ¶åæ¯å¦ç»å½è¿ä¸ä¸ªæ¡ä»¶æ¯ä¸è¶³ä»¥å¤æ­è¯·æ±æ¹æ¯å¦æè®¿é®èµæºçæéçï¼ä¸ºæ­¤ Authing è¿æä¾äºç¨æ·è§è²ç¸å³ç APIã

## æ¯æçåè°å½æ°åè¡¨

| åè°å½æ°                     | å¯¹åºäºä»¶                         | åæ°     | åæ°è¯´æ                                                                 |
| :--------------------------- | :------------------------------- | :------- | :----------------------------------------------------------------------- |
| onLogin                      | æåç»å½                         | userInfo | ç¨æ·ä¿¡æ¯ã                                                               |
| onLoad                       | Authing appId éªè¯éè¿ï¼å è½½å®æ | data     | AuthenticationClient å¯¹è±¡                                                |
| onRegister                   | ç¨æ·æ³¨åæå                     | userInfo | ç¨æ·æ°æ®ãå onLogin åè°å½æ°ç `userInfo` åæ°ä¸è´ï¼ä½æ¯ `token` ä¸ºç©ºã |
| onResetPassword              | éç½®å¯ç æå                     | data     | éç½®å¯ç ç»æ                                                             |
| onRegisterTabChange          | æ³¨å tab åæ¢äºä»¶                | data     | åæ¢åç tab                                                             |
| onPwdReset                   | å¯ç éç½®æåäºä»¶                 | data     | -                                                                        |
| onPwdEmailSend               | å¿è®°å¯ç é®ä»¶åéæå             | data     | -                                                                        |
| onPwdPhoneSend               | å¿è®°å¯ç ææºéªè¯ç åéæå       | data     | -                                                                        |
| onLoginTabChange             | ç»å½ tab åæ¢äºä»¶                | data     | -                                                                        |
| onRegisterInfoCompleted      | æ³¨åè¡¥åæåäºä»¶                 | data     | -                                                                        |
| onRegisterError              | ç¨æ·æ³¨åå¤±è´¥                     | `error`  | éè¯¯ä¿¡æ¯.                                                                |
| onLoginError                 | ç»å½å¤±è´¥                         | `error`  | éè¯¯ä¿¡æ¯ã                                                               |
| onRegisterInfoCompletedError | æ³¨åè¡¥åå¤±è´¥äºä»¶                 | `error`  | éè¯¯ä¿¡æ¯ã                                                               |
| onPwdResetError              | å¯ç éç½®äºä»¶å¤±è´¥äºä»¶             | `error`  | éè¯¯ä¿¡æ¯ã                                                               |
| onPwdPhoneSendError          | ææºå·éç½®å¯ç åééªè¯ç å¤±è´¥äºä»¶ | `error`  | éè¯¯ä¿¡æ¯ã                                                               |
| onPwdEmailSendError          | é®ç®±éç½®å¯ç åééªè¯ç å¤±è´¥äºä»¶   | `error`  | éè¯¯ä¿¡æ¯ã                                                               |
| onLoadError                  | Authing appId éªè¯å¤±è´¥äºä»¶       | `error`  | éè¯¯ä¿¡æ¯ã                                                               |

## èªå®ä¹ UI

AuthingGuard æ¯æé«åº¦èªå®ä¹ï¼å¯ä»¥éè¿ options åæ°ä¼ å¥ï¼å¦ï¼

```jsx
<AuthingGuard
	userPoolId={userPoolId}
	options={{
		title: 'ä½ çåºç¨åç§°',
		logo: 'ä½ çåºç¨å¾æ ',
		// å°æ³¨ååç»å½åå¹¶ï¼å¦æç¨æ·ä¸å­å¨ä¼èªå¨åå»ºå¹¶ç»å½
		forceLogin: true,
		placeholder: {
			// èªå®ä¹ç¨æ·åè¾å¥æ¡ç placeholder
			username: 'xxxxx'
		}
	}}
	onLogin={onLogin}
/>
```

<!--
### å å¥èªå®ä¹ CSS

authing-rn-sdk è¿æ¯æéè¿ `options.css` ä¼ å¥èªå®ä¹ CSS æ ·å¼ï¼è¿ä½¿å¾å¼åèå¯ä»¥é«åº¦èªå®ä¹è¡¨åæ ·å¼ãå¦ææå®äº `options.css`ï¼ä¼å¨ DOM ç head ä¸­æå¥ä¸ä¸ª `<style type="text/css"></style>` èç¹ã ç¤ºä¾ï¼

```jsx
const css = `
body {
    background: #6699 !important;
}
`
<AuthingGuard
  userPoolId={userPoolId}
  options={{
    css,
  }}
  onLogin={onLogin}
/>
```

ææå¦å¾æç¤ºï¼

<img height="500px" src="http://lcjim-img.oss-cn-beijing.aliyuncs.com/2019-12-06-100834.png" alt="" style="display:block;margin: 0 auto;"/> -->
