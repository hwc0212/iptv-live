# LemonIPTV GitHub 定制版

[下载安装包](https://github.com/hwc0212/iptv-live/raw/refs/heads/main/apps/LemonIPTV-GitHub-v1.1.11-hwc.1.apk) · [可构建源码](LemonIPTV-GitHub-v1.1.11-hwc.1-source.zip) · [安全检查记录](SECURITY-REVIEW.md) · [SHA-256](SHA256SUMS.txt)

应用名 `LemonIPTV GitHub`，包名 `com.hwc0212.lemoniptv`，版本 `1.1.11-hwc.1`。独立签名，与原版 `com.lemoniptv.lite` 并存；不能作为原版的覆盖升级。源码声明最低 Android 5.0/API 21，本次实测为 Android 9/API 28、ARMv7 小米盒子。

初始默认源只有：

~~~text
https://raw.githubusercontent.com/hwc0212/iptv-live/main/channels.m3u
~~~

以后编辑仓库根目录 `channels.m3u` 即可；在播放器菜单清除缓存后，完全退出并重新打开应用。GitHub Raw 可能缓存数分钟。

本版移除原版的未鉴权局域网管理和 APK 上传入口、应用内自动下载安装流程及安装其他 APK 的权限，恢复系统正常 HTTPS 校验。Guava 传递依赖固定到修复版 `33.7.2-android`。播放器、遥控换台、收藏和节目单功能保留。

升级本定制版时须使用同一签名的后续包；签名指纹见 `audit-summary.json`。签名私钥与口令仅保存在所有者本机，不在此仓库。手机或电视上的外部文件管理器／系统安装器负责安装，应用本身不再申请安装权限。

原应用代码的 MIT 许可通知保留。Jellyfin FFmpeg 扩展声明 GPLv3，相关许可与精确源码入口见 `THIRD_PARTY_NOTICES.txt`、`LICENSE-GPL-3.0.txt`；其他依赖按各自许可提供。

这是一份有范围说明的检查与修改记录，不是绝对无后门或漏洞的认证。原版数据和安装包未被删除；返回原版也会恢复其原有安全行为。完整验证和当前已知限制见安全记录。
