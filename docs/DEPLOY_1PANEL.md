# 1Panel 部署（使用 Fork 自动构建镜像）

## 使用说明

1. 在 1Panel 新建 `Docker Compose` 应用，内容使用仓库根目录的 `docker-compose.1panel.yml`。
2. 把 `PROXY_API_KEY` 和 `KIRO_GATEWAY_API_KEY` 改成同一个随机密钥。
3. 把 `ADMIN_PASSWORD` 改成强密码。
4. 确保服务器可访问 `ghcr.io`，并已配置镜像拉取凭据（如仓库是私有包）。
5. 启动后访问 `http://<服务器IP或域名>:8088/admin`。

## 镜像地址

- `ghcr.io/muqing-kg/kiro-gateway:latest`
- `ghcr.io/muqing-kg/kiro-go:latest`

## 自动化能力

- 上游同步：`.github/workflows/sync-upstream.yml`
- 自动构建镜像：`.github/workflows/build-images.yml`

## 注意

- `kiro-gateway` 仅内网通信，编排中使用 `expose`，不对公网开放端口。
- 生产环境请在 1Panel 反向代理层启用 HTTPS 与访问控制。
