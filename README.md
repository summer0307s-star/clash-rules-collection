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

### 1. 添加「GitHub规则」代理组

在 `proxy-groups` 段落添加：

```yaml
- name: GitHub规则
  type: select
  proxies:
    - 默认
    - 自动选择
    - 香港
    - 中国台湾
    - 日本
    - 韩国
    - 新加坡
    - 美国
    - 英国
    - 手动选择
    - DIRECT
```

### 2. 添加 rule-providers

```yaml
rule-providers:
  github-rules-custom-domains:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/custom-domains.list"
    path: ./ruleset/github-rules-custom-domains.list
    interval: 86400
  github-rules-dino-chat:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/dino-chat.list"
    path: ./ruleset/github-rules-dino-chat.list
    interval: 86400
  github-rules-ai:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/ai.list"
    path: ./ruleset/github-rules-ai.list
    interval: 86400
  github-rules-binance:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/binance.list"
    path: ./ruleset/github-rules-binance.list
    interval: 86400
  github-rules-tailscale:
    type: http
    behavior: domain
    format: text
    url: "https://raw.githubusercontent.com/summer0307s-star/clash-rules-collection/main/rules/tailscale.list"
    path: ./ruleset/github-rules-tailscale.list
    interval: 86400
```

### 3. 在 rules 中引用

```yaml
rules:
  - RULE-SET,github-rules-custom-domains,GitHub规则
  - RULE-SET,github-rules-dino-chat,GitHub规则
  - RULE-SET,github-rules-ai,Ai
  - RULE-SET,github-rules-binance,BI
  - RULE-SET,github-rules-tailscale,全球直连
```

## 说明

- 本仓库仅包含**规则**（域名、进程路径），**不包含任何代理节点或订阅信息**。
- 欢迎补充更多应用规则， especially for `com.dino.chat` 这类 iOS App 的进程路径分流。

## 推荐的 GitHub 规则源

| 仓库 | 说明 |
|---|---|
| [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) | Mihomo/Clash 官方规则集 |
| [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) | 主流 Clash Premium 规则集 |
| [Aethersailor/Custom_OpenClash_Rules](https://github.com/Aethersailor/Custom_OpenClash_Rules) | OpenClash 综合配置 |
| [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite) | 轻量自定义规则方案 |
