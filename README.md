# OpenNoesis vLLM CI（GitHub ↔ GitCode）

GitCode 流水线未开通时，用 **GitHub Actions** 拉取 `OpenNoesis/vllm` 并跑门禁。

## 仓库

| 仓库 | 作用 |
|------|------|
| [hongwei-2026/opannoesis-vllm-ci](https://github.com/hongwei-2026/opannoesis-vllm-ci) | CI / 镜像同步（本仓） |
| [hongwei-2026/opannoesis-vllm](https://github.com/hongwei-2026/opannoesis-vllm) | GitCode 代码镜像（只读浏览 + 可跑上游 workflow） |

## Secrets

| Name | 说明 |
|------|------|
| `GITCODE_TOKEN` | GitCode PAT（读仓 / 可选写评论） |

## 工作流

1. **vllm-gate** — 浅克隆 GitCode `OpenNoesis/vllm`，跑 Python 编译门禁（模型目录）
2. **mirror-from-gitcode** — 浅克隆后 force-push 到 `hongwei-2026/opannoesis-vllm`

手动：Actions → 选 workflow → Run workflow（可填 `ref`，默认 `main`）。
