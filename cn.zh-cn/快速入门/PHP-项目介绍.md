# 项目介绍<a name="devcloud_qs_0301"></a>

## 文档目的<a name="section19479174"></a>

本章节通过示例项目“小蝌蚪即时交互游戏”介绍如何使用DevCloud开发基于PHP语言的H5应用。

## 项目详情<a name="section1555010156104"></a>

-   项目名称：小蝌蚪即时交互游戏。
-   项目简介：“小蝌蚪即时交互游戏“采用PHP（workerman框架）+HTML5技术开发，是一款以workerman作为应用服务器，前端采用HTML5+WebSocket开发。游戏交互很简单，点击屏幕小蝌蚪可以自由游动，其它玩家可以看到周围玩家的游动状态，并且可以即时聊天。

    ![](figures/PHP-产品页面展示.png)

-   项目架构 :
    -   前端采用HTML5开发。
    -   以PHP的workerman框架开发后台游戏服务器。
    -   后端PHP多进程支持。
    -   采用WebSocket协议。
    -   PHP实时推送技术。
    -   独立运行，不依赖Mysql、apache、nginx等软件。

-   部署环境：Ubuntu 16.04。
-   涉及华为云服务：
    -   本示例项目将使用到[软件开发平台DevCloud](https://www.huaweicloud.com/devcloud/)的以下服务：
        -   [项目管理ProjectMan](https://www.huaweicloud.com/product/projectman.html)
        -   [代码托管CodeHub](https://www.huaweicloud.com/product/codehub.html)
        -   [代码检查CodeCheck](https://www.huaweicloud.com/product/codecheck.html)
        -   [编译构建CloudBuild](https://www.huaweicloud.com/product/cloudbuild.html)
        -   [发布CloudRelease](https://www.huaweicloud.com/product/cloudrelease.html)
        -   [部署CloudDeploy](https://www.huaweicloud.com/product/clouddeploy.html)
        -   [流水线CloudPipeline](https://www.huaweicloud.com/product/cloudpipeline.html)

    -   本示例项目还将使用到华为云以下产品：
        -   [统一身份认证服务IAM](https://www.huaweicloud.com/product/iam.html)
        -   [弹性云服务器ECS](https://www.huaweicloud.com/product/ecs.html)



## 项目过程<a name="section491654214598"></a>

DevCloud基本操作流程请参考[软件开发平台使用流程](zh-cn_topic_0110467970.md)。

本示例中将依次进行以下步骤：

1.  [准备工作](zh-cn_topic_0268298500.md)
2.  [步骤一：管理项目规划](PHP-管理项目规划.md)
3.  [步骤二：管理项目代码](PHP-管理项目代码.md)
4.  [步骤三：静态代码扫描](zh-cn_topic_0261083603.md)
5.  [步骤四：构建并归档软件包](PHP-构建并归档软件包.md)
6.  [步骤五：部署软件包至云主机](PHP-部署软件包至云主机.md)
7.  [步骤六：流水线实现持续交付](zh-cn_topic_0261083604.md)
8.  [释放资源](zh-cn_topic_0268298523.md)

  

