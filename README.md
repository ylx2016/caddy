# Caddy + NaiveProxy 自动构建

自动编译内置 [forwardproxy@naive](https://github.com/klzgrad/forwardproxy) 与 [caddy-l4](https://github.com/mholt/caddy-l4) 插件的 Caddy，定时检查上游更新并发布。

## 最新版本

- **版本**：`v2.11.7-naive-e747854`
- **构建时间**：2026-10-24 23:04 UTC

## 下载

经 UPX `--best --lzma` 压缩（体积小，启动时解压进内存）；如遇低内存设备或杀软误报，改用 `-uncompressed` 原始档。

| 架构 | 压缩版 | 原始版 |
| --- | --- | --- |
| linux/amd64 | [caddy-linux-amd64](https://github.com/ylx2016/caddy/releases/latest/download/caddy-linux-amd64) | [caddy-linux-amd64-uncompressed](https://github.com/ylx2016/caddy/releases/latest/download/caddy-linux-amd64-uncompressed) |
| linux/arm64 | [caddy-linux-arm64](https://github.com/ylx2016/caddy/releases/latest/download/caddy-linux-arm64) | [caddy-linux-arm64-uncompressed](https://github.com/ylx2016/caddy/releases/latest/download/caddy-linux-arm64-uncompressed) |

[查看全部 Release](https://github.com/ylx2016/caddy/releases)

## 包含插件

- `github.com/klzgrad/forwardproxy@naive`（naive 分支，替换 `caddyserver/forwardproxy@caddy2`）
- `github.com/mholt/caddy-l4`

## 说明

- 定时任务每周日 02:00 UTC 运行，仅当 naive 分支有新提交时才编译；手动触发则强制重编。
- Caddy 源码版本取自 naive 仓库的 `CADDY_VERSION`（naive 的补丁是按该版本写的），
  不是 `caddyserver/caddy` 的最新 release —— 上游发新 release 后要等 naive 跟进才会切过去。
- 编译前会把 naive 的两个补丁打进 Caddy 源码：`caddy-read-idle-timeout.patch`
  （backport `IdleTimeoutsFromContext` 等 API，naive 的 `forwardproxy.go` 依赖它）
  与 `caddy-sing-quic-bbrv1.patch`（换用 sagernet 的 quic-go 以启用 BBRv1）。
- 每个构建产物在发布前都做过自检：amd64 实际运行 `caddy version` 与 `list-modules`，
  arm64 因 runner 架构跑不了，改用 ELF 头 + 内嵌符号做静态校验。
- 每次构建都会更新本 README（版本号与构建时间），以此产生提交、保持仓库活跃，避免 GitHub 因「60 天无活动」自动停用定时任务。
- 仅保留最新 3 个 Release。

<!-- 本文件由 GitHub Actions 自动生成，请勿手动编辑 -->
