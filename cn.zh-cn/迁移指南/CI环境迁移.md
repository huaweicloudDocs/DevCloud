# **CI环境迁移**<a name="devcloud_migration_0010"></a>

## **CI环境介绍**<a name="section617215583119"></a>

企业在对项目代码进行构建之前，需要根据项目语言，建立一个可以进行编译构建的Runner环境，这个Runner注册在该项目下，负责从GitLab代码托管中拉取代码，并根据工程文件“.gitlab-ci.yml“中的配置，执行相应的动作。

![](figures/GitLabCICDMigration_001_RunnerEnv.png)

## **GitLab与DevCloud CI环境对照**<a name="section20664530194415"></a>

下表中列出了GitLab Runner与DevCloud CI环境的对照。

<a name="table19485195543513"></a>
<table><thead align="left"><tr id="row4485195593518"><th class="cellrowborder" valign="top" width="10%" id="mcps1.1.6.1.1"><p id="p1048515514358"><a name="p1048515514358"></a><a name="p1048515514358"></a><strong id="b13792128363"><a name="b13792128363"></a><a name="b13792128363"></a>迁移示例项目</strong></p>
</th>
<th class="cellrowborder" valign="top" width="10%" id="mcps1.1.6.1.2"><p id="p104854552358"><a name="p104854552358"></a><a name="p104854552358"></a><strong id="b15649551143619"><a name="b15649551143619"></a><a name="b15649551143619"></a>GitLab Runner环境</strong></p>
</th>
<th class="cellrowborder" valign="top" width="30%" id="mcps1.1.6.1.3"><p id="p134861955133517"><a name="p134861955133517"></a><a name="p134861955133517"></a><strong id="b665375118367"><a name="b665375118367"></a><a name="b665375118367"></a>GitLab Runner详细描述</strong></p>
</th>
<th class="cellrowborder" valign="top" width="20%" id="mcps1.1.6.1.4"><p id="p1948635523510"><a name="p1948635523510"></a><a name="p1948635523510"></a><strong id="b8653951183611"><a name="b8653951183611"></a><a name="b8653951183611"></a>DevCloud构建环境</strong></p>
</th>
<th class="cellrowborder" valign="top" width="30%" id="mcps1.1.6.1.5"><p id="p84868557356"><a name="p84868557356"></a><a name="p84868557356"></a><strong id="b6654951173612"><a name="b6654951173612"></a><a name="b6654951173612"></a>DevCloud详细描述</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row18486195573510"><td class="cellrowborder" rowspan="3" valign="top" width="10%" headers="mcps1.1.6.1.1 "><p id="p17486115514355"><a name="p17486115514355"></a><a name="p17486115514355"></a>Java项目</p>
</td>
<td class="cellrowborder" valign="top" width="10%" headers="mcps1.1.6.1.2 "><p id="p16486145511355"><a name="p16486145511355"></a><a name="p16486145511355"></a>Linux操作系统</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="30%" headers="mcps1.1.6.1.3 "><p id="p64861255193515"><a name="p64861255193515"></a><a name="p64861255193515"></a>GitLab Runner构建环境是项目组自行搭建的，Runner可能运行在一台服务器中，也可能运行在容器中，这是由项目组来决定的。</p>
</td>
<td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.6.1.4 "><p id="p174861455203515"><a name="p174861455203515"></a><a name="p174861455203515"></a>maven3.5.3-jdk8-open</p>
</td>
<td class="cellrowborder" rowspan="3" valign="top" width="30%" headers="mcps1.1.6.1.5 "><p id="p1486175563512"><a name="p1486175563512"></a><a name="p1486175563512"></a>DevCloud的编译构建服务，提供了云端构建环境，无需搭建，提供了22种系统集成环境，包括Maven，Gradle等。</p>
</td>
</tr>
<tr id="row1948645573519"><td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p16486105553514"><a name="p16486105553514"></a><a name="p16486105553514"></a>JDK</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.2 "><p id="p1948695543519"><a name="p1948695543519"></a><a name="p1948695543519"></a>maven3.5.3-jdk7</p>
</td>
</tr>
<tr id="row94861355123512"><td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p94866555352"><a name="p94866555352"></a><a name="p94866555352"></a>Maven</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.2 "><p id="p348605523512"><a name="p348605523512"></a><a name="p348605523512"></a>maven3.6.1-jdk10</p>
</td>
</tr>
</tbody>
</table>

## **CI环境迁移流程**<a name="section1969133719115"></a>

CI环境迁移包括以下两个步骤：

-   [步骤一：获取GitLab Runner环境](#section96451434131312)

    Runner环境迁移需要首先了解Runner已有的操作系统、软件以及版本信息。

-   [步骤二：创建DevCloud构建任务，完成云构建环境和工具版本选择](#section58678201410)

    在DevCloud服务中创建构建任务，并选择模板和工具版本，即可实时使用匹配的云构建环境。


## **步骤一：获取GitLab Runner环境**<a name="section96451434131312"></a>

1.  进入GitLab待迁移的工程，在“Settings  \>  CI/CD“下展开Runners项，点击已经注册的Runner查看详细信息。
2.  获取GitLab Runner安装地址，查看操作系统等详细信息。

    ![](figures/GitLabCICDMigration_003_RunnerInfo.png)

3.  登录GitLab Runner服务器，进入Runner容器实例，在maven安装文件夹中通过命令**java -version**及**mvn --version**查看jdk及maven版本信息。

    本文案例使用的版本为：jdk1.8.0，maven3.5.3。

    ![](figures/GitLabCICDMigration_004_RunnerMaven.png)


## **步骤二：创建DevCloud构建任务，完成云构建环境和工具版本选择**<a name="section58678201410"></a>

1.  进入已经创建好的DevCloud项目中，在“构建&发布  \>  编译构建“页面单击“新建任务“，输入任务名称，单击“下一步“。
2.  源码源选择“DevCloud“，源码仓库选择在CodeHub中创建的仓库，分支选择“master“，单击“下一步“。
3.  构建模板选择“Maven“，单击“确定“，系统将自动跳转至“构建步骤“页面。

    >![](public_sys-resources/icon-note.gif) **说明：** 
    >系统通常会根据工程代码的文件推荐合适的模板。
    >若推荐模板不适用，可在系统模板中选择需要使用的构建模板；或选择“不使用模板，直接创建“，根据需要选择并配置构建步骤。

4.  编辑构建步骤“Maven构建“：根据GitLab Runner中的配置，选择合适的**工具版本**，单击“新建“，完成任务创建。

    ![](figures/GitLabCICDMigration_008_DevcloudCIVersion.png)


