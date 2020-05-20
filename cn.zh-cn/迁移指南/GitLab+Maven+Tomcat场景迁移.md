# **GitLab+Maven+Tomcat场景迁移**<a name="devcloud_migration_0019"></a>

本节介绍的迁移场景为：

-   编程语言：Java。
-   源码托管在GitLab私有库中。
-   Jenkins任务使用Maven构建工具。
-   运行在Jenkins服务器的Linux节点。
-   部署目标机需要提前安装Tomcat环境。

![](figures/Jenkins_Maven_001.png)

本节中各迁移步骤涉及到的服务及功能如下表所示：

<a name="table17414202975516"></a>
<table><thead align="left"><tr id="row3414162920552"><th class="cellrowborder" valign="top" width="33.333333333333336%" id="mcps1.1.4.1.1"><p id="p6414112912555"><a name="p6414112912555"></a><a name="p6414112912555"></a><strong id="b5296123011517"><a name="b5296123011517"></a><a name="b5296123011517"></a>迁移步骤</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.29332933293329%" id="mcps1.1.4.1.2"><p id="p1541432955518"><a name="p1541432955518"></a><a name="p1541432955518"></a><strong id="b03001930121514"><a name="b03001930121514"></a><a name="b03001930121514"></a>Jenkins</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.373337333733375%" id="mcps1.1.4.1.3"><p id="p2414329135511"><a name="p2414329135511"></a><a name="p2414329135511"></a><strong id="b12303113018155"><a name="b12303113018155"></a><a name="b12303113018155"></a>DevCloud</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row1141422910559"><td class="cellrowborder" valign="top" width="33.333333333333336%" headers="mcps1.1.4.1.1 "><p id="p341412965510"><a name="p341412965510"></a><a name="p341412965510"></a>步骤一：源码管理迁移</p>
</td>
<td class="cellrowborder" valign="top" width="33.29332933293329%" headers="mcps1.1.4.1.2 "><p id="p1414132955517"><a name="p1414132955517"></a><a name="p1414132955517"></a>GitLab托管</p>
</td>
<td class="cellrowborder" valign="top" width="33.373337333733375%" headers="mcps1.1.4.1.3 "><p id="p1341413297558"><a name="p1341413297558"></a><a name="p1341413297558"></a>DevCloud代码仓库服务托管</p>
</td>
</tr>
<tr id="row34147291552"><td class="cellrowborder" valign="top" width="33.333333333333336%" headers="mcps1.1.4.1.1 "><p id="p94141629155510"><a name="p94141629155510"></a><a name="p94141629155510"></a>步骤二：Maven构建迁移</p>
</td>
<td class="cellrowborder" valign="top" width="33.29332933293329%" headers="mcps1.1.4.1.2 "><p id="p1841413294557"><a name="p1841413294557"></a><a name="p1841413294557"></a>Jenkins的任务中选择Maven构建步骤</p>
</td>
<td class="cellrowborder" valign="top" width="33.373337333733375%" headers="mcps1.1.4.1.3 "><p id="p241414295557"><a name="p241414295557"></a><a name="p241414295557"></a>DevCloud中创建Maven构建任务</p>
</td>
</tr>
<tr id="row12414529135517"><td class="cellrowborder" valign="top" width="33.333333333333336%" headers="mcps1.1.4.1.1 "><p id="p114141293558"><a name="p114141293558"></a><a name="p114141293558"></a>步骤三：构建包迁移</p>
</td>
<td class="cellrowborder" valign="top" width="33.29332933293329%" headers="mcps1.1.4.1.2 "><p id="p2414929115518"><a name="p2414929115518"></a><a name="p2414929115518"></a>软件包发布到Jenkins服务器</p>
</td>
<td class="cellrowborder" valign="top" width="33.373337333733375%" headers="mcps1.1.4.1.3 "><p id="p24144297557"><a name="p24144297557"></a><a name="p24144297557"></a>软件包发布到软件发布库</p>
</td>
</tr>
<tr id="row16414229115513"><td class="cellrowborder" valign="top" width="33.333333333333336%" headers="mcps1.1.4.1.1 "><p id="p94149299559"><a name="p94149299559"></a><a name="p94149299559"></a>步骤四：Tomcat部署迁移</p>
</td>
<td class="cellrowborder" valign="top" width="33.29332933293329%" headers="mcps1.1.4.1.2 "><p id="p16414829155514"><a name="p16414829155514"></a><a name="p16414829155514"></a>SSH部署</p>
</td>
<td class="cellrowborder" valign="top" width="33.373337333733375%" headers="mcps1.1.4.1.3 "><p id="p1941412911554"><a name="p1941412911554"></a><a name="p1941412911554"></a>通过DevCloud提供的原子步骤组合部署</p>
</td>
</tr>
</tbody>
</table>

