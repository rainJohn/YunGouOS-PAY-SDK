# YunGouOS-PAY-SDK

![https://yungouos.oss-cn-shanghai.aliyuncs.com/YunGouOS/logo/merchant/logo.png](https://yungouos.oss-cn-shanghai.aliyuncs.com/YunGouOS/logo/merchant/logo.png)


# 介绍

YunGouOS微信支付/支付宝官方合作伙伴，YunGouOS-PAY是徐州市云宝网络科技有限公司研发的支付产品。

过去我们只将支付提供给自身系统使用，我们对市面上各种第四方支付深感痛恨 我们深知一些个人用户对支付的渴望。

为此，我们开放了重量级产品，YunGouOS旗下“支付系统”正式对外开放。

我们使命是为更多开发者、个体户、个人创业者、小微企业提供正规的官方支付接口。

基于微信/支付宝官方授权的服务商模式为中小商家提供便捷的支付接入服务。


# 如何使用

在官网提交资料，由微信/支付宝审核，审核通过后下发商户号，对接使用。

# 相关地址

官网地址：[https://www.yungouos.com](https://www.yungouos.com "https://www.yungouos.com")

接口文档：[https://open.pay.yungouos.com](https://open.pay.yungouos.com "https://open.pay.yungouos.com")

# 快速上手

## 前言

所有方法均提供了同步和异步两种调用方式，支持Promise化使用

下面以微信扫码支付举例

```js
//同步
WxPay.nativePayAsync

//异步（将方法名结尾的Async去掉即为异步，返回的是Promise对象，按照Promise语法进行后续处理即可）
WxPay.nativePay

```

## 一、安装

### 方式一：NPM安装（推荐）

1、项目根目录命令行执行

```sh
npm i yungouos-pay-sdk
```

2、项目中引入

```js
import {WxPay,AliPay} from 'yungouos-pay-sdk'
```

## 二、使用

### 1、微信支付

#### 扫码支付（同步）

```js
let result = WxPay.nativePayAsync(out_trade_no, total_fee, mch_id, body, type, attach, notify_url, auto, auto_node, config_no, payKey);
//二维码链接地址
console.log(result);
```

#### 扫码支付（异步）

```js
WxPay.nativePay(out_trade_no, total_fee, mch_id, body, type, attach, notify_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 刷卡支付（同步）

```js
let result = WxPay.codePayAsync(out_trade_no, total_fee, mch_id, body, auth_code, attach,receipt,notify_url, auto, auto_node, config_no, payKey);
```

#### 刷卡支付（异步）

```js
WxPay.codePay(out_trade_no, total_fee, mch_id, body, auth_code, attach,receipt,notify_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 公众号支付/JSAPI（同步）

```js
let result = WxPay.jsapiPayAsync(out_trade_no, total_fee, mch_id, body, openId, attach, notify_url, auto, auto_node, config_no, payKey);
```

#### 公众号支付/JSAPI（异步）

```js
WxPay.jsapiPay(out_trade_no, total_fee, mch_id, body, openId, attach, notify_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 收银台支付（同步）

```js
let result = WxPay.cashierPayAsync(out_trade_no, total_fee, mch_id, body, attach, notify_url, return_url, auto, auto_node, config_no, payKey);
```

#### 收银台支付（异步）

```js
WxPay.cashierPay(out_trade_no, total_fee, mch_id, body, attach, notify_url, return_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 刷脸支付（同步）

```js
let result = WxPay.facePayAsync(out_trade_no, total_fee, mch_id, body, openId, face_code, attach, notify_url, auto, auto_node, config_no, payKey);
```

#### 刷脸支付（异步）

```js
WxPay.facePay(out_trade_no, total_fee, mch_id, body, openId, face_code, attach, notify_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### H5支付（同步）

```js
let result = WxPay.wapPayAsync(out_trade_no, total_fee, mch_id, body, attach, notify_url, return_url, auto, auto_node, config_no, payKey);
```

#### H5支付（异步）

```js
WxPay.wapPay(out_trade_no, total_fee, mch_id, body, attach, notify_url, return_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### APP支付（同步）

```js
let result = WxPay.appPayAsync(app_id, out_trade_no, total_fee, mch_id, body, attach, notify_url, auto, auto_node, config_no, payKey);
```

#### APP支付（异步）

```js
WxPay.appPay(app_id, out_trade_no, total_fee, mch_id, body, attach, notify_url, auto, auto_node, config_no, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 订单退款（同步）

```js
let result = WxPay.refundAsync(out_trade_no, mch_id, money, refund_desc, payKey);
```

#### 订单退款（异步）

```js
WxPay.refund(out_trade_no, mch_id, money, refund_desc, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 查询退款结果（同步）

```js
let result = WxPay.getRefundResultAsync(refund_no, mch_id, payKey);
```

#### 查询退款结果（异步）

```js
WxPay.getRefundResult(refund_no, mch_id, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### 下载对账单（同步）

```js
let result = WxPay.downloadBillAsync(refund_no, mch_id, payKey);
```

#### 下载对账单（异步）

```js
WxPay.downloadBill(refund_no, mch_id, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

### 2、支付宝

#### 扫码支付（同步）

```js
let result = AliPay.nativePayAsync(out_trade_no, total_fee, mch_id, body, type, attach, notify_url, payKey);
//二维码链接地址
console.log(result);
```

#### 扫码支付（异步）

```js
AliPay.nativePay(out_trade_no, total_fee, mch_id, body, type, attach, notify_url, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```

#### wap支付（同步）

```js
let result = AliPay.wapPayAsync(out_trade_no, total_fee, mch_id, body, attach, notify_url, payKey);
//wap支付链接地址
console.log(result);
```

#### wap支付（异步）

```js
AliPay.wapPay(out_trade_no, total_fee, mch_id, body, attach, notify_url, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```


#### 发起退款（同步）

```js
let result = AliPay.refundAsync(out_trade_no, mch_id, money, refund_desc, payKey);
//发起退款结果
console.log(result);
```

#### 发起退款（异步）

```js
AliPay.refund(out_trade_no, mch_id, money, refund_desc, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```


#### 查询退款结果（同步）

```js
let result = AliPay.getRefundResultAsync(out_trade_no, mch_id, money, refund_desc, payKey);
//查询退款结果
console.log(result);
```

#### 查询退款结果（异步）

```js
AliPay.getRefundResult(out_trade_no, mch_id, money, refund_desc, payKey).then((response)=>{
    //接口返回结果
    console.log(response);
});
```