# zalopay v1.0.0

[ZaloPay](https://zalopay.com.vn) - Thanh toán trong 2 giây

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
