<style>
    table{
        margin: initial;
    }
</style>

# 礼包功能介绍

## 礼包兑换流程

 <img src="../../images/gift/exchange-process.jpg" width = "773" height = "704" alt="Android_1" align=center />

## 礼包表结构

### 游戏表

Table：azura_game

| name      | type        | 说明   | 备注              |
|-----------|-------------|------|-----------------|
| id        | int(10)     | ID   |                 |
| gameName  | string(32)  | 游戏名称 |                 |
| gameNo    | string(16)  | 游戏编号 |                 |
| createdAt | int(10)     | 创建时间 |                 |
| updatedAt | int(10)     | 更新时间 |                 |
| deletedAt | int(10)     | 删除时间 |                 |

### 礼包表

Table：azura_game_gift

| name            | type        | 说明 | 备注                |
|-----------------|-------------|----|-------------------|
| id              | int(10)     | ID |                   |
| gameId          | int(10)     | 游戏ID |                   |
| giftName        | string(32)  | 礼包名称 |                   |
| exchangeCeiling | tinyint(3)  | 单账号兑换上限  | 默认1 同一个礼包多张券可兑换限制 |
| receiveGrade    | tinyint(3)  | 领取等级  | 0不限制              |
| giftConf        | string(128) | 礼包配置  |                   |
| exchangeUrl     | string(196) | 礼包兑换接口  | 游戏提供兑换API         |
| createdAt       | int(10)     | 创建时间 |                   |
| updatedAt       | int(10)     | 更新时间 |                   |
| deletedAt       | int(10)     | 删除时间 |                   |

### 礼包批次表

Table：azura_game_gift_batch

| name            | type        | 说明              | 备注            |
|-----------------|-------------|-----------------|---------------|
| id              | int(10)     | ID              |               |
| gameId          | int(10)     | 游戏ID |                   |
| giftName        | string(32)  | 礼包名称 |                   |
| exchangeCeiling | tinyint(3)  | 单账号兑换上限  | 默认1 同一个礼包多张券可兑换限制 |
| receiveGrade    | tinyint(3)  | 领取等级  | 0不限制              |
| giftConf        | string(128) | 礼包配置  |                   |
| exchangeUrl     | string(196) | 礼包兑换接口  | 游戏提供兑换API         |
| giftId          | int(10)     | 礼包ID            |               |
| isPublic        | tinyint(3)  | 通用礼包码  | 1通过 0不通用      |
| num             | smallint(5) | 礼包码数量           |               |
| startTime       | int(10)     | 礼包开始时间          |               |
| endTime         | int(10)     | 礼包过期时间          |               |
| status          | tinyint(3)  | 状态 |状态 0待生成、1成功、2生成中 |
| createdAt       | int(10)     | 创建时间            |               |
| updatedAt       | int(10)     | 更新时间            |               |
| deletedAt       | int(10)     | 删除时间            |               |

### 礼包码表

Table：azura_game_gift_code

| name         | type       | 说明   | 备注                |
|--------------|------------|------|-------------------|
| id           | int(10)    | ID   |                   |
| gameId       | int(10)    | 游戏ID |                   |
| giftId       | int(10)    | 礼包ID |                   |
| batchId      | int(10)    | 批次ID |                   |
| code         | string(16) | 兑换码  |                   |
| exRoleId     | string(32) | 兑换角色ID |                   |
| exRoleServer | string(32) | 兑换区服   |                   |
| exRoleNick   | string(64) | 兑换角色昵称 |                   |
| exRoleGrade  | int(10)    | 兑换角色等级 |                   |
| exTime       | int(10)    | 兑换时间 |                   |
| status       | tinyint(3) | 状态   | 0待兑换、1兑换成功、2兑换失败  |
| createdAt    | int(10)    | 创建时间 |                   |
| updatedAt    | int(10)    | 更新时间 |                   |
| deletedAt    | int(10)    | 删除时间 |                   |
