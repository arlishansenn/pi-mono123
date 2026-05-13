# 自我训练指南：用 Pi 完成第一个 PRD，并安装 RPIV

> 这是员工自己照着做的练习手册。
>
> 目标：自己安装 Pi，安装常用 skills，用 Pi 生成 `prd.md`，让 Pi 自己提交并 push 到 GitHub，然后完成第二节课的 RPIV 安装。

---

## 自我训练目标

完成后，你应该能做到：

1. 自己打开 Pi；
2. 自己完成 `/login`；
3. 自己用 `/model` 选择 DeepSeek 模型；
4. 自己安装 Pi package；
5. 自己安装 Matt Pocock skills；
6. 自己用 `/grill-me` 澄清需求；
7. 自己用 `/to-prd` 生成 `prd.md`；
8. 自己用一句话让 Pi commit 并 push 到 GitHub；
9. 自己安装 `@juicesharp/rpiv-pi`，运行 `/rpiv-setup`，并重启 Pi Agent session。

---

## 第 1 步：确认 Pi 可用，并完成第一次登录

在终端输入：

```bash
pi
```

如果能进入 Pi 对话界面，说明可以继续。

如果提示未登录，在 Pi 里输入：

```text
/login
```

### 中国大陆员工推荐设置

第一次登录时，推荐选择 **DeepSeek**。

原因：DeepSeek 是国内员工更常见、访问和付款路径通常更方便的模型服务，Pi 也支持 DeepSeek API Key。

操作步骤：

1. 在 `/login` 里选择 `DeepSeek`；
2. 粘贴公司提供的 DeepSeek API Key；
3. 登录成功后，在 Pi 里输入：

```text
/model
```

4. 搜索并选择：

```text
deepseek/deepseek-v4-flash
```

日常写 PRD、自我训练、普通任务，默认用：

```text
DeepSeek V4 Flash
```

如果任务明显更复杂，需要更强推理能力，再切换到：

```text
deepseek/deepseek-v4-pro
```

> 注意：不要用个人 key 处理公司资料。如果没有 key，先找负责人申请。

---

## 第 2 步：练习安装 Pi package

Pi package 可以给 Pi 增加工具、skill、prompt 或主题。

练习命令：

```bash
pi install npm:@foo/pi-tools
```

或者：

```bash
pi install git:github.com/badlogic/pi-doom
```

然后查看安装结果：

```bash
pi list
```

> 注意：这里只是学习安装方式。真实工作中安装第三方 package 前，要确认来源可信。

---

## 第 3 步：安装产品/需求常用 skills

本教程使用 Matt Pocock skills：

https://github.com/mattpocock/skills

安装：

```bash
npx skills@latest add mattpocock/skills
```

安装时，选择你使用的 agent，并确保包含：

```text
/setup-matt-pocock-skills
```

进入你的项目目录，启动 Pi：

```bash
pi
```

然后在 Pi 中运行：

```text
/setup-matt-pocock-skills
```

如果是第一次练习，可以按默认值来：

- issue tracker：GitHub 或 local markdown；
- triage labels：默认；
- domain docs：single-context。

---

## 第 4 步：用 `/grill-me` 让 Pi 追问你

进入 Pi 后输入：

```text
/grill-me

我要写第一个产品 PRD，主题是“员工请假审批系统”。
请你像产品负责人一样追问我关键问题，直到需求足够清楚。
```

你需要认真回答 Pi 的问题。

不要一开始就急着写文档。先让 Pi 帮你把需求问清楚。

---

## 第 5 步：生成 `prd.md`

当 Pi 已经问完关键问题后，输入：

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

生成后继续输入：

```text
请检查 prd.md 是否清楚、完整、可执行。
如果有明显缺口，请列出来，并帮我补充到文档里。
```

---

## 第 6 步：不要手敲 git 命令，让 Pi 自己提交

确认 `prd.md` 内容满意后，不需要自己输入任何提交相关的命令。

直接在 Pi 里说：

```text
请检查当前改动，把 prd.md commit 并 push 到 GitHub。
commit message 用：docs: add first product requirements document
```

或者：

```text
请把 prd.md 提交并 push 到 GitHub。
```

Pi 会自己完成需要的 git 操作。

---

## 第二节课：安装 RPIV 工作流

第二节课的目标是安装 RPIV，并完成一次基础设置。

### 2.1 安装 RPIV Pi package

在终端执行：

```bash
pi install npm:@juicesharp/rpiv-pi
```

安装完成后，可以查看 package 是否出现：

```bash
pi list
```

### 2.2 启动 Pi 并运行 `/rpiv-setup`

进入你的项目目录，启动 Pi：

```bash
pi
```

然后在 Pi 里输入：

```text
/rpiv-setup
```

`/rpiv-setup` 会读取：

```text
~/.pi/agent/settings.json
```

它会预览两类内容：

1. 缺失的 sibling 配置；
2. 建议清理的 legacy entries。

你只需要检查预览内容是否合理。确认无误后，按提示确认一次，Pi 会自动应用设置。

### 2.3 重启 Pi Agent session

`/rpiv-setup` 完成后，退出当前 Pi session，然后重新进入：

```bash
pi
```

重启后，新的 RPIV 配置才会完整生效。

### 2.4 第二节课完成标准

完成后，你应该能确认：

- `@juicesharp/rpiv-pi` 已安装；
- `/rpiv-setup` 已运行；
- 你看过配置预览；
- 你确认并应用过设置；
- 你已经重启 Pi Agent session。

---

## 自我检查清单

完成后检查：

- [ ] 我能打开 Pi；
- [ ] 我完成了 `/login`；
- [ ] 我会用 `/model` 切换模型；
- [ ] 我知道默认推荐使用 `deepseek/deepseek-v4-flash`；
- [ ] 我知道 `pi install npm:...` 和 `pi install git:...` 的区别；
- [ ] 我安装了 Matt Pocock skills；
- [ ] 我运行过 `/setup-matt-pocock-skills`；
- [ ] 我用 `/grill-me` 让 Pi 追问过需求；
- [ ] 我生成了 `prd.md`；
- [ ] 我让 Pi 自己 commit 并 push 到 GitHub；
- [ ] GitHub 仓库里能看到 `prd.md`；
- [ ] 我安装了 `@juicesharp/rpiv-pi`；
- [ ] 我运行了 `/rpiv-setup`；
- [ ] 我确认并应用了设置；
- [ ] 我重启了 Pi Agent session。

---

## 最终交付

把你的 GitHub 仓库链接发给负责人。

仓库里至少要有：

```text
prd.md
```

`prd.md` 应该说明：

- 为什么要做这个产品；
- 谁会使用；
- 用户怎么完成核心流程；
- 需要哪些功能；
- 暂时不做什么；
- 怎么判断完成。
