# 集成SDK功能 #

    MyExternalInterface.getInstance().isStartLog(true);//TAG: mySDK

<font color=red size=2>在启动activity里oncreate加上,可以开启日志调试，正式上线包需要改成false</font>

## 1.在自己的Application onCreate里调用 ##

    MyExternalInterface.getInstance().APPInit(Application application,boolean isProduction);
     
    参数：isProduction：传入运行的环境
     	  true 表示正式环境 production 
    	  false 表示测试环境sandbox 

<font color=red size=2>注意：正式上线包一定要把环境改成true</font>

## 2. 初始化SDK ##

    接口定义：
    public void SDKInit(Activity activity,String gameId,String appkey,String channelId,SDKInterfaceInitListener initListener)
####1. 接口参数说明####

参数名|类型|参数说明
 ---|----|----
activity|Activity|上下文实例
gameId|	String|	游戏ID|
appkey|	String|	游戏加密密钥
channelId|String|渠道 ID，目前固定为“GP”
initListener|SDKInterfaceInitListener|	初始化回调接口
####2. 调用示例代码####
```java
    MyExternalInterface.getInstance().SDKInit(MainActivity.this, GAMEID, SIGN_KEY, CHANNELID, new SDKInterfaceInitListener() {
            @Override
            public void initSuccess(String result) {
                Log.d(TAG, "SDKInitsuccese-result====" + result);
                if(result.equals("true")){
                    //同意了协议直接登录
                    login();
                }else{
                    //没有同意协议调用协议界面
                    MyExternalInterface.getInstance().SDKProtocol(MainActivity.this, new BaseListener() {
                        @Override
                        public void onSuccess(int code, String msg) {
                            //同意协议
                            login();
                        }
                        @Override
                        public void onFail(int code, String msg) {
                            Log.d(TAG,"不同意协议 code="+code);
                        }
                    });
                }
            }
            @Override
            public void initFail(String result) {
                Log.d(TAG, "SDKInitfail-result====" + result);
            }
        });
```
## 3. 登录 ##
    接口定义：
    	public void SDKLogin(Activity activity,SDKLoginListener listener)

####1. 接口参数说明####
参数名|类型|参数说明
 ---|----|----
activity|Activity|上下文实例
listener|SDKLoginListener|登录的回调

####2. 接口回调说明####
    登录成功回调 
	public void onSuccess(int code, SdkLogincallBack sdkLogincallBack)
sdkLogincallBack中会得到登录验证时所需要的参数

参数名|类型|参数说明
 ---|----|----
gameSign|	string|	登录成功后，得到的加密字符串
loginTime|	string|	用户登录的时间
uid	|String| 用户的uid（⚠️请用该ID和游戏数据做关联对应） 
subId|	String| Yeeha平台子账号subId 
mainId|	String	|Yeeha平台id（可能为空）
token|	string|	主平台token
username|	String|	用户名
loginWay|	String|	登录的方式 1:游客登录   2:Fb登录 3:账号密码登录 4:Twitter登陆 5：自动登录 6：Google登录
fbBind|	String|	0表示没有绑定，1表示绑定了
twitterBind|	String|	0表示没有绑定，1表示绑定了

####3. 调用示例代码####
```java
     MyExternalInterface.getInstance().SDKLogin(MainActivity.this, new SDKLoginListener() {
            @Override
            public void onSuccess(int code, SdkLogincallBack sdkLogincallBack) {
                String gameSign = sdkLogincallBack.gameSign;
                String loginTime = sdkLogincallBack.loginTime;
                String uid = sdkLogincallBack.uid;
                String username = sdkLogincallBack.username;
                String loginWay = sdkLogincallBack.loginWay;
                String fbBind = sdkLogincallBack.fbBind;
                String twitterBind = sdkLogincallBack.twitterBind;
                String subId = sdkLogincallBack.subId;
                String mainId = sdkLogincallBack.mainId;
                String token = sdkLogincallBack.token;
                Log.d(TAG, "gameSign==" + gameSign + "\nloginTime==" + loginTime + "\nuid==" + uid + "\nusername==" + username
                        + "\nloginWay==" + loginWay + "\nfbBind==" + fbBind + "\ntwitterBind==" + twitterBind+ "\nsubId==" + subId+ "\nmainId==" + mainId
                        + "\ntoken==" + token);
            }

            @Override
            public void onFail(int code, String msg) {
                Log.d(TAG, "code==" + code + "\nmsg==" + msg);
            }
        });
```
####4. 实现onActivityResult 方法####
```java
    @Override
    public void onActivityResult(int requestCode, int resultCode, Intent data) {
 		MyExternalInterface.getInstance().onActivityResult(MainActivity.this, requestCode, resultCode, data, new BaseListener() {
            @Override
            public void onSuccess(int code, String msg) {     
            }
            @Override
            public void onFail(int code, String msg) {      
            }
        });
    }
```
## 3.账号管理界面 ##
    接口定义：
    public void SDKAccountManage(Activity activity, SDKInterfaceExitListener exitListener)
####1. 接口参数说明####
参数名|类型|参数说明
 ---|----|----
activity|Activity|上下文实例
listener|SDKInterfaceExitListener|切换账号的回调

####2. 调用示例代码####
```java
    MyExternalInterface.getInstance().SDKAccountManage(this, new SDKInterfaceExitListener() {
            @Override
            public void exitSuccess(String result) {
                    //点了切换账号确定接口，游戏需要返回登录界面，再次调用sdk登录
                    BaseSDKUtils.logD(TAG,"exitSuccess===="+result);
                    sdkLogin();
            }
            @Override
            public void exitFail(String result) {
            }
        });
```

