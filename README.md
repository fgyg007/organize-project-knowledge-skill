# Organize Project Knowledge

A reusable Codex skill for turning scattered project documents into one reliable, evidence-based operating system.

It helps answer four questions without creating more competing documents:

1. What has already been done?
2. What needs to be done now?
3. How should it be tested?
4. What evidence counts as accepted?

[中文说明](#中文说明)

## What it does

Use this skill when a project has duplicate documents, unclear ownership, mixed current and historical information, confusing test checklists, or multiple storage locations that should not be identical.

The skill guides Codex to:

- audit the whole documentation system before editing individual files;
- define one source of truth for each information class;
- separate current state, history, roadmap, technical debt, procedures, pending tests, and completed evidence;
- separate AI/platform tests from human black-box acceptance checklists;
- turn a completed pending checklist into the acceptance record instead of creating a duplicate;
- define explicit boundaries between private workspaces and Git/public repositories;
- back up and hash documentation before large reorganizations;
- verify results with file counts, SHA-256, link checks, duplicate checks, secret scans, and scoped Git diffs;
- maintain project knowledge when meaningful events happen rather than creating arbitrary monthly files.
- create a resumable checkpoint for unfinished work without turning it into a second project-memory authority;
- restore a paused task by validating the checkpoint against current repository and external state.

This is a project-knowledge and evidence-management skill. It is not a sprint planner, issue tracker, or replacement for project-specific technical tests.

## Install

### Option 1: Ask the skill installer

Paste this into Codex:

```text
Use $skill-installer to install the skill from https://github.com/fgyg007/organize-project-knowledge-skill.
```

### Option 2: Install with Git

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/fgyg007/organize-project-knowledge-skill.git ~/.agents/skills/organize-project-knowledge
```

Codex detects installed skills automatically. If the skill does not appear, restart Codex.

To update a Git installation later:

```bash
git -C ~/.agents/skills/organize-project-knowledge pull --ff-only
```

See the official [Codex skill documentation](https://learn.chatgpt.com/docs/build-skills) for current skill behavior and locations.

## Use

Mention the skill explicitly in a Codex prompt:

```text
Use $organize-project-knowledge to audit this project's documentation. Tell me what is authoritative, duplicated, obsolete, private, or missing. Do not change files yet.
```

```text
Use $organize-project-knowledge to design a target structure that separates current state, project history, roadmap, technical debt, pending tests, and acceptance records.
```

```text
Use $organize-project-knowledge to back up this documentation, implement the approved reorganization, repair links, and verify the result.
```

```text
Use $organize-project-knowledge to explain what we tested before, what remains untested, which checks belong to AI or the platform, and which checks require a human checklist.
```

Save unfinished work for another session or agent:

```text
Use $organize-project-knowledge to save a resumable checkpoint for this unfinished task, including verified work, unresolved issues, and the exact next action.
```

Resume from a checkpoint:

```text
Use $organize-project-knowledge to restore the latest checkpoint, reconcile it with current repository state, and tell me the next action before continuing.
```

Codex may also select the skill automatically when a request matches its description.

## Audit mode and implementation mode

- **Audit mode:** inspect and report without changing files.
- **Implementation mode:** create a recoverable backup, reorganize files, update links and sync rules, validate the result, and report evidence.

State the mode in your prompt when you want to prevent or authorize changes.

## Information model

| Information class | Purpose |
| --- | --- |
| Current state | One concise source of what is true now and the next action. |
| Project history | An append-only record of decisions, completed work, and verification. |
| Roadmap | Intended future work that has not started. |
| Technical debt | Known problems and explicitly deferred remediation. |
| Procedures | Repeatable instructions that do not claim execution. |
| Pending AI/platform tests | Checks executable by automation, agents, CI, or the platform. |
| Pending human tests | Checkbox-oriented black-box acceptance work for a person. |
| Acceptance records | Dated results from AI, platform, and human testing with evidence. |
| Archives | Historical material that is no longer a current entry point. |
| Work checkpoints | Temporary recovery pointers for unfinished tasks; never a replacement for current project memory or append-only history. |

The private workspace and Git repository do not need the same structure. The skill defines authority, allowed synchronization, sync direction, and private boundaries instead of blindly mirroring folders.

## Safety

- Do not publish passwords, tokens, API keys, private endpoints, or unmasked secrets.
- Do not treat a procedure or an unchecked checklist as proof that a test passed.
- Do not delete or compress historical material before creating and verifying a recoverable backup.
- Do not overwrite unrelated user changes or include them in a cleanup commit.
- Do not call files duplicates based only on similar filenames; compare hashes and meaning.
- Do not copy full logs, conversations, or secrets into work checkpoints; link to authoritative evidence.

## Repository structure

```text
organize-project-knowledge/
├── SKILL.md           # Instructions loaded by Codex
├── agents/
│   └── openai.yaml    # Skill display metadata
├── README.md          # Human-facing installation and usage guide
└── LICENSE            # MIT license
```

## License

[MIT](LICENSE)

---

## 中文说明

这是一个用于整理项目知识体系的 Codex skill。它解决的不是“文件排版不好看”，而是下面这些更根本的问题：

- 同一个问题有多份文档同时回答，不知道应该信哪份；
- 当前状态、历史记录、未来计划和技术债混在一起；
- 测试流程、待测试清单和验收记录互相重复；
- 不清楚以前测过什么、现在要测什么、由 AI 还是人工来测；
- 私有工作区、NAS 和 Git 被误当成必须完全镜像的目录；
- 整理完成后只有“看起来整齐”，没有备份、哈希、链接或重复项检查作为证据。
- 任务中途暂停或换 AI 工具时，没有可验证、可恢复的工作检查点。

### 安装

推荐直接在 Codex 中说：

```text
使用 $skill-installer 从 https://github.com/fgyg007/organize-project-knowledge-skill 安装这个 skill。
```

也可以手动安装：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/fgyg007/organize-project-knowledge-skill.git ~/.agents/skills/organize-project-knowledge
```

如果安装后没有出现，重启 Codex。以后更新可以运行：

```bash
git -C ~/.agents/skills/organize-project-knowledge pull --ff-only
```

### 怎么使用

只检查、不修改：

```text
使用 $organize-project-knowledge 全面检查这个项目的文档体系，告诉我哪些是权威文档、重复文档、旧入口、归档和隐私内容。先不要修改文件。
```

先制定整理方案：

```text
使用 $organize-project-knowledge 为这个项目设计整理方案，明确当前状态、项目历史、路线图、技术债、待 AI/平台测试、待人工测试和验收记录分别放在哪里。
```

备份并执行整理：

```text
使用 $organize-project-knowledge 先备份并校验项目文档，然后执行已经确认的整理方案，修复链接，最后用数量、哈希、重复项、密钥扫描和 Git 状态验收。
```

专门梳理测试体系：

```text
使用 $organize-project-knowledge 梳理这个项目以前测过什么、以后要测什么；把 AI/平台可执行测试、人工黑盒 Checklist 和包含证据的验收记录分开。
```

保存或恢复未完成任务：

```text
使用 $organize-project-knowledge 为当前未完成任务保存上下文检查点，记录已验证结果、未解决问题和下一条可执行动作。
```

### 它遵循的核心规则

1. 先扫描整个项目，再处理局部文件。
2. 每类信息只有一个权威来源，其他文档只链接，不重复抄写。
3. 当前项目记忆负责“现在是什么”，项目历史记忆负责“发生过什么”。
4. AI/平台测试、人工 Checklist 和已完成验收证据分别管理。
5. 待验收文件执行完成后，补充结论和证据，再把同一文件移入验收记录，不重新复制一份。
6. 私有工作区与 Git 不必目录一致，但必须明确权威归属、同步白名单和隐私边界。
7. 大规模整理前先做可恢复备份，并记录路径、大小和 SHA-256。
8. 用真实事件维护文档，不在开发阶段机械地按月份拆分。
9. 上下文检查点只是未完成任务的临时恢复指针；任务完成后将事实合并回项目记忆和历史，再归档检查点。

完整的执行规则见 [SKILL.md](SKILL.md)。
