
> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
> 
> **SDK 接入请参照 [快速开始](/started/quickstart-ios.md) 或 [IOS登录](/core/login/access-ios.md) 页面**
> **具体埋点 请查看 [埋点文档](/core/daq/access-events-table.md) **

# 接口定义

## 1.1 应用激活事件上报
> * 请先初始化 SDK 可参考 [IOS登录](/core/login/access-ios.md) 
> * 在  - (void)applicationDidBecomeActive:(UIApplication *)application 方法中调用

示例代码:

```objectivec
- (void)applicationDidBecomeActive:(UIApplication *)application {
    [ROCSdkManager activateApp];
}
	
```

## 1.2 埋点事件上报
接口定义:
```objectivec
+ (void)azlEventName:(nonnull NSString *)eventName 
	 callbackParameter:(nullable NSDictionary *)dic;
```

接口对象参数包含字段说明:

| 参数      |  类型  | 说明   |
| :-------- | :----: | :------ |
| eventName | 字符串 | 事件名（埋点文档中对应的事件名，⚠️不能自定义） |
| dic  | 键值对对象 | 包含携带参数的对象，具体各个点需要携带的参数请参考埋点文档|

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