## 4.生命周期方法 ##
####1. 调用示例代码####
在Activity的onStart里调用

    MyExternalInterface.getInstance().onStart(MainActivity.this, "");

在Activity的onStop里调用
	
	MyExternalInterface.getInstance().onStop (MainActivity.this, "");

在activity的onDestroy里调用

	MyExternalInterface.getInstance().onDestroy(MainActivity.this);


## 5.Firebase推送 ##
####1.在Firebase创建的应用下载json文件####
 <img src="/images/Android_9.png" width = "550" height = "400" alt="Android_9" align=center />
在AndroidManifest.xml 的application节点下加入

    <service
          android:name="com.myBest.sdk.service.MyFirebaseMessagingService"
            android:exported="false">
            <intent-filter>
                <action android:name="com.google.firebase.MESSAGING_EVENT" />
            </intent-filter>
    </service>

####2.在 Android 13+ 上请求运行时通知权限####
Android 13 引入了用于显示通知的新运行时权限。这会影响在 Android 13 或更高版本上运行且使用 FCM 通知的所有应用。

默认情况下，FCM SDK（23.0.6 或更高版本）包含清单中定义的POST_NOTIFICATIONS权限。但是，您的应用还需要通过常量android.permission.POST_NOTIFICATIONS请求此权限的运行时版本。在用户授予此权限之前，您的应用将无法显示通知。

在请求权限的方法中判断Android版本13+以上加上请求通知的权限 Manifest.permission.POST_NOTIFICATIONS

    // This is only necessary for API level >= 33 (TIRAMISU)
    if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.TIRAMISU)

## 6.配置Google登录 ##
拷贝credentials.json文件放在同样的目录位置
<img src="/images/Android_10.png" width = "390" height = "290" alt="Android_10" align=center />

    	<!--google 登录配置-->
        <meta-data
            android:name="Google_SingIn_Key"
            android:value="@string/google_singin_key"></meta-data>
和Facebook配置一样，具体值写在string.xml里

## 7.关于混淆 ##
如果开启了混淆 minifyEnabled 是true，则需要在proguard-rules加入以下代码

    #---------------------------------MySDK---------------------------------
    -keepclassmembers class com.myBest.sdk.utils.JsInterationUtils {
    	<methods>;
    }
    
    -dontwarn com.facebook.**
    -keep class com.facebook.** { *; }
    
    -dontwarn com.google.**
    -keep class com.google.** { *; }
    
    #okhttp3.x
    -dontwarn okhttp3.**
    -keep class okhttp3.** { *;}
    -dontwarn okio.**
    #retrofit
    -dontwarn retrofit.**
    -keep class retrofit.** { *; }
    -keepattributes Signature
    -keepattributes Exceptions
    -dontwarn okio.**
    #retrofit2.x
    -dontwarn retrofit2.**
    -keep class retrofit2.** { *; }
    -keepattributes Signature
    -keepattributes Exceptions
    #--------------------------Adjust-------------------------------
    -keep public class com.adjust.sdk.** { *; }
    -keep class com.google.android.gms.common.ConnectionResult {
    	int SUCCESS;
    }
    -keep class com.google.android.gms.ads.identifier.AdvertisingIdClient {
    	com.google.android.gms.ads.identifier.AdvertisingIdClient$Info getAdvertisingIdInfo(android.content.Context);
    }
    -keep class com.google.android.gms.ads.identifier.AdvertisingIdClient$Info {
    	java.lang.String getId();
    	boolean isLimitAdTrackingEnabled();
    }
    -keep class dalvik.system.VMRuntime {
    	java.lang.String getRuntime();
    }
    -keep class android.os.Build {
    	java.lang.String[] SUPPORTED_ABIS;
    	java.lang.String CPU_ABI;
    }
    -keep class android.content.res.Configuration {
    	android.os.LocaleList getLocales();
    	java.util.Locale locale;
    }
    -keep class android.os.LocaledList {
    	java.util.Locale get(int);
    }
    -keep public class com.android.installreferrer.** { *; }
    #--------------------------Adjust-------------------------------
    
    ################### region for xUtils
    -keepattributes Signature,*Annotation*
    -keep public class org.xutils.** {
    	public protected *;
    }
    -keep public interface org.xutils.** {
     public protected *;
    }
    -keepclassmembers class * extends org.xutils.** {
     public protected *;
    }
    -keepclassmembers @org.xutils.db.annotation.* class * {*;}
    -keepclassmembers @org.xutils.http.annotation.* class * {*;}
    -keepclassmembers class * {
    	 @org.xutils.view.annotation.Event <methods>;
    }
    #################### end region
    ##---------------Gson  ----------
    # Gson uses generic type information stored in a class file when working with fields. Proguard
    # removes such information by default, so configure it to keep all of it.
    -keepattributes Signature
    
    # For using GSON @Expose annotation
    -keepattributes *Annotation*
    
    # Gson specific classes
    -keep class sun.misc.Unsafe { *; }
    #-keep class com.google.gson.stream.** { *; }
    ##---------------Gson  ----------
    # Application classes that will be serialized/deserialized over Gson
    #---------------------------------实体类---------------------------------
    -keep class com.myBest.sdk.Javabean.** { *; }
    
    -keep class com.myBest.sdk.Interfaces.** { *; }
    -keep class com.myBest.sdk.listener.** { *; }
    -keep class com.android.vending.billing.** { *; }
    -keep class com.myBest.sdk.helpers.MyInputMapProvider{ *; }
    
    #---------------------------------MySDK---------------------------------