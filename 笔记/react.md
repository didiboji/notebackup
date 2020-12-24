[MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript)

[javascript.info](http://javascript.info/)

[社区支持论坛](https://react.docschina.org/community/support.html)

# 在页面中引入

##### 在静态html页面上引入react



```html
通过CDN获取UMD版本
通过设置跨域属性crossorigin，可以获取跨域的具体错误信息
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>

    <script src="https://unpkg.com/babel-standalone@6.26.0/babel.js"></script>
  
	<body>
    <div id="root"></div>

    <script type="text/babel">
      // React code will go here
    </script>
  </body>
```

react会替换DOM容器内任何已有的内容

```jsx
//在DOM中添加一个h1标签：
ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);
```

- [React](https://reactjs.org/docs/react-api.html) -React顶级API
- [React DOM-](https://reactjs.org/docs/react-dom.html)添加特定于DOM的方法
- [Babel-](https://babeljs.io/)一种JavaScript编译器，可让我们在旧版浏览器中使用ES6 +

创建一个React组件

```jsx
class app extends React.Component{
  render(){
    return ()
  }
}
ReactDOM.render(<app />,getElementById('root'));
```

完整代码
```jsx
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />

    <title>Hello React!</title>
2.引入react，react-dom
<script crossorigin src="https://unpkg.com/react@16/umd/react.development.js"></script>
<script crossorigin src="https://unpkg.com/react-dom@16/umd/react-dom.development.js"></script>
    和babel
    <script src="https://unpkg.com/babel-standalone@6.26.0/babel.js"></script>
  </head>

  <body>
    1.新建DOM
    <div id="root"></div> 

    <script type="text/babel">
      3.使用ES6类创建一个称为的React组件App
      class App extends React.Component {
        render() {
          return <h1>Hello world!</h1>
        }
      }
4.使用React DOMrender()方法将App我们创建的类渲染到rootHTML中的div中
      ReactDOM.render(<App />, document.getElementById('root'))
    </script>
  </body>
</html>
```



##### 组件重用

##### 压缩js代码

```html
<script src="https://unpkg.com/react@16/umd/react.production.min.js" crossorigin></script>
<script src="https://unpkg.com/react-dom@16/umd/react-dom.production.min.js" crossorigin></script>
```

[压缩方式](https://gist.github.com/gaearon/42a2ffa41b8319948f9be4076286e1f3)

##### 使用jsx

引入jsx

```jsx
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
可以在任何 `<script>` 标签内使用 JSX，方法是在为其添加 `type="text/babel"` 属性
//或
安装node.js
在终端上跳转到你的项目文件夹，然后粘贴这两个命令：
步骤 1： 执行 npm init -y （如果失败，这是修复办法）
步骤 2： 执行 npm install babel-cli@6 babel-preset-react-app@3
可以继续使用 <script> 标签而不做任何更改
```

```jsx
//js
return React.createElement(
	'button',
  {onClick:()=>{this.setState({liked:true})} },
  'Like'
)
//jsx
return (<button onClick={()=>{this.setState({liked:true}) }}>
  Like
</button>)
```

运行 JSX 预处理器

创建一个名为 `src` 的文件夹并执行这个终端命令：<font color=red>src</font>

```powershell
npx babel --watch src --out-dir . --presets react-app/prod
```

# 创建新的React应用

```shell
npx create-react-app appname
```

简单组件

```jsx
const SimpleComponent = ()=>{
  return <div>Example</div>
}
```

# 组件

##### 函数组件

```jsx
function(props){
  return <div>输出{props.name}</div>
}
```

##### 类组件

```jsx
class App extend React.Component{ //定义class组件需要继承React.Component
  render(){
    return <h1>{this.props.name}</h1>
  }
}
```

React Element(元素),可以是DOM标签，也可以是组件

<font color=red>Props的只读性</font>,组件不能修改自身的Props

纯函数不会更改自己的入参



##### props和state可能会异步更新

```jsx
this.setState((state,props)=>{
  
})
```



##### 一般不需要使用addEventListener为已创建的DOM元素添加监听器，只需要在该元素初始渲染的时候添加监听器即可



##### jsx回调中绑定this的三种方法



##### &&运算符

根据左侧的判断来决定是否渲染右侧的内容

```jsx
{arr.length > 0 && 
<h2>这个数组长{arr.length}</h2>}
```

