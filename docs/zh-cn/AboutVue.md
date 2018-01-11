## About Vue
!> 发布vue到GitHub之后图片路径找不到
```js
更改 build/utils.js 文件中 ExtractTextPlugin 插件的options 配置：

if (options.extract) {
  return ExtractTextPlugin.extract({
    use: loaders,
    publicPath: '../../',         // 注意配置这一部分，根据目录结构自由调整
    fallback: 'vue-style-loader'
  })
} else {
  return ['vue-style-loader'].concat(loaders)
}
```
