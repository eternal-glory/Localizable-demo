
# Localizable-demo
国际化

[TOC]

##iOS启动图适配多语言

###1 首先准备各种尺寸的启动图(以下单位均为px)
* iPhone 5                        640x1136  （@2x）
* iPhone 6、7、8            750x1334 （@2x）
* iPhone6P、7P、8P      1242x2208 (@3x)
* iPhone X  S                    1125x2436 (@3x)
* iPhone XR                      828x1792   (@2x)
* iPhone XS Max              1242x2688 (@3x)

###2 多语言适配启动图
① 在工程的tagets确保这里的引用文件为 user asset catalog 也就是不引用图片管理器里面的启动图

![user asset catalog](https://upload-images.jianshu.io/upload_images/1870246-33ac8024b6952d7d.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/860)

②在工程目录新建一个Image文件夹，命名为LaunchImage ，把所有尺寸的启动图全部都拖进去，把图片重新命名（好像不是很重要，xcode6之后会自动管理启动图命名）如图

![](https://upload-images.jianshu.io/upload_images/1870246-854bc9a580864e81.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/249)

选中一张图片
![](https://upload-images.jianshu.io/upload_images/1870246-ecd9e4b46daf750c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/239)

③在info.plist添加UILaunchImages

```
<key>UILaunchImages</key>
    <array>
        <dict>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>7.0</string>
            <key>UILaunchImageName</key>
            <string>Default-568@2x</string>
            <key>UILaunchImageOrientation</key>
            <string>Portrait</string>
            <key>UILaunchImageSize</key>
            <string>{320,568}</string>
        </dict>
        <dict>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>7.0</string>
            <key>UILaunchImageName</key>
            <string>Default-800-667h@2x</string>
            <key>UILaunchImageOrientation</key>
            <string>Portrait</string>
            <key>UILaunchImageSize</key>
            <string>{375, 667}</string>
        </dict>
        <dict>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>7.0</string>
            <key>UILaunchImageName</key>
            <string>Default-800-Portrait-736h@3x</string>
            <key>UILaunchImageOrientation</key>
            <string>Portrait</string>
            <key>UILaunchImageSize</key>
            <string>{414, 736}</string>
        </dict>
        <dict>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>11.0</string>
            <key>UILaunchImageName</key>
            <string>Default-812h@3x</string>
            <key>UILaunchImageOrientation</key>
            <string>Portrait</string>
            <key>UILaunchImageSize</key>
            <string>{375, 812}</string>
        </dict>
        <dict>
            <key>UILaunchImageMinimumOSVersion</key>
            <string>11.0</string>
            <key>UILaunchImageName</key>
            <string>Default-896h@3x</string>
            <key>UILaunchImageOrientation</key>
            <string>Portrait</string>
            <key>UILaunchImageSize</key>
            <string>{414, 896}</string>
        </dict>
    </array>
```

其中第一个key为支持的最低版本，第二个key为该启动图名称，第三个key为启动图方向，我这里都是竖屏，横屏未适配，第四个key为启动图尺寸（物理分辨率)。

>至此 完成，需要注意的是你需要把app先卸载掉才能正确显示你设置的启动图，也就是说启动图在整个APP只产生一次，当你切换系统语言的时候需要卸载APP重新安装才会显示正确的启动图