# AngularWithNetCore
如果你需要创建或编辑一个 proxy.conf.json 文件，通常这个文件用于配置代理设置，特别是在开发环境中，比如 Angular + NetCoreApi, 你需要用angular来请求Netcore web api, 整个配置文件可以避免跨域的问题。

## 以下是一个示例 proxy.conf.json 文件的内容，以及如何配置它。

示例 proxy.conf.json

### 示例代码



```
{
  "/api": {
    "target": "http://localhost:3000",
    "secure": false,
    "changeOrigin": true,
    "logLevel": "debug"
  }
}
```

## 说明
- "/api": 这是你希望代理的请求路径前缀。所有以 /api 开头的请求都会被代理到目标服务器。
- "target": 这是目标服务器的地址(Netcore web API)。在这个例子中，所有 /api 请求都会被转发到 http://localhost:3000。
- "secure": 如果目标服务器使用 HTTPS，设置为 true。在开发环境中，通常设置为 false。
- "changeOrigin": 设置为 true 可以修改请求头中的 Origin 字段，以匹配目标 URL。
- "logLevel": 设置日志级别，可以帮助调试代理请求。
使用 proxy.conf.json
如果你在使用 Angular CLI，可以在 angular.json 文件中配置代理：

```
"serve": {
  "options": {
    "proxyConfig": "src/proxy.conf.json"
  }
}
```

# 总结
proxy.conf.json 文件用于配置代理设置，帮助在开发环境中转发 API 请求。根据你的需求，可以修改目标地址和其他设置
