# @ flyskywhy / react-native-smart-barcode

https://www.npmjs.com/package/@flyskywhy/react-native-smart-barcode



## 安装

对于RN> = 0.60

```shell
npm install @flyskywhy/react-native-smart-barcode --save
cd ios
pod install
```



## 安装（Android）

- 在AndroidManifest.xml中，添加摄像头权限

```
...
<uses-permission android:name="android.permission.CAMERA"/>
<uses-permission android:name="android.permission.VIBRATE"/>
<uses-feature android:name="android.hardware.camera"/>
<uses-feature android:name="android.hardware.camera.autofocus"/>
...
```



## 安装（iOS）

- 在您的info.plist中添加属性`Privacy - Camera Usage Description`（适用于ios 10）



## 完整演示

参见[ReactNativeComponentDemos](https://github.com/cyqresig/ReactNativeComponentDemos)



## 用法

```jsx
import React, { Component } from 'react';
import { View, StyleSheet, Alert } from 'react-native';

import Barcode from '@flyskywhy/react-native-smart-barcode';
import TimerEnhance from 'react-native-smart-timer-enhance';

// 扫描页面
class BarcodeTest extends Component {
  // 构造
  constructor(props) {
    super(props);
    // 初始状态
    this.state = {
      viewAppear: false,
    };
  }

  render() {
    return (
      <View style={{ flex: 1, backgroundColor: 'black' }}>
        {/* {this.state.viewAppear ?  */}
        <Barcode style={{ flex: 1 }} ref={(component) => (this._barCode = component)} onBarCodeRead={this._onBarCodeRead} />
        {/* : null} */}
      </View>
    );
  }

  componentDidMount() {
    let viewAppearCallBack = (event) => {
      console.log('event', event);
      this.setTimeout(() => {
        this.setState({
          viewAppear: true,
        });
      }, 255);
    };
    this._listeners = this.props.navigation.addListener('didfocus', viewAppearCallBack);
  }

  componentWillUnmount() {
    this._listeners();
  }

  _onBarCodeRead = (e) => {
    console.log(`e.nativeEvent.data.type = ${e.nativeEvent.data.type}, e.nativeEvent.data.code = ${e.nativeEvent.data.code}`);
    this._stopScan();

    Alert.alert(e.nativeEvent.data.type, e.nativeEvent.data.code, [{ text: 'OK', onPress: () => this._startScan() }]);
  };

  _startScan = (e) => {
    this._barCode.startScan();
  };

  _stopScan = (e) => {
    this._barCode.stopScan();
  };
}

export default TimerEnhance(BarcodeTest);

```



## Props

| Prop                   | Type   | Optional | Default   | Description                                       |
| :--------------------- | :----- | :------- | :-------- | :------------------------------------------------ |
| barCodeTypes           | array  | Yes      |           | determines the supported barcodeTypes             |
| scannerRectWidth       | number | Yes      | 255       | determines the width of scannerRect               |
| scannerRectHeight      | number | Yes      | 255       | determines the height of scannerRect              |
| scannerRectTop         | number | Yes      | 0         | determines the top shift of scannerRect           |
| scannerRectLeft        | number | Yes      | 0         | determines the left shift of scannerRect          |
| scannerLineInterval    | number | Yes      | 3000      | determines the interval of scannerLine's movement |
| scannerRectCornerColor | string | Yes      | `#09BB0D` | determines the color of scannerRectCorner         |

