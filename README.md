# Lab Report Typst Generator

> AI-powered workflow for generating structured lab reports in Typst format.

## 项目简介

这是一个面向**电路与电子技术实验报告**的 AI 生成工作流（SOP）。给定实验素材（PDF/PPT/数据/图片），AI 按严格的串行管道生成符合浙江大学《电路与电子技术实验》模板规范的 Typst 代码。

## 准备工作 (Prerequisites)

在开始使用本工作流之前，请确保您的本地环境已准备就绪：

1. **准备 Typst 模板**：
   - 本项目依赖特定的浙大实验报告 Typst 模板。
   - 请先前往 [ZJU-simpleLabReport-Typst](https://github.com/CrossStar/ZJU-simpleLabReport-Typst) 下载模板文件并解压到您的本地电脑。
   - 记住该模板文件夹在您本地的**绝对路径**（例如 `D:\ZJU-simpleLabReport-Typst`），AI 会在启动时向您索要。
2. **安装 Typst 编译器**：
   - AI 仅负责生成 `.typ` 源代码，您需要在本地将其编译为 PDF。
   - 建议安装 [Typst CLI](https://github.com/typst/typst) 或使用 VS Code 插件 `Typst LSP` / `Typst Preview`。
3. **安装 AI 客户端**：
   - 推荐使用支持长上下文和本地文件读取的 AI 助手（如 [Claude Code](https://docs.anthropic.com/zh-CN/docs/agents-and-tools/claude-code/overview)）。

## 工作流程

```
素材接收 → 图片公式解析 → 内容填充 → 绘图拦截 → 最终输出
```

| 阶段 | 描述 |
|------|------|
| **素材接收** | 等待用户提供模板绝对路径、成品 PDF + PPT、原始数据、图片命名公式 + 实验图片 |
| **图片公式解析** | 解析命名公式逻辑，确认分组规则 |
| **内容填充** | 按七个章节顺序填充内容，图片按公式分组排版 |
| **绘图拦截** | 遇绘图需求立即暂停，等待用户确认 |
| **最终输出** | 验证全部检查项后，一次性输出完整 .typ 代码 |

## 核心规则

### 表头字段

| 字段 | 值 |
|------|------|
| 专业 |  |
| 姓名 |  |
| 学号 |  |
| 地点 |  |
| 日期 | 自动读取当前日期 |

**强制留空**：课程名称、指导老师、成绩、实验名称、实验类型、同族学生姓名

### 正文章节（严禁合并/调序）

1. 实验目的和要求
2. 实验内容和原理
3. 主要仪器设备
4. 操作方法和实验步骤
5. 实验数据记录和处理
6. 实验结果与分析
7. 思考与讨论

## AI 使用方法

### 使用 Claude Code

```bash
# 克隆项目
git clone https://github.com/YOUR_USERNAME/lab-report-typst-sop.git
cd lab-report-typst-sop

# 启动 Claude Code
claude

# 在 Claude Code 中读取 SKILL.md 开始工作流
```

### 启动确认语

将以下内容发送给 AI：

> 我已准备就绪。请按顺序发送：
> 1. 模板绝对路径
> 2. 成品 PDF 与 PPT
> 3. 原始数据
> 4. 图片命名公式与实验图片
>
> 我将严格遵守各项参数与留空原则，对图片进行结构化分层展示，遇到绘图需求会第一时间向您确认，为您输出高水准的 Typst 代码。

## 项目结构

```
lab-report-typst-sop/
├── README.md           # 本文件
├── SKILL.md            # AI Agent 工作流定义（核心）
├── CLAUDE.md           # Claude Code 入口
├── AGENTS.md           # 通用 AI Agent 说明
└── reference/          # 参考资料
    └── template_info.md # Typst 模板结构说明
```

## 技术栈

- **排版语言**: Typst
- **AI 工作流**: Skill-based Agent Pipeline
- **数据可视化**: Python (matplotlib / numpy / pandas)

## 许可

MIT License
