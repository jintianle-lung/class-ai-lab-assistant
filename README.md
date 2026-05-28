# CLASS-AI Lab Assistant

CLASS-AI Lab Assistant is an open classroom workflow for turning course materials into teachable AI-assisted programming labs.

It is designed for teachers, teaching assistants, and beginners who want an AI agent to guide them step by step:

```text
lecture materials -> knowledge points -> tiny runnable baseline -> improvement ladder
-> project/code -> diagrams -> walkthrough -> student defense script
```

The goal is not to let AI replace learning. The goal is to make the learning process visible, runnable, and explainable.

## Who It Is For

- Teachers who want to use AI during class without losing control of the lesson.
- Students who want help turning PPTs and lecture notes into runnable projects they can explain.
- Teaching assistants who need repeatable lab templates.
- Agent builders using Trae, OpenCode, Resonix, DeepSeek, Claude, ChatGPT, Codex, or similar tools.

## Core Idea

CLASS-AI combines two ideas:

1. **Classroom AI loop**
   - Capture lecture materials.
   - Link concepts to code or tasks.
   - Ask AI during class.
   - Scaffold a lab.
   - Show diagrams and explanations.
   - Assess student understanding.

2. **Karpathy-style engineering loop**
   - Start with the smallest runnable baseline.
   - Add one improvement at a time.
   - Keep every step runnable.
   - Make diagrams point to actual code.
   - Require the student to explain the result back.

## Quick Start For Non-Technical Users

Open:

[pack/START_HERE_先看这个.md](pack/START_HERE_%E5%85%88%E7%9C%8B%E8%BF%99%E4%B8%AA.md)

Then copy this into your AI agent:

```text
请严格按照 CLASS-AI-Agent-Pack 里的《傻瓜式课堂实验向导.md》工作。
你不要一次性生成完整结果。
你要像问卷一样一步步问我，每次只问一个问题，给我选项。
我回答后，你再进入下一步。
现在开始。
```

## Quick Start For Trae

1. Create a new Agent.
2. Copy the content of [trae/system-prompt.md](trae/system-prompt.md) into the Agent instruction/system prompt.
3. Upload the `pack/` folder or the files inside it as knowledge.
4. Upload your PPT, lecture notes, assignment prompt, and sample code.
5. Say:

```text
开始。请按 CLASS-AI 傻瓜式课堂实验向导一步步问我。
```

## Quick Start For OpenCode / Small Free Models

Some free models follow long prompts poorly. Use the compact version:

[opencode/small-model-system-prompt.md](opencode/small-model-system-prompt.md)

If your agent supports `AGENTS.md`, use:

[opencode/AGENTS.md](opencode/AGENTS.md)

## Repository Structure

```text
.
├── README.md
├── LICENSE
├── docs/
│   └── CLASS-AI-framework.zh-CN.md
├── pack/
│   ├── START_HERE_先看这个.md
│   ├── 傻瓜式课堂实验向导.md
│   ├── agent-instruction.md
│   ├── teacher-intake-form.md
│   ├── student-intake-form.md
│   ├── output-template.md
│   ├── ai-use-levels.md
│   ├── windows-programming-template.md
│   └── example-paint-project.md
├── trae/
│   └── system-prompt.md
├── opencode/
│   ├── AGENTS.md
│   └── small-model-system-prompt.md
├── examples/
│   └── windows-gdi-paint-lab.md
└── skills/
    └── course-ai-lab-assistant/
```

## The 8-Step Wizard

For beginner-facing use, agents should follow this strict sequence:

1. Ask identity: teacher, student, or TA.
2. Ask course type and topic.
3. Ask what materials were uploaded.
4. Extract and confirm knowledge points.
5. Pick an AI-use level.
6. Design the smallest runnable baseline.
7. Create a 2-4 step improvement ladder.
8. Generate diagrams, walkthrough, defense script, and reflection questions.

## Example Use Case

For a Windows programming class:

```text
Lecture: WM_PAINT, GDI, HDC, pen, brush, document-view idea.
Task: create a drawing program based on a reference project.
Baseline: open a window and draw one hard-coded line in WM_PAINT.
Iteration 1: draw with mouse drag.
Iteration 2: store strokes in a document list.
Iteration 3: redraw from document data in WM_PAINT.
Iteration 4: save/load and export.
```

## License

MIT License.

