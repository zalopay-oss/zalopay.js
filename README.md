# zalopay v1.0.1

[ZaloPay](https://zalopay.com.vn) - Pay in 2 seconds

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
    packageId: "com.zing.zalo"
});
```

(function) promotionEvent: open Zalo Pay apps
```js
ZaloPay.promotionEvent({
    campaignId: 1,
    internalApp: 12
});
```