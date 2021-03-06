# wechaty-robot

[![](https://img.shields.io/badge/Powered%20By-Wechaty-yellowgreen.svg)](https://github.com/wechaty/wechaty)
[![](https://img.shields.io/badge/Wechaty-%E5%BC%80%E6%BA%90%E6%BF%80%E5%8A%B1%E8%AE%A1%E5%88%92-orange.svg)](https://github.com/juzibot/Welcome/wiki/Everything-about-Wechaty)

基于 wechaty-puppet-padplus 协议的微信机器人助手，适用于微信好友管理及群管理，可以帮你省去一系列重复繁琐的操作。

### 功能

- [x] 自动处理好友请求
- [x] 私聊关键字回复
- [x] 通过指令完成指定任务
- [x] 群管理（拉人进群、踢人出群、@群成员）
- [x] 发送图片、链接、名片

#### 结构

```js
|-- img                     # 储项目所使用到的图片与其他相应资源。
|-- src/
|---- listeners/
|------ on-scan.js          # 机器人需要扫描二维码时监听回调
|------ on-room.js          # 进入房间监听回调
|------ on-message.js       # 消息监听回调
|------ on-friend.js        # 好友添加监听回调
|---- config.js             # 配置文件
|---- index.js              # 入口文件
|-- package.json
```

### 依赖

wechaty：wechaty 核心库<br />wechaty-puppet-padplus：wechaty 的 ipad 协议实现

### 代码介绍

```javascript
// init
const bot = new Wechaty({
  puppet: new PuppetPadplus({
    token: config.token
  }),
  name: config.name
})

bot.on('scan', onScan) // 机器人需要扫描二维码时监听
bot.on('login', (user) => log.info('StarterBot', '%s login', user))
bot.on('logout', (user) => log.info('StarterBot', '%s logout', user))
bot.on('message', onMessage(bot)) // 消息监听
bot.on('friendship', onFriendShip) // 添加好友监听
bot.on('room-join', onRoomJoin) // 加入房间监听

bot
  .start()
  .then(() => {
    log.info('StarterBot', 'Starter Bot Started.')
  })
  .catch((e) => log.error('StarterBot', e))
```

### 本地运行

1. 克隆项目

```shell
git clone https://github.com/zoudingyi/wechaty-robot.git

cd wechaty-robot
```

2. 安装依赖

```shell
npm install
```

3. 启动项目

```shell
npm run serve
```

### 使用

修改`config`配置

    打开`src/config.js` 文件，将里面的配置改为自己的。然后就可以运行了

### 效果图

![效果图](./img/chat.png)
