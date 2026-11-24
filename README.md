# dsh-wb-bootstrap

dsh 客户端（Android App）的**公开引导清单**分发点。

- 匿名可读，无需 token、无需登录。
- 唯一消费者：`dsh-mobile` 客户端的清单导入 / 重绑逻辑。
- 唯一写入者：服务端"出服务"（地址变更后自动提交），**请勿手工改这里**。
- 真源在数据侧（私有仓），这里只是对外镜像；改动只增不减。

## 怎么读

```
https://raw.githubusercontent.com/cyber-lai/dsh-wb-bootstrap/main/endpoints.json
```

## 字段

| 字段 | 含义 |
| --- | --- |
| `schema` | 固定 `dsh/bootstrap/1` |
| `updatedAt` | 本文件最后一次被出服务写入的时间 |
| `entries[].id` | 入口标识（与 profile 名一致） |
| `entries[].baseUrl` | 当前公网入口（cpolar 域名，会变） |
| `entries[].port` | 本机监听端口 |
| `entries[].instanceId` | 该实例的稳定标识（64 位 hex），客户端据此精确重绑 |
| `entries[].lanGateway` | 局域网网关（仅同网可用的加速入口） |

客户端匹配规则：**只认 `instanceId` 相同、且地址不同的那条**，同名不算、无 id 只作展示。

<!-- dsh-wb:entry:begin -->

## 当前入口（链接自带本次 token）

https://33cf5546.r2.cpolar.top/?token=aVrOf4tCQZwDtrsGOpoVvYNZ6S-QuBmX63NNYwQym5w

- origin: https://33cf5546.r2.cpolar.top
- 刷新: 2026-11-24T13:26:01.270Z
- 来源: publisher-memory
- token 每次重启都会换：这一段由实例自动刷新，块外内容不会被改动。
- 打开后若 401/403，说明这份内容比实例旧：等一分钟再刷新。

<!-- dsh-wb:entry:end -->
