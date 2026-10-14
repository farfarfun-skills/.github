# farfarfun skills

[farfarfun](https://github.com/farfarfun) 的 **Skills 聚合镜像**子组织，汇集以下两类来源，每小时与上游对齐，并整体镜像至 Gitee：

- **社区 Skill 的 fork** —— 来自 Anthropic、Vercel Labs、mattpocock、吴恩达 context-hub 等团队维护的项目，共 20 个
- **farfarfun 自研 Skill 的镜像** —— 以 `farfarfun-skill--` 为名称前缀，源头位于 [farfarfun-skill](https://github.com/farfarfun-skill) 组织，共 4 个

> ⚠️ 本组织的仓库**均以 fork 关系接入，仅作镜像用途，不接受 PR**。修改社区项目请提交至各自上游；修改 farfarfun 自研 Skill 请前往 [farfarfun-skill](https://github.com/farfarfun-skill)。本组织仅负责汇总、与上游同步及镜像至 Gitee。

## 组织定位

| 需求 | 解决方式 |
| --- | --- |
| 批量安装 Skill，无需逐一查找仓库 | 26 个仓库集中于同一组织，可通过 `fundeploy tool skills-sync install all` 一次性获取 |
| 持续跟进上游更新，避免手工 `git pull` | 由 [`action-daily`](https://github.com/farfarfun-skills/action-daily) 每小时自动同步全部 fork |
| 国内网络访问 GitHub 不稳定 | 全部 26 个仓库每小时镜像至 [gitee.com/farfarfun-skills](https://gitee.com/farfarfun-skills)，`skills-sync` 亦默认从 Gitee 拉取 |

## 自动化

[`action-daily`](https://github.com/farfarfun-skills/action-daily) 为组织级自动化仓库，包含两个 workflow：

- **Daily sync** —— 首先由 [`farfarfun-action/sync-forks`](https://github.com/farfarfun-action/sync-forks) 将名称含 `--` 的 fork 从各自上游更新，随后由 [`farfarfun-action/mirror-repo`](https://github.com/farfarfun-action/mirror-repo) 将组织内**全部**仓库（含 `.github` 及其自身）镜像至 Gitee 同名组织。每小时执行**增量**同步（仅比对 GitHub 侧 commit id，跳过未变更的仓库），每日执行一次**全量**同步，双向校验并自动修复状态漂移。
- **Disable org workflows** —— 每日将除自身以外所有仓库的 workflow 置为 disabled。fork 会连带引入上游的 workflow，若不关闭将持续消耗 Actions 额度。

因此，`<上游 owner>--<仓库名>` 的命名格式是**自动化流程的识别依据**，新接入的 fork 必须按此格式重命名，否则不会纳入同步范围。

## 仓库列表

### farfarfun 自研（镜像）

源头位于 [farfarfun-skill](https://github.com/farfarfun-skill)，由 [`publish-skill`](https://github.com/farfarfun-skill/publish-skill) 推送至此。源头组织中不含 `skills/` 目录的仓库（`publish-skill`、`skill-router`、`.github`）不在镜像范围内。

| 仓库 | 说明 |
| --- | --- |
| [`farfarfun-skill--project-manager`](https://github.com/farfarfun-skills/farfarfun-skill--project-manager) | 面向 AI Agent 的项目治理 Skill，覆盖仓库结构、研发全生命周期门禁、README 与 Topics 审计 |
| [`farfarfun-skill--service-governance`](https://github.com/farfarfun-skills/farfarfun-skill--service-governance) | 服务工程规范 Skill，覆盖发布治理、Bash 生命周期与多仓库子模块编排 |
| [`farfarfun-skill--lang-spec-hub`](https://github.com/farfarfun-skills/farfarfun-skill--lang-spec-hub) | 面向 AI 编码代理的多语言开发规范 Skill（Python、Java 等） |
| [`farfarfun-skill--paperclip-governance`](https://github.com/farfarfun-skills/farfarfun-skill--paperclip-governance) | Paperclip 平台专属治理 Skill，覆盖执行隔离与任务协调 |

> 各 Skill 的适用范围与选择建议，参见源头组织的路由表 [`skill-router`](https://github.com/farfarfun-skill/skill-router)。

### 社区 fork

| 仓库 | 说明 |
| --- | --- |
| [`anthropics--skills`](https://github.com/farfarfun-skills/anthropics--skills) | Anthropic 官方 Agent Skills 实现 |
| [`vercel-labs--skills`](https://github.com/farfarfun-skills/vercel-labs--skills) | 开放 agent skills 生态的 CLI 工具（`npx skills`） |
| [`vercel-labs--agent-skills`](https://github.com/farfarfun-skills/vercel-labs--agent-skills) | Vercel 官方 agent skills 合集 |
| [`addyosmani--agent-skills`](https://github.com/farfarfun-skills/addyosmani--agent-skills) | 面向 AI coding agent 的生产级工程 skills |
| [`andrewyng--context-hub`](https://github.com/farfarfun-skills/andrewyng--context-hub) | 为 coding agent 提供可版本化、可校验的精选文档上下文 |
| [`mattpocock--skills`](https://github.com/farfarfun-skills/mattpocock--skills) | Matt Pocock（AI Hero）发布的工程向 skills |
| [`alirezarezvani--claude-skills`](https://github.com/farfarfun-skills/alirezarezvani--claude-skills) | 345 个以上 Claude Code skills / plugins 的合集，覆盖工程、市场、产品与合规等领域 |
| [`wshobson--agents`](https://github.com/farfarfun-skills/wshobson--agents) | 大型 agentic 插件市场，涵盖 plugin、agent、skill 与 command |
| [`ibelick--ui-skills`](https://github.com/farfarfun-skills/ibelick--ui-skills) | 面向 Design Engineer 的 UI skills 合集 |
| [`jakubkrehel--skills`](https://github.com/farfarfun-skills/jakubkrehel--skills) | 用于构建高质量界面的 agent skills 合集 |
| [`ConardLi--garden-skills`](https://github.com/farfarfun-skills/ConardLi--garden-skills) | Web 设计、知识检索、图片生成等 Skills 合集 |
| [`JimLiu--baoyu-skills`](https://github.com/farfarfun-skills/JimLiu--baoyu-skills) | 宝玉分享的 20 余个日常 AI 协作 Claude Code / Codex skills |
| [`Agents365-ai--drawio-skill`](https://github.com/farfarfun-skills/Agents365-ai--drawio-skill) | 将文本转换为专业 draw.io 图表，内置 UML、BPMN、C4 等 11 种预设 |
| [`tt-a1i--archify`](https://github.com/farfarfun-skills/tt-a1i--archify) | 生成可验证的架构图、时序图与数据流图，输出为自包含 HTML |
| [`yizhiyanhua-ai--fireworks-tech-graph`](https://github.com/farfarfun-skills/yizhiyanhua-ai--fireworks-tech-graph) | 通过自然语言生成生产级 SVG / PNG 技术图表 |
| [`JuliusBrussee--caveman`](https://github.com/farfarfun-skills/JuliusBrussee--caveman) | 压缩 AI agent 的输出 token 用量，实测可节省约 65% |
| [`dietrichgebert--ponytail`](https://github.com/farfarfun-skills/dietrichgebert--ponytail) | 引导 AI agent 以资深工程师的取舍方式工作，用最少的代码解决问题 |
| [`anbeime--skill`](https://github.com/farfarfun-skills/anbeime--skill) | 自动采集 GitHub 上的 Skills 项目并分类整理的技能商店 |
| [`ComposioHQ--awesome-claude-skills`](https://github.com/farfarfun-skills/ComposioHQ--awesome-claude-skills) | Claude Skills 相关资源的 Awesome List |
| [`paperclipai--paperclip`](https://github.com/farfarfun-skills/paperclipai--paperclip) | 开源的 Agent 管理应用 |

### 组织基础设施

| 仓库 | 说明 |
| --- | --- |
| [`action-daily`](https://github.com/farfarfun-skills/action-daily) | 组织级自动化，负责 fork 同步、Gitee 镜像，以及禁用 fork 引入的 workflow |
| `.github` | 本组织主页（`profile/README.md`） |

## 使用方式

### 批量安装：fundeploy skills-sync（推荐）

[`farfarfun/fundeploy`](https://github.com/farfarfun/fundeploy) 提供的 `fundeploy tool skills-sync` 子命令是本组织镜像仓库的本地安装与更新工具，可替代手工 `git clone` 与 `cp` 操作：

```bash
fundeploy tool skills-sync list                  # 查看远端仓库与本地安装状态
fundeploy tool skills-sync install all           # 安装全部尚未安装的仓库
fundeploy tool skills-sync update all            # 更新全部已安装仓库，本地修改将被远端覆盖
fundeploy tool skills-sync delete all --yes      # 删除全部已安装仓库
```

该工具从本组织的 **Gitee 镜像**拉取（国内访问更快），默认安装至 `~/workspace/github/farfarfun-skills`（可通过 `SKILLS_SYNC_DIR` 覆盖），仅选取名称含 `--` 的仓库，并在同步后自动清理仓库内除 `.git` 以外的隐藏目录。

该工具与 [`action-daily`](https://github.com/farfarfun-skills/action-daily) 互为补充：`action-daily` 负责在组织侧保持 fork 与上游同步，`skills-sync` 负责将镜像同步至使用者本地。

### 手工安装单个 Skill

多数 Skill 遵循统一的安装约定：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R <skill-dir> "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安装完成后，可在 Agent 对话中直接引用：

```text
Use $<skill-name> to ...
```

各 Skill 的具体能力、调用方式与依赖要求，请参见对应仓库的 README。

## 其他 farfarfun 组织

farfarfun 的新项目默认在主组织孵化，当某一方向的仓库数量与功能完整度达到一定规模后，即毕业并独立为子组织；规划阶段已确定为独立产品线的，则直接建立子组织。

| 组织 | 产物 |
| --- | --- |
| [farfarfun](https://github.com/farfarfun) | 通用 Python 工具链，含 `far*` 基础库与 `fun*` 领域库 |
| [farfarfun-drive](https://github.com/farfarfun-drive) | 网盘与云存储，含统一接口框架与各网盘驱动 |
| [farfarfun-skill](https://github.com/farfarfun-skill) | **自研 Skill 的源头**，覆盖项目治理、服务规范与多语言开发规范，PR 与 issue 请提交至此 |
| [farfarfun-utools](https://github.com/farfarfun-utools) | uTools 插件，覆盖 AI 聊天、网址导航与两步验证码 |

## 联系

- 📧 **Email**: farfarfun@qq.com
- 🐙 **GitHub**: [@farfarfun](https://github.com/farfarfun)
