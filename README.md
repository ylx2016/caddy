# Caddy + NaiveProxy 自动构建

自动编译内置 [forwardproxy@naive](https://github.com/klzgrad/forwardproxy) 与 [caddy-l4](https://github.com/mholt/caddy-l4) 插件的 Caddy，定时检查上游更新并发布。

## 最新版本

- **版本**：`v2.11.4-naive-d62c80d`
- **构建时间**：2026-08-24 10:16 UTC

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

- 定时任务每周日 02:00 UTC 运行，仅当 Caddy 有新版本或 naive 分支有新提交时才编译；手动触发则强制重编。
- 每个构建产物在发布前都做过自检（`caddy version` + 确认 forward_proxy / layer4 模块已编入）。
- 每次构建都会更新本 README（版本号与构建时间），以此产生提交、保持仓库活跃，避免 GitHub 因「60 天无活动」自动停用定时任务。
- 仅保留最新 3 个 Release。

<!-- 本文件由 GitHub Actions 自动生成，请勿手动编辑 -->
