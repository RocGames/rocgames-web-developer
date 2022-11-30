# 登录
## 1. 登录说明
原生游戏对接Android、IOS的SDK获取用户信息进行校验并进入游戏。H5游戏需要提供游戏入口地址(LoginUrl)，平台拼接用户信息，游戏验证信息并进入游戏。加密签名AppKey由平台提供，用于交互数据签名校验。

## 2. 参数说明
| 参数    | 类型 |是否参与签名 |     说明 |
| :--:    | :--:   | :--: | :-- |
| uid     | int    | 是 | 用户id
| time    | int    | 是 | 登录时间戳
| channel | string | 是 | 登录渠道
| subId   | string | 是 | Yeeha平台子账号Id（唯一id）
| mainId  | string | 是 | Yeeha平台UID（可能为空）
| token   | string | 否 | Yeeha平台登录token
| sign    | string | 否 | 加密串

## 3. 加密方式
示例代码:
```php
$sign  =  md5($uid  . $time . $subId . $mainId . $AppKey);
```

## 4. H5游戏登录示例
```
LoginUrl?uid=1000000&time=1589339441&subId=998612205984587798&mainId=1000001&channel=GP&sign=0a9f7072d945d2f1bad594406dbae8fb
```