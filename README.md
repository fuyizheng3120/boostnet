# BoostNet

Surge 5 分流规则配置，开箱即用。

**广告拦截** ([Sukka RuleSet](https://github.com/SukkaW/Surge)) + **国内外智能分流** ([Loyalsoldier](https://github.com/Loyalsoldier/surge-rules))，白名单模式。

## 特性

- 广告 / 钓鱼 / 隐私追踪全面拦截（Sukka 规则集，自动更新）
- 国内域名 & IP 直连，国外流量走代理
- AI 服务（OpenAI / Claude / Gemini）、Telegram 独立策略组
- Apple / iCloud 国内直连
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
| `AI` | OpenAI / Claude / Gemini 等 AI 服务 |
| `Telegram` | Telegram 相关流量 |
| `🎯Direct` | 直连（国内流量） |
| `✈️Final` | 兜底规则（未匹配流量） |

## 规则来源

- [Sukka/Surge](https://github.com/SukkaW/Surge) — 广告拦截 & AI 服务分流
- [Loyalsoldier/surge-rules](https://github.com/Loyalsoldier/surge-rules) — 国内外域名 & IP 分流
- [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) — GeoIP 数据库

## License

MIT
