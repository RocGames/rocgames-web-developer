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
### 2.1 悬浮窗展示接口

> *通常进入到游戏后调用*

接口参数对象 **dic** 包含字段说明:

| 参数  |  类型  | 说明                  |
| :----| :----: | :--------------------|
| link | 字符串  | 跳转地址  我们运营提供   |

```objectivec
+ (void)showFloatingView:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager showFloatingView:@{@"link":@"https://www.baidu.com"];

```

### 2.2 玩家游戏数据交互接口

> *通常进入到游戏后调用*

接口参数对象 **dic** 包含字段说明:

| 参数       |  类型    | 说明                               |
| :----------| :----: | :----------------------------------|
| uid        | 字符串  | 登陆成功时返回的UID                   |
| playerid   | 字符串  | 游戏角色ID                           |
| playerName | 字符串  | 游戏角色名  (没有就传空符串@""）        |
| pay_total  | 字符串  | 玩家累充金额 (未充值传@"0") (⚠️传 美金) |
| serverid   | 字符串  | 游戏区服ID  (没有就传字符串@"1"        |
| level      | 字符串  | 游戏角色等级 (没有就传空符串@""）       |

```objectivec
+ (void)updatePlayerInfo:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager updatePlayerInfo:@{@"uid":@"001",
                                  @"playerid":@"1000000",
                                  @"playerName":@"龙傲天",
                                  @"pay_total":@"6.99",
                                  @"serverid":@"1",
                                  @"level":@"18",
                                  }];

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
| currency       | 字符串    |币种     如:CNY、USD、TWD   |
| currencySymbol | 字符串    |货币符号  如:¥、$、NT$       |

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

| 参数  | 类型  | 说明    |
| :----| :---: | :------|
| link | 字符串 | web链接 |

```objectivec
+ (void)showWebWindow:(NSDictionary *)dic;
```

调用示例如下:

```objectivec
[ROCSdkManager showWebWindow:@{@"link":@"https://www.baidu.com"}];
                                     
```
## 7. 拍脸图游戏端参数获取

> - 可以传多组数据对应多张脸图
> - 图片大小要统一 目前是1500x800
> - 可以跳转的图片上的按钮不要求摆放的位置，点击整张图片等于点击了按钮 
> - 表现效果 比如有2张: A先弹出来 点了右上角的× A关闭，B弹出来 点了右上角的× B关闭，整个拍脸系统关闭 （图片需要下载 在未显示的时候会有一个底图显示 写着 【稍等正在加载】）

接口返回数组中元素对象 **dic** 包含字段说明:

> *jumpJudge字段  =0时，填入一级界面名称需要和策划商量，不能填二级三级界面名称或者某个单独按钮点击后的界面*
> 
>  *jumpPath字段  空字符串代表点击图片没反应不跳转任何界面*

| 返回参数        | 类型  |必要参数 | 说明                        				|
| :----          | :---: | :-: | :-----------------								 |
| faceDrawingId | 字符串 | 是  | 脸图id          						 					|
| order         | 字符串 | 是  | 脸图顺序                      				|
| path          | 字符串 | 是  | 图片链接（需要展示在界面上的图片）				|
| jumpJudge     | 字符串 | 是  | 跳转判断 0=游戏界面 1=网址	|
| jumpPath      | 字符串 | 是  | 跳转路径 （可为空字符串）				|
| startTime     | 字符串 | 否  | 开始时间					|
| endTime       | 字符串 | 否  | 结束时间					|
| levelUpLimit  | 字符串 | 否  | 等级上限					|
| levelDownLimit| 字符串 | 否  | 等级下限					|
| chargeUpLimit | 字符串 | 否  | 充值额度上限			 |
| chargeDownLimit| 字符串| 否  | 充值额度下限			 |
| platformId    | 字符串 | 否  | 平台 0=iOS  1=安卓		|
| serverId      | 字符串 | 否  | 区服Id 如:20001			  |


```objectivec
+ (NSArray *)getFaceDrawingInfo;
```

调用示例如下:

```objectivec
NSArray *arr = [ROCSdkManager getFaceDrawingInfo];
NSDictionary *dic = arr[0];
                                     
```