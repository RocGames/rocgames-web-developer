# SDK的额外功能接口 #
######
##1.游戏内活动页##
####a.是否开启活动页####

    接口定义：
	public void SDKisOpenActive (Context context, UpdateInfo updateInfo, OpenActivityListener listener)

	 	UpdateInfo 对象目前只需要传一个serverId参数 

| 参数     |  类型  | 说明                         |
| :--------| :----: | :--------------------------|
| serverId | String  |游戏区服ID 没有就传字符串@"1"   |
|listener|boolean|true表示开启，false表示不开启|
####b.示例代码####
```java
	UpdateInfo updateInfo = new UpdateInfo();
        updateInfo.serverId = "19012";
        MyExternalInterface.getInstance().SDKisOpenActive(MainActivity.this, updateInfo, new OpenActivityListener() {
            @Override
            public void onSuccess(boolean msg) {
                boolean isOpen = msg;
                BaseSDKUtils.logD(TAG, "isOpen==" + isOpen);
            }
        });
```

##2.调用活动页##
    接口定义：
	public void SDKWebPay (Activity activity,UpdateInfo updateInfo)

UpdateInfo对象说明

参数名|	类型|参数说明
 ---|----|----
uid|String|	登陆成功时返回的UID
serverId|String|游戏区服ID 没有就传字符串"1" 
roleId|	String|	游戏内的角色id
actionType|	String|	活动页类型

####a.示例代码####
```java
    UpdateInfo updataInfo = new UpdateInfo();
        updataInfo.uid = "1000393";
        updataInfo.serverId = "1";
        updataInfo.roleId = "5715379823933652993";
        updataInfo.actionType = "1";
		MyExternalInterface.getInstance().SDKWebPay(this,updataInfo);
```
##2.应用内评论##
    a.接口定义：Google评论对象初始化

		public void SDKPreRate(Context context, SDKInterfaceInitListener listener)

   			listener：Google评论对象初始化回调,成功之后再调用评论方法

    b.接口定义：调用评论 

   		public void SDKGoogleRate(Activity activity, Map<String, String> parMaps) 

   			parMaps：埋点数据集合

| 参数      |  类型  | 说明                         |
| :-------- | :----: | :------------------------- |
| uid       | String | 登陆成功时返回的UID            |
| serverid  | String | 游戏区服ID 没有就传字符串"1" |
| playerid  | String | 游戏内角色ID          			|
####a.示例代码####
```java
    MyExternalInterface.getInstance().SDKPreRate(this, new SDKInterfaceInitListener() {
            @Override
            public void initSuccess(String result) {
                Log.d(TAG, "SDKPreRate===" + result);
                toGoogleRate();
            }
            @Override
            public void initFail(String result) {
                Log.d(TAG, "SDKPreRate=" + result);
            }
        });	
	public void toGoogleRate() {
        Map<String, String> params = new HashMap<>();
        params.put("uid","1000393");
        params.put("serverid","1");
        params.put("playerid","d476b70c-961d-47cc-a62c-983b1a4ae2c0");
        MyExternalInterface.getInstance().SDKGoogleRate(this, params);
```
##3.悬浮窗功能##
> *通常进入到游戏后调用*

###1.开启悬浮窗###
	
	public void SDKShowFloat(Activity activity, WebInfo webInfo, SDKFloatListener listener)
		webInfo ：链接对象，目前只有link，表示要跳转的链接
		listener：点击了客服按钮

| 参数  |  类型  | 说明                  |
| :----| :----: | :--------------------|
| link | String  | 跳转地址  我们运营提供   |

####a.示例代码####
```java
    WebInfo webInfo=new WebInfo();
	webInfo.link="https://yeehagames.com/";
        MyExternalInterface.getInstance().SDKShowFloat(MainActivity.this,webInfo,new SDKFloatListener() {
        @Override
             public void onClick() {
                ToastUtils.showToast(MainActivity.this,"点击了客服logo");
                    }
                });
	}
```

###2.玩家游戏数据交互接口###
> *通常进入到游戏后调用*

	 public void SDKAIHelperUpData(Context context,String userJson) 

接口参数Json串 userJson 字段说明:

| 参数       |  类型    | 说明                               |
| :----------| :----: | :----------------------------------|
| uid        | String  | 登陆成功时返回的UID                   |
| playerid   | String  | 游戏角色ID                           |
| playerName | String  | 游戏角色名  (没有就传空符串@""）        |
| pay_total  | String  | 玩家累充金额 (未充值传@"0") (⚠️传 美金) |
| serverid   | String  | 游戏区服ID  (没有就传字符串@"1"        |
| level      | String  | 游戏角色等级 (没有就传空符串@""）       |

####a.示例代码####
```java
MyExternalInterface.getInstance().SDKAIHelperUpData(MainActivity.this,userJson);
```

###3.关闭悬浮窗###

    public void SDKFloatClose(Activity activity, WebInfo webInfo)
		webInfo ：链接对象，可传null

####a.示例代码####
	MyExternalInterface.getInstance().SDKFloatClose(MainActivity.this,null);

##4.获取手机系统语言##
    接口定义：
	 String SDKCurrentLanguage ()
 		默认返回 英文”en”
####a.示例代码####
    String lan=  MyExternalInterface.getInstance().SDKCurrentLanguage();

##5.账户绑定##
    接口定义：
	public void SDKBindEmail (Activity activity, BaseListener listener)
		listener :回调
		onSuccess(0, "success")
		onFail(1, "fail")
	目前不管回调什么都继续走游戏自己的逻辑
####a.示例代码####
```java
    MyExternalInterface.getInstance().SDKBindEmail(this, new BaseListener() {
            @Override
            public void onSuccess(int code, String msg) {
                Log.d(TAG, "msg==" + msg);
            }
            @Override
            public void onFail(int code, String msg) {
                Log.d(TAG, "msg==" + msg);
            }
        });
	}
```

##6.获取货币国家##
    接口定义：
	public void SDKgetCountryCode(String sku, SDKInterfacePayListener listener)
		sku：Google后台的商品id
		listener :成功回调会返回countryCode：国家币种  currencySymbol：币种符号
	    失败会返回默认的币种”USD”,符号 "$"
####a.示例代码####
```java
    MyExternalInterface.getInstance().SDKgetCountryCode("Google商品id", new SDKInterfacePayListener() {
                        @Override
                        public void onSuccess(String currencyCode,String currencySymbol) {
                            Log.d(TAG, "currencyCode=" + currencyCode + "   currencySymbol====" + currencySymbol);
                        }
                        @Override
                        public void onFail(String currencyCode,String currencySymbol) {
                            Log.d(TAG, "currencyCode=" + currencyCode + "   currencySymbol====" + currencySymbol);
                        }
                    });	
		}			
```

