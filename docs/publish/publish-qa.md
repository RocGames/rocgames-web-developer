# 测试流程
----
# 1.测试流程规范及说明文档
##  需求阶段

 -   目标：理解需求，制定计划
  
 -   工作内容：

    1.测试需求分析
    2.测试计划制定
    
 -   输出
  
    1. 测试需求分析文档
    2. 测试用例编写
    3. 测试计划书
    
 ##  开发阶段
 
 -   目标：项目测试，提升游戏质量
 
 -   工作内容：
  
    1. 确定版本发布功能点
    2. 功能测试用例设计
    3. 接口测试用例设计（如果有需求）
    4. 测试用例评审
    5. 进行功能测试/回归测试/验收测试
    6. bug追踪管理
    
 -   输出
  
    1. 功能/接口测试用例
    2. 缺陷报告
    
##   发布阶段
 -   目标：安全稳定的将游戏上线
  
 -   工作内容：
  
    1. 确认所有此次发布版本相关的bug是否已解决
    2. 确认所有功能的验收测试是否通过
    3. 和开发确认是否有版本回滚机制
    4. 和运维确认所更新的平台和渠道
    5. 和运维确认更新时间
    6. 开服前线上功能检查，着重测网络，语言本地化和支付相关
    7. 测试完成后通知到各方，并确认是否测试完成，是否能开服
    
 -   输出：
  
    1. bug修复清单
    2. 线上功能Checklist
    3. 版本测试报告
    
    
##  4.运营阶段

 -   目标：及时确认运营和客服反馈的线上问题，并第一时间反馈
  
 -   工作内容： 
  
    1. 确认所反馈的问题是否存在，尽可能的原环境复现问题
    2. 确认问题确实存在后，尽快反馈到开发或产品，并及时跟进解决
    3. 问题不管解决与否都需及时反馈到运营最后的解决方案
    
    
# 2.测试工具及专项测试方法

##  网络测试
  1. 所使用到的工具：Charles/Postman/Android Studio/WireShark/Fiddle等
  2. 各个工具的具体方法和作用
  
 -   弱网测试：
    
      1.使用到的工具：Charles or wireShark 
      
      2.弱网测试的目的：模拟不同网络环境下游戏的表现
      
      3.弱网测试中，Charles的使用方法
      
         https://zhuanlan.zhihu.com/p/140942687
 -   网络抓包：
    
      1.使用到的工具：Postman or WireShark/Charles
      
      2.抓包测试的目的：可用于接口测试，也可用于流量监控等
      
      3.Postman的使用方法
        https://blog.csdn.net/weixin_67553250/article/details/128192765
      
  
##  性能测试
  1.  所使用到的工具：Perdog
  2.  Perfdog介绍和使用方法

##  适配测试
  1. 目标：根据不同地区的机型覆盖率进行适配测试
  2. 覆盖率： 尽可能覆盖所发行地区的top100机型的适配，对top10的机型重点测试
  3. 测试方法： 公司的测试机,如果有需求找第三方进行适配测试并产出测试报告


...未完待续

