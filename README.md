# crashsdk
调试查看崩溃日志信息sdk工具，避免adb快速打印定位找不到具体bug

## 接入使用步骤，
1、下载crashsdk，依赖项目中
```
implementation project(path: ':crashsdk')
```
2、初始化SDK，可在Application中初始化，其他位置也ok

```
//配置全局异常崩溃操作
        if (BuildConfig.DEBUG) { //调试开发状态开启
            CrashConfig.Builder.create()
                    .backgroundMode(CrashConfig.BACKGROUND_MODE_SILENT) //背景模式,开启沉浸式
                    .enabled(true) //是否启动全局异常捕获
                    .showErrorDetails(true) //是否显示错误详细信息
                    .showRestartButton(true) //是否显示重启按钮
                    .trackActivities(true) //是否跟踪Activity
                    .minTimeBetweenCrashesMs(2000) //崩溃的间隔时间(毫秒)
//                .errorDrawable(R.drawable.base_ic_launcher) //错误图标
                    .restartActivity(MainActivity.class) //重新启动后的activity
//                .errorActivity(YourCustomErrorActivity.class) //崩溃后的错误activity
//                .eventListener(new YourCustomEventListener()) //崩溃后的错误监听
                    .apply();
        }
```
到这里，接入就完成了,注释的可自由选择配置

效果如下

![image](https://github.com/LiWeiQiangAndroid/crashsdk/raw/master/png/WX20200419-012840.png)  


Demo使用示例看 [crashsdkdemo](https://github.com/LiWeiQiangAndroid/crashsdkdemo)

