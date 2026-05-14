# OpenClaude

OpenClaude 是一个面向云端和本地模型提供商的开源编程智能体 CLI 工具。

支持 OpenAI 兼容 API、Gemini、GitHub Models、Codex OAuth、Codex、Ollama、Atomic Chat 及其他后端，同时保持统一的终端工作流：提示词、工具、智能体、MCP、斜杠命令和流式输出。

[![PR Checks](https://github.com/Gitlawb/openclaude/actions/workflows/pr-checks.yml/badge.svg?branch=main)](https://github.com/Gitlawb/openclaude/actions/workflows/pr-checks.yml)
[![Release](https://img.shields.io/github/v/tag/Gitlawb/openclaude?label=release&color=0ea5e9)](https://github.com/Gitlawb/openclaude/tags)
[![Discussions](https://img.shields.io/badge/discussions-open-7c3aed)](https://github.com/Gitlawb/openclaude/discussions)
[![Security Policy](https://img.shields.io/badge/security-policy-0f766e)](https://github.com/Gitlawb/openclaude/blob/main/SECURITY.md)
[![License](https://img.shields.io/badge/license-MIT-2563eb)](https://github.com/Gitlawb/openclaude/blob/main/LICENSE)

OpenClaude 同步镜像到 GitLawb：
[gitlawb.com/node/repos/z6MkqDnb/openclaude](https://gitlawb.com/node/repos/z6MkqDnb/openclaude)

[快速开始](#快速开始) | [安装指南](#安装指南) | [提供商](#支持的提供商) | [源码构建](#源码构建与本地开发) | [VS Code 扩展](#vs-code-扩展) | [赞助商](#赞助商) | [社区](#社区)

## 赞助商

<p align="center">
  <a href="https://gitlawb.com">
    <img src="https://gitlawb.com/logo.png" alt="GitLawb logo" width="96">
  </a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://bankr.bot">
    <img src="https://bankr.bot/favicon.svg" alt="Bankr.bot logo" width="96">
  </a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://atomic.chat/">
    <img src="https://github.com/Gitlawb/openclaude/raw/main/docs/assets/atomic-chat-logo.png" alt="Atomic Chat logo" width="96">
  </a>
</p>

<p align="center">
  <a href="https://gitlawb.com"><strong>GitLawb</strong></a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://bankr.bot"><strong>Bankr.bot</strong></a>
  &nbsp;&nbsp;&nbsp;&nbsp;
  <a href="https://atomic.chat/"><strong>Atomic Chat</strong></a>
</p>

## Star 历史

[![Star History Chart](https://api.star-history.com/chart?repos=gitlawb/openclaude&type=date&legend=top-left)](https://www.star-history.com/?repos=gitlawb%2Fopenclaude&type=date&legend=top-left)

## 为什么选择 OpenClaude

- 使用一个 CLI 跨越云端 API 和本地模型后端
- 通过 `/provider` 在应用内保存提供商配置
- 支持 OpenAI 兼容服务、Gemini、GitHub Models、Codex OAuth、Codex、Ollama、Atomic Chat 及其他提供商
- 将编程智能体工作流集中一处：bash、文件工具、grep、glob、智能体、任务、MCP 和 Web 工具
- 使用内置的 VS Code 扩展实现启动集成和主题支持

## 快速开始

### 安装

```bash
npm install -g @gitlawb/openclaude
```

如果安装后提示 `ripgrep not found`，请先全局安装 ripgrep 并在启动 OpenClaude 前确认同一终端中 `rg --version` 可用。

### 启动

```bash
openclaude
```

在 OpenClaude 内部：

- 运行 `/provider` 进行引导式提供商设置和保存配置
- 运行 `/onboard-github` 进行 GitHub Models 入门引导

### 最快的 OpenAI 设置

macOS / Linux：

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_API_KEY=sk-your-key-here
export OPENAI_MODEL=gpt-4o

openclaude
```

Windows PowerShell：

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_API_KEY="sk-your-key-here"
$env:OPENAI_MODEL="gpt-4o"

openclaude
```

### 最快的本地 Ollama 设置

macOS / Linux：

```bash
export CLAUDE_CODE_USE_OPENAI=1
export OPENAI_BASE_URL=http://localhost:11434/v1
export OPENAI_MODEL=qwen2.5-coder:7b

openclaude
```

Windows PowerShell：

```powershell
$env:CLAUDE_CODE_USE_OPENAI="1"
$env:OPENAI_BASE_URL="http://localhost:11434/v1"
$env:OPENAI_MODEL="qwen2.5-coder:7b"

openclaude
```

## 安装指南

入门指南：

- [非技术用户安装指南](https://github.com/Gitlawb/openclaude/blob/main/docs/non-technical-setup.md)
- [Windows 快速开始](https://github.com/Gitlawb/openclaude/blob/main/docs/quick-start-windows.md)
- [macOS / Linux 快速开始](https://github.com/Gitlawb/openclaude/blob/main/docs/quick-start-mac-linux.md)

高级和源码构建指南：

- [高级安装指南](https://github.com/Gitlawb/openclaude/blob/main/docs/advanced-setup.md)
- [Android 安装](https://github.com/Gitlawb/openclaude/blob/main/ANDROID_INSTALL.md)

## 支持的提供商

| 提供商 | 设置方式 | 备注 |
| --- | --- | --- |
| OpenAI 兼容 | `/provider` 或环境变量 | 支持 OpenAI、OpenRouter、DeepSeek、Groq、Mistral、LM Studio 及其他兼容 `/v1` 的服务器 |
| Hicap | `/provider` 或 OpenAI 兼容环境变量 | 使用 `api-key` 认证，从无需认证的 `/models` 发现模型，`gpt-` 模型支持 Responses 模式 |
| Gemini | `/provider` 或环境变量 | 仅支持 API key |
| GitHub Models | `/onboard-github` | 交互式引导并保存凭据 |
| Codex OAuth | `/provider` | 在浏览器中打开 ChatGPT 登录并安全存储 Codex 凭据 |
| Codex | `/provider` | 使用现有 Codex CLI 认证、OpenClaude 安全存储或环境变量凭据 |
| 小米 MiMo | `/provider` 或环境变量 | OpenAI 兼容 API，地址 `https://api.xiaomimimo.com/v1`；使用 `MIMO_API_KEY`，默认模型 `mimo-v2.5-pro` |
| Ollama | `/provider` 或环境变量 | 本地推理，无需 API key |
| Atomic Chat | `/provider`、环境变量或 `bun run dev:atomic-chat` | 本地模型提供商；自动检测已加载的模型 |
| Bedrock / Vertex / Foundry | 环境变量 | 支持环境下的额外提供商集成 |

## 功能特性

- **工具驱动的编程工作流**：Bash、文件读写编辑、grep、glob、智能体、任务、MCP 和斜杠命令
- **流式响应**：实时 token 输出和工具进度
- **工具调用**：多步骤工具循环，包含模型调用、工具执行和后续响应
- **图片输入**：支持视觉功能的提供商可使用 URL 和 base64 图片输入
- **提供商配置**：引导式设置及保存用户级提供商配置
- **本地和远程模型后端**：云端 API、本地服务器和 Apple Silicon 本地推理

## 提供商说明

OpenClaude 支持多个提供商，但各提供商的行为并不完全一致。

- Anthropic 特有功能可能在其他提供商上不可用
- 工具质量在很大程度上取决于所选模型
- 较小的本地模型可能难以处理长流程的多步骤工具调用
- 部分提供商的输出上限低于 CLI 默认值，OpenClaude 会在可能的情况下自动适配
- 小米 MiMo 在 OpenAI 兼容路由上使用 `api-key` 头认证，目前不支持在 OpenClaude 中报告 `/usage`

为获得最佳效果，请使用具有强大工具/函数调用支持的模型。

## 智能体路由

OpenClaude 可以通过基于设置的路由将不同的智能体分配到不同的模型。这对成本优化或按模型特长分配工作非常有用。

在 `~/.openclaude.json` 中添加：

```json
{
  "agentModels": {
    "deepseek-v4-flash": {
      "base_url": "https://api.deepseek.com/v1",
      "api_key": "sk-your-key"
    },
    "gpt-4o": {
      "base_url": "https://api.openai.com/v1",
      "api_key": "sk-your-key"
    }
  },
  "agentRouting": {
    "Explore": "deepseek-v4-flash",
    "Plan": "gpt-4o",
    "general-purpose": "gpt-4o",
    "frontend-dev": "deepseek-v4-flash",
    "default": "gpt-4o"
  }
}
```

当没有找到路由匹配时，全局提供商将作为回退。

> **注意：** `settings.json` 中的 `api_key` 值以明文存储。请保持此文件私有，不要将其提交到版本控制。

## 网页搜索与抓取

默认情况下，`WebSearch` 对非 Anthropic 模型使用 DuckDuckGo。这使 GPT-4o、DeepSeek、Gemini、Ollama 及其他 OpenAI 兼容提供商开箱即用即可使用免费的网页搜索。

> **注意：** DuckDuckGo 回退方式通过抓取搜索结果实现，可能会受到速率限制、被封锁，或受 DuckDuckGo 服务条款约束。如需更可靠的选项，请配置 Firecrawl。

对于 Anthropic 原生后端和 Codex 响应，OpenClaude 保持原生提供商的网页搜索行为。

`WebFetch` 可用，但其基于 HTTP 和 HTML 转 Markdown 的方式在 JavaScript 渲染的网站或阻止普通 HTTP 请求的网站上可能仍然失败。

设置 [Firecrawl](https://firecrawl.dev) API key 可启用 Firecrawl 驱动的搜索/抓取功能：

```bash
export FIRECRAWL_API_KEY=your-key-here
```

启用 Firecrawl 后：

- `WebSearch` 可使用 Firecrawl 的搜索 API，DuckDuckGo 仍是非 Claude 模型的默认免费路径
- `WebFetch` 使用 Firecrawl 的抓取端点替代原始 HTTP，可正确处理 JS 渲染的页面

[firecrawl.dev](https://firecrawl.dev) 免费版包含 500 积分。此 key 为可选项。

---

## 无头 gRPC 服务器

OpenClaude 可以作为无头 gRPC 服务运行，允许您将其智能体能力（工具、bash、文件编辑）集成到其他应用、CI/CD 流水线或自定义用户界面中。服务器使用双向流式传输实时文本块、工具调用，并为敏感命令请求权限。

### 1. 启动 gRPC 服务器

在 `localhost:50051` 上启动核心引擎作为 gRPC 服务：

```bash
npm run dev:grpc
```

#### 配置

| 变量 | 默认值 | 说明 |
|-----------|-------------|------------------------------------------------|
| `GRPC_PORT` | `50051` | gRPC 服务器监听端口 |
| `GRPC_HOST` | `localhost` | 绑定地址。使用 `0.0.0.0` 可暴露到所有接口（不建议在无认证情况下使用） |

### 2. 运行测试 CLI 客户端

我们提供了一个轻量级 CLI 客户端，完全通过 gRPC 通信。其行为与主交互式 CLI 一致，支持颜色渲染、token 流式输出，并通过 gRPC 的 `action_required` 事件提示您进行工具权限确认（y/n）。

在另一个终端中运行：

```bash
npm run dev:grpc:cli
```

*注意：gRPC 定义位于 `src/proto/openclaude.proto`。您可以使用此文件生成 Python、Go、Rust 或其他语言的客户端。*

---

## 源码构建与本地开发

```bash
bun install
bun run build
node dist/cli.mjs
```

常用命令：

- `bun run dev`
- `bun test`
- `bun run test:coverage`
- `bun run security:pr-scan -- --base origin/main`
- `bun run smoke`
- `bun run doctor:runtime`
- `bun run verify:privacy`
- 针对性运行 `bun test ...` 仅测试您修改的区域

## 测试与覆盖率

OpenClaude 使用 Bun 内置的测试运行器进行单元测试。

运行完整单元测试套件：

```bash
bun test
```

生成单元测试覆盖率：

```bash
bun run test:coverage
```

打开可视化覆盖率报告：

```bash
open coverage/index.html
```

如果已有 `coverage/lcov.info` 且只想重新构建 UI：

```bash
bun run test:coverage:ui
```

仅修改一个区域时使用针对性测试：

- `bun run test:provider`
- `bun run test:provider-recommendation`
- `bun test path/to/file.test.ts`

建议贡献者在提交 PR 前进行以下验证：

- `bun run build`
- `bun run smoke`
- `bun run test:coverage` 当您的更改影响共享运行时或提供商逻辑时，获取更广泛的单元覆盖率
- 针对性运行 `bun test ...` 测试您修改的文件和流程

覆盖率输出写入 `coverage/lcov.info`，OpenClaude 还会在 `coverage/index.html` 生成类似 Git 活动的热力图。

## 仓库结构

- `src/` - 核心 CLI/运行时
- `scripts/` - 构建、验证和维护脚本
- `docs/` - 安装、贡献者和项目文档
- `python/` - 独立 Python 辅助工具及其测试
- `vscode-extension/openclaude-vscode/` - VS Code 扩展
- `.github/` - 仓库自动化、模板和 CI 配置
- `bin/` - CLI 启动器入口

## VS Code 扩展

仓库中包含一个 VS Code 扩展 [`vscode-extension/openclaude-vscode`](https://github.com/Gitlawb/openclaude/blob/main/vscode-extension/openclaude-vscode)，用于 OpenClaude 启动集成、提供商感知的控制中心 UI 和主题支持。

## 安全

如果您认为发现了安全问题，请参阅 [SECURITY.md](https://github.com/Gitlawb/openclaude/blob/main/SECURITY.md)。

## 社区

- 使用 [GitHub Discussions](https://github.com/Gitlawb/openclaude/discussions) 进行问答、讨论和社区交流
- 使用 [GitHub Issues](https://github.com/Gitlawb/openclaude/issues) 报告已确认的 bug 和可执行的功能需求

## 贡献

欢迎贡献。

对于较大的更改，请先开一个 issue 以明确范围后再实施。有用的验证命令包括：

- `bun run build`
- `bun run test:coverage`
- `bun run smoke`
- 针对性运行 `bun test ...` 测试您修改的文件和流程


## 免责声明

OpenClaude 是一个独立的社区项目，与 Anthropic 无关联、未获其认可或赞助。

OpenClaude 源自 Claude Code 代码库，此后经过大量修改以支持多提供商和开放使用。"Claude" 和 "Claude Code" 是 Anthropic PBC 的商标。详见 [LICENSE](https://github.com/Gitlawb/openclaude/blob/main/LICENSE)。

## 许可证

详见 [LICENSE](https://github.com/Gitlawb/openclaude/blob/main/LICENSE)。
