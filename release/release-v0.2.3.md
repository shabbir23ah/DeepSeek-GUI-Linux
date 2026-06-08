# DeepSeek GUI v0.2.3

这一版把 Linux 分发补齐到了更适合日常发布的状态，重点是让 Debian 系发行版拿到原生安装包，同时保留已有的通用下载方式。

### Linux 现在有 `.deb`

- Linux 构建现在会产出 `.deb`，适合 Debian、Ubuntu、Mint 等发行版直接通过 `apt install ./xxx.deb` 安装。
- Debian 包补上了常见 Electron 运行依赖和托盘相关推荐依赖，安装后更接近普通桌面应用体验。
- 这次调整不会替换原有 Linux 产物，而是把 `.deb` 作为第一优先分发格式补进来。

### 继续保留 `.AppImage`

- 原有 `.AppImage` 仍然保留，方便继续覆盖更广的 Linux 发行版和无需安装的使用方式。
- Linux 更新元数据仍然沿用 `latest-linux.yml`，现有 Linux 更新链路不需要切换到新的协议。

### 新增便携 `.tar.gz`

- 除了 `.deb` 和 `.AppImage`，现在还会生成便携 `.tar.gz`，适合不想安装系统包、只想解压运行的场景。
- 这个包定位是“手动分发 / 自托管下载”产物，不依赖发行版包管理器。

### 发布链路同步更新

- R2 发布脚本现在会把 Linux `.deb`、`.AppImage` 和 `.tar.gz` 一起识别为可下载资产。
- 生成的 Linux release manifest 不再默认只有 AppImage，而是会列出多个 Linux 下载格式，便于下载页或自定义分发页面直接消费。

### 总结

v0.2.3 的重点不是桌面功能，而是 Linux 发布面更完整了：Debian 系用户有原生 `.deb`，跨发行版用户继续有 `.AppImage`，同时也提供了更轻量的便携 `.tar.gz`。
