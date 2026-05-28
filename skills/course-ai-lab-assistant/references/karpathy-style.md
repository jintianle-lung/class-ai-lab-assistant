# Karpathy-Style Adaptation For AI-Assisted Programming Classes

Use this reference when improving the framework, designing a course lab, or deciding whether a proposed activity has become too abstract.

## What To Borrow

Karpathy's public teaching and code examples are useful because they repeatedly do these things:

1. **From-scratch reconstruction**
   - Build a working thing from basic components.
   - Make the learner see the core loop instead of only consuming a finished framework.

2. **Tiny but complete systems**
   - A small autograd engine, a compact GPT training script, or a minimal neural-network tutorial can be small enough to inspect but complete enough to run.
   - For a Windows programming class, the equivalent is a small runnable program that includes input, state, rendering/output, and verification.

3. **Code-first explanation**
   - Diagrams and words serve the code, not the other way around.
   - If a diagram cannot point to a function or data structure, simplify it.

4. **Iterative growing**
   - Start with the simplest baseline.
   - Add one meaningful capability at a time.
   - Keep each step runnable.

5. **Empirical verification**
   - Run the program.
   - Look at the output.
   - Use failures and surprising behavior as teaching moments.

6. **AI-native but human accountable**
   - AI can help generate and explain, but the learner must still inspect, run, modify, and defend.

## Adapted Lab Pattern

Use this pattern instead of jumping straight to a full project:

```text
Baseline 0: one window / one concept / one visible behavior
Baseline 1: add user interaction
Baseline 2: add state/data model
Baseline 3: add persistence or polish
Final: explain the whole loop and verify it live
```

For example, in a Win32/GDI drawing lab:

```text
0. Open a window and handle WM_PAINT.
1. Draw one hard-coded line with HDC and HPEN.
2. Draw from mouse input.
3. Store strokes in a document list.
4. Redraw from stored strokes in WM_PAINT.
5. Add save/export only after redraw is correct.
```

## Karpathy-Style Checklist

Before accepting an AI-generated lesson or project, check:

- Can the student run a minimal version within 1-2 minutes?
- Can the student trace the main loop without opening more than 2-3 files?
- Is each diagram tied to function names or data structures?
- Is there a visible before/after improvement?
- Did the AI output include anything outside the course boundary?
- Does the final answer include verification evidence?
- Can the student explain one limitation or bug risk?

## Prompt Pattern

```text
Use a Karpathy-style teaching approach:
start from the smallest runnable baseline,
make the core loop visible,
avoid unnecessary abstractions,
grow the project in 2-4 inspectable steps,
and require verification after each step.

Course boundary: [allowed APIs]
Lecture concept: [concept]
Final task: [task]

Output:
1. baseline version,
2. improvement ladder,
3. concept-to-code map,
4. verification command/demo,
5. explanation script.
```

## What Not To Borrow Blindly

- Do not turn every class into deep learning or AI internals.
- Do not use advanced infrastructure just because it is elegant.
- Do not make students depend on long generated code they cannot inspect.
- Do not replace foundational practice with "vibe coding" before students understand the basics.

The useful transfer is the method: small, inspectable, runnable, explanatory.
