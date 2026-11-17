# MediaAssistant

MDCx 的 Emby 媒体助手，提供影片操作菜单、封面处理、演员搜索、批量计划任务和本机外部播放器入口。

[下载 MediaAssistant](https://github.com/xiarenyyds/MediaAssistant/releases/latest/download/MediaAssistant.dll) · [安装与使用](docs/INSTALLATION.md) · [更新日志](CHANGELOG.md)

## 安装

1. 将 `MediaAssistant.dll` 放入 Emby 插件目录，重启 Emby 后打开网页。Docker 通常为容器内 `/config/plugins` 对应的宿主机目录。
2. 打开 MDCx 主菜单“媒体助手”，生成令牌，配置监听；路径不同时再添加路径映射，路径相同且可访问时无需添加。点击底部“保存”，再点击“开始监听”。
3. 在 Emby 媒体助手设置中填写可访问的 MDCx 地址及令牌，分别选择各批量任务允许操作的媒体库。

## 功能

| 入口 | 功能 |
| --- | --- |
| 单部影片菜单 | 完整刮削、重读本地元数据、搜索封面、编辑封面、翻译标题和简介 |
| 演员菜单 | 搜索资料，选择头像和背景图，替换简介 |
| 计划任务 | 背景图质量洗版、批量翻译、重读本地 NFO、检查插件更新 |
| Emby Web 详情页 | 按当前设备显示可用的外部播放器入口，可在插件设置中开关及多选 |

插件向 MDCx 发送路径和命令，由后端处理并保存 NFO、图片，再通知 Emby 读取。不注册影片元数据或图片刮削器。重读本地 NFO 和检查插件更新不要求 MDCx 在线；其他后端任务要求 MDCx 运行且媒体路径可访问。

封面洗版只检查背景图，默认最低 800×535、0 KB；合格时跳过。需要替换时更新由它派生的封面及缩略图，独立图片保留。Amazon 竖版封面按后端设置处理。

## 运行要求与日志

基于 Emby 4.9 / .NET 8，已在 Docker Emby 4.10.2.0 测试；各平台使用同一个 DLL。网页菜单及播放器入口适用于 Emby Web。

后端任务记录位于 MDCx“日志管理 → 媒体助手”；Emby 侧任务日志位于其日志目录的 `plugin/` 子目录。

发布附件仅包含 DLL 和 `SHA256SUMS.txt`；文档直接在本仓库阅读。
