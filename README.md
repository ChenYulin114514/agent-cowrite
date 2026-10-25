# cowrite-project · 共笔项目协作 skill

让几十个 agent 和人，在不同电脑、不同 agent 软件上，共同维护一个项目而不撞车。

不依赖 Git 仓库式合并，靠一个共享文件夹里的六样设施加一套认领与仲裁规矩：

- **一页纸项目简介**（MANIFEST.md）——入伙只读它，省 token
- **登记簿**（LEDGER.md）——谁在、谁领了哪张卡
- **任务池**（INBOX/）——一张卡片一个活，卡尾带评论区
- **工作台**（DESK/）——每人一个格子
- **舞台**（STAGE/）——仅比稿时用
- **定稿库**（ARCHIVE/）——每个定稿改动留痕，可审计

核心规矩：领卡先写先得（意图广播）；撞车走裁判分流——拆得开就拆细，拆不动就比稿盲评，平手升级给人。完整守则见 `skills/cowrite-project/SKILL.md`。

## 安装（四种途径，选一种）

### 1. 一条命令（推荐）

适用于 Claude Code、Codex、Cursor、OpenCode 等 50 多种 agent，CLI 会自动适配进对应软件的指令位：

```
npx skills add 陈玉林114514/agent-cowrite --skill cowrite-project
```

- 加 `-g` 装全局（所有项目生效）；不加则只对当前项目生效
- 先预览不安装：`npx skills add 陈玉林114514/agent-cowrite --list`
- 验证装好没：`npx skills list`
- 以后更新：`npx skills update`
- 只给某个软件装：`-a claude-code`（可重复写多个）

### 2. 让 agent 自己抓原文（任何能上网的 agent）

把下面这句话发给你的 agent：

> 抓取 https://raw.githubusercontent.com/陈玉林114514/agent-cowrite/main/skills/cowrite-project/SKILL.md ，按文件里的说明把自己适配安装好

仓库在 Gitee 的话，把链接换成：
`https://gitee.com/陈玉林114514/agent-cowrite/raw/main/skills/cowrite-project/SKILL.md`

### 3. WorkBuddy

拿 `cowrite-project.zip`，解压到 `~/.workbuddy/skills/`（用户级，所有项目生效），或放进某个项目的 `.workbuddy/skills/`（项目级）。

### 4. 手动塞进软件的指令位

| 软件 | 放哪 |
|---|---|
| Claude Code | 项目文件夹里的 `CLAUDE.md` |
| Cursor | `.cursor/rules/cowrite.mdc`（老版本用 `.cursorrules`） |
| Codex 等认 AGENTS.md 的 | 项目根目录 `AGENTS.md` |
| 其他 | 守则全文粘贴进它的"自定义指令 / 项目知识" |

内容一律用 `skills/cowrite-project/SKILL.md` 的正文。

## 开一个新项目

1. 一个人当项目所有者，按 SKILL.md 里"新建项目的家"一节搭六样设施的空架子，MANIFEST 里写明谁是裁判
2. 选定同步盘（坚果云 / OneDrive / NAS / 局域网共享文件夹），把文件夹共享给所有协作者
3. 每人登记簿第一行写：**人名＋软件名**（防止同名撞车）
4. 拿一张小卡试跑一次，顺圈了再上大活

注意：同步盘同时改同一个文件会蹦出"冲突副本"——守则要求认领写在任务卡文件里、登记簿只增行，就是从设计上绕开它；真撞了也有评论区和裁判兜底。

## 更新规矩

改 SKILL.md → 推送仓库 → 其他人 `npx skills update`（或重新抓原文）。守则第 5 条：任何人发现简介过期，建卡"更新简介"，别忍着。

## 许可

MIT
