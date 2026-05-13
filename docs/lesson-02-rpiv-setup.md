# 第二课：安装 RPIV 并完成 `/rpiv-setup`

> 目标：安装 `@juicesharp/rpiv-pi`，运行 `/rpiv-setup`，检查设置预览，确认应用，并重启 Pi Agent session。

---

## 本课目标

完成后，你应该能做到：

1. 安装 RPIV Pi package；
2. 运行 `/rpiv-setup`；
3. 看懂它预览的 missing siblings 和 legacy entries；
4. 确认并应用设置；
5. 重启 Pi Agent session。

---

## 第 1 步：安装 RPIV Pi package

在终端执行：

```bash
pi install npm:@juicesharp/rpiv-pi
```

安装完成后，可以查看 package 是否出现：

```bash
pi list
```

看到 `@juicesharp/rpiv-pi` 后，继续下一步。

---

## 第 2 步：启动 Pi

进入你的项目目录，启动 Pi：

```bash
pi
```

---

## 第 3 步：运行 `/rpiv-setup`

在 Pi 里输入：

```text
/rpiv-setup
```

`/rpiv-setup` 会读取：

```text
~/.pi/agent/settings.json
```

然后预览两类内容：

1. 缺失的 sibling 配置；
2. 建议清理的 legacy entries。

你不需要手动改 JSON 文件。先看预览，确认它准备修改什么。

---

## 第 4 步：确认并应用设置

如果预览内容合理，按提示确认一次。

确认后，`/rpiv-setup` 会自动把需要的配置写入 `~/.pi/agent/settings.json`。

---

## 第 5 步：重启 Pi Agent session

设置应用后，退出当前 Pi session，然后重新进入：

```bash
pi
```

重启后，新的 RPIV 配置才会完整生效。

---

## 自我检查清单

- [ ] 我安装了 `@juicesharp/rpiv-pi`；
- [ ] 我运行了 `/rpiv-setup`；
- [ ] 我看过 missing siblings 预览；
- [ ] 我看过 legacy entries 预览；
- [ ] 我确认并应用了设置；
- [ ] 我重启了 Pi Agent session。
