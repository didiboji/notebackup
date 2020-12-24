# MAC操作

新建文件

```touch fileName.xxx（fileName是文件名，xxx是后缀名）```



## Xcode

`yarn react-native run-ios`只是运行应用的方式之一。你也可以在 Xcode 中直接运行应用。注意 0.60 版本之后的主项目文件是`.xcworkspace`，不是`.xcodeproj`。



### 模拟定位

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



## item


### Oh My Zsh

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



### 在终端内使用命令打开vscode

打开vscode，快捷键command + shift + p 打开命令面板，输入 `shell command’`，找到: “Install ‘code’ command in PATH”，点击就可以了

在命令行中执行`code`就可以打开VS Code