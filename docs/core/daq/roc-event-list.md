> [!DANGER|style:flat|label:声明]
> 
> ver.2023001
> 
> 点击右侧图标可查看目录。
> 
> 以 ”af_” 开头的字段，代表有可能被共享给第三方平台用于营销效果优化，如果对此有异议，或者需要禁止共享可提前与对接人员说明。

# 一、统计埋点

> [!TIP|icon:'fa fa-info-circle'|label:说明]
> 
> <aside>
> 主要用于游戏业务的统计分析，展示主要的转化路径与核心指标，详细内容如下。
> </aside>

## （一）通用统计

---

### 更新 `af_update` 
<button class="section" target="af_update" show="详情" hide="收起"></button>

<!--sec data-title="af_update" data-id="af_update" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger | 
| --- | --- | --- | 
| af_update | 了解更新消耗时常与成功率 | 用户更新完成 | 
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_description | 首次更新 | 基于此次更新的额外描述 |
| roc_update_time | 92463 | 更新耗费时常，单位毫秒 |
<!--endsec-->

### 登录 `af_login`
<button class="section" target="af_login" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="af_login" data-id="af_login" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_login | 了解注册用户的留存情况 | 用户成功登录 |
#### 参数
| Parameter name | Example value |
| --- | --- |
| login_method | Guest, Email, Facebook, Google, Apple, Yeeha, Relogin |
| roc_user_id | 用户身份唯一识别编码 |
<!--endsec-->

### 注册 `af_complete_registration`
<button class="section" target="af_complete_registration" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="af_complete_registration" data-id="af_complete_registration" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_complete_registration | 了解用户喜欢的注册方式 | 用户成功注册 |
#### 参数
| Parameter name | Example value |
| --- | --- |
| af_registration_method | Guest, Email, Facebook, Google, Apple, Yeeha, Relogin |
| roc_user_id | 用户身份唯一识别编码 |
<!--endsec-->


### 首充 `roc_first_deposit`
<button class="section" target="roc_first_deposit" show="详情" hide="收起"></button>

<!--sec data-title="roc_first_deposit" data-id="roc_first_deposit" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_first_deposit | 用于针对首次存款的用户来优化广告活动，需要与af_purchase 事件同时触发 | 用户首次成功购买 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | 199.99 | 浮点值，购买的最终价格 |
| af_currency | THB, USD | 货币代码 |
| af_quantity | 1 | 购买的物品数量 |
| af_content_id | 10001 | 购买的物品或礼包ID |
| af_content_type | 战令 | 购买的物品分类 |
| af_content | 11赛季战令 | 购买的物品或礼包显示名称 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 发货方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | Apple Store | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 购买 `af_purchase`
<button class="section" target="af_purchase" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="af_purchase" data-id="af_purchase" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_purchase | 用于LTV和ROI计算，偏好分析，目标优化与调整等。 | 用户成功购买 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | 199.99 | 浮点值，购买的最终价格 |
| af_currency | THB, USD | 货币代码 |
| af_quantity | 1 | 购买的物品数量 |
| af_content_id | 10001 | 购买的物品或礼包ID |
| af_content_type | 战令 | 购买的物品分类 |
| af_content | 11赛季战令 | 购买的物品或礼包显示名称 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 发货方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | Apple Store | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 等级 `af_level_achieved`
<button class="section" target="af_level_achieved" show="详情" hide="收起"></button>

<!--sec data-title="af_level_achieved" data-id="af_level_achieved" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_level_achieved | 关联活跃与付费，用于维度分析 | 用户成功升级或主线关卡 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_level | 1 | 升级后的当前升级 |
| af_score | 44322 | 战力等级或相关分数 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->
    
### 教程 `af_tutorial_completion`
<button class="section" target="af_tutorial_completion" show="详情" hide="收起"></button>

