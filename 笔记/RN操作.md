
### React





### React Native

#### TextInput

##### 输入框遮挡滚动

当ScrollView中包含TextInput，且TextInput的textAlign设置为right时，此时触摸到TextInput上面，拖动滑动会发现没有任何滑动效果，这是因为事件被TextInput消费掉了

https://www.jianshu.com/p/8b8c37472d9c



##### 安卓textinput内容置顶属性
`textAlignVertical="top"`

##### react native 键盘弹起遮挡textinput

使用原生组件KeyboardAvoidingView包裹，使用position属性可能导致内容无法被顶起



##### Android键盘弹出将底部顶起

将AndroidManifest.xml文件中找到android:windowSoftInputMode:将其值更改为stateAlwaysHidden|adjustPan

https://blog.csdn.net/Cui_xing_tian/article/details/90259792



##### view不会被安卓键盘顶起



##### List组件置顶与置底
`ListHeaderComponent={}`头部组件。可以是 React Component, 也可以是一个 render 函数，或者渲染好的 element。
`ListFooterComponent={}`尾部组件。可以是 React Component, 也可以是一个 render 函数，或者渲染好的 element

##### Android <text>不居中
includeFontPadding:false,


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

##### 上下左右
paddingVertical:相当于同时设置paddingTop和paddingBottom
paddingHorizontal:相当于同时设置paddingLeft和paddingRight

##### 修改手机状态栏
`{/* 增加判断，如果是安卓，则手机状态栏变成红色 */}`
`{Platform.OS === 'ios' ? null : <StatusBar backgroundColor="red" />}`
https://www.reactnative.cn/docs/statusbar


##### 标题栏iOS居中，android不居中
headerTitleAlign
如何对齐标题。可能的值：
* left
* center
默认为centeriOS和leftAndroid。


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

##### 安卓修改版本
android/app/build.gradle
```java
android {
    defaultConfig {
        versionName "1.0" //这个就是版本号
    }
}
```



##### 为方法数超过 64K 的应用启用 MultiDex

`android > app > build.gradle`

```java
android {
    defaultConfig {
        ...
        multiDexEnabled true
    }
    ...
}
```



# iOS后台计时器停止问题

短时间保活的方式有beginBackgroundTaskWithName；

``iOS>UTruck>AppDelegate.m``

https://developer.apple.com/documentation/uikit/uiapplication/1623051-beginbackgroundtask

另一种方法：


```js
if (timeLeft > 0) { //timeLeft是返回的倒计时的数值

   this.state.begin = 1;

   let that = this;

   let beginTime = new Date().getTime(); //点击发送验证码后的开始时间

   this.interval = setInterval(function () {

​    //计时器开始工作，每工作一次，返回一个新的时间newTime，进入后台，这个时间就停止了

​    let newTime = new Date().getTime();

​    //difftime就是两个时间之间的时间差

​    let difftime = (newTime - beginTime) / 1000;

​    //将difftime转换成整型

​    difftime = parseInt(difftime);

​    //如果开始时间和计时器工作时间的差大于等于90，则清除计时器，如果没有就显示倒计时

​    if (difftime > 89) {

​     clearInterval(that.interval);

​     callback(that);

​    } else {

​     that.setState({

​      timeLeft: 90 - difftime,

​     });

​    }

   }, 1000);

  }
```


https://blog.csdn.net/weixin_30419799/article/details/95000074?utm_medium=distribute.pc_relevant_bbs_down.none-task--2~all~first_rank_v2~rank_v25-21.nonecase&depth_1-utm_source=distribute.pc_relevant_bbs_down.none-task--2~all~first_rank_v2~rank_v25-21.nonecase



##### RN打包

##### RN安卓高德key
