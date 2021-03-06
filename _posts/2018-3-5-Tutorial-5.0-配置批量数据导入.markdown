---
layout: post
title:  "配置批量数据导入"
date:   2020-05-05
visible: 1
---

前面教程介绍了使用表单添加数据记录的操作。手工录入数据效率比较低。如果您要录入的数据保存在文本或Excel文件中的话，可以使用Ebaas平台提供的批量导入数据的功能。批量导入的功能是通过数据导入向导来配置和执行的。数据导入向导类似于一个ETL工具，可用于从多种格式的文件中抽取数据，将其转换为所需的格式，并将其加载到数据库中。

下面，我们将介绍如何使用数据导入向导从一个文本文件将“事务”数据记录导入到“事务”数据类的过程。

#### 下载数据文件

为了节省您的时间，我们为您准备了一个已经包含多个事务数据的文本(CSV)文件。您可以点击下面的链接下载并保存：

[下载事务数据文件][1]

[1]:{{ site.url }}/assets/事务数据.csv

{% include note.html content="数据导入向导支持TXT，CSV，Excel等格式文件导入。特殊格式的文件需要编写导入转换器并进行配置。" %}

事务数据文件见下图：
<img src="{{'/assets/img/2018-3-5-配置批量数据导入0.png' | prepend: site.baseurl }}" alt=""><br>

#### 打开数据导入向导

数据导入向导是DesignStudio的一部分。首先打开DesignStudio。

然后，通过单击“文件”菜单下的“导入数据...”菜单项打开导入向导。如下图所示。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入1.png' | prepend: site.baseurl }}" alt=""><br>
在弹出的“连接数据库”窗口，选中“事务跟踪管理”数据模型 => 以admin用户身份登录 （admin用户的用户名是“admin”，默认密码是“admin”）。如下图所示。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入2.png' | prepend: site.baseurl }}" alt=""><br>
单击“确定”按钮，在弹出的“数据导入向导”面板中，单击“下一步”按钮，如下图所示。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入3.jpg' | prepend: site.baseurl }}" alt=""><br>

#### 选择导入文件

在向导的第一步中 => "数据源类型"选择“文本文件(txt)”（CSV是文本格式），然后单击“文件名”右边的“...”按钮，如下图所示：
<img src="{{'/assets/img/2018-3-5-配置批量数据导入4.png' | prepend: site.baseurl }}" alt=""><br>
在弹出的窗口，选择前面步骤下载的文件，如下图所示。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入5.png' | prepend: site.baseurl }}" alt=""><br>
结果见下图，单击“下一步”按钮。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入6.png' | prepend: site.baseurl }}" alt=""><br>

#### 指定文件格式

向导的第二步是确定如何正确解析文件。选择下面的格式设置：

* “行分隔符”选择默认：{CR}{LF}；
* “第一行为列名”选项打勾；
* 列分隔符选择：“逗号”；

如下图所示。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入7A.png' | prepend: site.baseurl }}" alt=""><br>

#### 预览提取的数据

向导的第三步是使用设置预览从文件中提取的数据，如下图所示。如果提取的数据看起来不正确，则可以返回上一步更改设置并重试。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入8A.png' | prepend: site.baseurl }}" alt=""><br>

#### 数据转换

这一步指定数据导入的目标数据类，属性的对应关系以及数值的转换。

单击“目标数据类”下面“请点击选择一数据类”，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入9.png' | prepend: site.baseurl }}" alt="">

在弹出的“选择导入的数据类”窗口，选择“事务”数据类作为目标类，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入10.png' | prepend: site.baseurl }}" alt=""><br>

然后，通过在“转换关系”列中单击“...”在源（提取的数据）与目标之间创建映射，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入11.png' | prepend: site.baseurl }}" alt=""><br>

弹出“变换对话框”中，单击选择左边“源数据”的“主题”选择框，然后再单击选择右边“目标数据”的“主题”选择框，两端会连接一根直线，将源属性映射到目标属性。如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入12A.png' | prepend: site.baseurl }}" alt=""><br>
其它属性映射连接依次类推，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入13A.png' | prepend: site.baseurl }}" alt=""><br>

{% include note.html content="如果源数据与目标数据的属性名相同的话，可以点击下方的‘自动同名映射’按键自动建立连线。" %}

#### 预览转换后的数据

向导的第五步允许您检查和验证转换后的数据,如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入19.png' | prepend: site.baseurl }}" alt=""><br>

点击“校验”按钮，向导会根据数据模型定义的属性值校验条件校验。如果数据符合校验条件，会弹出“数据符合校验条件”信息框，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入14.png' | prepend: site.baseurl }}" alt=""><br>

{% include note.html content="如果出现校验错误，向导会在相应的数据行左边显示红色标识。选择错误数据行，点击下方的‘修改’按键，在弹出的编辑窗口中，点击‘校验’按键，查看错误信息。再回到前面转换步骤进行相应的修复" %}


#### 导入数据并保存导入脚本

在向导的最后一步是导入数据并保存脚本。 如果您需要将数据导入到数据库，则将“即刻导入数据库”选项打勾。如果这是一个重复导入数据的任务，您可以通过为其配置一个名称来保存配置为导入脚本，这样您可以在下次执行导入数据时使用导入脚本，避免再进行前面的配置。

保存脚本，请将“保存数据导入脚本”选项打勾，并在“脚本名称”输入:导入事务数据脚本，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入15.png' | prepend: site.baseurl }}" alt=""><br>
单击“下一步”按钮开始将转换后的数据导入数据库并保存导入脚本。<br>
数据导入成功，会进入到下一个“数据导入成功”面板，单击“结束”按钮，如下图。<br>
<img src="{{'/assets/img/2018-3-5-配置批量数据导入16.png' | prepend: site.baseurl }}" alt=""><br>


导入的数据可以在DesignStudio工具里切换到“数据模型编辑器”里查看，如下图。
<img src="{{'/assets/img/2018-3-5-配置批量数据导入18.png' | prepend: site.baseurl }}" alt=""><br>

