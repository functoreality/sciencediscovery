# 安全与信任边界

ScienceDiscovery 是本地运行的单用户工作区，不是多用户生产服务。

## 默认暴露和访问

二进制和本地模式下，适配器和 API 默认只监听回环地址。Docker 在容器内监听 `0.0.0.0:4310`，但 Compose 默认只将该端口发布到宿主回环地址。访问使用一个 bearer token，且不终止 TLS。将接口暴露到其他网络必须是受信任、受保护网络中的显式部署选择。请保护 `Open to sign in` 链接和本地服务访问令牌。

## 执行边界

Python、R 和 Shell 命令在 fail-closed 的平台沙箱中运行：Linux 使用 Bubblewrap，macOS 本地源码模式使用 Seatbelt。沙箱只向执行暴露 Session 工作区，并采用已配置的网络策略。它并不代表所有产品组件都在沙箱内。控制 API、适配器、JiuwenSwarm、PDF worker，以及发往模型或 provider 的请求，都是沙箱外的受信任控制面操作。

实现和运维限制见[沙箱执行](../developer-docs/sandbox-execution.md)。
