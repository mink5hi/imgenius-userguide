# OPC触发器的使用

本文以通过OPC触发器读取OPC服务器上阀门运行次数或电机运行时间的标记点，当运行次数或者运行时间达到设置值时，从而触发imgenius系统自动产生一个维保任务的实际场景为例，配置步骤如下。

## 软件安装

### TOPServer安装


* 点击打开安装文件，点击下一步，按提示安装，如图：

  ![](./images/TOPSERVER安装0.png)
  ![](./images/TOPSERVER安装1.png)

* 选择同意，点击下一步，如图：

  ![](./images/TOPSERVER安装2.png)

* 安装路径、程序存储路径默认即可，点击下一步，如图：

  ![](./images/TOPSERVER安装3.png)
  ![](./images/TOPSERVER安装4.png)
  ![](./images/TOPSERVER安装5.png)
  ![](./images/TOPSERVER安装6.png)

* 安装驱动，点击下一步，如图：

  ![](./images/TOPSERVER安装7.png)
  ![](./images/TOPSERVER安装8.png)

* 一直点击下一步，直至完成，如图：

  ![](./images/TOPSERVER安装9.png)
  ![](./images/TOPSERVER安装10.png)
  ![](./images/TOPSERVER安装11png)
  ![](./images/TOPSERVER安装12.png)
  ![](./images/TOPSERVER安装13.png)

### OPC触发器安装

* 点击打开iDong imgenius Integration Agent V1.2.2安装包文件夹 ，继续打开Redist文件夹，找到Redist\OPC .NET API 2.00 Redistributables 2.00.100目录下的setup.exe安装文件，如图：

  ![](./images/OPC安装0.png)
  ![](./images/OPC安装1.png)

* 点击打开setup.exe安装文件，按提示点击下一步进行安装，直至结束如图：
  ![](./images/OPC安装2.png)
  ![](./images/OPC安装3.png)
  ![](./images/OPC安装4.png)
  ![](./images/OPC安装5.png)
  ![](./images/OPC安装6.png)

* 返回安装包文件夹首页，找到setup.exe安装文件，点击打开并按提示安装直至完成，如图： 
  ![](./images/OPC安装7.png)
  ![](./images/OPC安装8.png)
  ![](./images/OPC安装9.png)
  ![](./images/OPC安装10.png)
  ![](./images/OPC安装11.png)


## imgenius demo解决方案配置

* 新建一个解决方案，包含阀门和电机等资产类别，并且新建1#阀门、2#阀门、3#阀门、1#电机、2#电机、3#电机
  ![](./images/解决方案1.png)
  ![](./images/解决方案2.png)

* 新建一个业务流程
  ![](./images/解决方案3.png)

  > [!warning] 
  > 执行节点必须配置一个流程后函数，主要目的是用于访问Restful服务，从而达到通知作业组活动状态变化的目的
  ![](./images/函数1.png)

* 新建两个作业规范

  ![](./images/解决方案4.png)

* 新建一个维护保养的作业组，并配置可用作业规范，选择上一步发布的两个规范
  ![](./images/解决方案5.png)

## 软件配置

### TOPServer配置

本例以新建6个标记为例：分别是1#阀门运行次数、2#阀门运行次数、3#阀门运行次数、1#电机运行时间、2#电机运行时间、3#电机运行时间

* 点击打开TOP Server配置程序，如图：

  ![](./images/TOPSERVER配置1.png)

* 新建一个通道并命名，此例命名为sim，如图

  ![](./images/TOPSERVER配置2.png)
  ![](./images/TOPSERVER配置3.png) 

* 设备驱动选择Simulator，然后按默认选择点击下一步，直到结束，如图

  ![](./images/TOPSERVER配置4.png)
  ![](./images/TOPSERVER配置5.png) 
  ![](./images/TOPSERVER配置6.png)
  ![](./images/TOPSERVER配置7.png)
  ![](./images/TOPSERVER配置8.png)

* 新建一个设备并命名，此例命名为PLC，然后按默认选择点击下一步，直到结束，如图

  ![](./images/TOPSERVER配置9.png)
  ![](./images/TOPSERVER配置10.png) 
  ![](./images/TOPSERVER配置11.png)
  ![](./images/TOPSERVER配置12.png)
  ![](./images/TOPSERVER配置13.png)
  ![](./images/TOPSERVER配置14.png)

* 新建标记，1#阀门运行次数V001、数据类型均选择长整型，如图

  ![](./images/TOPSERVER配置15.png)
  ![](./images/TOPSERVER配置16.png) 
  

* 重复上一步步骤，分别新建2#阀门运行次数V002、3#阀门运行次数V003、1#电机运行时间M001、2#电机运行时间M002、3#电机运行时间M006，如图
  ![](./images/TOPSERVER配置17.png)

