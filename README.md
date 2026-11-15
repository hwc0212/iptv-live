# IPTV 频道清单

LemonIPTV 固定订阅地址：

~~~text
https://raw.githubusercontent.com/hwc0212/iptv-live/main/channels.m3u
~~~

日常只编辑 [channels.m3u](channels.m3u)，保存到 main 分支，订阅地址无需更换。更新后在 LemonIPTV 菜单执行“清除缓存”，再完全退出并重新打开应用。GitHub Raw 缓存可能导致数分钟延迟；持续播放中的软件不会立即重载整个频道表。

## 定制安装包

[下载 LemonIPTV GitHub 定制版](https://github.com/hwc0212/iptv-live/raw/refs/heads/main/apps/LemonIPTV-GitHub-v1.1.11-hwc.1.apk) · [安装与源码说明](apps/README.md) · [安全检查记录](apps/SECURITY-REVIEW.md)

此包默认订阅本仓库，使用独立包名与签名，与原版并存。已移除未鉴权网页管理／APK 上传和旧自动安装入口，恢复 HTTPS 校验，并更新受已知漏洞影响的 Guava 依赖；检查范围与剩余限制见安全记录。

## 当前内容

共 96 个频道、163 条流地址：18 个央视频道（CCTV-1 至 CCTV-17，另含 CCTV-5+）、34 个省级卫视、37 个地方频道、7 个国际频道。CCTV-1、CCTV-13 排在最前；同名条目是多线路，LemonIPTV 会合并并在失败时尝试备用地址。

[checks.json](checks.json) 是本次检测快照，区分网络取流检查与盒子人工验收。手工编辑频道后需重新检测，不能把旧记录当作最新结果。部分频道仅经过列表和视频分片检查，不能承诺长期稳定。

2026-11-15 更新：检查 483 条候选，仅收录通过两轮取流、音视频节目表检查和直播分片持续推进检查的线路。移除 10 条旧线路，其中部分虽返回 HTTP 200，却停留在旧录像或不再更新；不是只按状态码筛选。

此前用户已确认 CCTV-1、CCTV-13 主线路的实际台标、画面和声音正常；这些主线路保留。本次新增的 CCTV-5、CCTV-5+、CCTV-16 均显示 1920×1080，并由用户确认实际台标、画面、声音正常。盒子逐台核对 18 个央视频道的播放器分辨率和活动音轨，并抽测江苏、安徽、浙江卫视、广州综合、江苏公共新闻；重开后仍使用本仓库并解析出 4 个分组、96 个频道。完整记录见 [checks.json](checks.json)。

播放器元信息和活动音轨不等同于每条备用线路都经过人工画面验收。逐频道解码帧计数未能取得，因此未将它标为通过；备用线路及其余频道未全部经过人工观看和长期测试。有效性以检测时的家中网络为准。

## 增删频道

每条线路使用两行：

~~~m3u
#EXTINF:-1 tvg-id="CCTV1" tvg-name="CCTV-1 综合" group-title="央视频道",CCTV-1 综合
https://example.com/public/live.m3u8
~~~

示例 URL 仅表示格式。填入已验证可访问且有权使用的公开地址；同一频道的备用线路保持相同的 tvg-name 和 group-title。删除失效线路时一并删除对应的 EXTINF 行。

## 来源与范围

- [iptv-org/iptv](https://github.com/iptv-org/iptv/blob/master/streams/cn.m3u)
- [Kinghuchao/tvbox-live](https://github.com/Kinghuchao/tvbox-live/blob/main/docs/cctv.m3u)
- [DataShare-duo/IPTV-Source](https://github.com/DataShare-duo/IPTV-Source/blob/main/movie_live.txt)

本仓库只整理公开链接和检测结果，不提供视频中转服务。不会绕过鉴权、付费或地域限制，返回拒绝访问的地址不纳入清单。频道名称以实际台标与播放内容为准，不保留已发现的明显错标地址。

若新清单有问题，可通过 GitHub 文件历史恢复上一版 channels.m3u；LemonIPTV 中原有源也可手动切回。

