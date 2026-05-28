---
name: course-ai-lab-assistant
description: Use when a teacher or student wants to turn classroom materials such as PPT slides, lecture notes, teacher explanations, code demos, or lab requirements into an AI-assisted programming lesson, in-class AI activity, course experiment, runnable project, code walkthrough, architecture diagram, flowchart, README, or student presentation script. Especially suited for Windows/C++/MFC/Win32/GDI programming courses where AI should be used during class and after class without replacing teacher judgment or student understanding.
---

# Course AI Lab Assistant

This skill turns a programming lecture into a teachable AI-assisted lab cycle:

```text
classroom input -> knowledge map -> AI-in-class activity -> scoped implementation
-> runnable project -> visual explanation -> student oral defense
```

The goal is not "AI writes the assignment." The goal is: teacher-led AI use that helps students connect lecture concepts to runnable code and then explain the code back clearly.

## Karpathy-Style Teaching Bias

Use this bias whenever the user asks for a classroom framework, coding lab, or AI-assisted implementation.

1. **Start with a tiny working baseline.**
   - Prefer a minimal runnable program before adding features.
   - Avoid architecture diagrams that do not correspond to executed code.

2. **Build from first principles before abstraction.**
   - Show the core loop directly: input -> state -> computation -> output.
   - Add helper classes only when they clarify a real repeated idea.

3. **Keep the full stack visible.**
   - Students should see how the lecture concept becomes data structures, event handlers, rendering, files, and verification.
   - Do not hide the most important mechanism behind a framework unless the course already taught it.

4. **Use AI as an amplifier, not an oracle.**
   - Ask AI to propose, simplify, visualize, and generate tests.
   - Require humans to run, inspect, compare, and explain.

5. **Every artifact must support a demo or explanation.**
   - Code must run.
   - Diagrams must point to actual functions.
   - README steps must be executable.
   - The student must be able to reproduce the main behavior live.

Read `references/karpathy-style.md` when designing or improving the teaching framework itself.

## Core Framework: CLASS-AI

Use this six-stage framework.

1. **Capture**
   - Gather PPTs, teacher speech notes, board writing, sample code, assignment requirements, and student questions.
   - Preserve the teacher's constraints: allowed APIs, forbidden advanced frameworks, expected IDE/compiler, grading focus.

2. **Link**
   - Extract lecture concepts and map each concept to possible code behavior.
   - Output a table: `concept -> code construct -> visible behavior -> evidence/demo`.

3. **Ask in Class**
   - Design short teacher-controlled AI prompts for live classroom use.
   - Students should inspect, critique, and improve AI output instead of accepting it blindly.

4. **Scaffold**
   - Build the smallest useful runnable project that demonstrates the lecture concepts.
   - First produce a "baseline pass" that proves the core mechanism works; only then add polish.
   - Keep the implementation within the course boundary. Do not introduce frameworks that the teacher has not taught unless explicitly approved.

5. **Show**
   - Generate teaching artifacts: architecture diagram, event/data flow, key-code walkthrough, README, demo checklist, and likely teacher Q&A.
   - Every visual must include code anchors such as filenames, function names, or message/API names.

6. **Assess**
   - Decide the permitted AI-use level and require a student explanation artifact.
   - The student must be able to explain what AI produced, what they changed, how it maps to class content, and how it was verified.

## Research-Informed Principles

Apply these principles from established AI-in-education guidance:

- Human-centered and teacher-led: AI supports teacher judgment, not replacement.
- AI literacy: include how AI works, when it fails, how to evaluate outputs, and responsible use.
- Pedagogical fit: AI use must serve the learning objective, not just save time.
- Student agency: require critique, modification, and explanation so students do not cognitively offload the task.
- Transparent assessment: state the allowed AI-use level before students start.
- Evidence over claims: runnable code, screenshots, diagrams, tests, or oral explanation must support the final submission.

For source details, read `references/research-brief.md` when the user asks for literature, rationale, or school-facing policy language.

## AI-Use Levels For Assignments

Use this course-friendly scale adapted from AI Assessment Scale ideas:

```text
Level 0 - No AI: closed-book concept or syntax practice.
Level 1 - AI explains: AI may explain concepts, but no code generation.
Level 2 - AI plans: AI may create flowcharts, pseudocode, and checklists.
Level 3 - AI collaborates: AI may generate partial code; student edits and explains.
Level 4 - AI builds with student defense: AI may generate a runnable project; student must modify, verify, and orally defend.
Level 5 - AI exploration: teacher and students co-design a new AI-supported workflow or tool.
```

