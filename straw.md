# 麦秆（内测中）

麦秆（straw）是一个代理客户端，可以帮助用户快速使用 Embla 的节点。同时，麦秆 还会在本地进行节点检测，帮助用户快速找到最优的节点使用。

## 获取方式

麦秆目前处于内测阶段，暂时无法获取，如果您有兴趣参与内测，请联系我们。

## 使用方式

- 下载麦秆
- 在控制台输入`straw.exe login`，如果是linux系统，运行 `./straw login`, 按提示进行用户登录
- 在登陆完成后，输入`straw.exe`，如果是linux系统，运行 `./straw`，即可开始使用，当然您也可以选择双击麦秆图标来启动麦秆

## 第三方接入

如果您期望自己开发 GUI 或接入到自己的系统中，可以通过 `./straw.exe server`, 如果是linux系统，运行 `./straw server` 使 `straw` 暴露一个 HTTP 服务，您可以通过 HTTP 请求来控制 `straw`。

HTTP 服务的端口为 `25046`

可见如下接口配置直接导入 [Postman](https://www.postman.com/) 中使用

https://embla.cf/docs/straw.postman_collection.json