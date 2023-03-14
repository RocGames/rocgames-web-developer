
> [!TIP|iconVisibility:hidden|labelVisibility:hidden]
> 
> **SDK 接入请参照 [快速开始](/started/quickstart-and.md) 或 [Android登录](/core/login/access-and.md) 页面**
>


# 接口定义
```java
    public void SDKAdjustPoints(Context context, String eventKey, Map<String, String> parMaps)
```

# 参数说明
| 参数      |  类型  | 说明   |
| :-------- | :----: | :------ |
| eventKey | 字符串 | 埋点参数字段，具体的传值请看埋点文档的事件名 |
| parMaps  | 字符串 | 埋点所需传的参数集合，具体的传值请看埋点文档携带参数 |

> [!WARNING|label:注意|iconVisibility:hidden]
> 
> **eventKey 复制埋点文档的事件名值**
>

> [!WARNING|label:注意|iconVisibility:hidden]
> 
> **parMaps key值复制具体对应埋点需求的携带参数，value需要游戏传具体值**
>

# 示例代码
```java
    // 进入游戏的埋点
    Map<String,String> params =new HashMap<>();
    params.put("uid","1000393");
    params.put("serverid","1");
    params.put("playerid","d476b70c-961d-47cc-a62c-983b1a4ae2c0");
    MyExternalInterface.getInstance().SDKAdjustPoints(this,"entry_game",params);
	
```