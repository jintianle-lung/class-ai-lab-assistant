# Explanation Templates

Use these templates to generate student-facing explanation packs.

## 30-Second Summary

```text
这个项目把本节课的 [核心概念] 做成了一个可运行程序。
它的核心是 [关键机制]：用户操作先触发 [消息/事件]，
程序再通过 [关键函数] 更新数据或界面。
我重点改进/实现的是 [功能]，对应课上讲的 [知识点]。
```

## 2-Minute Technical Explanation

```text
第一步，程序从 [入口函数] 开始，创建窗口并进入消息循环。
第二步，用户操作会变成 Windows 消息，例如 [消息1]、[消息2]。
第三步，窗口过程函数 [WndProc/消息映射函数] 根据消息类型调用不同处理函数。
第四步，程序把核心数据保存在 [数据结构/文档类] 中。
第五步，显示时由 [绘图函数] 读取这些数据，并使用 [GDI/MFC API] 画到窗口。
所以这个程序不是只靠临时绘制，而是可以在刷新时恢复显示。
```

## Concept-To-Code Table

```markdown
| 课上知识点 | 对应代码 | 实现作用 | 演示方法 |
|---|---|---|---|
| [concept] | `[file:function]` | [effect] | [demo] |
```

## Architecture Diagram Prompt

```text
生成一张中文课程汇报架构图，主题是 [project]。
包含三列：
1. 课上知识点
2. 代码模块/函数
3. 程序运行效果
使用清晰箭头展示：用户操作 -> 消息处理 -> 数据更新 -> 绘图/输出。
文字要大而清楚，不要复杂背景，不要超出课程技术栈。
```

## Flowchart Prompt

```text
生成一张中文流程图，说明 [feature] 的执行过程。
节点包括：
[message/event] -> [handler] -> [data change] -> [render/output] -> [visible result]
每个节点下方写一行对应代码函数名。
```

## Teacher Q&A Template

```markdown
### Q1: 这个功能对应课上哪个知识点？
A: 对应 [concept]，代码中通过 `[function/API]` 实现。

### Q2: 为什么要这样设计？
A: 因为 [reason]。如果直接 [bad approach]，会导致 [problem]。

### Q3: AI 在这里帮了什么？
A: AI 帮助整理了 [concept/code/diagram]，但我验证了 [evidence]，并修改了 [student change]。

### Q4: 怎么证明程序能运行？
A: 我运行了 [command/demo]，结果是 [result]。
```

## Reflection Prompt

```text
请根据本次实验写一段学生复盘：
1. 我从 PPT/课堂中提取了哪些知识点？
2. AI 给出的内容有哪些是有用的？
3. AI 哪些地方需要我判断或修改？
4. 最终代码如何证明我理解了本节课？
5. 如果再做一次，我会如何改进？
```

