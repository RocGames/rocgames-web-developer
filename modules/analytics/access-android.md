# 统计埋点 #
    接口定义：
		public void SDKAdjustPoints(Context context, String eventKey, Map<String, String> parMaps)

####1. 接口参数说明####
eventKey：埋点参数字段，具体的传值请看埋点文档                         
parMaps ：埋点所需传的参数集合，具体的传值请看埋点文档

<font color=red size=2>说明：eventKey 复制埋点文档的这列里的值</font>

 <img src="../images/Android_11.png" width = "380" height = "500" alt="Android_11" align=center />

<font color=red size=2>parMaps key值复制具体对应埋点需求的附加参数这列，value需要游戏传具体值</font>
 <img src="../images/Android_12.png" width = "460" height = "700" alt="Android_12" align=center />

####2. 示例代码####
```java
    例：进入游戏的埋点
		Map<String,String> params =new HashMap<>();
        params.put("uid","1000393");
        params.put("serverid","1");
        params.put("playerid","d476b70c-961d-47cc-a62c-983b1a4ae2c0");
        MyExternalInterface.getInstance().SDKAdjustPoints(this,"click_entry_game",params);
	
```