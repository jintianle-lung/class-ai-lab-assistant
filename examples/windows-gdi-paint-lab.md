# Example: Windows GDI Paint Lab

## Input

```text
Course: Windows Programming
Topic: MFC document-view and GDI drawing
Teacher points:
1. Document stores data, view displays data.
2. GDI draws through DC, pen, and brush.
3. WM_PAINT should redraw the window.
Task: build a drawing program similar to a reference PaintORama project, but improved.
Allowed: C++, Win32, MFC, GDI.
Avoid: Qt, Direct2D, OpenGL, web frontend.
```

## Knowledge Map

| Lecture concept | Code/API | Visible behavior | Student explanation |
|---|---|---|---|
| Program entry | `WinMain` | Opens a window | GUI program starts here |
| Message handling | `WndProc` | Handles menu/mouse/paint | Windows programs are message-driven |
| GDI drawing | `HDC`, `HPEN`, `HBRUSH` | Draws lines and shapes | Drawing happens through device context |
| Mouse messages | `WM_LBUTTONDOWN`, `WM_MOUSEMOVE`, `WM_LBUTTONUP` | Drag to draw | Press starts, move previews, release commits |
| Correct redraw | `WM_PAINT`, `RenderDocument` | Drawing remains after resize/cover | Redraw from stored data |
| Document-view idea | `DrawingDocument`, `Stroke` | Stores all shapes | Data is separated from display |

## Tiny Baseline

```text
V0: create a window and draw one fixed line in WM_PAINT.
Verification: run the program and see the line.
```

## Improvement Ladder

| Version | New feature | Concept | Verification |
|---|---|---|---|
| V0 | Window + fixed line | `WinMain`, `WM_PAINT`, `HDC` | Window shows line |
| V1 | Mouse drag line | mouse messages | Drag draws a line |
| V2 | Store strokes | document data | Multiple strokes remain in memory |
| V3 | Redraw from strokes | document-view, `WM_PAINT` | Resize window; drawing remains |
| V4 | Save/export | serialization/files | Reopen data or export BMP |

## Student Defense Script

```text
This project demonstrates GDI drawing and document-view thinking.
Mouse messages create drawing data. The document stores that data as strokes.
WM_PAINT does not invent new data; it reads the document and redraws all strokes.
This solves the problem of drawings disappearing after window redraw.
```

