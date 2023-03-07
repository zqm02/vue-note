# 分析优化

由于`vue-cli`是利用`webpack`进行打包，我们仅需要一个`webpack`插件`webpack-bundle-analyzer`即可分析打包结果

为了避免在开发环境中启动`webpack-bundle-analyzer`，我们仅需要添加以下代码即可

```js
const BundleAnalyzerPlugin =
  require("webpack-bundle-analyzer").BundleAnalyzerPlugin;

//vue.config.js

module.exports = {
  //通过configureWebpack选项，可对webpack进行额外的配置
  //该配置最终会和vue-cli的默认配置进行合并(webpack-merge)
  configureWebpack: {
    plugins: [new BundleAnalyzerPlugin()],
  },
};
```

# 优化公共库打包体积

## 使用 CDN

cdn 全称为 Content Delivery Network，称之为内容分发网络

它的基本原理是：架设多台服务器，这些服务定期从资源站拿取资源保存本地，到让不同地域的用户能够访问最近的服务器获得资源

## 启用现代模式
