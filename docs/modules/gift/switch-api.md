<center><font size="64px">礼包兑换API接口</font></center>



## 一、文档说明

### 1.1 修订记录

| <div style="width:100px">日期</div> | <div style="width:250px">修订内容</div> | <div style="width:100px">说明</div> |
|------------|----------------------------------|--------------------------------------|
| 2022-11-15 | v1.0.0 版本文档完成                |                                      |



## 二、报文格式

- 请求方式: POST
- 编码格式: application/json
- 响应结构: JSON

### 2.1 请求地址
| key | <div style="width:350px">value</div> | 说明   |
|-----|--------------------------------------|------|
| URL |                                      | 测试环境 |
| URL |                                      | 生成环境 |

### 2.2 接口响应说明
#### 2.2.1 成功
```json
{
    "status":true,
    "code":200,
    "msg":"SUCCESS",
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
    "status":false,
    "code":"-110110",
    "msg":"ERROR",
}
```

### 2.3 签名机制
#### 2.3.1 概述
系统使用MD5签名验签技术保障双方的身份可靠性和数据完整性。<br/>
对于报文的签名处理机制如下：<br/>
（1）将报文除签名域（sign）外的所有取值不为空（空是指null或"",不包含"null"和 空格）的数据元，按照报文域第一个字符的键值ASCII码递增排序（字母升序排序），如果遇到相同字符则按照第二个字符的键值ASCII码递增排序，依次类推。 <br/>
（2）将排序后的数据元与其对应值，组合成“参数=参数值”的格式，并把这些参数用&字符连接起来，此时生成的字符串作为待签名的字符串。 <br/>
（3）对待签名字符串追加&key=signKey，使用MD5算法做摘要。<br/>
（4）将生成的签名赋值给sign报文域，拼接到请求报文中。<br/>

#### 2.3.2 签名 signKey

| key | value  | 说明   |
|-----------|-------------|------|
| signKey |  4b275ac216d7d8385206c9766485db6f  | 测试环境 |
| signKey |    | 生成环境 |

#### 2.3.3  加密方式
- 待签名数据
```json
    {
        "role_id":"角色ID",
        "role_server":"游戏区服",
        "prop":[
                    {
                      "name":"道具名称",
                      "num":"1"
                    }
                ],
      "order_id":"订单ID",
      "channel":"渠道",
      "extra":"扩展信息",
      "sign":"签名"
    }
```

- 拼装成待验签的字符串如下
> $string = 'channel=渠道&exOrderId=订单ID&extra=扩展信息&prop=[{"name":"道具名称","num":"1"}]&roleId=角色ID&roleServer=游戏区服&sign=签名&key=4b275ac216d7d8385206c9766485db6f';
- md5签名
> $sign = md5($string);


## 三、客户端SDK-兑换礼包
### 3.1 请求地址
> URL：

### 3.2 请求参数

| name       | type     | required   | 说明     |
|------------|----------| ---- |--------|
| gameNo     | int      | 是   | 游戏id   |
| exCode     | string   | 是   | 兑换码    |
| roleId     | int      | 是   | 角色ID   |
| roleServer | int      | 是   | 角色区服ID |
| roleNick   | string   | 是   | 角色昵称   |
| roleGrade  | int      | 是   | 角色等级   |

### 3.3 请求示例
```json
    {
      "gameNo":"游戏编号",
      "exCode":"兑换码",
      "roleId":"角色ID",
      "roleServer":"兑换区服ID",
      "roleNick":"角色昵称",
      "roleGrade":"角色等级",
    }
```


## 四、游戏端-兑换礼包

### 4.1 请求地址
> URL：游戏提供兑换礼包接口

### 4.2 请求参数
| uid        | int    | required | 用户ID   |
|------------|--------|----------|--------|
| roleId     | int    | 是        | 角色ID   |
| roleServer | int    | 是        | 角色区服ID   |
| prop       |        | 是        | 礼包   |
| prop.name  | string | 是        | 道具名称   |
| prop.num   | int    | 是        | 数量     |
| exOrderNo  | string | 是        | 兑换订单编号 |
| channel    | string | 是        | 渠道   |
| extra      | string | 是        | 扩展信息   |
| sign       | string | 是        | 签名    |

### 4.3 请求示例
```json
    {
      "roleId":"角色ID",
      "roleServer":"游戏区服",
      "prop":[
        {
          "name":"道具名称",
          "num":"1"
        },
        {
          "name":"道具名称",
          "num":"1"
        }
      ],
      "exOrderId":"订单ID",
      "channel":"渠道",
      "extra":"扩展信息",
      "sign":"签名"
}
```