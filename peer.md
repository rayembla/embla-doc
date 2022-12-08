# peer挖矿

`peer` 是一个Embla的分布式检测客户端，主要用于节点的检测抓取。

用户可以通过 `peer` 挖矿来获取Embla的积分，积分可以用于购买节点或使用其他服务。

### 使用说明

1. 给机器人发送 `/new_peer` 生成一个新的 peer ID
2. 给机器人发送 `/my_peers` 查看已生成的 peer ID
3. 通过按钮选择刚刚生成的 peer ID，进入 peer 管理页面
4. 点击按钮刷新秘钥，更新后再点击生成配置文件，并下载配置文件
5. 下载对应的版本的 `peer`，并将配置文件与系在后的peer放在同一目录下
    - windows_amd64: https://qvcp1z.gq/resource/peer/windows_amd64
    - linux_amd64: https://qvcp1z.gq/resource/peer/linux_amd64
    - linux_arm64: https://qvcp1z.gq/resource/peer/linux_arm64
    - linux_arm_v5: https://qvcp1z.gq/resource/peer/linux_arm_v5
    - linux_arm_v6: https://qvcp1z.gq/resource/peer/linux_arm_v6
    - linux_arm_v7: https://qvcp1z.gq/resource/peer/linux_arm_v7
    - darwin_amd64: https://qvcp1z.gq/resource/peer/darwin_amd64
    - darwin_arm64: https://qvcp1z.gq/resource/peer/darwin_arm64
6. 在终端（CMD、bash、Powershell等）中，进入peer所在目录，直接运行 `peer.exe`，如果是linux系统，运行 `./peer`，等待刷新凭证成功

如果你需要他后台运行，且自动启动

1. 等待 peer 运行一段时间，通过 Ctrl + C 关闭在正在运行的 peer，以管理员的权限在 peer 所在目录启动终端
2. 运行 `peer.exe -s install`，如果是linux系统，运行 `./peer -s install`，安装 peer 为系统服务，这样可以使得 peer
   在系统重启后自动启动
3. 可以通过 `peer.exe -s status` 来查看当前服务的运行状态
4. 可以通过 `peer.exe -s start` 来启动服务
5. 可以通过 `peer.exe -s stop` 来停止服务
6. 可以通过 `peer.exe -s restart` 来重启服务
7. 可以通过 `peer.exe -s reinstall` 重新安装服务
8. 可以通过 `peer.exe -s install` 来安装服务
9. 可以通过 `peer.exe -s uninstall` 来卸载服务

### 关于无法启动的问题

如果你在运行 `peer` 的时候，发现了他直接退出了，可以尝试如下步骤

1. 检查 `peer` 是否有执行权限，请尝试使用管理员权限运行
2. 检查统计目录是否存在peer的配置文件，如果不存在，可以重新获取配置文件
3. 检查是否存在360、腾讯电脑管家等软件，如果有，可以选择不使用peer或卸载这些软件
[关于不允许不允许使用360、腾讯电脑管家等软件的说明](https://qvcp1z.cf/docs#/?id=%e5%85%b3%e4%ba%8e%e4%b8%8d%e5%85%81%e8%ae%b8%e4%b8%8d%e5%85%81%e8%ae%b8%e4%bd%bf%e7%94%a8360%e3%80%81%e8%85%be%e8%ae%af%e7%94%b5%e8%84%91%e7%ae%a1%e5%ae%b6%e7%ad%89%e8%bd%af%e4%bb%b6%e7%9a%84%e8%af%b4%e6%98%8e)
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
