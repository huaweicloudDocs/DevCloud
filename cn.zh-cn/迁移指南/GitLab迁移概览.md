# **GitLab迁移概览**<a name="devcloud_migration_0001"></a>

本文主要介绍由GitLab向[软件开发平台DevCloud](https://www.huaweicloud.com/devcloud/)迁移的方案建议与操作指导。

GitLab是一个基于Git的、开源的、Web端代码管理工具。企业在公网或内网搭建GitLab服务器，研发团队成员使用Git终端工具与服务器进行交互操作。

迁移的目标代码托管平台DevCloud[代码托管服务](https://www.huaweicloud.com/product/codehub.html)（下文统称为CodeHub ）。CodeHub是基于Git的在线代码托管服务，是具备安全管控、成员/权限管理、分支保护/合并、在线编辑、统计服务等功能的云端代码仓库。使用代码托管服务，可以解决软件开发者在跨地域协同、多分支并发、代码版本管理、安全性等方面遇到的问题。

下表中列出了GitLab与DevCloud研发管理功能对照。

<a name="table98331417452"></a>
<table><thead align="left"><tr id="row3842143454"><th class="cellrowborder" colspan="2" valign="top" id="mcps1.1.6.1.1"><p id="p178416146455"><a name="p178416146455"></a><a name="p178416146455"></a><strong id="b1429702318345"><a name="b1429702318345"></a><a name="b1429702318345"></a>GitLab常见功能点</strong></p>
</th>
<th class="cellrowborder" valign="top" id="mcps1.1.6.1.2"><p id="p18843144453"><a name="p18843144453"></a><a name="p18843144453"></a><strong id="b3313182312340"><a name="b3313182312340"></a><a name="b3313182312340"></a>DevCloud对应功能点</strong></p>
</th>
<th class="cellrowborder" valign="top" id="mcps1.1.6.1.3"><p id="p38461494511"><a name="p38461494511"></a><a name="p38461494511"></a><strong id="b163341223183416"><a name="b163341223183416"></a><a name="b163341223183416"></a>能否迁移</strong></p>
</th>
<th class="cellrowborder" valign="top" id="mcps1.1.6.1.4"><p id="p28417144451"><a name="p28417144451"></a><a name="p28417144451"></a><strong id="b6335102313341"><a name="b6335102313341"></a><a name="b6335102313341"></a>DevCloud详细描述</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row208415146451"><td class="cellrowborder" rowspan="3" valign="top" width="10%" headers="mcps1.1.6.1.1 "><p id="p13840142457"><a name="p13840142457"></a><a name="p13840142457"></a>项目管理</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.1.6.1.1 "><p id="p9859144944617"><a name="p9859144944617"></a><a name="p9859144944617"></a>群组</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.1.6.1.2 "><p id="p38441424513"><a name="p38441424513"></a><a name="p38441424513"></a>项目</p>
</td>
<td class="cellrowborder" valign="top" width="10%" headers="mcps1.1.6.1.3 "><p id="p7841214114518"><a name="p7841214114518"></a><a name="p7841214114518"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.6.1.4 "><p id="p18841714204514"><a name="p18841714204514"></a><a name="p18841714204514"></a>项目是DevCloud管理的基本单位，一个项目可以包含多个代码仓库。</p>
</td>
</tr>
<tr id="row1784161410451"><td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p14859174914460"><a name="p14859174914460"></a><a name="p14859174914460"></a>子群组</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p88421474520"><a name="p88421474520"></a><a name="p88421474520"></a>不涉及</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.2 "><p id="p188491418458"><a name="p188491418458"></a><a name="p188491418458"></a>×</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.3 "><p id="p108481454513"><a name="p108481454513"></a><a name="p108481454513"></a>无。</p>
</td>
</tr>
<tr id="row1184111416456"><td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p685916495469"><a name="p685916495469"></a><a name="p685916495469"></a>项目仓库</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p11845146457"><a name="p11845146457"></a><a name="p11845146457"></a>代码仓库</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.2 "><p id="p108418142459"><a name="p108418142459"></a><a name="p108418142459"></a>√</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.3 "><p id="p9841814114516"><a name="p9841814114516"></a><a name="p9841814114516"></a>可以为DevCloud新建项目创建多个代码仓库。</p>
</td>
</tr>
<tr id="row148471454512"><td class="cellrowborder" rowspan="2" valign="top" width="10%" headers="mcps1.1.6.1.1 "><p id="p98421484511"><a name="p98421484511"></a><a name="p98421484511"></a>角色管理</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.1.6.1.1 "><p id="p1859164914463"><a name="p1859164914463"></a><a name="p1859164914463"></a>群组成员</p>
</td>
<td class="cellrowborder" valign="top" width="15%" headers="mcps1.1.6.1.2 "><p id="p4841714124512"><a name="p4841714124512"></a><a name="p4841714124512"></a>项目成员</p>
</td>
<td class="cellrowborder" valign="top" width="10%" headers="mcps1.1.6.1.3 "><p id="p1984101413450"><a name="p1984101413450"></a><a name="p1984101413450"></a>√</p>
</td>
<td class="cellrowborder" valign="top" width="50%" headers="mcps1.1.6.1.4 "><p id="p573919455445"><a name="p573919455445"></a><a name="p573919455445"></a>DevCloud项目成员默认分为七种角色，也可以根据项目需求自定义角色。</p>
</td>
</tr>
<tr id="row178414147456"><td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p1986010496461"><a name="p1986010496461"></a><a name="p1986010496461"></a>项目成员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.1 "><p id="p168431464517"><a name="p168431464517"></a><a name="p168431464517"></a>仓库成员</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.2 "><p id="p1784114124519"><a name="p1784114124519"></a><a name="p1784114124519"></a>√</p>
</td>
<td class="cellrowborder" valign="top" headers="mcps1.1.6.1.3 "><p id="p11841614194513"><a name="p11841614194513"></a><a name="p11841614194513"></a>DevCloud仓库成员分为三种，与项目成员角色进行对应。</p>
</td>
</tr>
</tbody>
</table>

## **GitLab研发场景介绍**<a name="section744493042910"></a>

企业在开展一个新项目时，一般由技术经理/架构师先完成项目架构，包括在GitLab服务器中新建仓库、设置成员角色，并上传架构代码到服务器，然后由研发人员拉取架构代码，在此基础上进行功能开发。

![](figures/GitLabRepoMigration_001_Workflow.png)

## **迁移场景介绍**<a name="section10358125816543"></a>

企业准备迁移时可能处于三种研发阶段：

-   新项目开始 ：此场景无存量代码，不涉及已有代码库迁移，是在DevCloud中新建项目以及仓库，进行各种研发操作，推荐阅读[项目成员迁移](GitLab迁移-项目成员迁移.md)和[代码分支迁移](代码分支迁移.md)。
-   项目研发过程中：此场景中有部分代码，不但包括已有代码迁移，也包括对分支的操作，推荐阅读[项目成员迁移](GitLab迁移-项目成员迁移.md)、[已有代码迁移](GitLab迁移-已有代码迁移.md)、[代码分支迁移](代码分支迁移.md)。
-   项目完成后：此场景有完整的代码，只是将DevCloud平台作为归档代码的迁移备份，推荐阅读[项目成员迁移](GitLab迁移-项目成员迁移.md)和[已有代码迁移](GitLab迁移-已有代码迁移.md)。

## **迁移前准备**<a name="section1558104283716"></a>

-   **帐号申请**：使用软件开发平台DevCloud前，请确保您已拥有已实名认证的华为云帐号；若您还没有华为云帐号，请先注册，并完成实名认证。
-   **Git客户端安装**：DevCloud代码托管服务支持与常用的Git终端工具交互，如Git Bash、TortoiseGit、EGit，Sourcetree等，您选择一个熟悉的工具安装即可。

