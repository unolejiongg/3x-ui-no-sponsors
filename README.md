# 3X-UI 去赞助版

基于官方 **3X-UI v3.9.0** 的非官方修改版，移除面板赞助展示，并禁用网页端面板更新。

## 下载

👉 [下载 v3.9.0 去赞助版](https://github.com/unolejiongg/3x-ui-no-sponsors/releases/tag/v3.9.0-no-sponsors.1)

展开发布页底部的 **Assets** 下载文件。

## 修改内容

- 移除概览、侧边栏和登录页的赞助卡片。
- 移除赞助商菜单、快捷搜索入口和页面路由。
- 后端赞助接口返回空列表，停止拉取远程赞助内容。
- 禁用网页端面板更新、更新检查和更新频道切换。
- 取消概览页自动检查更新，将更新按钮改为普通版本号。
- 保留 Xray 内核与 Geo 文件更新功能。

## 文件说明

| 文件 | 用途 |
|---|---|
| `x-ui` | 编译好的面板程序 |
| `source.tar.gz` | 与程序对应的修改后源码 |
| `SHA256SUMS` | 文件校验值 |
| `说明.txt` | 修改说明与构建步骤 |

请下载附件中的 `source.tar.gz` 获取完整修改后源码。
GitHub 自动生成的 **Source code (zip/tar.gz)** 是本仓库快照。

## 适用环境

- 架构：Linux amd64 / x86_64。
- 已验证系统：Debian 13。
- 其他发行版可能存在 glibc 兼容性问题。
- 不适用于 ARM 设备。
- `x-ui` 仅为面板程序替换文件，不是完整安装包，不包含 Xray 等运行附件。

## 使用说明

适用于已经安装官方 **3X-UI v3.9.0** 的兼容系统。

1. 下载并校验文件。
2. 备份原面板程序及数据库。
3. 停止 `x-ui` 服务。
4. 替换 `/usr/local/x-ui/x-ui`，设置可执行权限。
5. 启动服务，检查面板、订阅和节点连接。
6. 强制刷新浏览器，加载新版界面。

重启服务时，代理连接可能短暂中断。

## 更新说明

网页端面板更新已禁用，官方安装或升级脚本仍会覆盖此版本。

升级时需基于新版源码重新应用修改并编译。
此版本不会自动获得后续面板功能更新与安全修复。

## 源码构建

构建环境：Go 1.27.1、Node.js 26、npm、GCC。

解压 `source.tar.gz`，在源码根目录依次执行：

    cd frontend
    npm ci --no-audit --no-fund
    npm run build
    cd ..
    CGO_ENABLED=1 GOMAXPROCS=1 GOMEMLIMIT=800MiB go build -p 1 -buildvcs=false -ldflags="-s -w" -o x-ui .

## 许可证与致谢

本修改版遵循 **GPL-3.0**。
原项目许可证及版权声明保留在源码包中。

原项目：[MHSanaei/3x-ui](https://github.com/MHSanaei/3x-ui)

本项目为非官方修改版，与原项目维护者无关联。
感谢原项目及其贡献者。
