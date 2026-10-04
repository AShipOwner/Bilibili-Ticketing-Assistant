<p align="center"><img src="icon.png" width="112" height="112" alt="Bilibili Ticketing Assistant 图标"></p>

# Bilibili Ticketing Assistant（BTicket）

B 站会员购抢票助手 —— Android 正式版安装包发布仓库。

> ⚠️ 本仓库**仅用于发布 APK 与校验值，不开源**：仓库内容只有安装包、图标与说明文件，源码不在这里。

- 官网 / 云控入口：<https://bta.bushili.fun/>
- 下载请走 [Releases](../../releases) 的最新版本，或直接在官网点「下载 App」。
- App 内的「检查更新」由云控下发，指向的同样是本仓库的 Release 资产 ——
  安装包带宽全部由 GitHub CDN 承担，业务服务器不再承接 APK 下载。

## 当前版本

| 版本 | versionCode | 直接下载 |
|---|---|---|
| Alpha5 | 10 | <https://github.com/BuShiLiNB/Bilibili-Ticketing-Assistant/releases/download/v10/Alpha5.apk> |
| Alpha4 | 8 | <https://github.com/BuShiLiNB/Bilibili-Ticketing-Assistant/releases/download/v8/Alpha4.apk> |
| Alpha3 | 6 | <https://github.com/BuShiLiNB/Bilibili-Ticketing-Assistant/releases/download/v6/Alpha3.apk> |

## 安装包校验

每条 Release 都附带 `SHA256SUMS.txt`，列出该版本全部资产的 SHA-256。下载后可比对：

```powershell
Get-FileHash .\Alpha5.apk -Algorithm SHA256
```

```bash
sha256sum Alpha5.apk
```

签名证书 SHA-256 指纹：`3ED83E5AE5934A2867EE9A7334FB5CECED2499C29588AB463020AF8905512248`
（指纹不一致的包请勿安装。App 安装前也会强制校验 SHA-256。）

## 安装说明

1. 下载 APK 后在手机上打开，系统会提示「允许安装未知来源应用」，允许即可。
2. 从旧版本升级可直接覆盖安装，登录状态与本地数据保留。
3. 仅需 arm64-v8a 机型（近年绝大多数安卓手机），Android 8.0+。

## 发布流程（维护者）

```powershell
powershell -File scriptsuild-release.ps1            # 构建并生成 release-manifest.json
powershell -File scripts\publish-apk-github.ps1       # 上传 GitHub Release + 写云控更新通道
```

发布脚本会先校验 `release-manifest.json` 的 `apkSHA256` 与待上传文件一致，
再验证匿名 HEAD 能取回完整字节数，最后才注册云控 —— 避免出现「公告一个版本、实际发另一个版本」。
