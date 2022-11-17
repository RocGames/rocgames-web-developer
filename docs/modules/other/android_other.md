# 其他的额外功能 #
######
##1.游戏内活动页##
####a.是否开启活动页####

    接口定义：
	public void SDKisOpenActive (Context context, UpdateInfo updateInfo, OpenActivityListener listener)

	 UpdateInfo 对象目前只需要传一个serverId参数 
	 String serverId  :服务器id
	
	 listener回调boolean ，true表示开启，false表示不开启

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
uid|String|	用户uid
serverId|String|服务器id
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