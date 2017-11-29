# 使用vue-cli创建项目后配置

### 1.修改默认端口

`config/index.js` 8080变更为6002

### 2.Eslint语法检查太过严格，使用自己的规则。

`.eslintrc.js`修改成自己的规则


### 3.添加Less

a.引入less和less-loader库
    
```
cnpm install less less-loader --save-dev
```

b.不需要做任何操作了，因为只要安装了less，vue-cli就会把less配置到项目中去。


### 4.给项目添加favicon.ico

`build/webpack.dev.config.js` 中的`new HtmlWebpackPlugin({`节点内`inject: true`后，添加：

`favicon: 'src/assets/img/favicon.ico'`

文件`build/webpack.dev.config.js` 同样的位置添加。



### 5.设置http代理

`config/index.js`在dev节点下添加：
```
proxyTable: {
      '/api': {
        target: 'http://127.0.0.1:9090',
        changeOrigin: true,
        pathRewrite: {
          '^/api': '/api'
        }
      }
    },
```