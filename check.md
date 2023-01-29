# 节点检测

> 节点检测是指对节点进行检测，以判断节点是否正常工作。
>
> 本机器人的检测不对检测结果做可靠性做保证，仅供参考。
>
> 禁止使用检测结果进行任何商业行为以及宣传行为。

## 检测方法

### 主动检测

> 参考 [用户身份](user) 模块的相关权限问题

```
/check <actions>
<节点内容>
```

例如

```
/check google update download
vmess://8264c2db2b634d219e9bd0771ef8d32b
```

#### actions

actions是需要检测的行为，多个用空格隔开，支持的行为有

| action   | 含义          |
|----------|-------------|
| google   | Google检测    |
| download | 下载速度测试      |
| update   | 上传速度测试      |
| netflix  | netflix解锁检测 |
| youtube  | youtube解锁检测 |
| disney   | disney解锁检测  |
| risk     | 欺诈风险检测      |
| base     | Google检测    |
| speed    | 上传下载检测      |
| unlock   | 所有流媒体检测     |
| all      | 所有的检测项      |
| full     | 所有的检测项      |
| default  | 所有的检测项      |
|          | 所有的检测项      |

#### 被动检测

当机器人在群组中时，当有人发送节点链接时，机器人会自动检测节点的可用性。
