# farfarfun skills

面向 AI 编码 Agent（Claude Code、Codex 等）的 **Skills 聚合镜像**组织。这里把两类来源收在一起、每小时跟上游对齐，并整体镜像到 Gitee：

- **社区热门 Skill 的 fork** —— Anthropic、Vercel Labs、mattpocock、吴恩达 context-hub 等团队维护的项目，20 个
- **farfarfun 自研 Skill 的镜像** —— 名称带 `farfarfun-skill--` 前缀，源头在 [farfarfun-skill](https://github.com/farfarfun-skill) 组织，4 个

> ⚠️ 本组织的仓库**都是以 fork 关系接入的镜像，不接受 PR**。改社区项目请去各自上游；改 farfarfun 自研 Skill 请去 [farfarfun-skill](https://github.com/farfarfun-skill)。这里只负责「汇总 + 跟上游同步 + 镜像到 Gitee」。

## 为什么有这个组织

| 需求 | 这里怎么满足 |
| --- | --- |
| 一次装一批 Skill，不用到处找仓库 | 26 个仓库集中在一个组织，`fundeploy tool skills-sync install all` 一条命令拉齐 |
| 上游更新了想跟上，但不想手工 `git pull` | [`action-daily`](https://github.com/farfarfun-skills/action-daily) 每小时自动从上游同步所有 fork |
| 国内网络访问 GitHub 不稳 | 全部 26 个仓库每小时镜像到 [gitee.com/farfarfun-skills](https://gitee.com/farfarfun-skills)，`skills-sync` 也走 Gitee 拉取 |

## 自动化

[`action-daily`](https://github.com/farfarfun-skills/action-daily) 是组织级自动化仓库，两个 workflow：

- **Daily sync** —— 先用 [`farfarfun-action/sync-forks`](https://github.com/farfarfun-action/sync-forks) 把名称含 `--` 的 fork 从各自上游更新，再用 [`farfarfun-action/mirror-repo`](https://github.com/farfarfun-action/mirror-repo) 把组织内**所有**仓库（含 `.github` 和它自己）镜像到 Gitee 同名组织。每小时跑**增量**（只比对 GitHub 侧 commit id，跳过未变动的仓库），每天一次跑**全量**，双向校验并自愈漂移。
- **Disable org workflows** —— 每天把除它自己之外所有仓库的 workflow 置为 disabled。fork 会带着上游的 workflow 一起进来，不关掉会白烧 Actions 额度。

正因如此，仓库名的 `<上游 owner>--<仓库名>` 格式是**自动化的识别依据**，新 fork 进来必须按这个格式改名，否则不会被同步。

## 仓库列表

### farfarfun 自研（镜像）

源头在 [farfarfun-skill](https://github.com/farfarfun-skill)，由 [`publish-skill`](https://github.com/farfarfun-skill/publish-skill) 推送过来；源头组织里不含 `skills/` 目录的仓库（`publish-skill`、`skill-router`、`.github`）不在镜像范围内。

| 仓库 | 说明 |
| --- | --- |
| [`farfarfun-skill--project-manager`](https://github.com/farfarfun-skills/farfarfun-skill--project-manager) | 面向 AI Agent 的项目治理 Skill：仓库结构、研发全生命周期门禁、README 与 Topics 审计 |
| [`farfarfun-skill--service-governance`](https://github.com/farfarfun-skills/farfarfun-skill--service-governance) | 服务工程规范 Skill：发布治理、Bash 生命周期、多仓库子模块编排 |
| [`farfarfun-skill--lang-spec-hub`](https://github.com/farfarfun-skills/farfarfun-skill--lang-spec-hub) | 面向 AI 编码代理的多语言开发规范 Skill（Python、Java 等） |
| [`farfarfun-skill--paperclip-governance`](https://github.com/farfarfun-skills/farfarfun-skill--paperclip-governance) | Paperclip 平台专属治理 Skill：执行隔离、任务协调 |

> 选哪个 Skill、每个 Skill 具体管什么，看源头组织的路由表 [`skill-router`](https://github.com/farfarfun-skill/skill-router)。

### 社区 fork

| 仓库 | 说明 |
| --- | --- |
| [`anthropics--skills`](https://github.com/farfarfun-skills/anthropics--skills) | Anthropic 官方 Agent Skills 实现 |
| [`vercel-labs--skills`](https://github.com/farfarfun-skills/vercel-labs--skills) | 开放 agent skills 生态的 CLI 工具（`npx skills`） |
| [`vercel-labs--agent-skills`](https://github.com/farfarfun-skills/vercel-labs--agent-skills) | Vercel 官方 agent skills 合集 |
| [`addyosmani--agent-skills`](https://github.com/farfarfun-skills/addyosmani--agent-skills) | 面向 AI coding agent 的生产级工程 skills |
| [`andrewyng--context-hub`](https://github.com/farfarfun-skills/andrewyng--context-hub) | 为 coding agent 提供可版本化、可校验的精选文档上下文 |
| [`mattpocock--skills`](https://github.com/farfarfun-skills/mattpocock--skills) | Matt Pocock（AI Hero）出品的工程向 skills |
| [`alirezarezvani--claude-skills`](https://github.com/farfarfun-skills/alirezarezvani--claude-skills) | 345+ Claude Code skills / plugins 大合集，覆盖工程、市场、产品、合规等多领域 |
| [`wshobson--agents`](https://github.com/farfarfun-skills/wshobson--agents) | 大型 agentic 插件市场：plugin / agent / skill / command 全家桶 |
| [`ibelick--ui-skills`](https://github.com/farfarfun-skills/ibelick--ui-skills) | 面向 Design Engineer 的 UI skills 合集 |
| [`jakubkrehel--skills`](https://github.com/farfarfun-skills/jakubkrehel--skills) | 帮助搭建优秀界面的 agent skills 合集 |
| [`ConardLi--garden-skills`](https://github.com/farfarfun-skills/ConardLi--garden-skills) | Web 设计、知识检索、图片生成等 Skills 合集 |
| [`JimLiu--baoyu-skills`](https://github.com/farfarfun-skills/JimLiu--baoyu-skills) | 宝玉分享的 20+ 个日常 AI 协作 Claude Code / Codex skills |
| [`Agents365-ai--drawio-skill`](https://github.com/farfarfun-skills/Agents365-ai--drawio-skill) | 文本转专业 draw.io 图表（UML、BPMN、C4 等 11 种预设） |
| [`tt-a1i--archify`](https://github.com/farfarfun-skills/tt-a1i--archify) | 生成可验证的架构/时序/数据流图，自包含 HTML |
| [`yizhiyanhua-ai--fireworks-tech-graph`](https://github.com/farfarfun-skills/yizhiyanhua-ai--fireworks-tech-graph) | 用自然语言生成生产级 SVG/PNG 技术图表 |
| [`JuliusBrussee--caveman`](https://github.com/farfarfun-skills/JuliusBrussee--caveman) | 压缩 AI agent 输出 token 用量（约省 65%） |
| [`dietrichgebert--ponytail`](https://github.com/farfarfun-skills/dietrichgebert--ponytail) | 让 AI agent 像资深工程师一样"偷懒"，写最少的代码 |
| [`anbeime--skill`](https://github.com/farfarfun-skills/anbeime--skill) | 自动抓取 GitHub 全网 Skills 项目并分类整理的技能商店 |
| [`ComposioHQ--awesome-claude-skills`](https://github.com/farfarfun-skills/ComposioHQ--awesome-claude-skills) | Claude Skills 相关资源的 Awesome List |
| [`paperclipai--paperclip`](https://github.com/farfarfun-skills/paperclipai--paperclip) | 开源的 Agent 管理应用 |

### 组织基础设施

| 仓库 | 说明 |
| --- | --- |
| [`action-daily`](https://github.com/farfarfun-skills/action-daily) | 组织级自动化：fork 同步、Gitee 镜像、禁用 fork 带来的 workflow |
| `.github` | 本组织主页（`profile/README.md`） |

## 使用方式

### 批量安装：fundeploy skills-sync（推荐）

[`farfarfun/fundeploy`](https://github.com/farfarfun/fundeploy) 的 `fundeploy tool skills-sync` 子命令是本组织镜像仓库的本地安装/更新工具，替代手工 `git clone` / `cp`：

```bash
fundeploy tool skills-sync list                  # 查看远端 + 本地安装状态
fundeploy tool skills-sync install all           # 安装全部未安装的仓库
fundeploy tool skills-sync update all            # 更新全部已安装仓库（本地修改会被远端覆盖）
fundeploy tool skills-sync delete all --yes      # 删除全部已安装仓库
```

它从本组织的 **Gitee 镜像**拉取（国内更快），默认落到 `~/workspace/github/farfarfun-skills`（可用 `SKILLS_SYNC_DIR` 覆盖），只挑选名称含 `--` 的仓库，同步后自动清理仓库内除 `.git` 外的隐藏目录。

和 [`action-daily`](https://github.com/farfarfun-skills/action-daily) 是互补关系：`action-daily` 负责组织侧让 fork 跟上游保持同步，`skills-sync` 负责把这些镜像同步到使用者本地。

### 手工安装单个 Skill

多数 Skill 遵循同一套约定：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R <skill-dir> "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安装后在 Agent 对话中直接引用：

```text
Use $<skill-name> to ...
```

具体每个 Skill 的能力、调用方式和依赖，参见各仓库自己的 README。

## 其他 farfarfun 组织

| 组织 | 产物 |
| --- | --- |
| [farfarfun](https://github.com/farfarfun) | 通用 Python 工具链：`far*` 基础库 + `fun*` 领域库 |
| [farfarfun-drive](https://github.com/farfarfun-drive) | 网盘 / 云存储：统一接口框架 + 各网盘驱动 |
| [farfarfun-skill](https://github.com/farfarfun-skill) | **自研 Skill 的源头**：项目治理、服务规范、多语言开发规范（PR / issue 走这里） |
| [farfarfun-utools](https://github.com/farfarfun-utools) | uTools 插件：AI 聊天、网址导航、两步验证码 |

## 联系

- 📧 **Email**: farfarfun@qq.com
- 🐙 **GitHub**: [@farfarfun](https://github.com/farfarfun)
