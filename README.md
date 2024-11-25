## Project
 
 项目基本结构
 
- app - 宿主应用，组合个业务模块形成应用
- framework - 项目框架，引用各种库并加入第三方依赖形成有业务倾向的框架
- libs - 项目业务相关或不稳定的的一些库 
  - lib1
  - lib2
  - lib3
- modules - 项目业务模块，依赖framework，各个模块是互相隔离无感知的
  - foo
  - bar
  - zoo
- repo - 项目仓库，已经成型稳定 
  - aar - 功能库，单一职责，应该在任何项目都可以单独引入使用

## Repo

``` groovy
repositories {
    maven { url "https://gitee.com/ezy/repo/raw/cosmo/"}
} 
```

## Foundation

- **init** - https://github.com/czy1121/init  
  一个 Kotlin + Flow 实现的 Android 应用初始化启动库，通过有向无环图(DAG)来调度应用初始化任务。
- **router** - https://github.com/czy1121/router  
  一个 kotlin + ksp 实现的路由库，通过 uri 实现页面间跳转
- **servicelocator** - https://github.com/czy1121/servicelocator   
  一个简单的服务定位器模式实现，如果觉得Dagger/Koin太重，可以试试这个。
- **flowbus** - https://github.com/czy1121/flowbus  
  一个简单的事件总线实现(基于SharedFlow)
- **httpapi** - https://github.com/czy1121/httpapi  
  使用 Coroutine + Retrofit 打造的最简单HTTP请求库
- **base** - https://github.com/czy1121/base  
  页面基类 BaseActivity/BaseFragment 统一了子类初始化UI(onSetupUI)的位置
- **binding** - https://github.com/czy1121/binding    
  简化 DataBinding/ViewBinding 使用，提供生命周期感知能力，支持多种使用环境(ComponentActivity/Fragment/CustomDialog/ViewGroup)
- **argument** - https://github.com/czy1121/argument   
  通过 Kotlin 委托属性获取 Activity/Fragment 的参数，可配合 router 使用
- **screenadapt** - https://github.com/czy1121/screenadapt    
  低成本屏幕适配(今日头条屏幕适配方案)
- **dialog** - https://github.com/czy1121/dialog      
  - AlertDialog扩展(tip/alert/confirm/choose)   
  - 自定义对话框(CustomDialog) - BottomDialog/DropdownDialog/SideDialog  
  - 一些简单的对话框 - LoadingDialog/InputDialog/ActionSheetDialog/PickerDialog
- **popup** - https://github.com/czy1121/popup     
  简单易用的 PopupWindow  
  
## UI
 
- **loading** - https://github.com/czy1121/loading    
  一些 loading 动画
- **statelayout** - https://github.com/czy1121/statelayout    
  简单实用无侵入高扩展的页面多状态布局(content,loading,empty,error)
- **tablayout** - https://github.com/czy1121/tablayout    
  简化 TabLayout 使用，包含文本和图标的 customView 代替 TabLayout.TabView，支持远程动态加载图标
- **bannerview** - https://github.com/czy1121/bannerview   
  简单好用的水平轮播控件 
- **pickerview** - https://github.com/czy1121/pickerview   
  使用 RecyclerView 实现的滚轮控件，这个可以显示3个以上元素(系统自带的 NumberPicker 写死了只能显示3个)。 
- **pullrefresh** - https://github.com/czy1121/pullrefresh   
  实现了嵌套滚动机制的下拉刷新控件。
- **scrollinglayout** - https://github.com/czy1121/scrollinglayout   
  垂直方向支持多个子视图持续连贯滚动的容器，并且支持吸顶功能。
- **shapeable** - https://github.com/czy1121/shapeable    
  ShapeableDrawable/ShapeableLinearLayout/ShapeableFrameLayout 可自定义 背景色/形状/阴影/描边
