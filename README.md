# GooFlow 

> 这是一个用来在WEB端构建流程图的JQuery插件，在线流程设计器。可设计各种流程图、逻辑流图，数据流图，或是应用系统中需要走流程的功能实现。优秀的用户体验使得操作界面很容易上手，无论开者或用户都可轻松使用。并且兼容主流浏览器(ie8--ie edge，chrome，firefox)。

**Jax: 没想到吧，我又回来了！**
<p>GooFlow携全新的“私货”再次重装来袭！全新防侵权机制取代原JS挖矿，专治各种伸手党不服！加入新扩展接口及设定以适应更多领域场景要求。</p>
<p>1.3.9版本以后，所有功能开发完毕，今后将只有Bug修复才会更新。目前还在考虑是否开发Vue版。</p>
<p>只有本人发布的试用项目是真正的GooFlow。其余人等发布的同名或fork后自改版本，均不能保证其安全性、里面是否不含病毒或木马；若采用这些版本，风险程度无法估量，造成任何对系统的危害本人概不负责。</p>

官网：[https://gooflow.xyz](https://gooflow.xyz)<br>
要了解详细的使用方法，请查看[API文档](https://gooflow.xyz/docs)<br>
GooFlow已转为闭源项目，github上不再提供clone和下载。试用版请访问gitee上的[项目主页](https://gitee.com/gooflow/gooflow)



## 授权说明： ##
GooFlow已转为闭源项目，当前托管页中所放版本仅为试用版，会让CPU无意义空转耗能，且含有定时弹出的广告，只能用于本地功能测试，切不可放入实际项目中使用；<br>
如要应用于软件开发项目中，只能使用纯净未有任何附加的正式版，并需要联系作者本人购买使用授权，谢谢。（无论正式版还是试用版，如果逃避购买授权而直接用于项目，擅自窃取用作谋利，或者尝试破解程序，即属严重侵权行为，与盗窃无异。产生的一切任何后果责任由侵权者自负。请各位只想免费吃白饭的伸手党做好向作者本人及自己的公司、客户负全责的觉悟。）<br>
联系方式：<br>
微信：18648945414<br>
QQ： 115247126<br>
邮箱： fool-egg@163.com <br>
## 特点 ##
* 跨领域:流程图设计器不止用在电信领域,在其它需要IT进行技术支持的领域中都有重大作用.
* 页面顶部栏、左边侧边栏均可自定义；
* 当左边的侧边栏设为不显示时，为只读状态，此时的视图区可当作是一个查看器而非编辑器。
* 当前最新版本已全部使用自定义的阿里巴巴矢量图标库，可不再需要一张用来显示图标样式的图片。
* 侧边工具栏除了基本和一些流程节点按钮外，还自定义新的节点按钮，自定义节点都可以有自有的图标、类型名称，定义后在使用可可在工作区内增加这些自定义节点。
* 顶部栏可显示流程图数据组的标题，也可提供一些常用操作按钮。
* 顶部栏的按钮，除了撤销、重做按钮外，其余按钮均可自定义点击事件。
* 可画直线、折线；折线还可以左右/上下移动其中段。
* 具有区域划分功能，能让用户更直观地了解哪些节点及其相互间的转换，是属于何种自定义区域内的。
* 具有标注功能，用橙红色标注某个结点或者转换线，一般用在展示流程进度时。
* 能直接双击结点、连线、分组区域中的文字进行编辑
* 在对结点、连线、分组区域的各种编辑操作，如新增/删除/修改名称/重设样式或大小/移动/标注时，均可捕捉到事件，并触发自定义事件，如果自定义事件执行的方法返回FALSE，则会阻止操作。
* 具有操作事务序列控制功能，在工作区内的各种有效操作都能记录到一个栈中，然后可以进行撤销（undo()）或重做（redo()），像典型的C/S软件一样。
* 能将流程图以png图片的格式导出并下载（纯JS实现，但不支持IE9及以下浏览器）

![Preview Image](https://git.oschina.net/uploads/images/2017/0531/145320_f0bb8c2c_472359.png "效果预览图")
<br><br>

## 开始使用 ##

### 一：传统方式的使用方法  ###
先在页头引入Css文件，在body末尾引入jquery和GooFloW主要功能文件;
``` html
<head>
    <link rel="stylesheet" type="text/css" href="./dist/GooFlow.min.css"/>
</head>
<body>
    <div id="demo"></div>
    ……
    <script type="text/javascript" src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min"></script>
    <script type="text/javascript" src="./dist/GooFlow.min.js"></script>
    <!-- 可选，将流程图导出为图片文件的扩展包 GooFlow.export.js -->
    <script type="text/javascript" src="./dist/GooFlow.export.min.js"></script>
    <!-- 可选，将流程图输出打印或另存为PDF的扩展包 GooFlow.print.js-->
    <script type="text/javascript" src="./dist/GooFlow.print.min.js"></script>
    <script type="text/javascript" src="./main.js"></script>
</body>
```
然后在业务js中调用方法；
``` javascript
/** main.js **/
    var options = {
        toolBtns:["start round mix","end round","task","node","chat","state","plug","join","fork","complex mix"],
        haveHead:true,
        headLabel:true,
        headBtns:["new","open","save","undo","redo","reload","print"],//如果haveHead=true，则定义HEAD区的按钮
        haveTool:true,
        haveDashed:true,
        haveGroup:true,
        useOperStack:true
    };
    var demo;
    $(document).ready(function(){
        demo = GooFlow.init("#demo",options);
        // demo = $.createGooFlow("#demo",options); //第二种初始化方法
        demo.setNodeRemarks(remark); //remarks为左侧工具栏按钮的title提示定义
        demo.loadData(jsondata); //jsondata为表达流程图详细的JSON数据
    });
```
<br>

### 二：AMD异步模式使用方法  ###
以**RequireJs**为例，先在RequireJs于项目的统一配置文件中加入如下设置，需要用到**require-css**(css.min.js)插件；
``` javascript
/** require.config.js **/
requirejs.config({
    //// ……
    map: {
        '*': {
            'css': 'https://cdn.bootcss.com/require-css/0.1.10/css.min.js' // https://github.com/guybedford/require-css, RequireJs's plugin
        }
    },
    paths: {
        jquery: 'https://cdn.bootcss.com/jquery/1.12.4/jquery.min',
        GooFlow: 'dist/GooFlow.min',
        'GooFlow.group': 'dist/GooFlow.group.min',  //可选，支持分组泳道显示的扩展包（从1.3.8rp版本开始）
        'GooFlow.export': 'dist/GooFlow.export.min',  //可选，将流程图导出为图片文件的扩展包
        'GooFlow.print': 'dist/GooFlow.print.min',    //可选，将流程图输出打印或另存为PDF的扩展包
    },

    shim:{
        'GooFlow':{
            deps:['css!../dist/GooFlow.min.css','jquery']
        }
    },
    //// ……
});
```
在将会异步引入main.js入口业务文件的html页面中,body末尾加上这一段;
``` html
<body>
    <div id="demo"></div>
    ……
    <script data-main="main.js" src="https://cdn.bootcss.com/require.js/2.3.5/require.min.js"></script>
    <script src="../assets/js/require.config.js"></script>
</body>
```
然后在具体的业务js文件中作包引入并初始化；
``` javascript
/** main.js **/
require(['jquery','GooFlow'], function ( $, GooFlow ) {
    // 初始化的代码
    var options = { …… };
    var demo = GooFlow.init("#demo",options);
    demo.setNodeRemarks(remark); //remarks为左侧工具栏按钮的title提示定义
    demo.loadData(jsondata);     //jsondata为表达流程图详细的JSON数据
});
```
如果想使用其它扩展包提供的功能，请务必保证在载入GooFlow.js后再载入相应的扩展包，以保证相应的功能正常；
``` javascript
/** main.js 扩展功能包 **/
require(['jquery', 'GooFlow'], function ( $, GooFlow ) {
    require(['GooFlow.export','GooFlow.print'], function (){
        // 初始化的代码
        var options = { …… };
        var demo = GooFlow.init("#demo",options);
        demo.setNodeRemarks(remark);         //remarks为左侧工具栏按钮的title提示定义
        demo.setHeadToolsRemarks(headBtns);  //headBtns为顶部标题栏按钮的title提示设置
        demo.loadData(jsondata);             //jsondata为表达流程图详细的JSON数据
        demo.onBtnSaveClick=function(){
            demo.exportDiagram(exportName);//流程图导出图片功能
        }
        demo.onPrintClick=function(){
            demo.print();//打印流程图或另存为PDF功能
        }
    });
});
```
<br>

**更新历史：**
- **1.3.9:** <br>重大更新！增加缩略导航图的功能，包括拖动定位和实时滚动。
- **1.3.9r1:** <br>重大更新！修正一些新发现的BUG；增加无向线段的支持，修改了虚线的设定方式；新增多选功能（只针对节点和连线），并能对多选的元素集合进行批量移动和删除。
- **1.3.8rp:** <br>修正一些新发现的BUG，全面提升正式版的运行效率；在试用版上使用新的防侵权机制取代原有的JS挖矿；将分组泳道支持单独从核心文件中抽离出来，形成一个独立的扩展功能块<code>GooFlow.group.min.js</code>；增加便笺元素（通过新功能块）；新增自定义背景图类型节点，适应更多场景。
- **1.3.7:** <br>修正计算流程图实际宽高算法的一个小BUG；初始化时增加设置节点和泳道初始默认名前缀的属性。
- **1.3.6:** <br>修正有时选中元素时，focus事件被触发两次的问题；加入右建单击绘图区空白处时，触发blur事件的操作方式；新增快捷设置某个元素的扩展业务属性的接口；新增流程图载入后再对某元素另行修改颜色或文字颜色的接口。
- **1.3.5:** <br>功能更新！分组泳道增加了“牛奶”色；用户可对单个节点或连线自定义特殊的图形颜色和文字颜色；设计器增加了 ctrl+c 复制节点和 ctrl+v 粘贴节点功能。
- **1.3.4:** <br>重要更新！修正了一些事件响应、图片导出、绘图区缩放方面的Bug；增加了椭圆、菱形、平行四边形、胶囊形4种特殊形状的节点。
- **1.3.3:** <br>重要功能上线！新增对Bpmn2.0规范下XML格式的流程图数据的支持，可读取或输出Bpmn2.0规范的XML格式数据；允许用户以json文件或者Bpmn2.0规范的XML文件的方式下载流程图数据至本地。 进一步优化代码。
- **1.3.2:** <br>优化了代码结构和用户体验；加强内聚性，简化了流程另存为图片功能和打印功能的内部实现，摆脱了1.1至1.2版本中对第三方插件的依赖，导出结果更清晰，并能向后兼容到IE9；各部分的按钮都可以通过内置接口方法进行配置；节点数据新增”areaId”可选属性:表示其属于哪一个区域组(泳道)。总体还加入了对amd、cmd开发模式规范的支持。
- **1.3:** <br>修正一些影响用户体验和使用的BUG，增加灵活的对工作区所有操作按钮注释配置功能。
- **1.2.1:** <br>改善对IE8的支持；优化手动调整元素大小的精确度；增加对流程图打印预览或另存为PDF的功能。
- **1.2:** <br>重大更新版本！增加了对节点、连线、泳道块的右键事件和双击事件方法设定（可return false以阻止浏览器默认事件发生）；增加虚线的绘制功能方法：应众多用户的要求增加了重要的流程图缩放功能接口！可缩放范围是从原始大小的50%至400%。（仅提供方法接口，具体操作缩放的页面组件元素用户另行选择绑定第三方的）
- **1.1:** <br>进一步修正了BUG；增加了导出工作区内流程图为图片并让用户下载的功能，目前仅能支持IE10以上、IE edge、Chrome、FireFox、Safari浏览器，该功能需求载入新的GooFlow.export.js扩展包。
- **1.0.2:** <br>修正了当某节点原来为marked，选中再取消后marked标红样式消失的问题。
- **1.0:** <br>首个正式版本，相对于以前的试用版，进一步修正了BUG，可自定义颜色项更多，并且做到了不再有一张图片，所有图标均匀为矢量字体。
