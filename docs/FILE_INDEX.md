---
title: FILE_INDEX — dsh-troubleshoot-starter
type: index
status: active
version: 1.0.0
date: 2026-09-14
---

# FILE_INDEX — dsh-troubleshoot-starter

## 根目录
- AGENTS.md — 故障排查模式总纲
- README.md / MANUAL.md / MEMORY.md / LICENSE / .gitignore

## presets/troubleshooting/
- presets/troubleshooting/preset.yml
- presets/troubleshooting/agent.cordis.yml（persona + 工具集 + skill-filesystem）
- presets/troubleshooting/skills/README.md
- presets/troubleshooting/skills/ts-fault-domain/SKILL.md — 故障域分层（本机/远程/环境）
- presets/troubleshooting/skills/ts-sop/SKILL.md — 结构化 RCA 流程
- presets/troubleshooting/skills/ts-evidence/SKILL.md — 证据纪律

## scripts/
- scripts/install-dsh.sh — 安装 preset+skills
- scripts/init-ts-workbench.sh — 生成工作台骨架（sop 三层 + incidents + reports）

## prompts/
- prompts/incident.md — 报障
- prompts/review-sop.md — 经验库体检

## docs/
- docs/FILE_INDEX.md — 本文件
