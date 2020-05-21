# **概述**<a name="devcloud_qs_0601"></a>

## **文档目的**<a name="section16381121019282"></a>

本文通过示例项目“音频解析器”介绍如何使用DevCloud开发基于C++语言的客户端应用，为研发C++项目的企业或个人提供上云指导。

## **项目详情**<a name="section225901918283"></a>

-   项目名称：音频解析器。
-   项目简介：音频采样器是一个C++应用程序，它可以从MP3、WAV、FLAC或Ogg Vorbis格式的音频文件中生成波形数据，波形数据可用于生成音频的可视化呈现，外观类似于音频编辑应用程序；除此之外，该应用程序还可以进行音频格式转换等功能，为音频处理者提供多种服务。

    ![](figures/C++-产品页面展示.png)

      

-   项目周期：3周（敏捷迭代开发）。
-   构建环境：Ubuntu 16.04+GNU 5.4.0+Cmake3.5.1。
-   部署环境：Ubuntu 16.04。
-   华为云服务：
    -   [软件开发平台DevCloud](https://www.huaweicloud.com/devcloud/)
    -   [容器镜像服务SWR](https://www.huaweicloud.com/product/swr.html)
    -   [弹性云服务器ECS](https://www.huaweicloud.com/product/ecs.html)


## **前提条件**<a name="section7515102720286"></a>

使用DevCloud开展本例前，需要先进行以下步骤。若已有华为云账号及弹性云服务器，则可忽略。

-   注册华为云账号：在[华为云官网](https://www.huaweicloud.com/)注册华为云账号，并进行实名认证，此账号适用于所有华为云产品。
-   购买弹性云服务器：由于静态库不兼容CentOS系统而会导致不确定的错误，本项目部署将使用带有公网IP的Ubuntu16.04系统ECS。ECS的购买方式请参考[购买并登录Linux弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0132727313.html)。

>![](public_sys-resources/icon-note.gif) **说明：**   
>-   本例中对弹性云服务器的配置没有特殊要求，购买时选择最基本配置即可。  
>-   弹性云服务器的购买方式有“包周期”与“按需”，若只参考本例进行DevCloud体验，可选择“按需购买”方式，在体验之后将弹性云服务器删除，避免产生不必要的费用。  

## **项目过程**<a name="section6867945915"></a>

DevCloud基本操作流程请参考[快速上手DevCloud](https://support.huaweicloud.com/qs-devcloud/devcloud_qs_1000.html)。

本例中将依次进行以下步骤：

1.  [创建项目、进行项目规划](基于C++的客户端应用开发-创建项目-进行项目规划.md)
2.  [创建代码仓库、管理项目代码](基于C++的客户端应用开发-创建代码仓库-管理项目代码.md)
3.  [构建并归档软件包](基于C++的客户端应用开发-构建并归档软件包.md)
4.  [部署软件包至云主机](基于C++的客户端应用开发-部署软件包至云主机.md)

