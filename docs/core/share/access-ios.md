> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
>
> **SDK 接入请参照 [快速开始](/started/quickstart-ios.md) 或 [IOS登录](/core/login/access-ios.md) 页面**



# iOS分享
- facebook分享

---

## 1. 图片分享

> - 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> - 照片大小必须小于 12MB
> -  用户需要安装版本 7.0 或以上的原生 iOS 版 Facebook 应用

接口对象包含字段说明:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| img | 字符串 | 分享的图片 |
| dic | NSDictionary | 需要携带的额外参数对象 |
| block | 分享回调 | 0:分享成功  1:分享失败  2:分享取消  3:未安装FBAPP |

**dic**对象参数所包含的字段:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| uid | 字符串 | 登陆成功时返回的UID |
| serverid | 字符串 | 服务器ID 没有传@"1"|
| playerid | 字符串 | 为游戏内角色ID |
| channelid | 字符串 | 为游戏内角色ID iOS:@"AS",安卓:@"GP"|
| share_id | 分享回调 | 分享ID  用于区分是哪个位置的分享 |

```objectivec
+ (void)shareImage:(UIImage *)img
      analyticsDic:(NSDictionary *)dic
     callBackBlcok:(void (^)(NSString *))block;
```

调用示例: 

```objectivec
[ROCSdkManager shareImage:image
             analyticsDic:@{@"uid":@"xxxx",
                            @"serverid":@"xxxxx",
                            @"playerid":@"xxxxx",
                            @"share_id":@"xxxxx"}
            callBackBlcok:^(NSString * _Nonnull type) {
                        switch ([type intValue]) {
                            case 0:{
                                NSLog(@"分享成功");
                            }break;
                            case 1:{
                                NSLog(@"分享失败");
                            }break;
                            case 2:{
                                NSLog(@"分享取消");
                            }break;
                            case 3:{
                                NSLog(@"未安装FBAPP");
                            }break;
                            default:break;
                        }
    }];
```
## 2. 链接分享

> - 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> - 链接格式如: *https://www.baidu.com*

接口对象包含字段说明:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| link | 字符串 | 要分享的链接 |
| dsp | 字符串 | 分享内容描述 |
| dic | NSDictionary | 需要携带的额外参数对象 |
| block | 分享回调 | 0:分享成功  1:分享失败  2:分享取消  3:未安装FBAPP |

**dic**对象参数所包含的字段:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| uid | 字符串 | 登陆成功时返回的UID |
| serverid | 字符串 | 服务器ID 没有传@"1"|
| playerid | 字符串 | 为游戏内角色ID |
| channelid | 字符串 | 为游戏内角色ID iOS:@"AS",安卓:@"GP"|
| share_id | 分享回调 | 分享ID  用于区分是哪个位置的分享 |

```objectivec
+ (void)shareLink:(NSString *)link
              dsp:(NSString *)dsp
     analyticsDic:(NSDictionary *)dic
    callBackBlcok:(void (^)(NSString *))block
    
```

调用示例:

```objectivec
[ROCSdkManager shareLink:@"https://developers.facebook.com"
                     dsp:@"测测测"
            analyticsDic:@{@"uid":@"xxxx",
                           @"serverid":@"xxxx",
                           @"playerid":@"xxxx",
                           @"share_id":@"xxxx"}
           callBackBlcok:^(NSString * _Nonnull type) {
                    switch ([type intValue]) {
                        case 0:{
                            NSLog(@"分享成功");
                        }break;
                        case 1:{
                            NSLog(@"分享失败");
                        }break;
                        case 2:{
                            NSLog(@"分享取消");
                        }break;
                        case 3:{
                            NSLog(@"未安装FBAPP");
                        }break;
                        default:break;
                    }
                }];
```

## 3. 视频分享

> - 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> - 分享内容的用户应安装版本 26.0 或以上的 iOS 版 Facebook 客户端
> - 视频大小必须小于 50MB

接口对象包含字段说明:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| videoAsset | PHAsset | 照片库中的视频的相位集 |
| videoUrl | NSURL | 照片库中的视频的相位集 |
| previewImg | 分享回调 | 视频预览图 |
| dic | NSDictionary | 需要携带的额外参数对象 |
| block | 分享回调 | 0:分享成功  1:分享失败  2:分享取消  3:未安装FBAPP |

**dic**对象参数所包含的字段:

| 参数   | 类型 |     说明 |
| :-- | :---: | :-- |
| uid | 字符串 | 登陆成功时返回的UID |
| serverid | 字符串 | 服务器ID 没有传@"1"|
| playerid | 字符串 | 为游戏内角色ID |
| channelid | 字符串 | 为游戏内角色ID iOS:@"AS",安卓:@"GP"|
| share_id | 分享回调 | 分享ID  用于区分是哪个位置的分享 |

```objectivec
+ (void)shareVideo:(nonnull PHAsset *)videoAsset
      previewPhoto:(nullable UIImage *)previewImg
      analyticsDic:(NSDictionary *)dic
     callBackBlcok:(void (^)(NSString *))block;

//或

+ (void)shareVideoUrl:(nonnull NSURL *)videoUrl
         previewPhoto:(nullable UIImage *)previewImg
         analyticsDic:(NSDictionary *)dic
        callBackBlcok:(void (^)(NSString *))block;
        
```

调用示例:

```objectivec
[ROCSdkManager shareVideoUrl:videoAssetURL
                previewPhoto:image
                analyticsDic:@{@"uid":@"xxxx",
                               @"serverid":@"xxxx",
                               @"playerid":@"xxxx",
                               @"share_id":@"xxxx"}
               callBackBlcok:^(NSString * _Nonnull type) {
                   
                   switch ([type intValue]) {
                       case 0:{
                           NSLog(@"分享成功");
                       }break;
                       case 1:{
                           NSLog(@"分享失败");
                       }break;
                       case 2:{
                           NSLog(@"分享取消");
                       }break;
                       case 3:{
                           NSLog(@"未安装FBAPP");
                       }break;
                       default:break;
                   }
               }];

```
