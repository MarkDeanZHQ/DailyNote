# openAI qq机器人教程

大佬可通过以下三个网址自行完成部署

[mirai -- QQ机器人安装](https://github.com/mamoe/mirai)

[openAI插件](https://mirai.mamoe.net/topic/1848/openai-gpt-chatbot-插件?_=1671094139535)

[中国区注册OpenAI账号试用ChatGPT指南](https://readdevdocs.com/blog/makemoney/中国区注册OpenAI账号试用ChatGPT指南.html#注册-openai-账号)

小白或者想快速安装、不想在入门上花费学习成本的朋友，可参考本文。


思维导图
```mermaid
graph TB
A([mirai 机器人安装])
B[openAI 插件安装]
C[openAI官方注册]
D((大功告成))
A--->B
A--->C
B--->D
C--->D

```


此处提供两个平台 windows 和 Linux的安装方式
1. [windows 部署](#windows)
2. [linux 部署](#linux)


## 关于
看完本文有不懂的，或者有报错的朋友可以进群寻求帮助。[QQ群](https://qm.qq.com/cgi-bin/qm/qr?k=njfFgtevX5P0ErRoQY6EW_jM1evppA47&authKey=3LxW0ztWX8ub73jR6sPE4M38Mybv6fR2o1xoO%2BScA0Vbm1y6thzFfj75P6NaV2r4&noverify=0&group_code=767505703)

## windows

### 安装 [Mirai](https://github.com/mamoe/mirai)
* 安装文件下载： [mcl-console-loader](https://ghproxy.com/https://github.com/iTXTech/mirai-console-loader/releases/download/v2.1.2/mcl-2.1.2.zip)
* 下载后解压，双击 mcl.cmd
* 等待运行完成

官方文档：[mirai-console-loader 官方文档](https://github.com/iTXTech/mirai-console-loader)

#### 安装 [mirai-api-http-v2](https://github.com/project-mirai/mirai-api-http)
* 进入 `cmd` 并进入 `mirai-console-loader`文件夹下
* 运行 `.\mcl --update-package net.mamoe:mirai-api-http --channel stable-v2 --type plugin`
* 启动 mcl 完成自动更新和启动

#### 配置 mirai-api-http-v2
*   打开 `mcl/config/net.mamoe.mirai-api-http/setting.yml`，将下面的内容复制覆盖粘贴到文件中
*   若无此文件请检查 `mcl` 是否被成功添加并且添加后启动过一次 `mcl`，若没有请完成前文所述步骤再进行此步骤

```py
adapters:
  - http
  - ws
debug: false
enableVerify: true
verifyKey: 1234567890 # 你可以自己设定, 这里作为示范, 请保持和 config.yaml 中 verify_key 项一致
singleMode: false
cacheSize: 4096 # 可选, 缓存大小, 默认4096. 缓存过小会导致引用回复与撤回消息失败
adapterSettings:
  ## 详情看 http adapter 使用说明 配置
  http:
    host: localhost
    port: 23456 # 端口
    cors: [*]

  ## 详情看 websocket adapter 使用说明 配置
  ws:
    host: localhost
    port: 23456 # 端口
    reservedSyncId: -1 # 确保为 -1, 否则 WebsocketAdapter(Experimental) 没法正常工作.
```

##### 配置自动登录
* 登录 输入 `/login <QQ号> <QQ密码>`
* 配置自动登录 输入 `/autoLogin add <你的QQ号> <你的QQ密码>` 

常用命令：
* /help     # 查看指令帮助
* /logout \<qq\>    # 登出一个账号
* /autoLogin list    # 查看自动登录账号列表
* /autoLogin clear    # 清除所有配置
* /status     # 获取 Mirai Console 运行状态
* /stop     # 关闭 Mirai Console

##### 登录QQ验证
执行 `.\mcl` 启动 `mirai-console`

如果直接显示 `Event: BotOnlineEvent(bot=Bot(<你的QQ号>))`，并有收到新消息，那么恭喜你，你已经完成了 `mirai` 方面的配置了

出现如下情况
```
需要滑动验证码，完成后请输入ticket
url:http://xxx.xxx.xxx
```


*   情况一：有弹窗，并且使用的是 `Android` 系统手机（或使用电脑模拟器）
    *   点击 `Open with TxCaptchaHelper`，下载 [TxCaptchaHelper](https://ghproxy.com/https://github.com/KasukuSakura/mirai-login-solver-sakura/releases/download/v0.0.7/apk-release.apk) 并安装
    *   输入弹窗中的4位请求码并完成滑动验证，随后在电脑端点击确定
*   情况二：没弹窗（如 Linux NoGUI 用户）或者使用的 `IOS` 系统手机/其他不能运行 `apk` 程序系统的手机
    *   在电脑上打开浏览器，输入程序提供的url，应当会出现滑动认证的画面，此时先不要进行认证
    *   单击 `F12` 键，会出现一个 `DevTool`，找到上方选项卡，点击 `Network` 选项，再点击下方的 `Fetch/XHR` 选项
    *   完成滑动验证，此时在 `DevTool` 界面中应会出现新的请求，找到其中名为 `cap_union_new_verify` 选项卡，点击其中的 `Preview` 选项卡，在其中找到 `ticket` 的值填入 `mcl` 并回车
    *   gif演示：![浏览器获取ticket演示](vx_images/554032018239686.gif)

若显示需要手机验证码登录按提示操作即可


#### openAI 插件安装
1. [openai](https://github.com/RIvance/mirai-openai-gpt-chatbot)插件下载：[mirai-openai-chatbot-v0.2.jar](https://ghproxy.com/https://github.com/RIvance/mirai-openai-gpt-chatbot/releases/download/v0.2/mirai-openai-chatbot-v0.2.jar)
2. 移动该文件到 `mcl/plugins` 文件夹下
3. 启动 mcl 更新插件后，`Ctrl+C`退出
4. 进入 `mcl/config/org.ivance.chatbot`文件夹下,编辑 ChatBotPluginConfig.yml 文件
填入 api key![](vx_images/92541619227553.png)


关键字自定义![触发关键字 自定义](vx_images/188072219236943.png)


#### openAI api获取

进入[中国区注册OpenAI账号试用ChatGPT指南](https://readdevdocs.com/blog/makemoney/中国区注册OpenAI账号试用ChatGPT指南.html#前期准备)
注册后即可进入[openai 官网](https://openai.com/)获取api 


提供我的一个API：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
请谨慎分享，使用人数过多可能会失效。

之后启动 mcl 即可使用。

## linux

### 安装 [Mirai](https://github.com/mamoe/mirai)

#### 安装 [mcl-console-loader](https://ghproxy.com/https://github.com/iTXTech/mirai-console-loader/releases/download/v2.1.2/mcl-2.1.2.zip)
*  在终端中执行如下命令：
    
    `mkdir mcl
    cd mcl
    wget https://github.com/iTXTech/mirai-console-loader/releases/download/v2.1.2/mcl-2.1.2.zip
    unzip mcl-2.1.2.zip
    chmod +x mcl
    ./mcl`
* 等待运行完成
* `Ctrl + C` 退出 `mirai-console`

官方文档：[mirai-console-loader 官方文档](https://github.com/iTXTech/mirai-console-loader)

#### 安装 [mirai-api-http-v2](https://github.com/project-mirai/mirai-api-http)

首先，我们进入 `mcl` 文件夹下
*   按照 `mirai-api-http` 的 `README`，在终端中运行 `./mcl --update-package net.mamoe:mirai-api-http --channel stable-v2 --type plugin`
*   （当出现网络报错时执行）切换 `mirai-console-loader` 的 `repo`，运行 `./mcl --mrm-use forum`
*   启动 `mcl` 完成自动更新和启动

#### 配置 mirai-api-http-v2

*   打开 `mcl/config/net.mamoe.mirai-api-http/setting.yml`，将下面的内容复制覆盖粘贴到文件中
*   若无此文件请检查 `mcl` 是否被成功添加并且添加后启动过一次 `mcl`，若没有请完成前文所述步骤再进行此步骤

```py
adapters:
  - http
  - ws
debug: false
enableVerify: true
verifyKey: 1234567890 # 你可以自己设定, 这里作为示范, 请保持和 config.yaml 中 verify_key 项一致
singleMode: false
cacheSize: 4096 # 可选, 缓存大小, 默认4096. 缓存过小会导致引用回复与撤回消息失败
adapterSettings:
  ## 详情看 http adapter 使用说明 配置
  http:
    host: localhost
    port: 23456 # 端口
    cors: [*]

  ## 详情看 websocket adapter 使用说明 配置
  ws:
    host: localhost
    port: 23456 # 端口
    reservedSyncId: -1 # 确保为 -1, 否则 WebsocketAdapter(Experimental) 没法正常工作.

```

##### 配置自动登录
* 登录 输入 `/login <QQ号> <QQ密码>`
* 配置自动登录 输入 `/autoLogin add <你的QQ号> <你的QQ密码>` 

常用命令：
* /help     # 查看指令帮助
* /logout \<qq\>    # 登出一个账号
* /autoLogin list    # 查看自动登录账号列表
* /autoLogin clear    # 清除所有配置
* /status     # 获取 Mirai Console 运行状态
* /stop     # 关闭 Mirai Console


##### 登录QQ验证
执行 `.\mcl` 启动 `mirai-console`

如果直接显示 `Event: BotOnlineEvent(bot=Bot(<你的QQ号>))`，并有收到新消息，那么恭喜你，你已经完成了 `mirai` 方面的配置了

出现如下情况
```
需要滑动验证码，完成后请输入ticket
url:http://xxx.xxx.xxx
```


*   情况一：有弹窗，并且使用的是 `Android` 系统手机（或使用电脑模拟器）
    *   点击 `Open with TxCaptchaHelper`，下载 [TxCaptchaHelper](https://ghproxy.com/https://github.com/KasukuSakura/mirai-login-solver-sakura/releases/download/v0.0.7/apk-release.apk) 并安装
    *   输入弹窗中的4位请求码并完成滑动验证，随后在电脑端点击确定
*   情况二：没弹窗（如 Linux NoGUI 用户）或者使用的 `IOS` 系统手机/其他不能运行 `apk` 程序系统的手机
    *   在电脑上打开浏览器，输入程序提供的url，应当会出现滑动认证的画面，此时先不要进行认证
    *   单击 `F12` 键，会出现一个 `DevTool`，找到上方选项卡，点击 `Network` 选项，再点击下方的 `Fetch/XHR` 选项
    *   完成滑动验证，此时在 `DevTool` 界面中应会出现新的请求，找到其中名为 `cap_union_new_verify` 选项卡，点击其中的 `Preview` 选项卡，在其中找到 `ticket` 的值填入 `mcl` 并回车
    *   gif演示：![浏览器获取ticket演示](vx_images/554032018239686.gif)

若显示需要手机验证码登录按提示操作即可




#### openAI 插件安装
1. [openai](https://github.com/RIvance/mirai-openai-gpt-chatbot)插件下载：[mirai-openai-chatbot-v0.2.jar](https://ghproxy.com/https://github.com/RIvance/mirai-openai-gpt-chatbot/releases/download/v0.2/mirai-openai-chatbot-v0.2.jar)
2. 移动该文件到 `mcl/plugins` 文件夹下
3. 启动 mcl 更新插件后，`Ctrl+C`退出
4. 进入 `mcl/config/org.ivance.chatbot`文件夹下,编辑 ChatBotPluginConfig.yml 文件
填入 api key![](vx_images/92541619227553.png)


关键字自定义![触发关键字 自定义](vx_images/188072219236943.png)


#### openAI api获取

进入[中国区注册OpenAI账号试用ChatGPT指南](https://readdevdocs.com/blog/makemoney/中国区注册OpenAI账号试用ChatGPT指南.html#前期准备)
注册后即可进入[openai 官网](https://openai.com/)获取api 


提供我的一个API：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
请谨慎分享，使用人数过多可能会失效。

之后启动 mcl 即可使用。