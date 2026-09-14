# dsh-troubleshoot-starter — 故障排查模式框架（DSH）

> 企业运维故障排查 Agent 框架。与 dsh-engineering-starter 同族：DSH 专属 preset + 随包 skills + 一键安装。核心差异化：**故障域分层**——先区分本机/远程/环境差异，再进统一 RCA。

## 快速开始

```bash
scripts/install-dsh.sh                         # 装 preset → $DSH_HOME/.agent-presets/troubleshooting/
scripts/init-ts-workbench.sh ~/Documents/ts-workbench   # 生成工作台骨架（可选）
# DSH 新会话 → 选「故障排查模式」→ workspace 指向工作台/项目 → 描述故障
```

## 三种故障域（先判域再排查）

| 域 | 特征 | 证据源 | 经验归档 |
|---|---|---|---|
| **本机** | 进程/端口/资源/文件 | ps/systemctl/ss/top/df/日志/dmesg/journalctl | sop/本机经验/ |
| **远程** | 目标主机/API/云资源 | ssh/curl/traceroute/云控制台/依赖链 | 跨域先定边界 |
| **环境差异** | dev/test/prod 表现不同 | 配置 diff/网络隔离/凭据/配额/数据规模 | sop/环境基线/ |

统一 RCA：现象 → 时间线 → 变更(CMDB) → 指标 → 链路 → 日志 → 知识库 → 根因 → 报告。证据不足不臆测，事实/推断/建议三分。

## 设计要点

- **判域先行**：最小探测把故障定位到边界一侧，避免查错源。
- **证据纪律**：数据源确认、证据标注（来源/查询条件/结果）、工具失败如实。
- **经验分层**：通用结论换机器仍成立；本机经验带机器特征；环境基线对照差异。
- **preset 层 skills**：随 preset 走，不污染 `~/.agents/skills`。

## License

Apache-2.0
