# **工作项迁移**<a name="devcloud_migration_0016"></a>

## **问题类型迁移**<a name="section26811455114616"></a>

JIRA平台和DevCloud平台都将工作项分为不同的类型，用于区分不同大小的产品需求或缺陷。

-   **JIRA问题类型**

    JIRA可以用于跟踪许多不同类型的问题，也可以自定义问题类型，本文迁移的项目采用的是JIRA默认的问题类型：JIRA**普通问题类型**是指可以直接创建的问题类型，包括Epic、故事、任务、故障；**子任务类型**不能单独创建，需要在普通问题类型中创建。

    JIRA问题类型查看方式如下：

    -   使用管理员账号登录JIRA平台，在“问题  \>  问题类型方案“页面中查看项目采用的所有问题类型方案。
    -   普通用户账号进入待迁移的项目，单击页面左下角“项目设置“，在“问题类型“页面获取对应信息。

    ![](figures/JIRAProjectMigration_009_IssueType.png)

-   **DevCloud工作项类型**

    DevCloud的Scrum项目类型中采用的是标准的Scrum开发框架，工作项层级划分为Epic\>Feature\>Story\>Task&Bug。

    <a name="table191612332459"></a>
    <table><thead align="left"><tr id="row12916153320456"><th class="cellrowborder" valign="top" width="20%" id="mcps1.1.3.1.1"><p id="p89161339457"><a name="p89161339457"></a><a name="p89161339457"></a><strong id="b13198204134511"><a name="b13198204134511"></a><a name="b13198204134511"></a>工作项类型</strong></p>
    </th>
    <th class="cellrowborder" valign="top" width="80%" id="mcps1.1.3.1.2"><p id="p091623394513"><a name="p091623394513"></a><a name="p091623394513"></a><strong id="b193283034611"><a name="b193283034611"></a><a name="b193283034611"></a>类型说明</strong></p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row109166337455"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.3.1.1 "><p id="p109167335456"><a name="p109167335456"></a><a name="p109167335456"></a>Epic</p>
    </td>
    <td class="cellrowborder" valign="top" width="80%" headers="mcps1.1.3.1.2 "><p id="p19171533164518"><a name="p19171533164518"></a><a name="p19171533164518"></a>描述了旨在帮助最终用户解决商业与技术问题的一系列活动（activities）或者一个工作流（workflow）。对于规模和复杂性非常大的产品，可以拆分成多个Epic。Epic较大，一般无法或者不容易估算工作量。</p>
    </td>
    </tr>
    <tr id="row1091723394510"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.3.1.1 "><p id="p6917833184513"><a name="p6917833184513"></a><a name="p6917833184513"></a>Feature</p>
    </td>
    <td class="cellrowborder" valign="top" width="80%" headers="mcps1.1.3.1.2 "><p id="p4917113334518"><a name="p4917113334518"></a><a name="p4917113334518"></a>产品功能，代表产品的某个特性，可以做什么，可以提供什么服务。</p>
    </td>
    </tr>
    <tr id="row991717333455"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.3.1.1 "><p id="p12917123324518"><a name="p12917123324518"></a><a name="p12917123324518"></a>Story</p>
    </td>
    <td class="cellrowborder" valign="top" width="80%" headers="mcps1.1.3.1.2 "><p id="p9917183315456"><a name="p9917183315456"></a><a name="p9917183315456"></a>User Story的缩写，是从用户角度对产品需求的详细描述，更小粒度的功能。在项目开始初期，将Epic细化成带有优先级的Story列表，称为Product Backlog。</p>
    </td>
    </tr>
    <tr id="row491743320458"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.3.1.1 "><p id="p179175331454"><a name="p179175331454"></a><a name="p179175331454"></a>Task</p>
    </td>
    <td class="cellrowborder" valign="top" width="80%" headers="mcps1.1.3.1.2 "><p id="p139171933114520"><a name="p139171933114520"></a><a name="p139171933114520"></a>将一个Story划分成更小的单元，便于每天跟踪工作进度。</p>
    </td>
    </tr>
    <tr id="row1491793344518"><td class="cellrowborder" valign="top" width="20%" headers="mcps1.1.3.1.1 "><p id="p18917173334513"><a name="p18917173334513"></a><a name="p18917173334513"></a>Bug</p>
    </td>
    <td class="cellrowborder" valign="top" width="80%" headers="mcps1.1.3.1.2 "><p id="p0917183354519"><a name="p0917183354519"></a><a name="p0917183354519"></a>产品缺陷，既可以是Story的子工作项，便于追溯。也可以不属于某一个功能，独立存在。</p>
    </td>
    </tr>
    </tbody>
    </table>

