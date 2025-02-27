# 更新日志

## v2.3.x

### v2.3.9 (2019-10-19)

* **新增：**  多语言支持。https://wtmdoc.walkingtec.cn/#/Global/MultiLanguages
老版本升级后会遇到单元测试项目中MockController.cs文件报错，将报错的行替换为
_controller.GlobaInfo.SetModuleGetFunc(() => new List<FrameworkModule>());
即可。

* **新增：**  dotnet 3.0支持，线上新建项目时可选择dotnetcore3.0版本的项目

#### 前后端不分离模式
* **新增：**  集成了UEditor。https://wtmdoc.walkingtec.cn/#/UI/UEditor
* **新增：**  列表按钮现在可以设置Max属性，来控制打开窗体时最大化
* **修改：**  现在View页面不再强制要求Model必须继承BaseVM
* **修改：**  修改菜单无法删除的历史遗留bug

### v2.3.6 (2019-9-27)

* **新增：**  Debug模式下，debug窗口会输出ef执行的sql语句
* **修改：**  移除EnableCors属性，集成dotnetcore自带的Cors实现跨域，并可在appsettings文件中进行配置

#### 前后端不分离模式
* **修改：**  代码生成器会为Controller生成独立的搜索和导出方法，方便对搜索和导出进行权限控制，之前公共方法仍然保留
* **修改：**  修复IE11下的显示问题
* **修改：**  修复PersistPoco导入时没有给IsValid赋值的问题
* **修改：**  修复SearchPanel中显示树形列表的问题

### v2.3.5 (2019-9-19)

本次更新增加了自定主键功能，除了默认的guid主键外，框架现在还支持自增整形和string类型的主键。
同时代码生成器也可以准确识别主键类型，生成对应的代码。
具体使用方式参见文档 https://wtmdoc.walkingtec.cn/#/Model/CustomKey

由于主键不一定是guid了，老项目更新的时候需要手动修改之前的文件，主要是两部分：
1. Controller里 BatchEdit，BatchDelete中的ids参数由guid[] 变为 string[]
2. batchvm中的CheckIfCanDelete方法，第一个参数由guid变为object
3. 老数据库中DataPrivileges表RelatedId字段类型由Guid变为Nvarchar
改起来还是比较简单的

#### 前后端不分离模式
* **修改：**  修复layui模式下三级菜单无法显示的bug
* **修改：**  修复selector控件不能搜索，不初始化的bug

#### React前后端分离模式
* **新增：**  增加菜单对字体图标的支持
* **修改：**  修复react模式下三级菜单无法显示的bug

### v2.3.4 (2019-9-5)

#### 前后端不分离模式
* **新增：**  现在Layui模式可以直接用代码生成器生成api
* **新增：**  现在Layui模式的菜单管理也可以配置api的权限，包括框架自带的api
* **新增：**  新建layui项目时自动添加swagger的支持，可以查看api文档
* **修改：**  修复grid排序时搜索条件不起作用的bug

#### React前后端分离模式
* **新增：**  新增Tab页关闭其他，关闭当前，关闭所有的功能

### v2.3.3 (2019-9-3)

* **新增：**  新增对Oracle的支持（鸣谢：hd2y）Oracle database version 18c is required.
* **新增：**  新增对DC使用事务的支持（鸣谢：AaronLucas）
* **修改：**  更新了默认数据的添加逻辑，现在使用EF的migration不会担心没有初始数据了
* **修改：**  新生成的项目会在DataContext.cs中自动加入IDesignTimeDbContextFactory类，方便使用Migration

#### 前后端不分离模式
* **修改：**  现在首页默认不展开菜单
* **修改：**  直接访问具体url可以准确定位左侧菜单
* **修改：**  更新默认生成的Login单元测试
* **修改：**  修复批量修改的一些bug
* **修改：**  修复维护菜单会改变菜单id的bug

#### React前后端分离模式
* **修改：**  修复grid中分组之后排序的bug
* **修改：**  修复grid中有时出现横向滚动条的bug
* **修改：**  新登陆页面


