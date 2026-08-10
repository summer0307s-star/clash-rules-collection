# 推荐的「规则代理组」配置

在 `proxy-groups` 段落添加一个专门的组来接 GitHub 规则集，例如：

```yaml
proxy-groups:
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

然后在 `rules` 中把 rule-provider 指向它：

```yaml
rules:
  - RULE-SET,custom-domains,GitHub规则
  - RULE-SET,dino-chat,GitHub规则
```

## 推荐的 GitHub 规则源

| 仓库 | 说明 |
|---|---|
| [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) | Mihomo/Clash 官方规则集（当前配置已用） |
| [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) | 主流 Clash Premium 规则集 |
| [Aethersailor/Custom_OpenClash_Rules](https://github.com/Aethersailor/Custom_OpenClash_Rules) | OpenClash 综合配置 |
| [zhanyeye/clash-rules-lite](https://github.com/zhanyeye/clash-rules-lite) | 轻量自定义规则方案 |
