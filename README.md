# cuteQQ

基于 [aardio](https://www.aardio.com/) 编写的局域网即时通讯工具，包含客户端与服务器两部分。

## 功能特性

- 注册 / 登录 / 修改密码 / 注销账号，密码采用「盐 + SHA-256」哈希存储
- 好友管理：添加 / 删除好友，好友列表
- 消息收发与离线消息（服务器 SQLite 存储，上线自动补发）
- 文件传输：分片发送，单文件上限 20MB，同名文件自动加前缀防覆盖
- 心跳保活：客户端 30 秒一跳，服务器巡检并清理死连接
- 断线自动重连：失败自动重试并恢复登录会话
- 顶号踢线：账号异地登录时旧连接被强制下线
- 输入校验：用户名白名单、密码长度、文件名清洗等安全加固

## 目录结构

```
cuteQQ/
├── client/          # 客户端（aardio 工程）
│   ├── default.aproj
│   ├── main.aardio
│   ├── dlg/         # 各窗口界面
│   ├── lib/         # wsHelper / chatBox / userList 等库
│   └── res/         # 图标、头像、提示音
└── server/          # 服务器（aardio 工程）
    ├── default.aproj
    ├── main.aardio
    ├── lib/         # chatServer / db / security 等库
    └── res/         # 默认头像
```

## 运行方式

1. 使用 aardio IDE 打开 `server/default.aproj`，发布服务器端程序并运行（默认监听 8080 端口）；
2. 使用 aardio IDE 打开 `client/default.aproj`，发布客户端程序并运行；
3. 客户端首次启动后，在设置中填写服务器地址（默认 `ws://127.0.0.1:8080`），注册账号即可使用。

> 服务器运行时会生成 SQLite 数据库文件（含用户与消息数据），已被 `.gitignore` 排除，请勿提交。

> AI生成
