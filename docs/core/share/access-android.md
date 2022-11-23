# Facebook 分享功能 #

> - 请先初始化 SDK 可参考 [Android登录](/core/login/access-and.md) 

Android 11,需要在 AndroidMainfest.xml 加上下面内容，不然可能会分享不了图片:

    <manifest package="com.example.app">

		<queries>
			<package android:name="com.facebook.katana" />
        	<provider android:authorities="com.facebook.katana.provider.PlatformProvider" />
    	</queries>
    ...
	</manifest>

 <img src="/images/Android_8.png" width = "550" height = "80" alt="Android_8" 
 align=center />

####1.Facebook分享链接####
    接口定义：
	public void SDKFacebookShare(Activity activity, ShareInfo shareInfo, SDKInterfaceShareListener callback)

#####a.接口参数说明#####

参数名|	类型|	参数说明
 ---|----|----
activity|Activity|上下文实例
shareInfo|ShareInfo|分享的信息对象
callback|SDKInterfaceShareListener|	分享的回调

ShareInfo对象说明

参数名|	类型| 参数说明
 ---|----|----
andLink|String|	分享的链接
dsp|String|	分享的描述信息
uid|String|	用户uid
serverId|String|服务器id
roleId|	String|	游戏内的角色id
shareId|String|	分享点所在位置id（具体值具体定义）

#####b.分享回调说明#####
    msg = "0"; 为分享成功状态，回调shareSuccess
	msg = "1", 为分享失败状态, 回调shareFail
	msg ="2";为分享取消状态，回调shareFail
	msg ="3";为用户没有安装Facebook app，回调shareFail

#####c.调用示例代码#####
```java
    ShareInfo shareInfo = new ShareInfo();
        shareInfo.andLink = "https://www.baidu.com";
        shareInfo.dsp = "测试分享";
        shareInfo.uid = "10000";
        shareInfo.serverId = "1";
        shareInfo.roleId = "123";
        shareInfo.shareId = "maipage";
        MyExternalInterface.getInstance().SDKFacebookShare(this, shareInfo, new SDKInterfaceShareListener() {
            @Override
            public void shareSuccess(String s) {
                Log.d(TAG, "s==" + s);
            }
            @Override
            public void shareFail(String s) {
                Log.d(TAG, "s==" + s);
            }
        });
```
####2.Facebook分享本地视频####
    接口定义：
	public void SDKFacebookShareVideo (Activity activity, ShareInfo shareInfo,File videoFile, SDKInterfaceShareListener callback)

参数名|	类型|	参数说明
 ---|----|----
activity|Activity|上下文实例
shareInfo|ShareInfo|分享的信息对象
videoFile|File|传入本地视频的File目录
callback|SDKInterfaceShareListener|	分享的回调


ShareInfo对象说明

参数名|	类型| 参数说明
 ---|----|----
uid|String|	用户uid
serverId|String|服务器id
roleId|	String|	游戏内的角色id
shareId|String|	分享点所在位置id（具体值具体定义）

#####a.调用示例代码#####
```java
	File dir = this.getExternalFilesDir("video");
 	File loadingvideo = new File(dir, "shareVideo.mp4");

    ShareInfo shareInfo = new ShareInfo();
        shareInfo.uid = "10000";
        shareInfo.serverId = "1";
        shareInfo.roleId = "123";
        shareInfo.shareId = "maipage";

        MyExternalInterface.getInstance().SDKFacebookShareVideo (this,shareInfo,loadingvideo,new SDKInterfaceShareListener(){
			@Override
            public void shareSuccess(String s) {
                Log.d(TAG, "s==" + s);
            }

            @Override
            public void shareFail(String s) {
                Log.d(TAG, "s==" + s);
            }
	});
```
####3.Facebook分享图片####
  
> -用户必须安装 7.0 或更高版本的原生 Android 版 Facebook 应用才能分享。

	接口定义：
	public void SDKFacebookSharePicture (Activity activity, ShareInfo shareInfo, Bitmap imageBitmap, SDKInterfaceShareListener callback)


参数名|	类型|	参数说明
 ---|----|----
activity|Activity|上下文实例
shareInfo|ShareInfo|分享的信息对象
imageBitmap|Bitmap|传入图片的bitmap
callback|SDKInterfaceShareListener|	分享的回调


ShareInfo对象说明

参数名|	类型| 参数说明
 ---|----|----
uid|String|	用户uid
serverId|String|服务器id
roleId|	String|	游戏内的角色id
shareId|String|	分享点所在位置id（具体值具体定义）


#####a.调用示例代码#####
```java
	File dir = this.getExternalFilesDir("picture");
            File sharePicture = new File(dir, "sharePicture.png");
            Uri uri = Uri.fromFile(sharePicture);
            Bitmap bitmap = MediaStore.Images.Media.getBitmap(this.getContentResolver(), uri);
    ShareInfo shareInfo = new ShareInfo();
        shareInfo.uid = "10000";
        shareInfo.serverId = "1";
        shareInfo.roleId = "123";
        shareInfo.shareId = "maipage";
        MyExternalInterface.getInstance().SDKFacebookSharePicture (this,shareInfo, bitmap,new SDKInterfaceShareListener(){
			@Override
            public void shareSuccess(String s) {
                Log.d(TAG, "s==" + s);
            }
            @Override
            public void shareFail(String s) {
                Log.d(TAG, "s==" + s);
            }
	});
```