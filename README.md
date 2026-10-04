# Bilibili Ticketing Assistant（BTicket）

B 站会员购抢票助手 —— Android 正式版安装包发布仓库。

> ⚠️ 本仓库**仅用于发布 APK 与校验值，不开源**。仓库内容只有安装包、图标与说明文件。

- 官网 / 云控入口：<https://bta.bushili.fun/>
- 下载请走 [Releases](../../releases) 的最新版本，或直接在官网点「下载 App」。
- App 内的「检查更新」由云控下发，同样指向本仓库的 Release 资产。

## 安装包校验

每个 Release 都会附带 `SHA256SUMS.txt`，列出该版本全部资产的 SHA-256。下载后可比对：

```powershell
Get-FileHash .\Alpha5.apk -Algorithm SHA256
```

```bash
sha256sum Alpha5.apk
```

签名证书 SHA-256 指纹：`3ED83E5AE5934A2867EE9A7334FB5CECED2499C29588AB463020AF8905512248`
（指纹不一致的包请勿安装。）

## 安装说明

1. 下载 APK 后在手机上打开，系统会提示「允许安装未知来源应用」，允许即可。
2. 从旧版本升级可直接覆盖安装，数据与登录状态保留。
3. 仅需 arm64-v8a 机型（近年绝大多数安卓手机）。
