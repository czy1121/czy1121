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

- **servicelocator** - https://github.com/czy1121/servicelocator   
  一个简单的服务定位器模式实现，如果觉得Dagger/Koin太重，可以试试这个。
- **router** - https://github.com/czy1121/router  
  一个 kotlin + ksp 实现的路由库，通过 uri 实现页面间跳转
- **flowbus** - https://github.com/czy1121/flowbus  
  事件总线(基于SharedFlow) 和 状态总线(基于StateFlow)
- **httpcall** - https://github.com/czy1121/httpcall  
  使用 Coroutine + Retrofit 打造的最简单HTTP请求库
- **dag** - https://github.com/czy1121/dag  
  有向无环图(DAG)，可用来调度应用初始化任务
- **base** - https://github.com/czy1121/base  
  页面基类 BaseActivity/BaseFragment 统一了子类初始化UI(onSetupUI)与首次加载数据(onLoadData)的位置
  
## UI

- **dialog** - https://github.com/czy1121/dialog      
  - AlertDialog扩展(tip/alert/confirm/choose)   
  - 自定义对话框(CustomDialog) - BottomDialog/DropdownDialog/SideDialog  
  - 一些简单的对话框 - LoadingDialog/InputDialog/ActionSheetDialog/PickerDialog
- **statelayout** - https://github.com/czy1121/statelayout    
  简单实用无侵入高扩展的页面多状态布局(content,loading,empty,error)
- **tabs** - https://github.com/czy1121/tabs    
  简化 TabLayout 使用，使用 TabItemView 代替 TabLayout.TabView，支持远程动态加载图标
- **bannerview** - https://github.com/czy1121/bannerview   
  简单好用的水平轮播控件 
- **pullrefresh** - https://github.com/czy1121/pullrefresh   
  实现了嵌套滚动机制的下拉刷新控件。
- **scrollinglayout** - https://github.com/czy1121/scrollinglayout   
  垂直方向支持多个子视图持续连贯滚动的容器，并且支持吸顶功能。
- **bk** - https://github.com/czy1121/bk    
  BKDrawable/BKFrameLayout/BKLinearLayout/BKTextView 可自定义 背景色/渐变/圆角/阴影/描边
  - 支持 背景色[正常/选中/按下/禁用]
  - 支持 渐变[类型/半径/方向/中心点XY坐标(0.0~1.0)/颜色(开始-中心-结束)]
  - 支持 圆角[半径，位置]，根据宽高自动计算圆角半径 min(height,width) / 2
  - 支持 阴影[颜色/半径/边距(容纳阴影的空间)]
    - 阴影颜色默认自动从背景或描边获取，也可以手动设置
    - 阴影绘制算法取自 [ShadowRenderer](https://github.com/material-components/material-components-android/blob/master/lib/java/com/google/android/material/shadow/ShadowRenderer.java)
  - 支持 描边[颜色/厚度/虚线长度/虚线间隙]
  - BKTextView 支持 图标[图标/尺寸/边距/着色/位置]，类似 MaterialButton 的图标
- **tv** - https://github.com/czy1121/tv    
  一些实用的自定义TextView
  - CamelTextView - 可额外设置两个文本(prefix/suffix)，可用于带单位的数值，比如：<sub>￥</sub><b>123.0</b><sub>元</sub>
  - ThreeTextView
    - 可额外设置两个文本(text2/text3)，text2 在 text 底下，text3 在右边
    - 可设置左右两个图标(leftIcon/rightIcon)
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
  
## Tool

- **binding** - https://github.com/czy1121/binding    
  简化 DataBinding/ViewBinding 使用，提供生命周期感知能力，支持多种使用环境(ComponentActivity/Fragment/CustomDialog/ViewGroup)
- **systembars** - https://github.com/czy1121/systembars  
  系统栏工具库 - 状态栏/导航栏/沉浸式
- **cipher** -  https://github.com/czy1121/  
  工具类：digest/encoding/hmac/rsa/aes  
- **mmkv** - https://github.com/czy1121/mmkv  
  使用 kotlin 委托属性封装的 mmkv 库，代替 SharedPreferences，简单好用
- **argument** - https://github.com/czy1121/argument   
  通过 Kotlin 委托属性获取 Activity/Fragment 的参数
- **html** - https://github.com/czy1121/html   
  兼容(HTML to Spanned) 7.0(API 24) 新增的一些标签和样式，可以通过自定义 ElementHandler 方便地实现自定义标签。
- **networkstate** - https://github.com/czy1121/networkstate   
  判断网络是否可用，判断网络(wifi/mobile/vpn)是否连接，获取网络类型，监听网络可用事件。
- **utility** - https://github.com/czy1121/utility   
  各种工具函数：context,toast,dimen,file,format,random...   
  

## Other

- **webcache** - https://github.com/czy1121/webcache  
  Android WebView 缓存管理，提升网页打开速度。
- **jsbridge** - https://github.com/czy1121/jsbridge    
  简单易用的 Android WebView 和 Javascript 交互框架。
- **update** - https://github.com/czy1121/update  
  清晰灵活简单易用的应用更新库
  
  
 ## Demo
  
- **ThemeDemo** - https://github.com/czy1121/ThemeDemo  
  Databinding+LiveData轻松实现无重启换肤   
