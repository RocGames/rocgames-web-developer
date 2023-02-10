<center><font size="64px">SDK功能API接口</font></center>



## 一、文档说明

### 1.1 修订记录

| <div style="width:100px">日期</div> | <div style="width:250px">修订内容</div> | <div style="width:100px">说明</div> |
|-----------------------------------|----------------------------------|--------------------------------------|
| 2022-02-06                         | v1.0.0 版本文档完成                |                                      |



## 二、报文格式

- 请求方式: POST
- 编码格式: application/json
- 响应结构: JSON

### 2.1 请求地址
| key | <div style="width:350px">value</div> | 说明   |
|-----|--------------------------------------|------|
| URL | http://m-uat.roc.games/api           |  |

### 2.2 接口响应说明
#### 2.2.1 成功
```json
{
    "success": true,
    "errCode": 0,
    "errMsg": "SUCCESS",
    "data":[
        {
        	# 更多参数请查阅相关接口
        }
    ]
}
```
#### 2.2.2 失败
```json
{
    "success": false,
    "data": {},
    "errCode": "-100001",
    "errMsg": "Validation errors"
}
```


### 2.3 签名机制
#### 2.3.1 概述
系统使用AWS4签名方式，参考既往接口即可。


## 三、拍脸图配置

### 3.1 请求地址
> URL：/platform/syncFace

### 3.2 说明
> - 可以传多组数据对应多张脸图
> - 图片大小要统一 目前是1500x800
> - 可以跳转的图片上的按钮不要求摆放的位置，点击整张图片等于点击了按钮
> - 表现效果 比如有2张: A先弹出来 点了右上角的× A关闭，B弹出来 点了右上角的× B关闭，整个拍脸系统关闭 （图片需要下载 在未显示的时候会有一个底图显示 写着 【稍等正在加载】）

### 3.3 请求参数

| 字段              | 类型     | 必填  | 说明                       | 
|-----------------|--------|-----|--------------------------|
| gameNo          | int    | 是   | 游戏编号                     |
| language        | int    | 是   | 英文en_US 繁体zh_HK 泰文th_TH  |
| faceList        |        | 是   | 脸图数组                     |
| - faceDrawingId | string | 是   | 脸图ID                     |
| - order           | string | 是   | 脸图顺序                     |
| - path            | string | 是   | 图片链接（需要展示在界面上的图片）        |
| - jumpJudge       | string | 是   | 跳转判断 0=游戏界面 跳转判断 0=游戏界面  |
| - jumpPath        | string | 是   | 图片链接（需要展示在界面上的图片）        |
| - startTime       | string | 否   | 开始时间                     |
| - endTime         | string | 否   | 结束时间                     |
| - levelUpLimit    | string | 否   | 等级上限                     |
| - levelDownLimit  | string | 否   | 等级下限                     |
| - chargeUpLimit   | string | 否   | 充值额度上限                   |
| - chargeDownLimit | string | 否   | 充值额度下限                   |
| - platformId      | string | 否   | 平台 0=iOS  1=安卓           |
| - serverId        | string | 否   | 区服Id 如:20001             |

