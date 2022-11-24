# 埋点文档
## 1. SDK自带埋点

>*SDK自带的埋点*

| 事件说明       | 事件名                       | 触发时机                           |携带参数      |         |          |          |         |       |
| :-----------  | :-------------------------- | :------------------------------- | :--------: |:-------: |:-------: |:-------: |:------: |:----: |
| sdk初始化      | sdk_initialization_complete | SDK初始化完成触发                   |     -      |    -     |     -    |     -     |   -    |   -   |
| sdk登录点击事件 | login_start                 | 点击登陆按钮时触发                   | login_type |    -     |     -    |     -     |   -    |   -   |
| sdk登录成功    | login_success               | 登录成功时触发                     | login_type |    -     |     -    |     -     |   -    |   -   |
| sdk登录失败    | login_unsuccess             | 登录失败时触发                     | login_type |    -     |     -    |     -     |   -    |   -   |
| sdk注册       | regist_start                | 点击SDK注册按钮时触发               |     -      |    -     |     -    |     -     |    -   |   -   |
| sdk注册成功    | regist_success             | 邮箱注册成功、三方账号第一次登录时触发 | login_type |    -      |    -    |     -     |    -    |   -  |
| sdk注册失败    | regist_unsuccess           | 邮箱注册失败时触发                   |     -      |    -     |     -    |     -     |    -    |  -   |
| 充值开始       | charge_start               | 点击充值按钮时触发                   | uid        | serverid | playerid | channelid |    -    |  -   |
| 充值成功       | charge_success             | 支付成功时触发                       | uid        | serverid | playerid | channelid | orderid |amount|
| 充值失败      | charge_unsuccess            | 支付失败时触发                       | uid        | serverid | playerid | channelid | orderid |  -   |
| 分享开始      | share_start                 | 点击分享按钮时触发                   | uid        | serverid | playerid | channelid | shareid |  -   |
| 分享成功      | share_success               | 分享成功时触发                       | uid        | serverid | playerid | channelid | shareid |  -   |
| 分享失败      | share_unsuccess             | 分享失败时触发                       | uid        | serverid | playerid | channelid | shareid |  -   |

## 2. 研发埋点

> *需要研发触发的埋点*

携带参数说明:

> - **均为字符串类型**
> - **amount:**金额
> - **level:**当前等级
> - **orderid:**订单号
> - **share_id:**分享位标识
> - **login_type:**登录方式
> - **serverid:**为服务器ID。
> - **playerid:**为游戏内角色ID。
> - **sourceip**:客户端源IP地址
> - **targetip:**服务器目标IP地址
> - **orderid:**iOS订单ID、google订单ID。
> - **channelid:**安卓为“GP” 、iOS为:“AS”
> - **uid:**是用户唯一标识，登录成功后返回。
> - **login_type:**0：游客登录 1：fb登录 2：平台登录 3：断线重连 4：平台注册 5：在线跨天 6：自动登录 7：苹果登录 8：谷歌登录

| 事件说明  | 事件名 | 触发时机 |携带参数  |  |  |  |  |  |  |
| :------  | :--- | :------ | :-----: |:--: |:--: |:--: |:--: |:--: |:--: |
| 游戏版本效验 | game_check | 版本校验开始时触发 | - |- |- |- |- |- |
| 游戏版本成功 | game_check_success | 版本校验成功时触发 | - |- |- |- |- |- |- |
| 游戏版本失败 | game_check_unsuccess | 版本校验失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | - |- |- | sourceip | targetip |- |- |
| 游戏版本更新开始 | game_updata | 资源更新开始时触发 | - |- |- |- |- |- |- |
| 游戏版本更新结束 | game_updata_success | 资源更新成功时触发 | - |- |- |- |- |- |- |
| 游戏版本更新失败 | game_updata_unsuccess | 资源更新失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | - |- |- | sourceip | targetip |- |- |
| 游戏弹出公告事件 | game_announcement | 公告弹出时触发 | - |- |- |- |- |- |- |
| 游戏弹出公告成功 | game_announcement_success | 公告内容加载完成时触发 | - | - | - | - |- |- |- |
| 游戏弹出公告失败 | game_announcement_unsuccess | 公告内容加载失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | - | - | - | sourceip | targetip | - |- |
| 游戏获取服务器列表事件 | game_serverlist | 获取服务器列表时触发 | - | - | - | - | - |- |- |
| 游戏获取服务器列表成功 | game_serverlist_success | 获取服务器列表成功时触发 | - | - | - | - | - |- |- |
| 游戏获取服务器列表失败 | game_serverlist_unsuccess | 获取服务器列表失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | - | - | - | sourceip | targetip |- |- |
| 登录游戏 | login_relogin | 游戏断线重连时触发 | uid | login_type | - | - | - |- |- |
| 点击进入游戏按钮事件 | entry_game | 点击进入游戏按钮时触发 | uid | serverid | playerid | - | - |- |- |
| 进入游戏成功 | entry_game_success | 进入游戏成功时触发 | uid | serverid | playerid | - | - |- |- |
| 进入游戏失败 | entry_game_unsuccess | 进入游戏失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | uid | serverid | playerid | sourceip | targetip |- |- |
| 游戏角色创建开始 | creat_role | 进入创角页面时触发 | uid | serverid | playerid | - | - |- |- |
| 游戏角色创建成功 | creat_role_success | 创角成功时触发 | uid | serverid | playerid | - | - |- |- |
| 游戏角色创建失败 | creat_role_unsuccess | 创角中断/失败时触发 ⚠️: 该事件仅在最终重试失败后触发 | uid | serverid | playerid | sourceip | targetip |- |- |
| 首次充值 | pay_1st | 第一次充值成功时触发 | uid | serverid | playerid | channelid | - |- |- |
| 用户累计充值金额 | pay_total | 用户充值成功时触发 | uid | serverid | playerid | amount (累计金额) | - |- |- |
| 用户升级 | level_up | 玩家每次升级时触发 | uid | serverid | playerid | - | - |- |- |
| 首次通过某关卡 | first_pass | 玩家首次通过某关卡时触发 | uid | serverid | playerid | type（场景类型） | chapterId（场景id） |- |- |
| 虚拟币消费 | spend_virtual_currency | 玩家消费虚拟币时触发 | uid | serverid | playerid | type（虚拟币类型） | value（数值） | reason（流动原因） | amount（流动后剩余总额度） |
| 虚拟币赚取 | earn_virtual_currency | 玩家获得虚拟币时触发，包含宝箱，抽奖等渠道 | uid | serverid | playerid | type（虚拟币类型） | value（数值） | reason（流动原因） | amount（流动后剩余总额度）|
| 玩家充值 | earn_currency | 用户成功充值现金货币时触发 | uid | serverid | playerid | type（货币类型, 无特殊就用USD） | value（充值金额） | amount（流动后账户总额度, 通常为游戏币） |- |
| 玩家充值 | spend_currency | 用户成功消费现金货币时触发 | uid | serverid | playerid | type（货币类型, 无特殊就用USD） | value（充值金额） | amount（流动后账户总额度, 通常为游戏币） |- |
| 商城按钮点击事件 | click_enter_store | 点击商城按钮时触发 | uid | serverid | playerid | - | - |- |- |
| 新手引导开始 | click_role_guide_start | 新手引导教程开启时触发 | uid | serverid | playerid | guideId（引导id）| - |- |- |