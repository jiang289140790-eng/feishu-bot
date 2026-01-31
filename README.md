# 飞书机器人 - Zeabur 部署版

这是一个飞书机器人长链接事件监听服务，可以部署到 Zeabur 云平台。

## 功能特性

- ✅ 使用长链接（WebSocket）接收飞书事件
- ✅ 自动接收和回复消息
- ✅ 支持环境变量配置
- ✅ 适合 Zeabur 部署

## 环境变量配置

在 Zeabur 中需要设置以下环境变量：

| 变量名 | 说明 | 示例 |
|--------|------|------|
| `FEISHU_APP_ID` | 飞书应用的 App ID | `cli_a9f66a3c66f8dcc2` |
| `FEISHU_APP_SECRET` | 飞书应用的 App Secret | `WUXA3I5rhyVaW0wc0fB9YefXyZgiBll2` |

## Zeabur 部署步骤

### 1. 上传代码到 GitHub

1. 创建一个新的 GitHub 仓库
2. 将此项目的所有文件上传到仓库

### 2. 在 Zeabur 中导入项目

1. 登录 Zeabur: https://zeabur.com
2. 点击 "New Project"
3. 选择 "Deploy from GitHub"
4. 选择刚才创建的仓库
5. Zeabur 会自动检测 Dockerfile 并开始构建

### 3. 配置环境变量

在 Zeabur 项目设置中添加：
- `FEISHU_APP_ID`: `cli_a9f66a3c66f8dcc2`
- `FEISHU_APP_SECRET`: `WUXA3I5rhyVaW0wc0fB9YefXyZgiBll2`

### 4. 重新部署

保存环境变量后，点击 "Redeploy" 重新部署服务。

## 飞书开放平台配置

### 1. 权限管理

开通以下权限：
- ✅ 获取与发送单聊、群组消息
- ✅ 接收消息 v2.0

### 2. 事件配置

- 订阅方式：**使用长链接接收事件（推荐）**
- 点击保存

### 3. 事件订阅

添加事件：
- ✅ `im.message.receive_v1` - 接收消息

### 4. 发布版本

创建并发布应用版本到企业内部。

## 本地测试

如果想在本地测试：

```bash
# 设置环境变量
export FEISHU_APP_ID="cli_a9f66a3c66f8dcc2"
export FEISHU_APP_SECRET="WUXA3I5rhyVaW0wc0fB9YefXyZgiBll2"

# 运行程序
go run main.go
```

## 查看日志

部署成功后，在 Zeabur 的 "Logs" 标签页可以查看实时日志。

成功启动会看到：
```
🤖 机器人 App ID: cli_a9f66a3c66f8dcc2
🚀 正在启动飞书事件长链接监听...
✅ 长链接已成功建立，正在监听事件...
```

## 故障排查

### 长链接无法建立
- 检查 App ID 和 App Secret 是否正确
- 检查飞书开放平台是否选择了"使用长链接"
- 检查网络连接

### 收不到消息
- 确认已在"事件订阅"中添加 `im.message.receive_v1` 事件
- 确认已发布应用版本
- 确认已开通相关权限

## 许可证

MIT License

Updated: 2026-01-31
