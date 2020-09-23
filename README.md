

### git操作





### React





### React Native

#### TextInput

##### 安卓textinput内容置顶属性
`textAlignVertical="top"`

##### react native 键盘弹起遮挡textinput

使用原生组件KeyboardAvoidingView包裹，使用position属性可能导致内容无法被顶起

##### view不会被安卓键盘顶起



##### List组件置顶与置底



##### React Native调试时，查看console打印
1）Android
`react-native log-android`
2）Ios
`react-native log-ios`

##### 强制刷新
`react-native start --reset-cache`

##### react native判断设备
`import React, {Platform} from 'react-native';
{Platform.OS === 'ios' ? 200 : 100}`

##### 上下左右
paddingVertical:相当于同时设置paddingTop和paddingBottom
paddingHorizontal:相当于同时设置paddingLeft和paddingRight

##### 修改手机状态栏
`{/* 增加判断，如果是安卓，则手机状态栏变成红色 */}`
`{Platform.OS === 'ios' ? null : <StatusBar backgroundColor="red" />}`
https://www.reactnative.cn/docs/statusbar

##### 上传图片
安卓只支持uri，ios支持uri和url，安卓和苹果图片路径也不相同

##### Drawer组件在安卓上的问题
Drawer的属性placement='top'时，抽屉会在页面顶部有一个不占文档流的样式

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

##### RN打包

##### RN安卓高德key



### MAC
##### item

##### Oh My Zsh

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
