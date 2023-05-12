> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
> 
> **SDK 接入请参照 [快速开始](/started/quickstart-ios.md) 或 [IOS登录](/core/login/access-ios.md) 页面**

# iOS 支付
- apple内购支付

---

## 1. 支付拉起
> * 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> * SDK已做订单单比化(一单结束才能进行下一单)，无需再做遮罩层。
> * 已做客户端自动补单功能，掉单后且没有提示发货相关的错误提示时(如:发货失败、重复的订单等)，可重启应用进行自动补单。

接口对象包含字段说明:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| productId | 字符串 | 传苹果内购ID |
| serverid | 字符串 | 游戏区服ID 没有就传字符串@"1"） |
| amount | 字符串 | 订单金额  (⚠️传 美金) |
| uid | 字符串 | 登陆成功时返回的UID |
| shopid | 字符串 | 游戏方自己的商品ID |
| roleid | 字符串 | 游戏角色ID |
| extra | 字符串 | 透传参数，会原样返回给你们（没有就传字符串@""） |

调用示例如下:

```objectivec
[ROCSdkManager pay:@{@"productId":@"com.game.brast.iap.tier4",
                     @"serverid":@"1299999",
                     @"amount":@"3.99",
                     @"uid":@"1000090",
                     @"shopid":@"104",
                     @"roleid":@"1000025",
                     @"extra":@"ff2e71064fde4f588c127f215df0aabb",
                     }];
```

