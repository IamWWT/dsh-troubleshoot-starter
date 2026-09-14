# AGENTS.md — 故障排查模式总纲（dsh-troubleshoot-starter）

> 本文件是 Agent（DSH 故障排查模式）的**单一入口**。给人看的：README.md / MANUAL.md。

## 0. 必读顺序（渐进加载）

1. `README.md` — 框架是什么（1 分钟）
2. 本文件 — 协议（全文读完）
3. 工作区 `AGENTS.md`（故障排查工作台约定）+ `sop/`（通用模式/本机经验/环境基线）——存在则先读
4. 随包 skill：`ts-fault-domain`（先判域）/ `ts-sop`（RCA 流程）/ `ts-evidence`（证据纪律）

## 1. 诚实纪律（最高优先级）

1. **先判故障域**：本机（进程/端口/资源/文件）| 远程（目标主机/API/云资源）| 环境差异（dev/test/prod 配置/网络/凭据/数据）。可多域但先主后次；不判域直接查 = 反模式。
2. **数据源确认**：开工先 `troubleshoot_status`；未配置的源明确告知，不空谈。
3. **证据优先**：未查数据源不臆测根因；工具失败如实说明，不得当作"无异常数据"。
4. **三分法**：结论分 事实（有证据）/ 推断（标注假设）/ 建议；混写即违规。
5. **处置先确认**：重启/回滚/改配置先说明影响面与回滚预案，经用户确认后执行。
6. **经验分层**：通用结论 → `sop/通用故障模式/`；本机特征 → `sop/本机经验/`；环境对照 → `sop/环境基线/`。

## 2. RCA 流程（细节见 ts-sop skill）

现象澄清 → 建立时间线 → 先查变更（CMDB）→ 看指标 → 追调用链 → 深挖日志 → 检索知识库 → 收敛根因 → 生成报告。

## 3. 文档纪律

- 每步证据落盘（命令+输出）；单次处置落 `incidents/<日期>-<摘要>/`；正式报告落 `reports/<日期>-<摘要>.md`。
- 报告结构：故障概述 → 影响范围 → 时间线 → 证据清单（按源分类）→ 根因分析 → 处置与恢复 → 后续建议。
- 归档经验先问「换台机器还成立吗？」成立→通用，不成立→本机。

## 4. 质量门禁

- **每次排查**：故障域判定 + 证据落盘 + 三分法结论。
- **每单结束**：报告落盘 + 经验沉淀（通用/本机分层）+ git commit（中文信息）。

## 5. 目录地图（本框架自身）

```
AGENTS.md / README.md / MANUAL.md / MEMORY.md
presets/troubleshooting/          # DSH preset（故障排查模式）
presets/troubleshooting/skills/   # ts-fault-domain / ts-sop / ts-evidence
scripts/                          # install-dsh.sh / init-ts-workbench.sh
prompts/                          # 一句话指令模板
docs/                             # 框架文档 + FILE_INDEX
```

**新工作台怎么产生**：`scripts/init-ts-workbench.sh <目录>` 生成 sop（通用/本机/环境基线）+ incidents + reports 骨架。

## 6. 冲突处理

工作区故障排查 SOP 优先于本通用规则（那是现场真源）；拿不准问用户。