<!--sec data-title="af_tutorial_completion" data-id="af_tutorial_completion" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_tutorial_completion | 确定用户可能遇到的问题，以及哪些教程表现不佳。 | 用户完成教程，或主动退出 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_success | true | 是否成功完成 |
| af_content_id | 1 | 教程ID |
| af_content | 恶魔关卡 | 教程名称 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 分享 `af_share`
<button class="section" target="af_share" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="af_share" data-id="af_share" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_share | 了解用户最有可能在何时与朋友共享应用程序 | 用户分享成功 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_description | 记录达成，升级，赢得比赛 | 分享的原因描述 |
| roc_share_platform | Facebook, WhatsApp, email | 分享发布的平台或渠道 |
| roc_share_location | 成就分享 | 分享所在位置标识 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 邀请 `af_invite`
<button class="section" target="af_invite" show="详情" hide="收起"></button>

<!--sec data-title="af_invite" data-id="af_invite" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_invite | 了解传播概率，修正ROI模型 | 用户发送邀请 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_description | 可以提现 | 用户填写的邀请的原因 |
| roc_invite_platform | Facebook, WhatsApp, email | 邀请发布的平台或渠道 |
| roc_invite_location | 1 | 邀请所在位置标识 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 成就 `af_achievement_unlocked`
<button class="section" target="af_achievement_unlocked" show="详情" hide="收起"></button>

<!--sec data-title="af_achievement_unlocked" data-id="af_achievement_unlocked" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_achievement_unlocked | 用于记录成就解锁事件 | 用户成就解锁 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_description | 全服第2393个解锁 | 成就解锁的额外说明 |
| af_level | 1000 | 成就等级 |
| af_score | 312 | 成就奖励或分数 |
| af_content_id | 321 | 成就ID |
| af_content | 地主恶霸 | 成就名称 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 绑定 `roc_account_bind`
<button class="section" target="roc_account_bind" show="详情" hide="收起"></button>

<!--sec data-title="roc_account_bind" data-id="roc_account_bind" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_account_bind | 用于记录账户绑定事件 | 用户绑定完成 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| bind_method | Guest, Email, Facebook, Google, Apple, Yeeha, Relogin | 绑定账户 |
| roc_bind_id | 134445 | 绑定渠道的用户id |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
| af_description | hoo@dh.com | 绑定的额外信息, 如：邮箱 |
<!--endsec-->

### 成就步骤 `af_achievement_step`
<button class="section" target="af_achievement_step" show="详情" hide="收起"></button>

<!--sec data-title="af_achievement_step" data-id="af_achievement_step" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_achievement_step | 用于记录成就解锁步骤 | 分步成就 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_description | 1/6 | 成就步骤的额外说明 |
| af_step | 48 | 成就步骤 |
| af_content_id | 321 | 成就ID |
| af_content | 地主恶霸 | 成就名称 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->  

## （二）角色扮演

---

### 创建角色 `roc_creat_role`
<button class="section" target="roc_creat_role" show="详情" hide="收起"></button>

<!--sec data-title="roc_creat_role" data-id="roc_creat_role" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_creat_role | 了解玩家活跃的游戏身份 | 创建游戏角色成功 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec--> 

### 赚虚拟币 `roc_earn_credits`
<button class="section" target="roc_earn_credits" show="详情" hide="收起"></button>

<!--sec data-title="roc_earn_credits" data-id="roc_earn_credits" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_earn_credits | 用于记录虚拟币赚取 | 虚拟币余额增加时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
| af_price | 100 | 货币价值 |
| af_content_type | 2 | 虚拟币品类 |
| af_content_id | 1 | 虚拟币id |
| af_content | 钻石 | 虚拟币名称 |
<!--endsec--> 

### 花虚拟币 `roc_spent_credits`
<button class="section" target="roc_spent_credits" show="详情" hide="收起"></button>

<!--sec data-title="roc_spent_credits" data-id="roc_spent_credits" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_spent_credits | 用于记录虚拟币支出 | 虚拟币余额支出时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
| af_price | 100 | 货币价值 |
| af_content_type | 2 | 虚拟币品类 |
| af_content_id | 1 | 虚拟币id |
| af_content | 钻石 | 虚拟币名称 |
<!--endsec-->   

### 商品列表 `af_list_view`
<button class="section" target="af_list_view" show="详情" hide="收起"></button>

