# 项目介绍<a name="devcloud_qs_0601"></a>

## 文档目的<a name="section16381121019282"></a>

本章节通过示例项目“音频解析器”介绍如何使用DevCloud开发基于C++语言的客户端应用。

## 项目详情<a name="section225901918283"></a>

-   项目名称：音频解析器。
-   项目简介：音频采样器是一个C++应用程序，它可以从MP3、WAV、FLAC或Ogg Vorbis格式的音频文件中生成波形数据，波形数据可用于生成音频的可视化呈现，外观类似于音频编辑应用程序；除此之外，该应用程序还可以进行音频格式转换等功能，为音频处理者提供多种服务。

    ![](figures/C++-产品页面展示.png)

      

-   构建环境：Ubuntu 16.04+GNU 5.4.0+Cmake3.5.1。
-   部署环境：Ubuntu 16.04。
-   华为云服务：
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
        -   [容器镜像服务SWR](https://www.huaweicloud.com/product/swr.html)
        -   [弹性云服务器ECS](https://www.huaweicloud.com/product/ecs.html)



## 项目过程<a name="section6867945915"></a>

DevCloud基本操作流程请参考[软件开发平台使用流程](zh-cn_topic_0110467970.md)。

本示例中将依次进行以下步骤：

1.  [准备工作](zh-cn_topic_0268298501.md)
2.  [步骤一：管理项目规划](C++-管理项目规划.md)
3.  [步骤二：管理项目代码](C++-管理项目代码.md)
4.  [步骤三：静态代码扫描](zh-cn_topic_0261083606.md)
5.  [步骤四：构建并归档软件包](C++-构建并归档软件包.md)
6.  [步骤五：部署软件包至云主机](C++-部署软件包至云主机.md)
7.  [步骤六：流水线实现持续交付](zh-cn_topic_0261083607.md)
8.  [释放资源](zh-cn_topic_0268298524.md)

  

