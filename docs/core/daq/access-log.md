**1.分类（topic）**
> * 诊断日志 ：RCDiagnosticLog  携带明确的事件号与事件内容，上下文，网络，设备与堆栈信息等。
> * 运行日志 ：RCRunLog 系统输出，三方IO的输入与输出等未明确的事件，可全量采集。
> * 统计日志 ：RCStatisticalLog 网络数据
> * 审计日志 ：RCAuditLog 支付 / 链改 / 核心资产 / 管理操作等的输入和输出，常用于审计对账。

**2.格式**

*1.诊断日志：*
> * 请求入口(sourceIp)和出口(targetIp)
> * 外部服务调用和返回
> * 资源消耗操作(resource_operation): 如读写文件等
> * 容错行为： 如云硬盘的副本修复操作
> * 程序异常(program_exception)： 如数据库无法连接，资源加载失败
> * 后台操作(background_operation)：定期执行删除的线程
> * 启动、关闭、配置加载(start_loading,close_load,configuration_loading)

*2.统计日志：*
> * 用户访问统计：用户IP(user_ip)、上传下载的数据量(flow_data，单位M)，请求耗时(request_time，单位s)等

*3.审计日志：*

> * 日志通过不同的关键字进行区分：支付 payLog, 链改 NFTLog ,核心资产变动 coreAssetsLog

*4.运行日志 ：*
> * 系统输出，三方IO的输入与输出等未明确的事件，可全量采集。

**3.关于RequestID**

****RequestID的作用:****

> * 一个系统通常通过RequestID来对请求进行唯一的标记，目的是可以通过RequestID将一个请求在系统中的执行过程串联起来。该RequestID通常会随着响应返回给调用者，如果调用出现问题，调用者也可以通过提供RequestID帮助服务提供者定位问题。前端生成，传给后端

****RequestID的生成：需要根据实际的使用场景来选择****
> * 对于简单的系统，可以简单采用一个随机数即可
> 
	RequestID = md5(time.Now() + random.Int())

**4.日志需要的信息**

****一、设备信息****

 序号| 字段定义 |字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----
1|os_name|操作系统平台名称|string|Android或iOS|是
2|os_brand |手机品牌 |string| | 是|
3|os_model| 手机型号|string| | 是
4|os_version|手机操作系统版本|string||是
5|cpu_abi|CPU架构|string||否
6|device_id|设备ID|string|传adjust id |是
7|screen_width|屏幕宽|string||否
8|screen_height|屏幕高|string||否
9|display_density |屏幕密度|string||否
10|simulator |是否为模拟器|string|0-否；1-是 |否
11|is_charging |是否正在充电|string|1：未知状态；2：充电中；3：放电中；4：未充电；5：充满|否
12|battery_pct |电池百分⽐|string|0-100|否
13|battery_temperature |电池温度|string|单位0.1，如359表示35.9°C|否

****二、环境信息****

 序号| 字段定义 | 字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----|----
1|network_type|网络类型|string|2G、3G、4G、5G、WiFi、Unknown|是
2|phone_carrier|运营商|string||是
3|is_root|是否Root|string|仅【Android】0-否；1-是|否
4|is_jailbreak|是否越狱|string|仅【iOS】0-否；1-是|否
5|longitude|经度|string||否
6|latitude|纬度|string||否
7|address|地址信息 |string||否
8|total_storage|内部存储总空间|string|单位M |否
9|free_storage|内部存储可用空间|string|单位M |否
10|total_ram|设备系统内存大小|string|单位M |否
11|free_ram|系统剩余内存|string|单位M |否
12|low_memory|系统是否处于低内存状态|string|0-否；1-是 |否
13|total_memory|分配给App的总内存|string|单位M|否
14|max_memory|分配给App最大内存|string|单位M|否
15|free_memory|App当前可用内存|string|单位M|否
16|permission_notification|推送是否打开|string|0-否；1-是|否
17|app_status|前后台状态|string|background-后台、forground-前台|否

****三、App信息****

 序号| 字段定义 | 字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----|----
1|app_packname|App包名|string| |是
2|app_version|app 版本号|string| |是
3|app_channel|app 渠道|string|Android:GP; iOS:AS |是

****四、SDK信息****

 序号| 字段定义 | 字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----|----
1|sdk_version|SDK版本号|string| |是

****五、用户信息 （sdk在用户登录之后获取并上报）****

 序号| 字段定义 | 字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----|----
1|user_id|用户ID|string| |是
2|sub_id|yeeha平台用户ID|string| |是

****六、日志信息****

 序号| 字段定义 | 字段说明 |字段类型|备注|是否一直携带
 ----|----|----|----|----|----
1|RequestID|唯一的标记|string|具体生成规律参考上面说明 |是
2|log_report_time|日志上报时间|string| yyyy-MM-dd HH:mm:ss|是
3|log_content|日志内容|string| |是


> * 注：
> 
 其中一，二，三，四，五块的内容sdk可自行收集，并且在初始化时上报，上报时可打上标记，此后的每条数据都加上这个标记
>
 // 设置tag信息，此tag会附加在每条日志上
>
   config.addTag("device_info", "目前自行生成的设备id");



研发所需要传入的日志信息，比如统计日志：
```java
 		Map<String, String> parMaps =new HashMap();
        parMaps.put("topic","RCStatisticalLog");
        parMaps.put("user_ip","192.xxx.xxx.xxx");
        parMaps.put("flow_data","100M");
        parMaps.put("request_time","10s");
        parMaps.put("RequestID","asd1234567890zxc");
        parMaps.put("log_report_time","2023-02-21 10:10:10");
        parMaps.put("log_content","日志内容，比如是否连接服务器成功，资源下载是否完成等");
```
