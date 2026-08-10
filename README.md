# clash-rules-collection

自用 Clash / Mihomo 代理规则集合，主要用于配合 Clash Verge Rev 使用。

## 规则文件

| 文件 | 类型 | 说明 |
|---|---|---|
| `rules/custom-domains.list` | `domain` | 常用自定义域名分流 |
| `rules/dino-chat.list` | `domain` | Dino 应用相关域名（配合 PROCESS-PATH 使用） |
| `rules/ai.list` | `domain` | AI 服务（OpenAI、Claude、Gemini 等） |
| `rules/binance.list` | `domain` | 币安及加密货币相关 |
| `rules/tailscale.list` | `domain` | Tailscale 相关域名 |

## 在 Clash Verge 中使用

在配置文件的 `rule-providers` 段落添加：

```yaml
rule-providers:
  custom-domains:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/custom-domains.list"
    path: ./ruleset/custom-domains.list
    interval: 86400
  dino-chat:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/dino-chat.list"
    path: ./ruleset/dino-chat.list
    interval: 86400
  ai:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/ai.list"
    path: ./ruleset/ai.list
    interval: 86400
  binance:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/binance.list"
    path: ./ruleset/binance.list
    interval: 86400
  tailscale:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/tailscale.list"
    path: ./ruleset/tailscale.list
    interval: 86400
```

在 `rules` 段落引用：

```yaml
rules:
  - RULE-SET,custom-domains,GitHub规则
  - RULE-SET,dino-chat,GitHub规则
  - RULE-SET,ai,Ai
  - RULE-SET,binance,BI
  - RULE-SET,tailscale,全球直连
```

## 说明

- 本仓库仅包含**规则**（域名、进程路径），**不包含任何代理节点或订阅信息**。
- 欢迎补充更多应用规则， especially for `com.dino.chat` 这类 iOS App 的进程路径分流。
