# BoostNet

Surge 6 分流规则配置，开箱即用。

**广告拦截** ([Sukka RuleSet](https://github.com/SukkaW/Surge)) + **国内外智能分流** ([Loyalsoldier](https://github.com/Loyalsoldier/surge-rules))，白名单模式。

## 特性

- 广告 / 钓鱼 / 隐私追踪全面拦截（Sukka 规则集，含 `reject-drop` 预匹配与搜狗输入法屏蔽）
- Apple 服务精细化分流：国内备案域名直连、Apple CDN 直连、Apple Intelligence 走 AI 组、其他服务走代理
- AI 服务（OpenAI / Claude / Gemini）、Telegram（域名 + IP + ASN）独立策略组
- 国内域名 & IP 直连，国外流量走代理
- 中国 IP 使用 Sukka `china_ip`（排除 HK 播报段），比 `GEOIP,CN` 更准
- Google CN 域名自动重定向至 google.com
- 所有规则集远程拉取，无需手动维护

## 使用方法

### 方式一：直接下载

1. 下载 [BoostNet.conf](./BoostNet.conf)
2. 导入到 Surge → 配置 → 从文件导入
3. 编辑配置，在 `[Proxy]` 和 `[Proxy Group]` 部分填入你的机场订阅地址

### 方式二：远程托管（推荐）

在 Surge 中使用远程配置 URL：

```
https://raw.githubusercontent.com/fuyizheng3120/boostnet/main/BoostNet.conf
```

下载后在本地编辑，填入你自己的机场订阅地址。

## 策略组说明

配置中使用了以下策略组名称，你的机场订阅需要包含或手动创建：

| 策略组 | 用途 |
|--------|------|
| `Proxies` | 默认代理节点选择 |
| `AI` | OpenAI / Claude / Gemini / Apple Intelligence 等 AI 服务 |
| `Telegram` | Telegram 相关流量 |
| `🎯Direct` | 直连（国内流量） |
| `✈️Final` | 兜底规则（未匹配流量） |

## 规则顺序

配置按以下优先级组织，确保分流准确：

1. 自定义规则（最高优先级）
2. LAN
3. 广告拦截 / 反钓鱼 / 隐私
4. Apple 细分（国内直连 / CDN / Intelligence / 其他服务）
5. AI / Telegram 域名
6. Loyalsoldier 白名单兜底（国外代理 / 国内直连）
7. IP 规则（广告 IP / Telegram IP+ASN / LAN IP / 中国 IP）
8. GEOIP,CN → 直连，FINAL → 代理

## 规则来源

- [Sukka/Surge](https://github.com/SukkaW/Surge) — 广告拦截、Apple 细分、AI / Telegram、IP 规则
- [Loyalsoldier/surge-rules](https://github.com/Loyalsoldier/surge-rules) — 国内外域名兜底分流
- [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) — GeoIP 数据库

## License

MIT
