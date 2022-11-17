# Google应用内充值 #
    接口定义：
		public void SDKPay(Activity activity, SdkPayInfo sdkPayInfo,String paySource)

####1. 接口参数说明####
参数名|	类型|参数说明
 ---|----|----
activity|Activity|上下文实例
sdkPayInfo|	SdkPayInfo|	充值的信息对象
paySource|String|充值渠道，Google为“GP”

SdkPayInfo对象说明

参数名|	类型	|参数说明
 ---|----|----
productId|String|充值的商品id，与google后台配置的一致
serverId|String|充值的区服号
uid|String|	充值的用户uid
shopId|	String|	充值的内部商品id，自己游戏内部用的id
roleId|	String|	游戏内的角色id
level|	String|	角色等级
amount|	String|	充值的金额（货币单位：美金）
extra|	String|	额外的参数(可选，数据会原样返回给服务端)

####2. 调用示例代码####
```java
    public String PAYSOURCEID = "GP";//Google支付为GP
	SdkPayInfo sdkPayInfo = new SdkPayInfo();
        sdkPayInfo.productId = "diamonds0.99";
        sdkPayInfo.serverId = "1";
        sdkPayInfo.uid = "10000";
        sdkPayInfo.shopId = "301";
        sdkPayInfo.roleId = "123";
        sdkPayInfo.level = "5";
        sdkPayInfo.amount = "0.99";
		sdkPayInfo.extra="123";
        MyExternalInterface.getInstance().SDKPay(this, sdkPayInfo,PAYSOURCEID);
```
