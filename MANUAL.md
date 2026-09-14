# MANUAL — dsh-troubleshoot-starter 使用手册

## 1. 安装

```bash
scripts/install-dsh.sh                   # preset → $DSH_HOME/.agent-presets/troubleshooting/
scripts/install-dsh.sh --uninstall       # 卸载（保留备份）
```

## 2. 新建工作台

```bash
scripts/init-ts-workbench.sh ~/Documents/ts-workbench
```

生成 sop/{通用故障模式,本机经验,环境基线} + incidents/ + reports/ + AGENTS.md。

## 3. 日常使用

- 描述故障 → Agent 先判故障域 → RCA → 报告。
- 经验沉淀：通用结论进 通用故障模式/，本机特征进 本机经验/，环境对照进 环境基线/。
- 环境基线：每个环境（dev/test/prod）一份组件版本/配置/网络快照。

## 4. 常见问题

| 问题 | 答案 |
|---|---|
| 需要数据源插件？ | 是——由 dsh-troubleshoot-workbench 等插件提供 troubleshoot_status/query_* 工具；未配置会明确告知 |
| 判域失败怎么办？ | 用最小探测（一条 curl/命令）定位边界，再决定往哪边深挖 |
| 本机 vs 通用经验？ | 「换台机器还成立吗？」成立→通用，不成立→本机 |
| 需要重启？ | 不需要，新会话生效 |
