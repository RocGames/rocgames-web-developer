
> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
> 
> **SDK 接入请参照 [快速开始](/started/quickstart-ios.md) 或 [IOS登录](/core/login/access-ios.md) 页面**
>

# 接口定义

在
```objectivec
- (void)applicationDidBecomeActive:(UIApplication *)application

```
方法中调用上报激活事件

# 参数说明
| 参数      |  类型  | 说明   |
| :-------- | :----: | :------ |
| eventName | 字符串 | 事件名（埋点文档中对应的事件名，⚠️不能自定义） |
| dic  | 字符串 | 包含携带参数的对象，具体各个点需要携带的参数请参考埋点文档 |


# 示例代码
```objectivec
- (void)applicationDidBecomeActive:(UIApplication *)application {
    [ROCSdkManager activateApp];
}
	
```

## 其它自定义埋点上报
### 接口对象参数包含字段说明:

> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
> 
> **接口对象参数包含字段说明**
>

调用示例如下:

```objectivec
[ROCSdkManager azlEventName:⚠️#事件名#⚠️ 
					callbackParameter:nil];

[ROCSdkManager azlEventName:⚠️#事件名#⚠️ 
					callbackParameter:@{@"uid":@"xxx", 
														  @"serverid":@"xxx", 
														  @"playerid":@"xxx",
                  					  }];
```