For programming labs, prefer Level 2 or 3 during early learning and Level 4 only when the deliverable includes strong explanation and modification evidence.

## Standard Workflow

When triggered, follow this workflow unless the user asks for a narrower output.

### 1. Intake

Collect or infer:

- Course topic and week/chapter.
- PPTs, lecture notes, screenshots, code demos, assignment prompt.
- Course boundary: allowed language, IDE, frameworks, libraries, and complexity.
- Output target: classroom activity, lab project, student handout, code implementation, or teacher guide.
- AI-use level.

If any input is missing, make a conservative assumption and label it.

### 2. Lecture Extraction

Create:

```text
Core concepts:
- concept
- short explanation
- class source: PPT slide / teacher note / demo code
- implementation affordance

Do-not-cross boundary:
- advanced topic to avoid
- reason
```

### 3. Concept-To-Code Map

Create a table:

```text
Lecture concept | Code/API | Program behavior | Demo evidence | Explanation line
```

For Windows programming, typical mappings include:

- `WinMain` -> program entry, window class registration, message loop.
- `WndProc` -> centralized message dispatch.
- `WM_COMMAND` -> menu/button command handling.
- `WM_PAINT` -> reliable redraw.
- `HDC` -> device context for drawing.
- `HPEN/HBRUSH` or `CPen/CBrush` -> line/fill style.
- document-view idea -> data model separated from rendering.
- serialization -> save/load editable data.

Read `references/windows-programming-template.md` for Windows/C++ course-specific patterns.

### 4. In-Class AI Activity

Generate 2-4 teacher prompts:

- Prompt A: explain the concept.
- Prompt B: produce minimal code or pseudocode.
- Prompt C: ask students to find errors or missing pieces.
- Prompt D: improve the output under course constraints.

Each prompt should include:

```text
teacher says:
expected AI output:
student task:
teacher correction points:
time box:
```

Keep live AI tasks short enough for class discussion.

### 5. Implementation Plan

For a coding lab, produce a scoped implementation:

- Baseline behavior: the smallest version that can run and prove the concept.
- Iteration steps: one improvement per step.
- Minimal feature list.
- Files to create/modify.
- Data model.
- Event/data flow.
- Verification method.
- What the student must modify manually.
- What the student must explain.

### 6. Build

When asked to implement:

- Inspect existing code first.
- Prefer the course toolchain and APIs.
- Add concise comments on lecture-linked code.
- Keep implementation inspectable; avoid clever abstractions that students cannot trace.
- Write a README with build/run/demo instructions.
- Verify using available compiler/tests.

### 7. Explanation Pack

Always produce the explanation pack for student defense:

- "One-screen mental model": the shortest accurate explanation of the program.
- 30-second summary.
- 2-minute technical explanation.
- Architecture diagram description.
- Event/data flow.
- Key code walkthrough.
- "What was improved from the reference/demo?"
- "What did AI help with, and what did the student verify/change?"
- Likely teacher questions and answers.

Use `references/explanation-templates.md` for reusable output templates.

## Classroom Guardrails

Never let the AI interaction hide the learning target.

Require at least one of:

- student runs the baseline before adding improvements,
- student edits generated code,
- student traces execution flow,
- student labels code with lecture concepts,
- student compares AI output with teacher demo,
- student explains one bug, limitation, or tradeoff,
- student verifies the program empirically.

Avoid:

- introducing unapproved frameworks,
- using code the student cannot explain,
- treating AI output as authoritative,
- submitting only generated artifacts without a human explanation trail,
- replacing foundational practice with automation before students understand the concept.

## Output Modes

Use the mode that matches the request:

- **Teacher Live Mode**: prompts, expected AI responses, discussion questions.
- **Lab Build Mode**: project plan, code implementation, README, verification.
- **Explain Back Mode**: diagrams, code walkthrough, oral defense script.
- **Policy Mode**: AI-use levels, allowed/prohibited uses, grading evidence.
- **Retrospective Mode**: what worked, what students misunderstood, next lesson adjustments.

If the user asks for a complete framework or repeatable workflow, produce all five modes as a package.

## Default Deliverables For A Programming Lesson

For a complete lesson package, produce these in order:

1. **Concept map**: lecture concept -> code/API -> observable behavior.
2. **Tiny baseline**: the smallest runnable version.
3. **Improvement ladder**: 2-4 incremental changes, each justified by a class concept.
4. **Final project**: runnable, commented, verified.
5. **Visual explanation**: architecture + event/data flow with function anchors.
6. **Defense script**: student explanation and teacher Q&A.
7. **Reflection**: what AI generated, what student changed, what evidence proves it works.
