# 官网储值
## 1. 储值说明
玩家在官网进行储值，根据游戏提供查询区服列表（ServerListUrl）和 角色信息地址（CheckUserUrl），获取角色信息发起三方支付。加密签名AppKey由平台提供，用于交互数据签名校验。

## 2. 区服列表
```
{
	"serverList": [{
		"serverId": 1,
		"serverName": "S1"
	}, {
		"serverId": 2,
		"serverName": "S2"
	}]
}
```
## 3. 查询角色参数说明
| 参数    | 类型 |是否参与签名 |     说明 |
| :--:    | :--:   | :--: | :-- |
| serverId| int    | 是   | 区服ID
| roleName| string | 是   | 角色名
| sign    | string | 否   | 加密串

## 3. 加密方式
示例代码:
```php
$sign  =  md5($serverId. $roleName . $AppKey);
```

## 4. 角色查询示例
```
CheckUserUrl?serverId=1&roleName=abc&sign=0a9f7072d945d2f1bad594406dbae8fb
```

## 5. 返回结果
查询成功code=1，查询失败code=0。
```
{
	"code": 1,
	"msg": "查询成功",
	"data": {
		"uid": 1000000,
		"roleId": "1000000000001"
	}
}
```