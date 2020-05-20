# **项目成员迁移**<a name="devcloud_migration_0006"></a>

## **迁移流程**<a name="section346110208281"></a>

项目成员迁移包括以下四个步骤：

-   [步骤一：获取SVN角色信息](#section15423192204911)

    从SVN中导出已有的用户信息。

-   [步骤二：创建项目](#section149687147492)

    在DevCloud中创建用于成员管理的项目，并添加项目成员。

-   [步骤三：为项目成员分配角色](#section388293011259)

    参照SVN中的角色，在DevCloud中为成员设置相应的角色。

-   [步骤四：创建代码仓库](#section480644834912)

    创建用于存放代码的空白仓库，并添加仓库成员。


## **步骤一：获取SVN角色信息**<a name="section15423192204911"></a>

1.  进入SVN服务器相应配置目录（本文为“/var/svnrepos/DevOpsOnDevCloud/conf“），查看passwd文件，获取相应用户名、密码等信息。

    ![](figures/SVNRepoMigration_002.png)

      

2.  进入SVN服务器相应配置目录（本文为“/var/svnrepos/DevOpsOnDevCloud/conf“），查看authz文件，获取该SVN服务器下相应用户组权限设置信息。

    ![](figures/SVNRepoMigration_003.png)

      


## **步骤二：创建项目**<a name="section149687147492"></a>

1.  使用华为云账号登录[DevCloud](https://devcloud.cn-north-4.huaweicloud.com/home)。
2.  在页面左上角根据您业务所在区域就近选择区域，可减少网络时延，提高访问速度；不同区域之间互不相通。

    例如您当前在北京，区域可以就近选择“华北-北京四“。

    ![](figures/SVNRepoMigration_004.png)

      

3.  单击页面右上角“新建项目“，创建新的项目。DevCloud支持Scrum和看板两种项目类型，建议选择看板项目。
4.  项目创建成功后，会直接跳转到“成员管理“界面中添加成员。

    -   如果“本企业用户“下已有需要添加的用户，直接勾选账号添加即可。
    -   如果还没有成员，则单击右上角“创建用户“跳转到统一身份认证服务IAM中，根据GitLab导出的用户进行创建。创建方法请参见[创建IAM用户](https://support.huaweicloud.com/usermanual-iam/iam_02_0001.html)。

    ![](figures/SVNRepoMigration_006.png)

      

    也可以后续通过“设置  \>  通用设置  \>  成员管理“页面添加成员。

    ![](figures/SVNRepoMigration_007.png)

      

    >![](public_sys-resources/icon-note.gif) **说明：**   
    >-   当项目中的成员数量小于等于5人时，不收取费用；当超过5人后，需要购买套餐才可以继续使用，套餐请参见[产品价格详情](https://www.huaweicloud.com/pricing.html?tab=detail#/devcloud)。  
    >-   新账号创建看板项目成功后，会看到弹框提示输入真实姓名，需完成此设置后才能添加项目成员。  


## **步骤三：为项目成员分配角色**<a name="section388293011259"></a>

DevCloud中每添加一个成员，都需为其配置一个项目角色，每个项目角色对应不同的代码仓库权限，从而实现基于角色的隔离权限。

SVN中通过设置User、Group来做权限管理，User对应DevCloud的项目成员，Group对应DevCloud的项目角色，根据角色权限，建议角色对应关系如下表所示。DevCloud中角色设置方法请参见[设置项目角色](https://support.huaweicloud.com/usermanual-projectman/devcloud_hlp_00026.html#section8)。

<a name="table1127719124361"></a>
<table><thead align="left"><tr id="row22779120369"><th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.1"><p id="p5278912153615"><a name="p5278912153615"></a><a name="p5278912153615"></a><strong id="b203146206"><a name="b203146206"></a><a name="b203146206"></a>SVN角色</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.2"><p id="p0278181215362"><a name="p0278181215362"></a><a name="p0278181215362"></a><strong id="b115841201"><a name="b115841201"></a><a name="b115841201"></a>DevCloud项目角色</strong></p>
</th>
<th class="cellrowborder" valign="top" width="33.33333333333333%" id="mcps1.1.4.1.3"><p id="p1127841216367"><a name="p1127841216367"></a><a name="p1127841216367"></a><strong id="b731042201"><a name="b731042201"></a><a name="b731042201"></a>DevCloud代码仓库角色</strong></p>
</th>
</tr>
</thead>
<tbody><tr id="row15278181214363"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.1 "><p id="p2021154015366"><a name="p2021154015366"></a><a name="p2021154015366"></a>SVN仓库管理员</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.2 "><p id="p827801293614"><a name="p827801293614"></a><a name="p827801293614"></a>项目创建者/项目经理</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p1727841263613"><a name="p1727841263613"></a><a name="p1727841263613"></a>仓库管理员</p>
</td>
</tr>
<tr id="row638252503613"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.1 "><p id="p19382182503614"><a name="p19382182503614"></a><a name="p19382182503614"></a>读写权限人员</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.2 "><p id="p6382182583618"><a name="p6382182583618"></a><a name="p6382182583618"></a>开发人员</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p9382125123615"><a name="p9382125123615"></a><a name="p9382125123615"></a>仓库普通成员</p>
</td>
</tr>
<tr id="row18278121223612"><td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.1 "><p id="p1827861223618"><a name="p1827861223618"></a><a name="p1827861223618"></a>只读权限人员</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.2 "><p id="p4278412143616"><a name="p4278412143616"></a><a name="p4278412143616"></a>测试经理、测试人员、浏览者、参与者</p>
</td>
<td class="cellrowborder" valign="top" width="33.33333333333333%" headers="mcps1.1.4.1.3 "><p id="p5278131283613"><a name="p5278131283613"></a><a name="p5278131283613"></a>仓库浏览者</p>
</td>
</tr>
</tbody>
</table>

## **步骤四：创建代码仓库**<a name="section480644834912"></a>

完成项目创建后，请为项目创建代码仓库，用于存放代码。

1.  进入项目，单击页面上方导航“代码  \>  代码托管“，进入代码托管服务。
2.  单击右上角“普通新建“按钮，输入代码仓库名称单击“确定“保存。
3.  单击仓库名称进入代码仓库，选择“成员列表“页签，。

    单击“添加成员“，根据SVN中的设置勾选仓库成员，单击“确定“保存。

    ![](figures/SVNRepoMigration_009.png)

      

4.  设置仓库角色：

    项目成员加入代码仓库时，项目角色与仓库角色的映射关系、以及三种仓库角色的操作权限请参考[代码托管-基础角色权限](https://support.huaweicloud.com/usermanual-codehub/codehub_hlp_0005.html#section0)。

    单击![](figures/icon-设为管理员.png)可以将仓库普通成员升级为仓库管理员，单击![](figures/icon-设为普通成员.png)可以将仓库管理员降级为仓库普通成员，单击![](figures/icon-移出成员.png)可以删除仓库成员。

    ![](figures/SVNRepoMigration_010.png)


  

