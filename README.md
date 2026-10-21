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

1. **vllm-gate** — **仅触发才跑**（无定时）。浅克隆 GitCode 后做编译门禁，并把日志链接回帖到 Issue  
2. **mirror-from-gitcode** — 可选镜像同步

### 怎么触发 CI

在 GitCode `OpenNoesis/vllm` 对应 Issue 评论单独一行：

```text
CI
```

（由 `opannoesis-task-bot` 轮询识别并 dispatch；开始/结束都会贴 Actions 链接）

也可在本仓 Actions → **vllm-gate** → Run workflow，填写 `issue_number` 以便回帖。