### v2.3.1 (2019-8-31)
修复了2.3.0版本中的一些bug
* **修改：**  修复菜单图标显示的问题
* **修改：**  修复主子表修改报错的问题
* **修改：**  修复Selector在IIS下无法显示的问题

### v2.3.0 (2019-8-30)

本次更新是一个大版本的更新，彻底重构了不分离模式的前端UI，大家可以愉快且免费的使用LayuiAdmin了

老项目更新说明：
本次更新全面支持了图标字体，放弃了使用图片附件作为菜单图标。FrameworkMenu表去掉了IconId和CustomIcon字段，新加入了字符串格式的Icon字段
老用户最快的升级方法是线上生成一个同名的新LayUI的项目，然后把你的model，viewmodel，controller考过去。。。

#### 前后端不分离模式
* **新增：**  LayUI升级为LayUIAdmin
* **新增：**  添加对图标字体的支持
* **新增：**  更新默认登录页
* **新增：**  新增Tree和TreeContainer控件
* **新增：**  新增Combobox和DateTime控件的默认配置（鸣谢：AaronLucas）
* **新增：**  新增对Sqlite数据库支持（鸣谢：xuegaoge)
* **修改：**  修复单元格内控件错位的bug
* **修改：**  修复多表头列表导出的bug
* **修改：**  修复LinkButton无法在当前页显示的问题

#### React前后端分离模式
* **修改：**  更新菜单管理模块，支持图标字体
* **修改：**  更新列表显示的逻辑

#### React前后端分离模式
还在路上，预计下个版本会和大家见面~~~

## v2.2.x

### v2.2.52 (2019-8-7)

本次更新主要修复了近期用户反馈的一些bug

#### 前后端不分离模式

* **新增：** GridAction的按钮现在可以通过IsRedirect属性设置在当前页或者Tab页，或者新窗口中显示
* **修改：** 修复layui普通checkbox样式问题
* **修改：** 修复菜单添加报错的bug
* **修改：** 修复多表头显示问题
* **修改：** 修复GridAction中IconCls属性不起作用的问题

#### React前后端分离模式

* **修改：** 修复Area下的api地址解析问题
* **修改：** 修复下拉菜单显示枚举错误的问题
* **修改：** 修复列表中switch现实问题

### v2.2.50 (2019-7-30)

* **修改：** 代码生成器加入对模型基类的验证
* **修改：** 修复日志过长导致截断的bug
* **修改：** 使用新Logo

#### 前后端不分离模式

* **新增：** 新增slider滑块控件
* **新增：** 新增transfer穿梭框控件
* **新增：** 新增对列表汇总行的支持
* **修改：** 修复了绑定字段为数组引起的bug
* **修改：** 修复菜单管理和数据权限管理中历史遗留的bug
* **修改：** 控件的默认id添加vm名称前缀，防止多tab页时出现id重名的控件
* **修改：** 修复checkbox无法触发change-func函数的bug
* **修改：** 使用layui的template重写列表前景色和背景色的实现

#### React前后端分离模式

* **修改：** 优化页面异步加载机制 路由规则调整
* **新增：** 新增aggrid，替代antd自带的grid

### v2.2.48 (2019-7-12)

* **修改：** 修复导入时，同样唯一性数据没有自动更新的bug
* **修改：** 修复批量修改时的验证bug
* **修改：** 修复前后端分离模式菜单排序的bug
* **修改：** 修复layui模式下，searchpanel中oldpost参数无效的bug

### v2.2.47 (2019-7-5)

* **新增：** 新增ValidateFormItemOnly属性，可以加在controller的方法上，用来指示框架只验证表单提交的字段

#### 前后端不分离模式

* **修改：** 修复Admin中更新用户的bug
* **修改：** 修复grid中form控件id的错误

### v2.2.46 (2019-7-3)

* **优化：** 优化ListVM查询速度
* **优化：** 修改ListVM对存储过程的支持，并配套相关文档

#### 前后端不分离模式

* **修改：** 修复grid中使用表单组件的bug
* **修改：** 修复GetFile方法没有正确输入视频content-type的bug

