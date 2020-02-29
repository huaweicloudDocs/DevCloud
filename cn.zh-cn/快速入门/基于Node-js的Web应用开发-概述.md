# **概述**<a name="devcloud_qs_0401"></a>

## **文档目的**<a name="section7678191414368"></a>

本文通过示例项目“iBlog个人独立博客系统”介绍如何使用DevCloud开发基于Node.js语言的Web应用，为研发Node.js项目的企业或个人提供上云指导。

## **项目详情**<a name="section1412202203617"></a>

-   项目名称：iBlog个人博客系统。
-   项目简介：iBlog是基于Node.js的开源个人博客系统。现代化的 UI 和用户体验。采用响应式布局，支持手机访问，支持离线访问。不仅仅是博客，更是 Demo，是适合新人入门学习的完整项目。

    ![](figures/Node-js-产品页面展示.png)

-   开发语言：node.js。
-   项目类型：使用 Node.js 和 MongoDB 开发的博客系统。
-   部署环境：Linux。
-   功能模块：功能模块、文章列表、文章详情、留言、关于、后台管理。
-   技术构成：

    <a name="table5581121094611"></a>
    <table><tbody><tr id="row105811710154613"><td class="cellrowborder" valign="top" width="25%"><p id="p7581610104616"><a name="p7581610104616"></a><a name="p7581610104616"></a>服务端 Node.js</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p95815107467"><a name="p95815107467"></a><a name="p95815107467"></a>web框架 Express 4</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p458116105462"><a name="p458116105462"></a><a name="p458116105462"></a>模板引擎Pug</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p3581161044619"><a name="p3581161044619"></a><a name="p3581161044619"></a>JS库 jQuery</p>
    </td>
    </tr>
    <tr id="row15814101469"><td class="cellrowborder" valign="top" width="25%"><p id="p1581101010462"><a name="p1581101010462"></a><a name="p1581101010462"></a>Web字体 Font Awesome</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p4581131014613"><a name="p4581131014613"></a><a name="p4581131014613"></a>持久化 MongoDB</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p17581141011466"><a name="p17581141011466"></a><a name="p17581141011466"></a>日志 ServerLog</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p6581101014467"><a name="p6581101014467"></a><a name="p6581101014467"></a>多语言 i18n</p>
    </td>
    </tr>
    <tr id="row35821310194615"><td class="cellrowborder" valign="top" width="25%"><p id="p11978941185011"><a name="p11978941185011"></a><a name="p11978941185011"></a>Service Worker库 Workbox</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p1097884119502"><a name="p1097884119502"></a><a name="p1097884119502"></a>UI库 Bootstrap 3</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p397814118507"><a name="p397814118507"></a><a name="p397814118507"></a>身份验证 Passport</p>
    </td>
    <td class="cellrowborder" valign="top" width="25%"><p id="p125821610134620"><a name="p125821610134620"></a><a name="p125821610134620"></a>-</p>
    </td>
    </tr>
    </tbody>
    </table>


## **前提条件**<a name="section1179533183612"></a>

使用DevCloud开展本例前，需要先进行以下步骤。若已有华为云账号及弹性云服务器，则可忽略。

-   注册华为云账号：在[华为云官网](https://www.huaweicloud.com/)注册华为云账号，并进行实名认证，此账号适用于所有华为云产品。
-   购买弹性云服务器：部署将使用带有公网IP的华为云ECS（本文中使用的操作系统为CentOS 7.4）。ECS的购买方式请参考[购买并登录Linux弹性云服务器](https://support.huaweicloud.com/qs-ecs/zh-cn_topic_0132727313.html)。

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   本例中对弹性云服务器的推荐配置为：2vCPUs|4GB|CentOS 7.4 64bit。  
    >-   弹性云服务器的购买方式有“包周期“与“按需“，若只参考本例进行DevCloud体验，可选择“按需购买”方式，在体验之后将弹性云服务器删除，避免产生不必要的费用。  


## **项目过程**<a name="section845204917528"></a>

DevCloud基本操作流程请参考[快速上手DevCloud](https://support.huaweicloud.com/qs-devcloud/devcloud_qs_1000.html)。

1.  [创建项目、进行项目规划](基于Node-js的Web应用开发-创建项目-进行项目规划.md)
2.  [创建代码仓库、管理项目代码](基于Node-js的Web应用开发-创建代码仓库-管理项目代码.md)
3.  [部署代码至云主机](基于Node-js的Web应用开发-部署代码至云主机.md)
4.  [创建流水线、实现持续交付](基于Node-js的Web应用开发-创建流水线-实现持续交付.md)

  

