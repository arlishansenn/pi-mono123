# 第一课：安装 Pi、设置模型、写第一个 PRD

> 适用对象：第一次使用 Pi 的产品经理、项目经理、运营同事或研发协作人员。
>
> 官网：https://pi.dev/

---

## 1. 安装 Pi

确认电脑已安装 Node.js 和 npm 后，在终端执行：

```bash
npm install -g @earendil-works/pi-coding-agent
```

检查是否安装成功：

```bash
pi --version
```

启动 Pi：

```bash
pi
```

如果 Pi 提示登录，在 Pi 里输入：

```text
/login
```

### 第一次登录推荐设置

面向中国大陆员工，优先推荐使用 **DeepSeek**，原因是访问和付款路径通常更适合大陆环境，且 Pi 支持 `DEEPSEEK_API_KEY`。

第一次 `/login` 时建议这样选：

1. Provider 选择：`DeepSeek`；
2. 按提示粘贴公司提供的 DeepSeek API Key；
3. 登录成功后，先正常进入 Pi。

然后设置模型。最稳妥的方式是在启动 Pi 时指定模型：

```bash
pi --model deepseek/deepseek-v4-flash
```

日常写 PRD、自我训练、普通任务，默认用：

```text
deepseek/deepseek-v4-flash
```

如果任务明显更复杂，需要更强推理能力，再切换到：

```bash
pi --model deepseek/deepseek-v4-pro
```

如果已经在 Pi 里面，也可以输入：

```text
/model
```

然后搜索 `deepseek-v4-flash`。注意选择 provider 是 `deepseek` 的模型；如果只看到 `openrouter` 下面的 `deepseek/...`，那是 OpenRouter 路由，不是 DeepSeek 官方 API Key 路由。

> 如果员工没有 DeepSeek API Key，先向负责人申请，不要使用个人 key 处理公司资料。

---

## 2. 安装 Pi package

Pi 可以从 npm 或 GitHub 安装扩展包。

### 示例 1：从 npm 安装

```bash
pi install npm:@foo/pi-tools
```

### 示例 2：从 GitHub 安装

```bash
pi install git:github.com/badlogic/pi-doom
```

查看已安装的 package：

```bash
pi list
```

管理启用/禁用：

```bash
pi config
```

> 安全提醒：Pi package 可能包含 extension、skill、prompt、theme。第三方包有系统权限，安装前应确认来源可信。

---

## 3. 安装产品经理常用 Skills

本教程推荐安装 Matt Pocock 的 skills：

GitHub：https://github.com/mattpocock/skills

安装命令：

```bash
npx skills@latest add mattpocock/skills
```

安装时选择你要使用的 coding agent，并确保选中：

```text
/setup-matt-pocock-skills
```

进入项目目录后启动 Pi：

```bash
pi
```

然后在 Pi 里输入：

```text
/setup-matt-pocock-skills
```

它会询问：

1. issue tracker 用 GitHub、GitLab、本地 markdown，还是其他系统；
2. triage 标签如何命名；
3. 项目文档和 ADR 放在哪里。

如果只是第一次练习，可以选择最简单的配置：

- issue tracker：GitHub 或 local markdown；
- triage 标签：使用默认值；
- domain docs：single-context。

---

## 4. 产品经理最常用的几个 Skill

建议员工先掌握这几个：

```text
/grill-me
/to-prd
/to-issues
/triage
```

### `/grill-me`

让 Pi 先追问需求，避免一开始就写错方向。

适合这样说：

```text
/grill-me

我要做一个“员工请假审批系统”，请先连续追问我关键产品问题，直到需求足够清楚。
```

### `/to-prd`

把已经讨论清楚的需求整理成 PRD。

适合这样说：

```text
/to-prd

请基于刚才的讨论，生成一个 prd.md 文件。
不要创建 issue，只在当前目录生成 prd.md。
```

### `/to-issues`

把 PRD 拆成可以交给研发或 AI agent 执行的任务。

适合这样说：

```text
/to-issues

请把 prd.md 拆成可以独立完成的 GitHub issues。
```

### `/triage`

整理和判断 issue 是否清楚、是否需要补充信息、是否可以交给 agent 执行。

---

## 5. 第一个练习任务：写 `prd.md`

在一个空项目目录里启动 Pi：

```bash
pi
```

然后直接输入：

```text
/grill-me

我要写第一个产品 PRD，主题是“员工请假审批系统”。
请你像产品负责人一样追问我关键问题，包括：
1. 谁会使用这个系统；
2. 现在的请假流程有什么问题；
3. 请假、审批、撤销、驳回分别怎么处理；
4. 需要哪些通知；
5. 成功标准是什么。
```

回答完 Pi 的问题后，再输入：

```text
/to-prd

请基于刚才的讨论，在当前目录生成 prd.md。
要求包含：
1. 背景
2. 目标
3. 用户角色
4. 用户故事
5. 核心流程
6. 功能需求
7. 非功能需求
8. 验收标准
9. 不做什么
10. 风险和待确认问题

不要创建 issue，只生成 prd.md 文件。
```

生成后，让 Pi 帮你检查：

```text
请检查 prd.md 是否清楚、完整、可执行。
如果有明显缺口，请列出来，并帮我补充到文档里。
```

---

## 6. 不手敲 git 命令，让 Pi 自己提交并 push

员工不需要记任何提交相关的命令。

PRD 确认无误后，直接在 Pi 里用自然语言说：

```text
请检查当前改动，把 prd.md commit 并 push 到 GitHub。
commit message 用：docs: add first product requirements document
```

或者更简单：

```text
请把 prd.md 提交并 push 到 GitHub。
```

Pi 会自己判断需要执行哪些 git 操作。

---

## 7. 完成标准

员工完成后，应能给负责人一个 GitHub 仓库链接，并且仓库里至少包含：

```text
prd.md
```

`prd.md` 应该能回答：

- 这个产品解决什么问题；
- 谁会用；
- 用户怎么完成核心流程；
- 哪些功能必须做；
- 哪些功能暂时不做；
- 怎么判断做完了。

