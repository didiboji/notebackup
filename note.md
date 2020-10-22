

### git操作

创建分支的同时切换到该分支上，命令如下：

```
git checkout -b [branch name]
```

git checkout -b [branch name] 的效果相当于以下两步操作：

```
git branch [branch name]
git checkout [branch name]
```
将新分支推送到github
```powershell
git push origin [branch name]
```

``git push origin --delete Chapater6``  可以删除远程分支Chapater6

``git branch -d Chapater8`` 可以删除本地分支（在主分支中）

SSH





### React





### React Native

#### TextInput

##### 安卓textinput内容置顶属性
`textAlignVertical="top"`

##### react native 键盘弹起遮挡textinput

使用原生组件KeyboardAvoidingView包裹，使用position属性可能导致内容无法被顶起

##### view不会被安卓键盘顶起



##### List组件置顶与置底
`ListHeaderComponent={}`头部组件。可以是 React Component, 也可以是一个 render 函数，或者渲染好的 element。
`ListFooterComponent={}`尾部组件。可以是 React Component, 也可以是一个 render 函数，或者渲染好的 element

##### Text组件隐藏部分内容

Text组件的属性`ellipsizeMode`

这个属性通常和下面的 `numberOfLines` 属性配合使用，表示当 Text 组件无法全部显示需要显示的字符串时如何用省略号进行修饰。

该属性有如下 4 种取值:

- `head` - 从文本内容头部截取显示省略号。例如： "...efg"
- `middle` - 在文本内容中间截取显示省略号。例如： "ab...yz"
- `tail` - 从文本内容尾部截取显示省略号。例如： "abcd..."
- `clip` - 不显示省略号，直接从尾部截断。

默认是 tail

`numberOfLines`

用来当文本过长的时候裁剪文本。包括折叠产生的换行在内，总的行数不会超过这个属性的限制。

此属性一般和`ellipsizeMode`搭配使用。

##### 上下左右
paddingVertical:相当于同时设置paddingTop和paddingBottom
paddingHorizontal:相当于同时设置paddingLeft和paddingRight

##### Drawer组件在安卓上的问题
Drawer的属性placement='top'时，抽屉会在页面顶部有一个不占文档流的样式



##### React Native调试时，查看console打印
1）Android
`react-native log-android`
2）Ios
`react-native log-ios`

##### 强制刷新
`react-native start --reset-cache`

##### 清除缓存

```xcrun simctl erase all```

##### react native判断设备
`import React, {Platform} from 'react-native';
{Platform.OS === 'ios' ? 200 : 100}`


##### 修改手机状态栏
`{/* 增加判断，如果是安卓，则手机状态栏变成红色 */}`
`{Platform.OS === 'ios' ? null : <StatusBar backgroundColor="red" />}`
https://www.reactnative.cn/docs/statusbar

##### 上传图片
安卓只支持uri，ios支持uri和url，安卓和苹果图片路径也不相同

##### 安卓修改版本
android/app/build.gradle
```java
android {
    defaultConfig {
        versionName "1.0" //这个就是版本号
    }
}
```



##### RN打包

##### RN安卓高德key



### MAC

新建文件

```touch fileName.xxx（fileName是文件名，xxx是后缀名）```



##### Xcode

`yarn react-native run-ios`只是运行应用的方式之一。你也可以在 Xcode 中直接运行应用。注意 0.60 版本之后的主项目文件是`.xcworkspace`，不是`.xcodeproj`。



模拟定位

1. 新建一个gpx文件

```shell
<?xml version="1.0" encoding="UTF-8" ?>
<gpx version="1.1"
    creator="GMapToGPX 6.4j - http://www.elsewhere.org/GMapToGPX/"
    xmlns="http://www.topografix.com/GPX/1/1"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.topografix.com/GPX/1/1 http://www.topografix.com/GPX/1/1/gpx.xsd">
    <wpt lat="31.23555959" lon="121.50097295">   这是上海中心的WGS-84坐标
    </wpt>
</gpx>
```



2. Product > Scheme > Edit Scheme > Run > Options (快捷键: cmd + shift + < )

3. 勾选「Allow Location Simulation」，并在「Default Location」选择 gpx 文件

4. 重新编译



##### item

##### Oh My Zsh

https://github.com/ohmyzsh/ohmyzsh

切到zsh

```shell
chsh -s /bin/zsh
```

切回bash

```shell
chsh -s /bin/bash
```

如果使用zsh，需要重新配置环境

bash 的环境变量是`.bash_profile`文件。
 zsh 的环境变量是`.zshrc`文件。

PS：如果从 bash 切换到 zsh，但想保留 bash 所设置的环境变量，可在 `.zshrc`文件末尾添加 `source ~/.bash_profile` 保存退出，并重启终端即可使用 bash 的环境变量。
链接：https://www.jianshu.com/p/8d822ce0d425
