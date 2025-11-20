# GitHub Actions 构建 qBittorrent（多接口并发支持）

## 功能
- 支持多个网络接口同时下载同一任务
- Tracker 和 Peer 分配到不同接口，但共享下载进度

## 使用步骤
1. Fork [qBittorrent 官方仓库](https://github.com/qbittorrent/qBittorrent)
2. 在 fork 仓库中创建 `.github/workflows` 目录，将 `build_windows.yml` 放入其中
3. 将 `libtorrent_multi_interface.patch` 上传到仓库根目录
4. 在 GitHub 仓库中启用 Actions
5. 手动运行 workflow 或推送代码触发构建
6. 构建完成后，下载 `qbittorrent-multi-interface.exe`（在 Release 或 Artifact 中）

## 补丁说明
- 修改 libtorrent 源码，增加多接口支持逻辑
- Tracker 和 Peer 按轮询策略分配接口
