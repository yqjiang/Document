# 前言
本文档重点说明的是可能和标准协议不一样的部分，其他的具体细节可以对应本目录下的抓包数据 qiniu-rtmp.pcap 和 rtmp_specification_1.0.pdf。
# 握手阶段
握手分为简单握手和复杂握手。先判断是否能复杂握手，如果能复杂握手，就复杂握手，否则使用简单握手。
# 交互阶段
命令顺序严格按照抓包。
其中 `connect()` 命令的 `flashVer` 字段，格式为 `FMLE/3.0 (compatible; obs-studio/0.12.0; FMSc/1.0)`，需要表明设备名称和软件名称。
# metadata 字段
必填字段为：
 - 播放：`cdn_ip` 边缘节点 IP
 - 推流：`framerate` 帧率

其他字段选填。

# Latency Benchmark 

关于延迟测量方法(Latency Benchmark)，
在推流 SDK 中每隔 15s 发送 `"currentTime", 1489631528` 的 CommandMessage。参数为当前时间戳，客户端收到后可以测量延迟。

# 数据阶段
音频 csid 为 6，视频/AMF0/AMF3消息 csid 为 4，其他 csid 为 5
