---
title: 内置环境变量
---

> 开始支持版本 `1.0.0-beta.15`
> 注意：环境变量在代码中的使用方式，[参考](./best-practice.md#最佳撸码方式)

Taro 在编译时提供了一些内置的环境变量来帮助用户做一些特殊处理

## process.env.TARO_ENV

用于判断当前编译类型，目前有 `weapp` / `h5` / `rn` 三个取值，可以通过这个变量来书写对应一些不同环境下的代码，在编译时会将不属于当前编译类型的代码去掉，只保留当前编译类型下的代码，例如想在小程序和 H5 端分别引用不同资源

```jsx
if (process.env.TARO_ENV === 'weapp') {
  require('path/to/weapp/name')
} else if (process.env.TARO_ENV === 'h5') {
  require('path/to/h5/name')
}
```

同时也可以在 JSX 中使用，决定不同端要加载的内容

```jsx
render () {
  return (
    <View>
      {process.env.TARO_ENV === 'weapp' && <ScrollViewWeapp />}
      {process.env.TARO_ENV === 'h5' && <ScrollViewH5 />}
    </View>
  )
}
```
