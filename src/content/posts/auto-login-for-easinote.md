---
title: 还在课前输密码？自动登录希沃，告别繁琐操作
published: 2025-03-15
description: 'Auto Login for EasiNote 是一个使用 Python 编写的 CLI 工具，可以用于自动登录希沃白板。通过 PyAutoGUI 实现自动识别并点击来模拟登录'
image: ''
tags: [编程, Python, 希沃白板, 自动化]
category: '技术'
draft: false 
---

## 来历

由于每天英语课都会被老师叫上去登希沃白板，我每天都得重复机械的登录账号，相当麻烦。这么简单的操作，应该很简单就能实现自动化？灵感就这么出来了。

~~果然偷懒是第一生产力（~~

于是我用 Python 写了一个 CLI 工具，通过 PyAutoGUI 实现自动识别并点击，从而实现自动登录希沃白板。

与 [ClassIsland](https://github.com/ClassIsland/ClassIsland/) 的 **「自动化」** 功能结合使用，体验更佳。参见 [使用 ClassIsland 自动化，全自动登录希沃白板！](/posts/easinote-login-automation/)

:::note
系统需求：Windows 10 及以上版本
:::

目前已在本人班级内的 Windows 10 希沃一体机上进行了一段时间的测试，基本没有问题。偶尔可能会因为同学或老师误触导致登录被打断，此时会进行错误重试。

::github{repo="hxabcd/auto-login-for-easinote"}

## 使用

使用已预先打包的可执行文件，直接通过命令行进行调用。

```shell
# 查看使用说明
auto_login_for_easinote.exe -h
```

### 指定账号密码

通过 `-a` 或 `--account` 参数指定账号

通过 `-p` 或 `--password` 参数指定密码

```shell
auto_login_for_easinote.exe -a ACCOUNT -p PASSWORD
```

### 显示警告

通过 `-w` 或 `--show-warning` 参数显示警告

```shell
auto_login_for_easinote.exe -a ACCOUNT -p PASSWORD -w
```

启用后，将会在自动登录前通过 Windows 的系统通知进行提示，超时时长 15 秒。

如超时或选择忽略，则继续登录；如选择取消，则结束程序。

此功能目的是避免某些不需要自动登录的特殊情况下希沃白板被强行退出，影响正常授课。

### 启用 4K 适配

通过 `--4k` 参数启用 4K 分辨率适配

```shell
auto_login_for_easinote.exe -a ACCOUNT -p PASSWORD --4k
```

### 显示日志输出

通过 `--debug` 参数显示日志输出

```shell
auto_login_for_easinote.exe -a ACCOUNT -p PASSWORD --debug
```

## 下载

0.2.0 实际上已经做完了，不过没打包（

[Release 0.1.0 · hxabcd/auto-login-for-easinote](https://github.com/hxabcd/auto-login-for-easinote/releases/tag/0.1.0)
