# Pi 员工入门培训

这份文档用于员工自我训练 [Pi](https://pi.dev/)：安装 Pi、安装工具包、安装产品/PM 常用 Skills，完成第一个 `prd.md` 文件，并在第二节课安装 RPIV 工作流。

## 培训目标

完成培训后，员工应能：

1. 在本机安装并启动 Pi。
2. 完成第一次 `/login`，并为中国大陆员工优先选择 DeepSeek。
3. 学会用 `/model` 选择模型，例如 `deepseek/deepseek-v4-flash`。
4. 知道如何安装 Pi package。
5. 安装并使用 Matt Pocock 的常用 Skills。
6. 用自然语言让 Pi 生成第一个产品 PRD。
7. 用自然语言让 Pi 把文档 commit 并 push 到 GitHub。
8. 第二节课安装 `@juicesharp/rpiv-pi`，运行 `/rpiv-setup`，并重启 Pi Agent session。

## 课程正文

### 第一课：安装 Pi、设置模型、写第一个 PRD

学习内容：

- 安装并启动 Pi；
- 第一次 `/login`；
- 面向中国大陆员工选择 DeepSeek；
- 用 `/model` 选择 `deepseek/deepseek-v4-flash`；
- 安装 Matt Pocock skills；
- 用 `/grill-me` 澄清需求；
- 用 `/to-prd` 生成 `prd.md`；
- 让 Pi 自己 commit 并 push 到 GitHub。

课程文档：

- [第一课：安装 Pi、设置模型、写第一个 PRD](docs/lesson-01-first-prd.md)

### 第二课：安装 RPIV 并完成 `/rpiv-setup`

学习内容：

- 安装 `@juicesharp/rpiv-pi`；
- 运行 `/rpiv-setup`；
- 查看 missing siblings 和 legacy entries 预览；
- 确认并应用设置；
- 重启 Pi Agent session。

课程文档：

- [第二课：安装 RPIV 并完成设置](docs/lesson-02-rpiv-setup.md)
