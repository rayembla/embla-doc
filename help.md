# 帮助文档

## 用户

### 查看当前用户身份等信息

向机器人发送 `/actor` 获取

### 用户身份

目前用户身份分为 `游客` 和 `普通用户`，游客属于未注册用户，可以通过邀请等方式获取邀请积分，再通过邀请积分注册成为普通用户。

为了保证节点的质量以及服务的安全性，才用了注册制，非注册用户无法使用本服务。

用户注册需要手动注册，注册入口在 `/actor` 中

注册时，会发放 500 初始的 通用积分 ，用于付费节点体验。

目前仅发放200个邀请注册名额给用户使用体验反馈

前10位注册的用户需要 3 邀请积分

前11-50注册用户需要 5 邀请积分

前51-200注册用户需要 10 邀请积分

### 邀请好友获取奖励

向机器人发送 `/invite_link` 获取邀请链接，其他人首次通过邀请链接进入时，会给予一定的奖励，用于兑换注册资格，后期可能会开放兑换其他奖励。

## 生成一个订阅(仅限注册用户)

> 订阅链接是支持全客户端的，如遇到不支持的客户端欢迎反馈以获得支持

### 免费节点

每个用户可以生成一个专属的免费订阅链接，节点每日更新，免费节点相对速度较慢、延时较高、且不稳定。

用户每日可以通过专属的免费订阅链接刷新一次订阅，但不保证免费节点的可用性。

用户可以通过向机器人发送 `/free` 获取他的专属免费订阅链接

### 付费节点

每个用户可以拥有多个订阅，每个订阅关联绑定一个 `token` ，同一 `token` 不允许在多个位置使用

每次的订阅更新或扣除一定的余额，随着获取到的节点的数量、质量的变化而变化

通过订阅获取节点需要保证积分余额不少于 250

如果您想生成一个订阅，可以尝试如下步骤：

1. 给机器人发送 `/new_token [备注]` 生成一个新的token
2. 给机器人发送 `/my_tokens` 进行token的管理

#### 订阅筛选

订阅允许通过参数进行节点筛选，例如原始的订阅链接为 `https://embla.org/pool/bot?token=token&user=user`
，添加了出口国家指定为美国和日本后，订阅链接为 `https://embla.org/pool/bot?token=token&user=user&out_country_code=US,JP`

| 参数               | 含义                                                         | 样例    |
|------------------|------------------------------------------------------------|-------|
| quality          | 节点质量，实验性<br>默认为随机<br>0-随机 1-低 2-中 3-高                      | 3     |
| risk_source      | 欺诈指数，用于一些特殊场景比如gv号的注册、转移等，实验性<br>默认为随机<br>0-随机 1-低 2-中 3-高 | 3     |
| count            | 订阅返回的节点数量<br>默认为10<br>最小为1,最大为50                           | 10    |
| out_country_code | 节点的出口区域                                                    | US,JP |
| in_country_code  | 节点的入口区域                                                    | HK,TW |
| disney_unlocked  | 是否可以进行Disney+解锁<br> 1 - 支持解锁                               | 1     |
| youtube_unlocked | 是否可以进行YouTube解锁<br> 1 - 支持解锁                               | 1     |
| netflix_unlocked | 是否可以进行Netflix解锁<br> 1 - 全解锁<br> 2 - 解锁自制剧<br> 3 - 解锁非自制剧   | 1     |
| convert_config   | 订阅转换的规则地址<br>对齐订阅转换当中的config字段，用于规则的生成<br>如果不填会使用默认的魔改的规则  |       |

### 节点名说明

<出口地区名><出口地区emoji>-<质量评分>-<节点唯一标识>|Netflix解锁|Disney+解锁|YouTube解锁[|D:下载速度]

### 关于无法获取订阅的问题

1. 阅读返回的具体内容，一般情况下都会有提示
2. 对于免费订阅一天只可以更新一次
3. 对于付费订阅，需要保证更新时积分不小于 250
4. 对于付费订阅，每一个订阅链接只可以被一个设备使用（同一个设备不同的客户端算是一个设备）
5. 如果一直提示 `您的网络信息未知，正在尝试解析您的网络环境，请稍后再试`
   时，请稍安勿操，等两分钟再试试，受限于资源问题，我们购买的检测服务部分存在请求限频的情况，所以会存在检测排队的情况
