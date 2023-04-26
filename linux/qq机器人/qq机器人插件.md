# qq机器人插件


## bilibili订阅
bilibili-dynamic-mirai-plugin-3.2.1.mirai2.jar
[b站动态-直播检测插件-v3船新版本-低延迟-美观-可配置性高](https://mirai.mamoe.net/topic/792/b站动态-直播检测插件-v3船新版本-低延迟-美观-可配置性高)


### 欢迎 与bilibili 卡片 绑定
simple-welcome-plugin-1.1.0.mirai.jar
[simple-welcome-plugin](https://github.com/Colter23/simple-welcome-plugin)


## 以图搜图 pixiv插件
[6?page=1](https://mirai.mamoe.net/topic/461/pixiv插件-查看排行榜-以图搜图-以图搜番-查看原图-查看作者作品-搜标签/6?page=1)

pixiv-1.7.4-fix.mirai.jar




## 每日新闻速报
news-reporter-1.4.3.mirai.jar



### 白名单

**为了避免打扰网友, 群聊使用白名单管理. 只有通过命令指定的群聊, 才会在群聊中触发本机器人.**

番剧群组白名单和新闻播报群组白名单是分开的两个名单，你可以使用 `/reporter_list` 命令来管理这两个名单。 该命令允许 `show`, `add`, `remove` 三种后缀。其中 `add`, `remove` 两个后缀需要跟一个群号。 在群号之后你可以用 `anime`, `news` 来指定操作哪一个白名单（留空表示二者都操作）。

举例如下：

将群号为 123456 的群加入番剧、新闻白名单： `/reporter_list add 123456`

将群号为 123456 的群加入番剧白名单： `/reporter_list add 123456 anime`

将群号为 123456 的群加入新闻白名单： `/reporter_list add 123456 news`

> 更多命令细节可以通过 /help 获取.


### 自定义语句

Bot 在回复命令时的很多语句，都可以通过 `/reporter_msg` 命令来自定义。

命令格式： `/reporter_msg <key> <list>`。

其中，`<key>` 的可能取值及其含义见下表。 `<list>` 是一个用逗号或分号分割的列表（也可以只是一个词），中文标点和英文标点都可以，但是不能有空格。 `<list>` 表示相应的**用户发出触发语句**可以使用 `<list>` 中的**任何一个**， 而**机器人回复的语句**会在列表中**随机选取**。

| key                       | 默认值                                     | 含义                                 |
| :------------------------ | :----------------------------------------- | :----------------------------------- |
| dailyTriggers             | 今日,每日,日常,daily,Daily                  | "今日番剧"/“每日新闻” 中的 “今日/每日” |
| animeTriggers             | 番剧,动画,B站番剧,B站番剧                   | "今日番剧"/“每日动画” 中的 “番剧/动画” |
| newsTriggers              | 新闻,速报,新闻速报                          | "今日新闻"/“每日速报” 中的 “新闻/速报” |
| waitMessages              | 稍等哦QwQ                                  | 需要进行长加载时的提示语               |
| animeDailyMessages        | 早上好呀,这是今天的B站番剧\\n(•̀ω•́)✧         | 早上的自动动画播报提示                 |
| animeReplyMessages        | 这是今天的B站番剧\\n(•̀ω•́)✧                 | 用关键词触发播报后的回复语             |
| noAnimeMessages           | 好像今天没有放送呢>\_<                      | 今天没有番剧时的提示语                 |
| newsDailyMessages         | 这是今天的新闻速报\\nq(≧▽≦q)              | 早上的自动新闻播报提示                 |
| newsReplyMessages         | "这是今天的新闻速报 \\nq(≧▽≦q)"           | 用关键词触发播报后的回复语             |
| noDisturbingGroupMessages | 为了防止打扰到网友，这个群不在日报白名单呢QwQ | 白名单提示                            |
| errorMessages             | 出错啦,等会再试试吧￣へ￣                    | 错误提示                              |


## 大学生网课搜题答案插件
HiveSearchForQQ-1.2.2.mirai.jar
### 插件指令：

|         触发词          |       含义        |
| ---------------------- | ----------------- |
| 搜题帮助                | 回复帮助提示       |
| 开启搜题                | 当前群搜索功能开启 |
| 关闭搜题                | 当前群搜索关闭关闭 |
| 开启所有人可变更搜题权限 | 所有人权限开启     |
| 关闭所有人可变更搜题权限 | 所有人权限关闭     |
回复 ： q+问题


## AI图片生成
novelai-helper-1.1.1.mirai2.jar

https://mirai.mamoe.net/topic/1657/novelai-helper-ai%E5%9B%BE%E7%89%87%E7%94%9F%E6%88%90-%E5%8F%AF%E5%AF%B9%E6%8E%A5%E8%87%AA%E5%BB%BA-colab%E5%9C%A8%E7%BA%BF%E8%BF%90%E8%A1%8C%E7%9A%84-naifu-api?_=1671083358566
### 指令

*   `/nai <word>` 生成一张图片 官方API需要登录  
    例如 `/nai 连裤袜 双马尾` (只有部分词条会自动翻译)  
    例如 `/nai swimsuit #seed=12346` (设置种子)  
    例如 `/nai swimsuit #steps=3` (AI迭代次数)  
    例如 `/nai "swimsuit, ahegao"` (如果需要以 `,` 分割词条, 请用 `"` 包裹)  
    例如 `/nai 连裤袜 [图片]` (以图生图, `[图片]` 是指指令消息中包含有图片)  
    可用的配置项有  
    `seed` 种子  
    `steps` 迭代次数  
    `width` 宽度  
    `height` 高度  
    `scale` 比例  
    `sampler` 采样器 可选值 `k_euler_ancestral`, `k_euler`, `k_lms`, `plms`, `ddim`  
    `strength` 以图出图中对原图的更改程度 可选值 \[0.00, 0.99\]  
    `noise` 以图出图中的噪声 可选值 \[0.00, 0.99\]
    
*   `/nai-fu <word>` 生成一张图片 自建API需要配置 naifu\_api  
    对接 `naifu`, `naifu` 是基于 novelai 官方 web 端的修改版，所以指令用法 和 `nai` 一致
    
*   `/nai-login <mail> <password>` 登录账号  
    例如 `/nai-login 114514@gmail.com 1919810`
    
*   `/nai-reload` 重新载入 `config.yml` 配置文件
    

### 配置

*   `config.yml` 配置文件 包括 `proxy`, `doh`, `ipv6`, `naifu_api` 等配置
    
    *   `proxy` 代理
    *   `doh` DNS
    *   `ipv6` 是否使用ipv6
    *   `naifu_api` 自建 naifu 地址
    *   `command_interval` 命令间隔延迟时间 单位毫秒
*   `ban.txt` 屏蔽的词条，可热编辑，保存后一段时间会自动启用


tar zx bore-v0.4.0-x86_64-unknown-linux-musl.tar.gz -C /usr/bin


## 权限对象指定
|     被许可人类型     | 字符串表示示例 |                  备注                   |
| ------------------- | ------------- | --------------------------------------- |
| 控制台              | console       |                                         |
| 任意其他客户端       | client\*      | 即 Bot 自己发消息给自己                  |
| 精确群              | g123456       | 表示群, **而不表示群成员, 不表示群成员** |
| 精确好友            | f123456       | 必须通过好友消息                         |
| 精确群临时会话       | t123456.789   | 群 123456 内的成员 789. 必须通过临时会话  |
| 精确群成员           | m123456.789   | 群 123456 内的成员 789. 同时包含临时会话  |
| 精确用户            | u123456       | 同时包含群成员, 好友, 临时会话            |
| 任意群              | g\*           | g 意为 group, **不表示群成员**           |
| 任意群的任意群员     | m\*           | m 意为 member                           |
| 精确群的任意群员     | m123456.\*    | 群 123456 内的任意成员. 同时包含临时会话  |
| 任意临时会话         | t\*           | t 意为 temp. 必须通过临时会话             |
| 精确群的任意临时会话 | t123456.\*    | 群 123456 内的任意成员. 必须通过临时会话  |
| 任意好友            | f\*           | f 意为 friend                           |
| 任意用户            | u\*           | u 意为 user. 任何人在任何环境             |
| 任意陌生人           | s\*           | s 意为 stranger. 任何人在任何环境         |
| 任意联系对象         | \*            | 即任何人, 任何群. 不包括控制台            |



### 课程表插件
[SuperCourseTimetableBot](https://github.com/StageGuard/SuperCourseTimetableBot)



## sagiri bot 安装历程


### poetry 已更新
官网：
https://python-poetry.org/docs/#installing-with-the-official-installer
curl -sSL https://install.python-poetry.org | python3 -

#### poetry install 不能用的情况
生成requirements文件
poetry export --output requirements.txt


### 能用的功能

#### 科学计算 mathwolf  /solve
/solve {content}


#### /发病


#### 热搜  微博/知乎/github+热搜

#### 塔罗牌

#### 来个老婆/随机老婆

#### 随机人设

#### 舔狗日记

#### 涩图

#### super langua/ncode

#### 来点钉宫

#### 来点{美国/俄罗斯}笑话

#### 搜番/搜图

#### cp文 cp 攻方 受方

#### 骰子  次数d点数

#### 缩写预测 {/}缩 内容

#### github 项目搜索 /github (-i 图片化输出) 项目名

#### 普通话转抽象  /抽象 文字

#### 热梗解释  。。是什么梗


#### steam{游戏名}