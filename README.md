# cosmo


仓库

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
  
## UI

- **dialog** - https://github.com/czy1121/dialog      
  AlertDialog扩展(tip/alert/confirm/choose)   
  自定义对话框(CustomDialog/BottomDialog/DropdownDialog/SideDialog)   
  LoadingDialog/InputDialog/ActionSheetDialog/PickerDialog
- **bk** - https://github.com/czy1121/bk    
  BKDrawable/BKFrameLayout/BKLinearLayout/BKTextView 可自定义 背景色/渐变/圆角/阴影/描边
  
  
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
