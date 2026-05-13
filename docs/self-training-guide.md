# 自我训练指南：用 Pi 完成第一个 PRD

> 这是员工自己照着做的练习手册。
>
> 目标：自己安装 Pi，安装常用 skills，用 Pi 生成 `prd.md`，再让 Pi 自己提交并 push 到 GitHub。

---

## 自我训练目标

完成后，你应该能做到：

1. 自己打开 Pi；
2. 自己安装 Pi package；
3. 自己安装 Matt Pocock skills；
4. 自己用 `/grill-me` 澄清需求；
5. 自己用 `/to-prd` 生成 `prd.md`；
6. 自己用一句话让 Pi commit 并 push 到 GitHub。

---

## 第 1 步：确认 Pi 可用

在终端输入：

```bash
pi
```

如果能进入 Pi 对话界面，说明可以继续。

如果提示未登录，在 Pi 里输入：

```text
/login
```

按提示完成登录。

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

## 自我检查清单

完成后检查：

- [ ] 我能打开 Pi；
- [ ] 我知道 `pi install npm:...` 和 `pi install git:...` 的区别；
- [ ] 我安装了 Matt Pocock skills；
- [ ] 我运行过 `/setup-matt-pocock-skills`；
- [ ] 我用 `/grill-me` 让 Pi 追问过需求；
- [ ] 我生成了 `prd.md`；
- [ ] 我让 Pi 自己 commit 并 push 到 GitHub；
- [ ] GitHub 仓库里能看到 `prd.md`。

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
