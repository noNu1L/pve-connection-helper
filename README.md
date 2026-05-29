# PVE Connection

Proxmox VE 连接管理工具，统一展示节点与虚拟机信息，支持一键生成 RDP / SSH / SMB 连接文件。


![img.png](https://github.com/noNu1L/pve-connection-helper/blob/main/document/images/v2.0.png?raw=true)

## 功能

- **说明** — 为节点或虚拟机添加自定义说明
- **连接凭据管理** — 集中管理各连接类型的用户名、密码、端口
- **快速连接** — 一键下载 RDP、SSH (Xshell)、SMB 连接脚本，或打开 Web 链接

## Docker 部署

```bash
docker run -d --name pve-connection --restart unless-stopped -p 8080:8080 youmiepie/pve-connection:latest
```

浏览器访问 `http://your-server-ip:80`

其他配置：[docker-compose/docker-compose.yaml](docker-compose/docker-compose.yaml)

## 开发

`src/main/resources/static/` 为前端构建产物，不纳入版本控制，**Maven 打包前需先在本地构建前端**。

```bash
# 1. 构建前端 (需要 Node.js 18+)
cd frontend
npm install
npm run build      # 输出到 ../src/main/resources/static/

# 2. 打包后端 (需要 JDK 17 + Maven)
cd ..
mvn clean package -DskipTests
# 产物: target/pve-connection.jar
```
前端开发模式（需后端同时运行在 8080 端口）：

```bash
cd frontend
npm run dev
```