### OPC触发器配置

以上一步TOPserver中新建6个标记1#阀门运行次数V001、2#阀门运行次数V002、3#阀门运行次数V003、1#电机运行时间M001、2#电机运行时间M002、3#电机运行时间M006为例，通过OPC触发器使之与imgenius demo解决方案的设备1#阀门、2#阀门、3#阀门、1#单机、2#电机、3#电机相关联

* 点击打开： 开始菜单\程序\ imgenius Integration Service\ iDong.imgenius Integration Agent ，如图

  ![](./images/OPC配置0.png)
  ![](./images/OPC配置2.png)
  ![](./images/OPC配置3.png)

   > [!warning] 
   > 软件打开后会显示在通知栏，配置时需要在通知栏点击图标显示配置界面

* 点击File，选择General Configuration，如图

  ![](./images/OPC配置4.png) 

* 点击弹出框Providers下的Add按钮，弹出界面如下，按实际情况完成以下设置，设置完成后点击save保存设置，如图
 
  ![](./images/OPC配置6.png)

   > [!tip] 
   > 若需要对设置进行修改，选中后点击Edit按钮进入修改即可；若选中后点击Delete按钮则可以删除。

* 根据实际解决方案的信息填写Imgenius框内的内容，填写完成后点击Save保存，此时将弹出是否重启服务对话框，可暂时选“否”；
 
  ![](./images/OPC配置7.png)
  ![](./images/OPC配置8.png)
**Service Endpoint**：服务端点
**Project Name**：解决方案名称
**User Name**：超管用户名
**Password**：超管密码
**Reload**：重新加载


* 再次点击File，选择General Configuration进入配置，接着点击Reload按钮加载信息，主要是把demo解决方案的相关资产、作业组、作业规范等信息读取上来，完成后点击Save保存，此时将弹出是否重启服务对话框，可暂时选“否”；

  ![](./images/OPC配置10.png)

* 点击File，选择Rules Configuration，如图

  ![](./images/OPC配置11.png)

* 点击弹出框Rules下的Add按钮，弹出界面如下

  ![](./images/OPC配置13.png)

  ***Data Item***

  **Provoder Name** -- 数据源选择
  **Item Name** -- 标记名，与Topserver对应
  **Data Type** -- 数据类型，与Topserver对应
，

  ***Trigger Rule***

  **Rule Type** -- counterRule：累加模式，可以设定初始值和目标值；CompareRule：比较模式，可以选择一个比较符，然后设定目标值
  **Rule ID** -- 默认即可，不可重复
  **Compare Rule Parameters** -- 根据实际项目填写，本例所有点都选择当值达到200时，产生一个维保计划。

  ***Actions***

  **Action Type** -- Scheduler ImTaskPlan：创建计划，若选择Scheduler ImTaskPlan（创建计划排程），需要填写Task Group（作业组）、Task Standard（作业规范）、Asset（资产）、持续时间，配置完成后保存；Create ImTaskJob：创建任务，若选择Create ImTaskJob（创建任务），需要填写Task Standard（作业规范）、Asset（资产）、持续时间，配置完成后保存。

* 重复上一步步骤，分别新建2#阀门运行次数V002、3#阀门运行次数V003、1#电机运行时间M001、2#电机运行时间M002、3#电机运行时间M006的配置

   ![](./images/OPC配置14.png)

* 是否重启服务，选择“是”

   ![](./images/OPC配置15.png)

* 点击File，选择Monitor Live Items，可查看标记的连接状态，如图

   ![](./images/OPC配置16.png)
   ![](./images/OPC配置17.png)

## Demo例子演示

* 打开企业运营管理中心计划界面，我们可以看到计划界面是空白的，没有任何计划，如图

   ![](./images/EOC1.png)

* 打开Topserver 软件，点击打开Quick client，并找到通道sim下的PLC及其标记点

   ![](./images/TOPSERVER配置18.png)

* 更改V001点的值为200

   ![](./images/TOPSERVER配置19.png)
   ![](./images/TOPSERVER配置20.png)
   ![](./images/TOPSERVER配置21.png)

* 查看OPC触发首页日志栏，可以看到值变化更新的日志

   ![](./images/EOC2.png)

* 再次打开企业运营管理中心计划界面，我们可以看到自动产生了一个阀门V001维保的计划，如图

   ![](./images/EOC3.png)

* 终端同步任务并执行，完成后同步上传，如图

   ![](./images/PDA1.png)
   ![](./images/PDA2.png)
   ![](./images/EOC4.png)

* 再次查看OPC触发首页日志栏，可以看到值变化更新的日志，系统将自动将阀门V001本次的执行维保时阀门运行次数的当前值写入下一次计数的初始值。

   ![](./images/EOC5.png)