<!--sec data-title="af_list_view" data-id="af_list_view" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| af_list_view | 用于记录商品等浏览列表事件 | 查看列表事 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_content_type | 促销商品 | 产品品类 |
| af_content_list | [1233,443,214] | 内容 ID列表 |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | MCard | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->   

## （三）博彩棋牌

---

### 提现申请 `roc_bonus_claimed`
<button class="section" target="roc_bonus_claimed" show="详情" hide="收起"></button>

<!--sec data-title="roc_bonus_claimed" data-id="roc_bonus_claimed" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_bonus_claimed | 分析用户提现频率，关联用户活跃度 | 用户申请提现时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | -100 | 提款的货币价值。记录为负收入值。 |
| af_currency | AUD | 提取的货币 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 资金方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | MCard | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->   

### 提现 `roc_withdraw_cash`
<button class="section" target="roc_withdraw_cash" show="详情" hide="收起"></button>

<!--sec data-title="roc_withdraw_cash" data-id="roc_withdraw_cash" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_withdraw_cash | 了解用户何时提取之前存入其博彩账户的资金 | 当用户从其博彩账户中提取资金时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | -100 | 提款的货币价值。记录为负收入值。 |
| af_currency | AUD | 提取的货币 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 资金方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | MCard | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->   

### 下注 `roc_placed_bet`
<button class="section" target="roc_placed_bet" show="详情" hide="收起"></button>

<!--sec data-title="roc_placed_bet" data-id="roc_placed_bet" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_placed_bet | 了解用户收益波动 | 下注或每局结算 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_price | 100 | 下注的货币价值 |
| af_currency | AUD | 下注货币 |
| roc_transaction_id | 9374 | 下注事件的唯一标识符 |
| roc_placed_id | 3456 | 下注的房间或牌桌ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->   

### 赠金下注 `roc_bonus_bet`
<button class="section" target="roc_bonus_bet" show="详情" hide="收起"></button>

<!--sec data-title="roc_bonus_bet" data-id="roc_bonus_bet" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_bonus_bet | 促销并了解实际收益 | 下注成功时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_price | 100 | 下注的货币价值 |
| af_currency | AUD | 下注货币 |
| roc_transaction_id | 9374 | 下注事件的唯一标识符 |
| roc_placed_id | 3456 | 下注的房间或牌桌ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 赠金下注 `roc_canceled_bet`
<button class="section" target="roc_canceled_bet" show="详情" hide="收起"></button>

<!--sec data-title="roc_canceled_bet" data-id="roc_canceled_bet" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_canceled_bet | 了解投注被取消的原因 | 当用户取消下注时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_price | 100 | 下注的货币价值 |
| af_currency | AUD | 下注货币 |
| roc_transaction_id | 9374 | 下注事件的唯一标识符 |
| roc_placed_id | 3456 | 下注的房间或牌桌ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->   

# 二、诊断埋点

> [!TIP|icon:'fa fa-info-circle'|label:说明]
> 
> <aside>
> 流程与运行诊断埋点，包含但不限于系统输出，组件IO，运行日志等。需要携带明确的事件号与事件内容，上下文，网络，设备与堆栈信息，用于发现系统瓶颈等问题。
> </aside>

## （一）流程诊断

---

### 打开应用 `roc_init_sdk`
<button class="section" target="roc_init_sdk" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_init_sdk" data-id="roc_init_sdk" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_init_sdk | 了解用户访问 | 打开应用时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| - | - | - |
<!--endsec-->   

### 版本检查 `roc_check_version`
<button class="section" target="roc_check_version" show="详情" hide="收起"></button>

<!--sec data-title="roc_check_version" data-id="roc_check_version" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_check_version | 应用版本检察 | 访问版本信息时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| - | - | - |
<!--endsec-->   

### 进入游戏 `roc_entry_game`
<button class="section" target="roc_entry_game" show="详情" hide="收起"></button>

