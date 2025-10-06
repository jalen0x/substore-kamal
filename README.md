# Substore Kamal

使用 Kamal 部署 Sub-Store 服务的配置项目。

## 项目说明

本项目基于 [Sub-Store](https://github.com/sub-store-org/Sub-Store) 镜像，使用 Kamal 实现自动化部署到远程服务器。

## 部署信息

- **服务名称**: substore
- **镜像**: jalen0x/substore (基于 xream/sub-store:latest)
- **域名**: sub-store.jalenx.me
- **端口**: 3001
- **SSL**: 已启用 (Let's Encrypt 自动证书)

## 前置要求

- Docker
- Kamal
- 有效的 Docker Hub 账号

## 配置说明

### 环境变量

在 `.kamal/secrets` 文件中配置以下密钥：

```bash
KAMAL_REGISTRY_PASSWORD=<docker-hub-access-token>
SUB_STORE_FRONTEND_BACKEND_PATH=<backend-path>
```

### 数据持久化

使用 Docker volume `substore_data` 挂载到容器 `/opt/app/data` 目录。

## 部署命令

```bash
# 首次部署
kamal setup

# 更新部署
kamal deploy

# 查看日志
kamal logs

# 进入容器 shell
kamal shell

# 回滚
kamal rollback
```

## 服务器配置

目标服务器: `120.26.229.237`

时区设置: `Asia/Shanghai`

## 注意事项

- 使用 Docker Hub Access Token 而非密码进行认证
- 构建架构为 amd64
- 健康检查路径为根路径 `/`，间隔 5 秒，超时 3 秒
