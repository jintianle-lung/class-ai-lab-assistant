# CLASS-AI 课堂实验助教

CLASS-AI 是一套给老师、助教和学生使用的 **课堂 AI 实验流程包**。

它的目的不是让 AI 直接代写作业，而是帮助大家把课堂内容变成：

```text
课堂材料 -> 知识点 -> 最小可运行实验 -> 逐步改进 -> 项目/代码
-> 架构图/流程图 -> 关键代码讲解 -> 学生验收讲稿
```

一句话理解：

> 老师讲完课后，AI 帮学生把“听懂的概念”变成“跑得起来的代码”，再把“跑得起来的代码”变成“讲得清楚的知识”。

## 适合谁用

- **老师**：想把 PPT、课堂讲解和实验要求变成课堂互动、实验项目和验收材料。
- **学生**：想根据老师 PPT 和作业要求完成项目，并准备讲解。
- **助教**：想快速整理实验包、讲稿、流程图和评分问题。
- **Agent 使用者**：想把这套流程放到 Trae、OpenCode、Resonix、DeepSeek、Claude、ChatGPT、Codex 等工具里使用。

## 核心思路

CLASS-AI 由两部分组成。

### 1. 课堂流程

```text
Capture  捕获课堂材料
Link     把知识点映射到代码/实验
Ask      课上调用 AI 互动
Scaffold 搭建最小实验
Show     生成图解和讲稿
Assess   验收与复盘
```

### 2. Karpathy-style 工程流程

```text
先做最小可运行版本
再一步一步加功能
每一步都能运行
图解必须对应代码
学生最后必须讲回来
```

这样可以避免 AI 一次性生成很大的项目，学生却看不懂。

## 给非技术用户的最快用法

先打开：

[pack/START_HERE_先看这个.md](pack/START_HERE_%E5%85%88%E7%9C%8B%E8%BF%99%E4%B8%AA.md)

然后把下面这段话复制给你的 AI Agent：

```text
请严格按照 CLASS-AI-Agent-Pack 里的《傻瓜式课堂实验向导.md》工作。
你不要一次性生成完整结果。
你要像问卷一样一步步问我，每次只问一个问题，给我选项。
我回答后，你再进入下一步。
现在开始。
```

Agent 应该会先问你：

```text
第 1 个问题：你现在的身份是？
A. 老师
B. 学生
C. 助教
D. 我不确定，让 AI 判断
```

## Trae 使用方法

1. 新建一个 Agent。
2. 把 [trae/system-prompt.md](trae/system-prompt.md) 的内容复制到 Agent 指令/系统提示词里。
3. 上传 `pack/` 文件夹，或者上传里面所有 `.md` 文件。
4. 上传 PPT、课堂笔记、作业要求、示例代码。
5. 对 Agent 说：

```text
开始。请按 CLASS-AI 傻瓜式课堂实验向导一步步问我。
```

## OpenCode / 免费小模型使用方法

有些免费模型不擅长读很长的提示词，所以提供了短版：

[opencode/small-model-system-prompt.md](opencode/small-model-system-prompt.md)

如果工具支持 `AGENTS.md`，使用：

[opencode/AGENTS.md](opencode/AGENTS.md)

## 仓库结构

```text
.
├── README.md                         中文主入口
├── LICENSE                           MIT 开源协议
├── docs/
│   └── CLASS-AI-framework.zh-CN.md   完整中文框架说明
├── pack/                             给老师/学生直接用的傻瓜式流程包
│   ├── START_HERE_先看这个.md
│   ├── 傻瓜式课堂实验向导.md
│   ├── 复制到Trae的系统提示词.md
│   ├── teacher-intake-form.md
│   ├── student-intake-form.md
│   └── ...
├── trae/
│   └── system-prompt.md              Trae 专用中文系统提示词
├── opencode/
│   ├── AGENTS.md
│   └── small-model-system-prompt.md  小模型/免费模型短提示词
├── examples/
│   └── windows-gdi-paint-lab.md      Windows GDI 画图实验示例
└── skills/
    └── course-ai-lab-assistant/      Codex Skill 版本
```

## 傻瓜式 8 步向导

Agent 应该严格按这 8 步走：

1. 问身份：老师、学生、助教。
2. 问课程类型和本节课主题。
3. 问上传了哪些材料。
4. 提取知识点并让用户确认。
5. 选择 AI 使用等级。
6. 设计最小可运行实验。
7. 生成 2-4 步逐步改进路线。
8. 生成图解、关键代码讲解、验收讲稿和复盘问题。

## 示例：Windows 程序设计课

如果本节课讲的是：

```text
WM_PAINT、GDI、HDC、画笔、画刷、文档-视图思想
```

那么 Agent 应该把项目拆成：

```text
V0：创建窗口，在 WM_PAINT 里画一条固定线
V1：用鼠标拖动画线
V2：把每一笔保存成 Stroke 数据
V3：WM_PAINT 从 Stroke 数据重绘，解决图形丢失
V4：增加保存、打开、导出
```

这样学生能看懂程序是怎么一步步长出来的。

## AI 使用等级

| 等级 | 含义 | 适合场景 |
|---|---|---|
| Level 0 | 不使用 AI | 闭卷测验、基础语法 |
| Level 1 | AI 只解释概念 | 新概念理解 |
| Level 2 | AI 生成流程图和伪代码 | 课上讨论 |
| Level 3 | AI 生成部分代码，学生修改 | 普通实验 |
| Level 4 | AI 生成完整项目，学生必须验证和答辩 | 综合作业 |
| Level 5 | 师生共同探索新 AI 教学方式 | 教改项目 |

## 最终希望学生能做到

学生不只是提交结果，而是能讲清楚：

```text
这节课讲了什么
代码用了哪些课堂知识点
程序是怎么运行的
AI 帮了什么
自己修改和验证了什么
如果老师追问，自己能不能解释
```

## 开源协议

MIT License。
