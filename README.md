# wakuwaku-wb

Wakuwaku 桌宠的**更新分发仓库**。这里不放源码，只放安装包。

## 这是干什么的

桌宠客户端「设置 → 关于 / 更新」里点检查更新时，会去查本仓库的 Releases 最新版：

    https://api.github.com/repos/Presbyter1/wakuwaku-wb/releases/latest

查到比自己新的版本就提示下载，装的就是 Releases 里那个
`wakuwaku-v<版本>-windows-x64.exe`。

## 发行通道

| 通道 | 地址 | 说明 |
| --- | --- | --- |
| 主 | 本仓库 Releases | 免费不限量，桌面端首选 |
| 保底 | 腾讯 COS `wakuwaku/update.json` | GitHub 连不上时兜底（国内网络常见） |

两个通道发同一份 exe，两边的 SHA-256 对不上时客户端会拒绝安装。

## 发布

在开发机上跑（需要 GitHub PAT：本仓库 Contents 读写权限）：

    python pub.py <版本号> "更新说明1" "更新说明2" ...

`pub.py` 把 `src-tauri\target\asset\wakuwaku-v<版本>-windows-x64.exe`
传到 Releases，同时传一份到 COS 并更新 `update.json`。

> 注：仓库必须至少有一个 commit 才能建 Release，所以留了这个 README。
