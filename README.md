# IPTV 频道清单

LemonIPTV 固定订阅地址：

~~~text
https://raw.githubusercontent.com/hwc0212/iptv-live/main/channels.m3u
~~~

日常只编辑 [channels.m3u](channels.m3u)，保存到 main 分支，订阅地址无需更换。更新后重开 LemonIPTV，或按菜单键执行“清除缓存”刷新列表。GitHub Raw 缓存可能导致数分钟延迟；持续播放中的软件不会立即重载整个频道表。

## 当前内容

共 96 个频道、163 条流地址：18 个央视频道（CCTV-1 至 CCTV-17，另含 CCTV-5+）、34 个省级卫视、37 个地方频道、7 个国际频道。CCTV-1、CCTV-13 排在最前；同名条目是多线路，LemonIPTV 会合并并在失败时尝试备用地址。

[checks.json](checks.json) 是本次检测快照，区分网络取流检查与盒子人工验收。手工编辑频道后需重新检测，不能把旧记录当作最新结果。部分频道仅经过列表和视频分片检查，不能承诺长期稳定。

2026-11-15 更新：检查 483 条候选，仅收录通过两轮取流、音视频节目表检查和直播分片持续推进检查的线路。移除 10 条旧线路，其中部分虽返回 HTTP 200，却停留在旧录像或不再更新；不是只按状态码筛选。

此前用户已确认 CCTV-1、CCTV-13 主线路的实际台标、画面和声音正常；这些主线路保留。本次新增 CCTV-5、CCTV-5+、CCTV-16 和省级/地方频道，实机复核结果见 checks.json。备用线路及其余频道未全部经过人工观看和长期测试。

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