<!--sec data-title="roc_entry_game" data-id="roc_entry_game" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_entry_game | 实际进入游戏世界玩家情况 | 进入游戏时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 点击登录 `roc_click_login`
<button class="section" target="roc_click_login" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_click_login" data-id="roc_click_login" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_login | 了解用户行为与登录完成率 | 用户点击登陆按钮时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| login_method | Guest, Email, Facebook, Google, Apple, Yeeha, Relogin | 登陆方式 |
<!--endsec-->
    
### 点击注册 `roc_click_registration`
<button class="section" target="roc_click_registration" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_click_registration" data-id="roc_click_registration" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_registration | 了解用户行为与注册完成率 | 用户点击注册按钮时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| registration_method | Guest, Email, Facebook, Google, Apple, Yeeha, Relogin | 注册方式 |
<!--endsec-->

### 点击客服 `roc_click_help`
<button class="section" target="roc_click_help" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_click_help" data-id="roc_click_help" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_help | 了解用户行为与客服效率 | 用户点击aihelp时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 点击商城 `roc_click_store`
<button class="section" target="roc_click_store" show="详情" hide="收起"></button>

<!--sec data-title="roc_click_store" data-id="roc_click_store" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_store | 了解用户行为与游戏商店 | 用户点击游戏商城时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### 展示协议 `roc_show_policy`
<button class="section" target="roc_show_policy" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_show_policy" data-id="roc_show_policy" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_store | 了解用户行为与游戏商店 | 用户点击游戏商城时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| - | - | - |
<!--endsec-->

### 点击协议 `roc_click_policy`
<button class="section" target="roc_click_policy" show="详情 (SDK已内置)" hide="收起"></button>

<!--sec data-title="roc_click_policy" data-id="roc_click_policy" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_click_store | 了解用户行为与游戏商店 | 用户点击协议时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| error_code | 10394 | 内部异常号 |
| error_msg | 10394 | 内部讯息（80字符以内） |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

## （二）异常诊断

---

### 异常事件 `roc_error_event`
<button class="section" target="roc_error_event" show="详情" hide="收起"></button>

<!--sec data-title="roc_error_event" data-id="roc_error_event" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_error_event | 了解游戏异常事件 | 发生内部处理异常时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_success | true | 是否同意协议 |
<!--endsec-->



# 三、审计埋点

> [!TIP|icon:'fa fa-info-circle'|label:说明]
> 
> <aside>
> 支付 / 链改 / 核心资产 / 管理操作等的输入和输出，常用于审计对账。
> </aside>

## （一）财务审计

---

### 充值 ` roc_deposit `

<button class="section" target="roc_deposit" show="详情" hide="收起"></button>

<!--sec data-title="roc_deposit" data-id="roc_deposit" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_deposit | 财务对账 | 用户充值成功 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | 199.99 | 浮点值，购买的最终价格 |
| af_currency | THB, USD | 货币代码 |
| af_quantity | 1 | 购买的物品数量 |
| af_content_id | 10001 | 购买的物品或礼包ID |
| af_content_type | 战令 | 购买的物品分类 |
| af_content | 11赛季战令 | 购买的物品或礼包显示名称 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 发货方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | Apple Store | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->

### `提现` roc_withdraw

<button class="section" target="roc_withdraw" show="详情" hide="收起"></button>

<!--sec data-title="roc_withdraw" data-id="roc_withdraw" data-show=false data-nopdf=true data-collapse=true ces-->
#### 说明
| Event nam | Purpose | Trigger |
| --- | --- | --- |
| roc_withdraw | 财务对账 | 当用户从其账户中提取资金时 |
#### 参数
| Parameter name | Example value | Description |
| --- | --- | --- |
| af_revenue | -100 | 提款的货币价值。记录为负收入值。 |
| af_currency | AUD | 提取的货币 |
| af_order_id | 6003847102 | 订单ID |
| af_receipt_id | 927734 | 资金方关联的凭据ID |
| roc_role_id | 10001 | 游戏内角色ID |
| roc_region_id | 20003 | 游戏角色所在区服ID |
| roc_pay_channel | MCard | 支付方式或渠道名称 |
| roc_user_id | 10000039 | 用户身份唯一识别编码 |
<!--endsec-->
    
    
