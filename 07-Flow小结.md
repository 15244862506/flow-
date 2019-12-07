# Flow小结

## Flow是什么？
Static Type Checker For JavaScript

静态类型检查工具

## Flow能做什么？

Flow能够给JavaScript提供静态类型检查的能力，其实就是为javascript添加了一个编译过程。


## Flow的使用
1. 安装Flow
```
npm i flow-bin -D
```
2. 需要编写Flow代码
   * 通过注释的方式为代码添加类型 （不会对js代码产生任何更改，影响）
   * 通过直接在js代码中书写类型 （改变了js代码的结构，需要通过babel进行转码之后，才能够正常的运行）

```js
// 文件中需要添加一个标记 告诉flow当前文件需要进行类型检查！
// @flow 

var 变量 /*: 类型*/ = 数据

var 变量: 类型 = 数据
```

3. 如果使用的是第二种方式，则需要配合babel使用
```
npm install babel-cli babel-preset-flow -D

// 通过babel进行转码之后，代码就可以正常运行
```

1. 通过注释的方式添加 (不会改写js代码，代码在添加完类型之后仍然可以正常运行)
2. 通过直接给数据添加类型，改写js代码，如果要正常运行，需要使用babel进行转码

## 使用flow进行类型检查
0. 在pacakge.json文件中，scripts属性中添加flow命令

1. 需要为flow创建一个配置文件.flowconfig
```shell
npm run flow init
```

2. 执行类型检查
```shell
npm run flow
```

## 使用babel对flow代码进行转码
如果给数据添加类型声明是通过第二种方式，直接修改的js代码，那么代码是不能正常运行的

我们需要通过babel对代码进行转码之后才能正常运行

1. 安装babel以及presets
```shell
npm i babel-cli babel-preset-flow -D
```
2. 配置package.json添加build命令调用babel
···json
{
    "scripts": {
        "build": "babel ./src -d ./dist"
    }
}
···
3. 执行build命令对文件进行转换
```shell
npm run build
```