6. 如果客户端提示 SSL 错误，可以尝试将订阅开头中的 `https` 改为 `http`
   ,当需注意，这种方式虽然可以绕过客户端的bug导致了无法订阅但是也同时会导致您的订阅信息可能会被第三方窃取篡改

[//]: # (### 随机获取一个节点)

[//]: # ()

[//]: # (如果您想随机获取一个节点，可以给机器人发送 `/re-ubu` ，会随机返回一个节点，以及这个节点的相关信息、临时的订阅链接、base64链接、评分等信息，并且会随机扣除一定的余额)

## 节点检测（内测）

如果想要检测一个节点，可以给机器人发送

```
/check <actions>
<节点内容>
```

例如

```
/check google update download
vmess://8264c2db2b634d219e9bd0771ef8d32b
```

### actions

actions是需要检测的行为，多个用空格隔开，支持的行为有

| action   | 含义              |
|----------|-----------------|
| google   | Google检测        |
| download | 下载速度测试          |
| update   | 上传速度测试          |
| netflix  | netflix解锁检测     |
| youtube  | youtube解锁检测     |
| disney   | disney解锁检测      |
| risk     | 欺诈风险检测          |
| base     | Google检测+欺诈风险检测 |
| speed    | 上传下载检测          |
| unlock   | 所有流媒体检测         |
| all      | 所有的检测项          |

## peer（仅内测用户）

一个给用户使用的客户端，作为服务的一部分，主要负责一些重资源的逻辑，比如抓取、检测等。有如下功能

- 节点抓取
- 节点检测
    - Google延时检测
    - 下载、上传速度检测
    - Netflix解锁检测
    - YouTube解锁
    - Disney+解锁
    - 欺诈风险检测
    - 安全性检测
- IP检测
- 摸鱼

peer通过任务执行来获取一定的钱包余额奖励

### 使用说明

如果您想参与peer来获取部分奖励的话，可以尝试如下步骤

1. 给机器人发送 `/new_peer` 生成一个新的 peer ID
2. 给机器人发送 `/my_peers` 查看已生成的 peer ID
3. 通过按钮选择刚刚生成的 peer ID，进入 peer 管理页面
4. 点击按钮刷新秘钥，更新后再点击生成配置文件，并下载配置文件
5. 下载对应的版本的 `peer`，并将配置文件与系在后的peer放在同一目录下
    - windows_amd64: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/windows_amd64
    - linux_amd64: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/linux_amd64
    - linux_arm64: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/linux_arm64
    - linux_arm_v5: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/linux_arm_v5
    - linux_arm_v6: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/linux_arm_v6
    - linux_arm_v7: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/linux_arm_v7
    - darwin_amd64: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/darwin_amd64
    - darwin_arm64: https://88236a229bf7425194ce71b18314a0ab.tk/resource/peer/darwin_arm64
6. 在终端（CMD、bash、Powershell等）中，进入peer所在目录，直接运行 `peer.exe`，如果是linux系统，运行 `./peer`，等待刷新凭证成功

如果你需要他后台运行，且自动启动

1. 等待 peer 运行一段时间，通过 Ctrl + C 关闭在正在运行的 peer，以管理员的权限在 peer 所在目录启动终端
2. 运行 `peer.exe -s install`，如果是linux系统，运行 `./peer -s install`，安装 peer 为系统服务，这样可以使得 peer 在系统重启后自动启动
3. 可以通过 `peer.exe -s status` 来查看当前服务的运行状态
4. 可以通过 `peer.exe -s start` 来启动服务
5. 可以通过 `peer.exe -s stop` 来停止服务
6. 可以通过 `peer.exe -s restart` 来重启服务
7. 可以通过 `peer.exe -s reinstall` 重新安装服务
8. 可以通过 `peer.exe -s install` 来安装服务
9. 可以通过 `peer.exe -s uninstall` 来卸载服务

以上方式只能尽可能的保证自动运行，但是由于系统的一些限制，不能保证其一定可以自动更新和自动运行

### 关于无法启动的问题

如果你在运行 `peer` 的时候，发现了他直接退出了，可以尝试如下步骤

1. 检查 `peer` 是否有执行权限，请尝试使用管理员权限运行
2. 检查统计目录是否存在peer的配置文件，如果不存在，可以重新获取配置文件
3.
检查是否存在360、腾讯电脑管家等软件，如果有，可以选择不使用peer或卸载这些软件 [关于不允许不允许使用360、腾讯电脑管家等软件的说明](https://88236a229bf7425194ce71b18314a0ab.tk/docs#/?id=%e5%85%b3%e4%ba%8e%e4%b8%8d%e5%85%81%e8%ae%b8%e4%b8%8d%e5%85%81%e8%ae%b8%e4%bd%bf%e7%94%a8360%e3%80%81%e8%85%be%e8%ae%af%e7%94%b5%e8%84%91%e7%ae%a1%e5%ae%b6%e7%ad%89%e8%bd%af%e4%bb%b6%e7%9a%84%e8%af%b4%e6%98%8e)
4. 程序闪退，可以尝试使用在终端打开，查看具体的错误信息

#### 关于不允许不允许使用360、腾讯电脑管家等软件的说明

360、腾讯电脑管家等存在窃取用户隐私同时监听用户行为的举动，对于一个翻墙行为来说是非常不安全的，十分容易造成被"请喝茶"
，所以我们不允许使用这些软件，如果你不想卸载这些软件，可以选择不使用peer。

如果您选择了写在这些不安全的软件，请确保卸载干净后启动，这些软件大部分都会存在强写在残留，可能会存在卸载后仍然会在运行的情况。

如果电脑没有这些程序可以存在以下情况

1. 曾经安装过程序但是没有卸载干净。请清理卸载残留后再次尝试
2. 被某些恶意程序静默安装了，请尝试查找并且卸载

#### 关于没有安装360等软件但是提示存在的检查帮助

360等软件可能会存在静默安装、卸载残留等问题，所以用户可能没有安装过或者安装过但是卸载了缺依然提示存在存在，这里只是给一些常见的检查方案并不代表程序的检测方式

##### 360

- 检查 `C:\Program Files (x86)\360` 目录是否有文件

#### 腾讯电脑管家

- 检查 `C:\Program Files (x86)\Tencent\QQPCMgr` 目录是否有文件

#### 金山毒霸

- 检查 `C:\Program Files (x86)\kingsoft\kingsoft antivirus\` 目录是否有文件

### 关于挖矿难度的说明

挖矿难度是基于总算力、总带宽、总节点、总抓取源等计算出来的基础挖矿难度以及基于用户的算力、带宽等计算出来的用户挖矿难度综合计算出来的。

用户通过 `/actor` 命令可以查看自己的挖矿难度。对于未参与挖矿的用户，展示的未全网的基础挖矿难度。

挖矿难度越高，可以挖取积分的难度越高，获取积分的速度越慢。挖矿难度越低，可以挖取的积分难度越低，获取积分的速度越快。

## 节点池

一个代理池，主要负责代理池相关的任务分发，并且筛选可用的节点对外提供订阅服务。有如下功能

- 收集抓取源
- 分发抓取任务
- 分发检测任务
- 用户定制化的订阅
- 可用节点的筛选
- 完整节点信息收集

### 获取奖励(仅限注册用户)

如果您想贡献订阅以换取积分，可以尝试如下步骤：

- 给机器人发送 `/add <订阅链接或存在节点的网页>` 添加订阅源

当您提供的订阅中获取到一个节点池中不存在的节点时，将会获得一定的奖励

## 钱包

会记录近期收到的奖励和消耗等信息

`/wallet` 查看钱包信息，并且可以通过选项导出两天的详细账单

`/trading_record` 查看钱包历史，尽可以查看最近5条交易记录

### 积分间相互兑换

您可以在 `/wallet` 中查看您的积分余额，然后在返回的详情下方的按钮中选择要对方的积分类型。

下方按钮只会展示目前开放的兑换类型。如果消失或者没有您想要的兑换类型，那就是暂时未开放兑换通道。

## 其他

### 查看近期产生的收益统计

向机器人发送 `state`，会返回近期产生的收益统计，但仅为参考数据，不作为最终的收益数据