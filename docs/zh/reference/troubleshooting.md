# 排障与常见问题

本页处理安装后的运行时问题。二进制、本地或 Docker 模式的首次启动问题，请参见[部署指南](../getting-started/deployment.md)。

## 模型请求失败

检查**系统配置**中的 provider 基础 URL、API Key 和任务模型。本地服务访问令牌只用于登录 ScienceDiscovery，不是模型 API Key。参见[运行时行为](runtime-behavior.md#模型)。

## 权限卡片阻止任务

批准前先核对请求的动作。持久授权在**系统配置 → Permissions**中管理。启用连接器不代表已授权执行。参见[权限与评审器](runtime-behavior.md#权限与评审器)。

## 连接器或代理无法连接

先检查服务器或 provider 设置。MCP 的认证和连接诊断见[配置自定义 MCP](../how-to/configure-custom-mcp.md)。模型、Web 和 MCP 流量的代理设置见[配置网络代理](../how-to/configure-network-proxy.md)。

## 运行超时或需要停止

使用 **Stop run** 取消当前运行。在**系统配置 → Timeouts**中配置产品墙钟超时。参见[超时与运行状态](runtime-behavior.md#超时与运行状态)。

## 数据在哪里

Project、Session、工作区、凭据和服务环境都在数据目录中。本地模式默认目录为 `.sciencediscovery-data`，Docker 为 `./data`。本地 ScienceMemory 后端的图数据另存于 `~/.science-agent/memory-graph`。参见[存储布局](configuration.md#存储布局)。删除 Project 或 Session 不可撤销，请先备份所有需要保留的数据位置。
