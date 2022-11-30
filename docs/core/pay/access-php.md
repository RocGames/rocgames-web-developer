# 游戏充值
## 1. 充值说明
玩家在游戏内发起购买商品操作时，当支付完毕，平台服务端会调用游戏方提供的充值回调地址（PaymentUrl）进行通知物品发放，请游戏方确保该笔订单只成功发放一次。

## 2. 参数说明
| 参数    | 类型 |是否参与签名 |     说明 |
| :--:    | :--:   | :--: | :-- |
| uid     | int    | 是   | 用户id
| price   | string | 是   | 充值金额
| serverId| int    | 是   | 区服ID
| roleId  | string | 是   | 角色ID
| shopId  | int    | 是   | 商品ID
| orderId | string | 是   | 订单号
| channel | string | 是   | 登录渠道
| payTime | int    | 是   | 付款时间戳
| extra   | string | 是   | 透传参数（可为空）
| sign    | string | 否   | 加密串

## 3. 加密方式
示例代码:
```php
$sign = md5($uid . $price . $serverId . $roleId . $shopId . $orderId . $channel . $payTime . $extra . $AppKey);
```
## 4. 游戏物品发放示例
```
PaymentUrl?uid=1000000&price=0.99&serverId=1&roleId=1000000000001&shopId=100&orderId=gp100000000000000000&channel=GP&payTime=1589339441&extra=100000000000&sign=0a9f7072d945d2f1bad594406dbae8fb
```
## 5. 返回结果
发货成功code=1，发货失败code=0。
```
{
	"code": 1,
	"msg": "发货成功|重复发货"
}
```