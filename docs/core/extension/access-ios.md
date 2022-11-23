> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
>
> **SDK 接入请参照 [快速开始](/started/quickstart-ios.md) 或 [IOS登录](/core/login/access-ios.md) 页面**



# SDK额外功能接口

> - 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> - 功能接口可选择使用, 我们运营也可能会指定部分需求

---

## 1. 商店评分

> *调用时机我们运营定*

接口参数对象 **dic** 包含字段说明:

| 参数      |  类型  | 说明                         |
| :-------- | :----: | :------------------------- |
| uid       | 字符串 | 登陆成功时返回的UID            |
| serverid  | 字符串 | 游戏区服ID 没有就传字符串@"1"） |
| playerid  | 字符串 | 为游戏内角色ID          			|
| channelid | 字符串 | 固定传 @"AS"                 |

```objectivec
+ (void)azlStorePRoduct:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager azlStorePRoduct:@{@"uid":@"xxxx",
                                 @"serverid":@"xxxx",
                                 @"playerid":@"xxxx",
                                 @"channel":@"AS"}];
                                     
```

## 2. Yeeha官网跳转悬浮窗

> *通常进入到游戏后跳用*

接口参数对象 **dic** 包含字段说明:

| 参数  |  类型  | 说明                  |
| :----| :----: | :--------------------|
| link | 字符串  | 跳转地址  我们运营提供   |

```objectivec
+ (void)azlStorePRoduct:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager azlStorePRoduct:@{@"link":@"https://www.baidu.com"];

```

## 3. 内嵌web活动页
### 3.1 是否开启活动页

接口参数对象 **dic** 包含字段说明:

| 参数     |  类型  | 说明                         |
| :--------| :----: | :--------------------------|
| serverId | 字符串  |游戏区服ID 没有就传字符串@"1"   |

```objectivec
+ (BOOL)isShowAct:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
BOOL isShowAct = [ROCSdkManager isShowAct:@{@"serverId":@"xxx"}];
                                     
```

### 3.2 活动页展示

接口参数对象 **dic** 包含字段说明:

| 参数     |  类型  | 说明                         |
| :--------| :----: | :--------------------------|
| uid      | 字符串  |登陆成功时返回的UID           |
| roleId   | 字符串  |游戏角色ID                   |
| serverId | 字符串  |游戏区服ID 没有就传字符串@"1"   |
| channel  | 字符串  |固定传 @"AS"                 |

```objectivec
+ (void)showLinkActView:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager showLinkActView:@{@"uid":@"xxxx",
                                 @"serverid":@"xxxx",
                                 @"roleId":@"xxxx",
                                 @"channel":@"AS"}];
                                     
```

## 4. 绑定相关接口
### 4.1 邮箱绑定接口

> *绑定失败SDK已做处理*

回调参数说明:

| 参数     |  类型  | 说明                         |
| :--------| :----: | :--------------------------|
| type | 字符串  |0:界面关闭事件  1:绑定成功 |

```objectivec
+ (void)showEmailBindView:(nullable void (^)(int type))complete;
```

调用示例如下:

```objectivec
 [ROCSdkManager showEmailBindView:^(int type) {
        switch (type) {
            case 0:{
                NSLog(@"界面已关闭");
            }break;
            case 1:{
                NSLog(@"绑定成功");
            }break;
            default:break;
        }
    }];
                                     
```

### 4.2 Facebook绑定接口

> *绑定失败SDK已做处理*

接口定义:

```objectivec
+ (void)bindFacebook:(void (^)(void))success
              cancle:(nullable void (^)(void))cancle
               error:(nullable void (^)(void))error;
```

调用示例如下:

```objectivec
 [ROCSdkManager bindFacebook:^{
        NSLog(@"成功");
    } cancle:^{
        NSLog(@"取消");
    } error:^{
        NSLog(@"出错");
    }];                             
```

## 5. 多币种相关

> - 建议做多币种时使用该接口，以保证商店显示币种同拉起显示币种相同
> - 通常在初始化完成SDK之后 获取一次，以读取相应币种的档位表来做游戏内的商品价格显示

接口参数说明:

| 参数     |  类型  | 说明                      |
| :---------| :------: | :--------------------|
| productId | 字符串    |传入任意该app的苹果内购ID |
| block     | 回调函数   |-                     |

回调参数说明:

| 参数            |  类型     | 说明                |
| :--------------| :------: | :-------------------|
| currency       | 字符串    |币种     如:CNY、USD   |
| currencySymbol | 字符串    |货币符号  如:¥、$      |

```objectivec
+ (void)getCurrency:(NSString *)productId
              block:(nonnull void (^)(NSString *_Nonnull currency, NSString *_Nonnull currencySymbol))block;
```

调用示例如下:

```objectivec
[ROCSdkManager getCurrency:@"xxxxxx"
                     block:^(NSString * _Nonnull currency, NSString * _Nonnull currencySymbol) {
        
        NSLog(@"货币符号:%@  币种:%@",currencySymbol, currency);
}];
                                     
```

## 6. 内置web页

接口参数对象 **dic** 包含字段说明:

| 参数     |  类型  | 说明     |
| :--------| :----: | :------|
| link     | 字符串  | web链接 |

```objectivec
+ (void)showWebWindow:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager showWebWindow:@{@"link":@"https://www.baidu.com"}];
                                     
```