#### React前后端分离模式

* **优化：** 优化配置文件
* **修改：** 修复添加操作没有正确验证model的bug

### v2.2.45 (2019-6-17)

* **新增：** wt:grid 增加MultiLine属性，用于控制是否允许单元格自动换行
* **修改：** 修改默认首页的样式，增加了对于调试模式的提示，以免新用户迷茫

### v2.2.44 (2019-6-14)

* **新增：** 新增自动化单元测试。在线生成项目时会同时生成单元测试项目，代码生成器也会在生成代码的同时为Controller生成单元测试。同时支持分离和不分离两种模式
* **修改：** 修复主子表导入bug，文档中ImportVM中同时加入了主子表导入的范例
* **修改：** 修复默认多字段排序的bug

#### 前后端不分离模式

* **修改：** 修复用户组数据权限修改时的bug

#### React前后端分离模式

* **新增：** 顶部菜单配置，可以在全局设置里将菜单配置成顶部显示
* **新增：** 富文控件中增加文件上传
* **新增：** 增加时间区间控件
* **新增：** 添加了默认的修改密码页面
* **优化：** 优化表格

#### VUE前后端分离模式

VUE目前进展稍慢，距离和大家见面还需要一段时间

### v2.2.42 (2019-5-28)

* **修改：** FrameworkMenu表中加入string类型的CustumIcon字段，已有项目可以手动修改数据库，添加这个字段

#### React前后端分离模式

* **新增：** 菜单维护加入自定义图标，可以设置antd自带图标
* **优化：** 优化编译速度，优化布局

#### 前后端不分离模式

* **新增：** Appsettings中增加TabMode配置，设置layui模式下Tab页样式 ，可选配置有Default和Simple
* **新增：** Appsettings中增加IsFilePublic配置，可以设置附件是否不需要登陆就可以查看和下载

### v2.2.40 (2019-5-18)

* **修改：** 修复枚举导出时不显示的bug

#### 前后端分离模式

* **修改：** 修复React依赖报错的问题

### v2.2.39 (2019-5-10)

* **修改：** 修复代码生成器对关联字段生成ImportVM时的bug

#### 前后端不分离模式