-   **JIRA问题类型与DevCloud工作项类型的映射**

    <a name="table169116377499"></a>
    <table><thead align="left"><tr id="row126921737174918"><th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.1"><p id="p1269212377494"><a name="p1269212377494"></a><a name="p1269212377494"></a><strong id="b4692143724911"><a name="b4692143724911"></a><a name="b4692143724911"></a>JIRA问题类型</strong></p>
    </th>
    <th class="cellrowborder" valign="top" width="50%" id="mcps1.1.3.1.2"><p id="p19692173704910"><a name="p19692173704910"></a><a name="p19692173704910"></a><strong id="b18692203713494"><a name="b18692203713494"></a><a name="b18692203713494"></a>对应DevCloud问题类型</strong></p>
    </th>
    </tr>
    </thead>
    <tbody><tr id="row17692637174916"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p126921337174918"><a name="p126921337174918"></a><a name="p126921337174918"></a>Epic</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p17692203734911"><a name="p17692203734911"></a><a name="p17692203734911"></a>Epic</p>
    </td>
    </tr>
    <tr id="row669217371490"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p18692153712493"><a name="p18692153712493"></a><a name="p18692153712493"></a>Epic子任务</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p18692143774918"><a name="p18692143774918"></a><a name="p18692143774918"></a>Feature</p>
    </td>
    </tr>
    <tr id="row66925374498"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p19692153713499"><a name="p19692153713499"></a><a name="p19692153713499"></a>故事</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p16692437174913"><a name="p16692437174913"></a><a name="p16692437174913"></a>Story</p>
    </td>
    </tr>
    <tr id="row46921637134916"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p18692737154911"><a name="p18692737154911"></a><a name="p18692737154911"></a>故事的子任务</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p14692937204920"><a name="p14692937204920"></a><a name="p14692937204920"></a>Task</p>
    </td>
    </tr>
    <tr id="row6692143714490"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p56921037104911"><a name="p56921037104911"></a><a name="p56921037104911"></a>任务</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p166928376491"><a name="p166928376491"></a><a name="p166928376491"></a>Task</p>
    </td>
    </tr>
    <tr id="row18692037134920"><td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.1 "><p id="p11692173717492"><a name="p11692173717492"></a><a name="p11692173717492"></a>故障</p>
    </td>
    <td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.3.1.2 "><p id="p369212372491"><a name="p369212372491"></a><a name="p369212372491"></a>Bug</p>
    </td>
    </tr>
    </tbody>
    </table>


## **工作流迁移**<a name="section118211452144818"></a>

JIRA平台和DevCloud平台中，不同类型的工作项可以有拥有属于自己的工作流，包括工作项状态和状态流转规则。

1.  **获取JIRA工作流**

    普通用户账号进入待迁移的项目，单击页面左下角“项目设置“，在“工作流“页面可单击不同问题类型过去相应的工作流。

    例如，下图是一个**Bug Workflow**，定义了**故障**问题类型工作流的状态和状态流转。

    ![](figures/JIRAProjectMigration_011_BugWorkflow.png)

2.  **创建DevCloud工作流**
    1.  进入DevCloud已创建的项目，在“设置  \>  项目设置  \>  Bug设置  \>  状态流转  \>  状态管理“中，按照JIRA中故障的状态创建Bug类型工作项的状态。
    2.  在“流转方向“页签中按照JIRA中故障的状态流转方向设置Bug类型工作项的状态流转方向。

        ![](figures/JIRAProjectMigration_012_NewState.png)



## **模块迁移**<a name="section1231020414495"></a>

1.  **获取JIRA模块**

    普通用户账号进入待迁移的项目，单击页面左侧“模块“，获取模块相关信息。

    ![](figures/JIRAProjectMigration_014_SrcModule.png)

2.  **创建DevCloud模块**

    进入DevCloud已创建的项目，在“设置  \>  项目设置  \>  模块设置“页面单击角“添加“，根据JIRA中的模块设置添加新模块和负责人。

    ![](figures/JIRAProjectMigration_015_DstModule.png)


## **工作项内容迁移**<a name="section18743815154912"></a>

1.  **导出JIRA工作项**

    1.  登录JIRA平台进入待迁移的项目，单击右上角**““**“显示所有问题和筛选器“**““**进入“筛选器“界面。
    2.  在“导出“下拉框中选择“CSV（所有域）“。

        ![](figures/JIRAProjectMigration_016_BacklogExport.png)

    >![](public_sys-resources/icon-note.gif) **说明：** 
    >若导出的CSV文件内容显示乱码，请参考以下步骤解决。
    >1.  用记事本打开CSV文件，选择另存为，编码格式由UTF-8更改为ANSI格式，保存。
    >2.  新建一个EXCEL空文件，在目录中选择“数据  \>  自文本“，选择刚更改完成编码格式的CSV文件，分隔符号设置（与保存时的分隔符相同）。

2.  **导出DevCloud工作项模板**

    进入DevCloud已创建的项目，在“工作  \>  工作项“中，单击页面右上角“更多操作  \>  导入“，在弹框中单击“下载模板“。

    ![](figures/JIRAProjectMigration_017_DownloadTemp.png)

3.  **填充DevCloud工作项模板**
    1.  自定义DevCloud工作项字段

        对比JIRA工作项列表与DevCloud工作项模板，当DevCloud工作项（如**Bug**问题类型）的字段不满足JIRA原有需求时，需要在DevCloud中添加缺少的字段。

        在“设置  \>  项目设置  \>  Bug设置  \>  字段与模板“页面，单击右上角“编辑模板“，在新界面单击右上角“新建字段“，根据JIRA工作项字段进行添加。

        新增字段后，在下载的模板中手动添加相应的字段列。

        ![](figures/JIRAProjectMigration_018_NewWord.png)

    2.  定义工作项字段取值域

        JIRA和DevCloud中相同的字段（如**优先级**字段）可能取值阈不同。JIRA平台**优先级**字段的取值域是Highest、High、Medium、Low、Lowest；DevCloud平台**优先级**字段的取值域为高、中、低。

        -   方法1：取值归类匹配：Highest/High\>高，Medium\>中，Lowest/Low\>低。
        -   方法2：增加新字段，如命名为**优先权限**（由于DevCloud中的“优先级”字段无法删除，所以取别名代替），并添加Highest，High，Medium，Low，Lowest取值域

    3.  内容迁移：将JIRA的字段信息拷贝至DevCloud模板对应列中。

4.  **导入DevCloud工作项**
    1.  返回工作项页面，单击“更多操作  \>  导入“，选择编辑好的EXCEL文件，单击“导入“。
    2.  关联工作项

        JIRA平台中通过**问题ID**和**父级ID**字段记录了父子关系。

        在DevCloud平台中，找到子工作项，编辑“父工作项“字段，根据JIRA中记录的父子关系，选择相应的父工作项。