## **步骤一：源码管理迁移**<a name="section18960143011168"></a>

本节采用代码仓库是自建的GitLab代码仓库，如下图所示：

![](figures/Jenkins_Maven_002.png)

在新进行构建任务迁移前，源码迁移可采取以下两种方式：

-   方式一：GitLab先迁移到DevCloud的CodeHub服务，具体迁移操作请参考[GitLab迁移至DevCloud](GitLab迁移至DevCloud.md)。
-   方式二：通过DevCloud服务接入点迁移。操作方式如下：

    进入DevCloud项目，在“设置  \>  通用设置  \>  服务扩展点管理“页面中单击“新建服务扩展点  \>  通用Git“，在弹出的页面中输入服务扩展点名称、GitLab代码仓库地址、用户名、密码等信息，单击“确定“保存。

    ![](figures/Jenkins_Maven_003.png)

      


本节后续几个步骤基于第二种源码迁移方式。

## **步骤二：Maven构建迁移**<a name="section0171106204813"></a>

本节采用的案例中，Jenkins使用的Maven构建环境配置方式、以及案例中使用的版本信息如下：

<a name="table157989282553"></a>
<table><thead align="left"><tr id="row67981228195517"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.1"><p id="p67989289559"><a name="p67989289559"></a><a name="p67989289559"></a><strong id="b1440893115516"><a name="b1440893115516"></a><a name="b1440893115516"></a>构建环境</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.2"><p id="p127981285553"><a name="p127981285553"></a><a name="p127981285553"></a><strong id="b174091834555"><a name="b174091834555"></a><a name="b174091834555"></a>Jenkins配置路径</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.3"><p id="p11798192820557"><a name="p11798192820557"></a><a name="p11798192820557"></a><strong id="b104261746368"><a name="b104261746368"></a><a name="b104261746368"></a>本文案例使用的版本</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row7798162805510"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.1 "><p id="p8798112820559"><a name="p8798112820559"></a><a name="p8798112820559"></a>Maven</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.2 "><p id="p19798132817558"><a name="p19798132817558"></a><a name="p19798132817558"></a>系统管理 &gt; 全局工具配置 &gt; Maven</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p3701161983613"><a name="p3701161983613"></a><a name="p3701161983613"></a>3.5.3</p>
</td>
</tr>
<tr id="row1779882814554"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.1 "><p id="p4798192818551"><a name="p4798192818551"></a><a name="p4798192818551"></a>JDK</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.2 "><p id="p779814282550"><a name="p779814282550"></a><a name="p779814282550"></a>系统管理 &gt; 全局工具配置 &gt; JDK</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p376117277369"><a name="p376117277369"></a><a name="p376117277369"></a>1.8</p>
</td>
</tr>
</tbody>
</table>

操作步骤如下：