* **修改：** upload控件增加修改尺寸的选项，当UploadType为ImageFile时，通过设置ThumbWidth和ThumbHeight，可以让服务器保存缩小后的图片
* **修改：** upload控件增加缩略图预览，当UploadType为ImageFile时默认开启缩略图预览，通过ShowPreview，PreviewWidth，PreviewHeight等参数可配置
* **修改：** 更改绑定布尔值时checkbox的样式
* **修改：** 修复layui模式下登录用户头像显示的问题，已经生成的项目可以将以下两个文件覆盖自己的项目对应的文件
    1. [LoginVM.cs](https://github.com/dotnetcore/WTM/blob/develop/demo/WalkingTec.Mvvm.Demo/ViewModels/HomeVMs/LoginVM.cs)
    1. [Header.cshtml](https://github.com/dotnetcore/WTM/blob/develop/demo/WalkingTec.Mvvm.Demo/Views/Home/Header.cshtml)

### v2.2.38 (2019-4-29)

* **修改：** 修改DpWhere逻辑，DpWhere中多个字段参数之间现在是or的关系

#### 前后端不分离模式

* **新增：** 新增layui下根据数据控制行内动作按钮是否显示。现在可以在Action上调用BindVisiableColName方法来指定某个隐藏列的名称，该隐藏列值为字符串'true'的时候，action按钮才显示
* **修改：** 修改了tab页模式下，多层弹出窗口grid不刷新的bug
* **修改：** 修复selector在searchpanel里，清空了不起作用的bug
* **修改：** 修改pindex页面使用tab，导致代码生成器显示错位的bug

### v2.2.36 (2019-4-25)

#### 前后端不分离模式

* **新增：** 新增layui下列表后台排序功能，在ListVM中设置列的时候，对需要排序的列调用SetSort(true)即可

### v2.2.35 (2019-4-22)

* **修改：** 修复代码生成器在Mac系统下无法工作的问题
* **修改：** 修复UpdateTime和UpdateBy字段没有自动写入的问题

#### 前后端不分离模式

* **修改：** 修复checkbox为false，表单字段不提交的bug

#### 前后端分离模式

* **修改：** 修复api在标记了Area属性时框架无法识别的bug

### v2.2.34 (2019-4-20)

#### 前后端不分离模式

* **修改：** 修复菜单管理中，修改菜单的bug

#### 前后端分离模式

* **修改：** 修复IsQuickDebug为false时，api无法正常访问的问题
* **修改：** 修复Excel导入的bug

### v2.2.33 (2019-4-16)

#### Features

* **修改：** 修改前后端分离模式中表单提交的逻辑，现在表单中没有定义的字段将不会被更新
* **修改：** 修改前后端分离模式中框架自带的一些前台页面的bug
* **修改：** 修改BaseCRUDVM中的删除逻辑，现在可以正确删除include了其他关联类的Entity

### v2.2.32 (2019-4-16)

#### Features

* **新增：** React前后端分离模式RTM版本正式发布！欢迎大家使用

### v2.2.28 (2019-4-9)

#### Features

* **修改：** 系统菜单表新增ClassName和MethodName两个字符串字段，已有项目升级时可手动在库中添加这两个字段
* **修改：** React的前后端分离模式接近完成

### v2.2.26 (2019-4-1)

#### Features

* **新增：** 新增对pgsql的支持
* **修改：** 重写菜单管理逻辑，菜单配置更简便
* **修改：** React的前后端分离模式稳步推进

### v2.2.22 (2019-3-20)

#### Features

* **修改：** 代码生成器会在Controller和VM的类上加入partial，这样方便大家另起一个文件写自定义的代码，而不用担心再次生成代码的时候会被覆盖
* **修改：** 修改<wt:combobox>支持多选枚举的绑定
* **修改：** React的前后端分离模式增加了多个控件，修改了若干实际项目中反应的问题，向正式版又前进了一大步

### v2.2.10 (2019-2-27)

#### Features

* **新增：** 新增在线生成项目，[https://wtmdoc.walkingtec.cn/setup](https://wtmdoc.walkingtec.cn/setup) ，生成WTM项目更快捷
* **修改：** 进一步完善React的前后端分离模式，当然目前还是预览

### v2.2.8 (2019-2-24)

#### Features

* **新增：** 框架开始支持前后端分离模式，可以创建React的前后端分离模式的项目，并生成前后端分离模式的代码
* **新增：** 新增MiddleTableAttribute，对于多对多的关系，可以在中间表的模型上标记[MiddleTable]，框架的代码生成器根据这个标记可以正确生成多对多关系的增删改查代码

### v2.2.4 (2019-01-11)

#### Bug Fixes

* 修改默认连接字符串的bug ([318840c](https://github.com/WalkingTec/WalkingTec.Mvvm/commit/318840c))
* 修改密码的bug ([1427fb7](https://github.com/WalkingTec/WalkingTec.Mvvm/commit/1427fb7))

### v2.2.3 (2019-01-08)

#### Bug Fixes

* 修改外部地址菜单刷新的bug ([918560f](https://github.com/WalkingTec/WalkingTec.Mvvm/commit/918560f))

### v2.2.2 (2019-01-04)

#### Bug Fixes

* 修改富文本必填验证的bug ([e9f2cd0](https://github.com/WalkingTec/WalkingTec.Mvvm/commit/e9f2cd0))

### v2.2.1 (2018-12-23)

#### Features

* **修改：** 修改文件上传相关配置，将 `SaveFileMode` 及 `UploadDir` 更改到 `FileUploadOptions` 中

#### Bug Fixes

* 解决 .net core 2.2下 IIS Inprogres s运行的问题 ([90256fe](https://github.com/WalkingTec/WalkingTec.Mvvm/commit/90256fe))

### v2.2.0 (2018-12-20)

#### Features

* **新增：** 添加富文本组件
* **新增：** 添加自定义路由的简便入口
* **修改：** CrossDomainAttribute现在可以指定允许的域名
