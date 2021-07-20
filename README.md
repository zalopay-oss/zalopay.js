# zalopay v1.0.4

[ZaloPay](https://zalopay.vn) - Pay in 2 seconds

## Install

In a browser:
```html
<script src="zalopay.min.js"></script>
```

## Example

(boolean) isZaloPay
```js
if(ZaloPay.isZaloPay) {
    //TODO
}
```

(function) showLoading<br />
(function) hideLoading
```js
ZaloPay.showLoading();
setTimeout(
    function() { ZaloPay.hideLoading(); },
    3000
);
```

(function) showDialog
```js
ZaloPay.showDialog({
    title: "ZaloPay",
    message: "ZaloPay showDialog",
    button: "OK"
});
```

(function) showToast
```js
ZaloPay.showToast({
    message: "ZaloPay showToast"
});
```

(function) showTooltip
```js
ZaloPay.showTooltip({
    message: "ZaloPay showTooltip",
    iconName: "history_ticket",
    iconLink: "https://images.pexels.com/photos/67636/rose-blue-flower-rose-blooms-67636.jpeg",
    position: 0
});
```

(function) pushView
```js
ZaloPay.pushView({
    url: "https://zalopay.vn/"
});
```

(function) share<br />
{type} int[1: screenshot | 2: message]
```js
ZaloPay.share({
    type: 1,
    caption: "caption string",
    content: "content string"
});
```

(function) closeWindow
```js
ZaloPay.closeWindow();
```

(function) transferMoney
```js
ZaloPay.transferMoney({
    zpid: "cuongbm2",
    amount: 20000,
    message: "Transaction_171231_1"
}, callback);
function callback(data) {
    if(typeof data === "object") {
        if(data.error === 1) {
            alert("Zalo Pay Callback: transferMoney Successed");
        } else if(data.error === 4) {
            alert("Zalo Pay Callback: User Canceled");
        } else {
            alert("Zalo Pay Callback: transferMoney Failed with code " + data.errorCode);
        }
    }
}
```

(function) payOrder with full order information
```js
ZaloPay.payOrder({
    appid: 3,
    appuser: "pmqc",
    apptime: 1486713401300,
    amount: 20000,
    apptransid: 170210144922653,
    embeddata: "embeddata123",
    item: "item123",
    description: "description123",
    mac: "5815251181fcf7d80d056ec8298f81dcc1654eb9edb3c19a961ef43eb129c307"
}, cb);
```

(function) payOrder with minify order information
```js
ZaloPay.payOrder({
    appid: 3,
    zptranstoken: "gOAWGD_NK4DFoq0mTA0iTw"
}, cb);
```

(function) promotionEvent: open another apps
```js
ZaloPay.promotionEvent({
    campaignId: 1,
    url: "zalo://launch?params=1",
    packageId: "com.zing.zalo",
    alternateUrl: "https://vng.com.vn"
    deeplinks: (optional) "{deeplinksURL}"
}, callback);
function callback(data) {
    if(typeof data === "object") {
        if(data.code === 1) {
            console.log("Success");
        } else if(data.code === 0 || data.code === -1) {
            console.log("Not exist app");
        } else {
            console.log("Unknown exception");
        }
    }
}
```

(function) promotionEvent: open Zalo Pay apps
```js

ZaloPay.promotionEvent({
    campaignId: 1,
    internalApp: 12,
    alternateUrl: "https://vng.com.vn",
    deeplinks: (optional) "{deeplinksURL}"
}, callback);
function callback(data) {
    if(typeof data === "object") {
        if(data.code === 1) {
            console.log("Success");
        } else if(data.code === 0 || data.code === -1) {
            console.log("Not exist app");
        } else {
            console.log("Unknown exception");
        }
    }
}
```

(function) setProperty: set color and background color for navigator
```js
ZaloPay.setProperty({
    navigation: {
        backgroundColor: "#c7c7cc", titleColor: "#000000"
    }
});
```

(function) setToolbarActions: set icon action in navigator
```js
ZaloPay.setToolbarActions([
    { iconId: "clickIcon1", iconName: "personal_settingaccount", iconColor: "#000000" },
    { iconId: "clickIcon2", iconLink: "https://cdn0.iconfinder.com/data/icons/entypo/92/button2-48.png" }
], navigatorAction);
function navigatorAction(type) {
    alert(JSON.stringify(type));
}
```

(function) getUserInfo: get user info of ZaloPay
```js
ZaloPay.getUserInfo(
    appid, callbackGetUserInfo
);
function callbackGetUserInfo(data) {
    if(typeof data === "object") {
        if(data.error === 1) {
            alert("Success UserInfo: " + JSON.stringify(data.data));
        } else {
            alert("Unknown exception" + JSON.stringify(data.data));
        }
    }
}
```

(function) isSSOSupported: check if SSO is supported

```javascript
if (ZaloPay.isSSOSupported("app-id")) {
    // Trigger OAuth2/SSO flow
} else {
    // Go with old flow
}
```