1.  进入DevCloud项目，在“构建&发布  \>  编译构建“页面单击“新建任务“，输入任务名称，单击“下一步“。
2.  源码源选择“通用Git“，Endpoint实例与Repo选择在[步骤一](#section18960143011168)中迁移的仓库，分支选择“master“，单击“下一步“。

    ![](figures/Jenkins_Maven_007.png)

      

3.  构建模板选择“Maven“，单击“确定“，系统将自动跳转至“构建步骤“页签。
4.  编辑构建步骤“Maven构建“：
    -   根据Jenkins中的构建环境，选择相应**工具版本**。
    -   根据Jenkins待迁移任务“Build“页面“Goals and options“命令行，在**命令**窗口输入相应的构建命令。

        ![](figures/Jenkins_Maven_006.png)

          



## **步骤三：构建包迁移**<a name="section108249396163"></a>

Jenkins默认会将构建包存储到本机。DevCloud提供发布仓库服务，可帮助用户进行构建包版本管理。

1.  进入Jenkins待迁移任务，在“构建后操作“页面查看归档路径。

    ![](figures/Jenkins_Maven_011.png)

      

2.  返回DevCloud构建任务，编辑构建步骤“上传软件包到软件发布库“，根据Jenkins设置输入**构建包路径**。

    ![](figures/Jenkins_Maven_012.png)

      

3.  单击“保存并执行“，任务构建成功后，在“构建&发布  \>  发布“页面可搜索到生成的构建包。

## **步骤四：Tomcat部署迁移**<a name="section18367252243"></a>

Jenkins部署过程主要包括：设置部署主机、在部署主机上安装Tomcat并启动。

-   **主机组迁移**
    1.  登录Jenkins，在“系统管理  \>  系统配置“页面，查看“SSH remote hosts“板块信息。

        ![](figures/Jenkins_Maven_004.png)

          

    2.  进入DevCloud项目，在“设置  \>  通用设置  \>  主机组管理“页面单击“新建主机组“，根据页面提示输入必要信息，单击“保存“。
    3.  单击“添加主机“，在弹窗中根据Jenkins设置输入主机信息，单击“添加“保存。

-   **部署任务迁移**

    本节采用的案例中，Jenkins使用的部署环境版本信息如下：

    <a name="table11140205514537"></a>
    <table><thead align="left"><tr id="row17141455125316"><th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.1"><p id="p914155555319"><a name="p914155555319"></a><a name="p914155555319"></a><strong id="b8565415165412"><a name="b8565415165412"></a><a name="b8565415165412"></a>部署环境</strong></p>
    </th>
    <th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.2"><p id="p17141145555312"><a name="p17141145555312"></a><a name="p17141145555312"></a><strong id="b1836564734915"><a name="b1836564734915"></a><a name="b1836564734915"></a>本文案例使用的版本</strong></p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row121411755155318"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p44751397541"><a name="p44751397541"></a><a name="p44751397541"></a>Tomcat</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p547593915411"><a name="p547593915411"></a><a name="p547593915411"></a>8.5.38</p>
    </td>
    </tr>
    <tr id="row31412553531"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p1475193913547"><a name="p1475193913547"></a><a name="p1475193913547"></a>JDK</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p547517398541"><a name="p547517398541"></a><a name="p547517398541"></a>1.8</p>
    </td>
    </tr>
    </tbody>
    </table>

    操作步骤如下：

    1.  进入Jenkins待迁移任务，在“构建后操作“页面查看“Send build artifacts over SSH“版块信息。

        ![](figures/Jenkins_Maven_013.png)

          

    2.  进入DevCloud项目，在“构建&发布  \>  部署“页面单击“新建任务“，输入任务名称，单击“下一步“。
    3.  部署模板选择“Tomcat应用部署“，单击“下一步“，系统将自动跳转至“部署步骤“页面。
    4.  配置部署步骤：

        -   **安装JDK**：选择前面创建的**主机组**，并根据需要选择在主机上安装的**JDK版本**。
        -   **安装Tomcat**：根据需要选择在主机安装的**Tomcat版本**，并根据实际情况修改**http端口**。
        -   **停止Tomcat服务**：输入Tomcat对应的路径。第一次执行停止Tomcat服务的时候，因Tomcat没启动，会提示失败，因此在这里需要勾选“失败后继续执行“。
        -   **选择部署来源**：选择在[步骤三](#section108249396163)构建生成的构建包，参考Jenkins配置“下载到主机的部署目录“。
        -   **启动Tomcat服务**：http端口与步骤“安装Tomcat“保持一致。

        >![](public_sys-resources/icon-note.gif) **说明：**   
        >若在DevCloud部署任务中使用的主机与Jenkins相同，可不执行安装JDK、Tomcat等步骤。  



