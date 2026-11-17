# wildduck for TerraMaster TOS

TOS 应用仓库说明：wildduck 的容器化部署与应用中心打包准备。

## 应用简介

wildduck 是一个可在自有 NAS 上运行的容器应用。

- 上游项目：https://wildduck.email/
- Docker 镜像：nodemailer/wildduck:1
- 项目仓库：https://github.com/waskevin/tnas-app-wildduck

## 双架构支持

本项目按双架构准备，目标平台为：

- linux/amd64（x86_64）
- linux/arm64（aarch64）

镜像版本固定为 1，不使用 latest。发布前应分别在 amd64 与 arm64 节点完成镜像拉取和启动检查。

## Docker 运行示例

```bash
docker run -d --name wildduck --restart unless-stopped -e TZ=Asia/Shanghai nodemailer/wildduck:1
```

如应用提供 Web UI，请根据上游文档和镜像暴露端口配置 TOS 应用端口映射；不要直接复用系统保留端口。数据目录应映射到 NAS 应用数据目录，以便升级和备份。

## 配置与数据

- 配置项以官方镜像文档为准。
- 不在仓库、镜像或 compose 文件中写入密码、令牌和私钥。
- 数据卷使用持久化目录，卸载时按用户选择保留或删除。

## 合规与维护

- 来源：上游项目和 Docker Hub 镜像。
- 版本：固定版本标签，变更时更新说明。
- 权限：默认不使用 privileged 和 host network。
- 许可证：以 wildduck 上游项目许可证为准。
- 本仓库仅包含 TerraMaster 应用说明与打包准备文件，不代表已提交 TerraMaster 审核。

## 相关链接

- 上游：https://wildduck.email/
- 镜像：https://hub.docker.com/r/nodemailer/wildduck