- **tv** - https://github.com/czy1121/tv    
  一些实用的自定义TextViewSuperTextView
  - SuperTextView - 两个文本一个图标，简化布局层级
    - 支持设置一个图标(icon/iconTint/iconSize/iconPadding/iconGravity)
    - 支持设置一个次要文本(subtext/subtextColor/subtextSize/subtextFont/subtextStyle/subtextGravity)
    - 支持文字描边
    - 支持文字渐变色(从上到下渐变)
    - 支持用尺寸设置字间距(和蓝湖等设计工具保持一致)
  - LiteTextView - 单行文本+可选图标，继承自 View 比 TextView 更轻量
    - 支持文本属性(text/textColor/textSize/fontFamily/textStyle/gravity)
    - 支持设置图标(icon/iconTint/iconSize/iconPadding/iconGravity) 
  - MarqueeTextView - 文本跑马灯效果(TextView 的跑马灯执行的条件过高)
    - 支持文本属性(text/textColor/textSize/fontFamily) 
  - ExpandableTextView - 可展开收缩的的文本，点击切换状态，右下角显示状态图标(展开/收缩)
  - ReadMoreTextView - 可展开收缩的的文本，点击切换状态，尾部显示状态文本(展开/收缩) 
- **rv** - https://github.com/czy1121/rv    
  RecyclerView 扩展：itemtype, loadmore, selection, decoration
  - rv-itemtype
    - 基于 ListAdapter 内置支持 AsyncListDiffer
    - 支持单类型列表(SingleTypeAdapter)和多类型列表(ItemTypeAdapter)
    - `ItemType<Item, Holder>` 表示列表里的一个类型
      - 通过 create 创建 Holder
      - 通过 matches 判断是否与数据(Item)关联
      - 通过 bind 将关联的数据(Item)呈现到 Holder
    - ItemSubtype 支持一个数据类型对应多个子类型布局
    - 内置的 ViewItemType 可以方便地将自定义视图(View)与数据(Item)关联组成一个ItemType
    - 内置的 LayoutItemType 可以方便地将布局(layoutResId)与数据(Item)关联组成一个ItemType
    - 内置的 bindingType 函数封装了 LayoutItemType 以支持 DataBinding
  - rv-loadmore，支持加载更多的多类型列表(LoadMoreAdapter)
    - 在 rv-itemtype, [statelayout](https://github.com/czy1121/statelayout) 的基础上实现了加载更多
    - 支持显示多种状态: loading, offline, empty, hasMore, ended, error
      - 开始加载：有网(loading), 无网(offline)
      - 完成加载：无数据(empty)
      - 完成加载/加载下一页：有数据有下一页(hasMore), 有数据无下一页(ended)
      - 加载下一页：出错(error)
  - rv-selection，基于 recyclerview-selection, ListAdapter 和 StringKey 的单选/多选库
    - selectionTracker 构造一个 SelectionTracker<String>
    - SelectionViewModel 保存了当前的选择状态
  - rv-decoration
    - DividerDecoration 为列表项之间添加分隔线
    - SpaceDecoration 为列表项之间添加空白
- **webview** - https://github.com/czy1121/webview  
  - webview-bundle - WebView 资源包管理，提升网页打开速度。
  - webview-simple - 一个简单封装的 WebView
  - webview-jsbridge - 简单易用的 WebView 和 Javascript 交互框架。
  
## Tool

- **deviceid** - https://github.com/czy1121/deviceid     
  获取设备标识(widevineId/instanceId/androidId/oaid)，采集设备信息。
- **cipher** -  https://github.com/czy1121/  
  工具类：digest/encoding/hmac/rsa/aes  
- **mmkv** - https://github.com/czy1121/mmkv  
  使用 kotlin 委托属性封装的 mmkv 库，代替 SharedPreferences，简单好用
- **html** - https://github.com/czy1121/html   
  兼容(HTML to Spanned) 7.0(API 24) 新增的一些标签和样式，可以通过自定义 ElementHandler 方便地实现自定义标签。
- **span** - https://github.com/czy1121/span   
  基于 `buildSpannedString` 扩展的 `DSL`，可方便的构建 `Spanned`，扩展支持了块级样式，文字描边，文字3D风格，标签风格...
- **networkstate** - https://github.com/czy1121/networkstate   
  判断网络是否可用，判断网络(wifi/mobile/vpn)是否连接，获取网络类型，监听网络可用事件。
- **utility** - https://github.com/czy1121/utility   
  各种工具函数：context,toast,dimen,file,format,random...  
- **systembars** - https://github.com/czy1121/systembars  
  系统栏工具库 - 状态栏/导航栏/沉浸式 
  

## Other

- **update** - https://github.com/czy1121/update  
  清晰灵活简单易用的应用更新库
  
  
 ## Demo
  
- **ThemeDemo** - https://github.com/czy1121/ThemeDemo  
  Databinding+LiveData轻松实现无重启换肤   
