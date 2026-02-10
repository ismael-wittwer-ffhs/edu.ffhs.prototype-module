# [Module Name] — FFHS

> **Prototype Module Repository**
> This is the template repository for creating new FFHS course modules. Replace the bracketed placeholders with your actual module information before use.

## Module Summary

`[Put your module summary here.]`

## Module Overview

| Field            | Value                          |
|------------------|--------------------------------|
| Module Code      | `[e.g. PCG]`              |
| Module Name      | `[e.g. Programming in C# for Games]`  |
| ECTS             | `[e.g. 5]`                    |
| Semester         | `[e.g. HS 2026]`              |
| Responsible      | `[Name]`                      |

## Folder Structure

```
├── src/
│   ├── input/          # Raw source material (PDFs, text files, etc.)
│   └── output/         # Processed markdown output from source material
├── content/
│   ├── block-1/        # Block 1 course content
│   ├── block-2/        # Block 2 course content
│   ├── block-3/        # Block 3 course content
│   ├── block-4/        # Block 4 course content
│   ├── block-5/        # Block 5 course content
│   └── exams/          # Exam materials
├── scripts/                # Helper scripts (Moodle transformers, markdown-to-PDF, etc.)
```

### `src/input/`
Place all raw source materials here — PDFs, Word documents, text files, or any other input that needs to be processed. This folder is excluded from Cursor indexing (via `.cursorignore`).

### `src/output/`
Contains the processed markdown versions of the input sources. These serve as the intermediate representation used to author the final course content.

### `content/block-[1-5]/`
The five blocks of the course. Each subfolder holds the final, structured content for that block (learning objectives, exercises, assessments, etc.).

## How to Adapt This Template

1. **Replace all `[placeholders]`** in this README with your actual module details.
2. **Rename the block folders** if your course uses different naming (e.g. `week-1`, `unit-1`). Adjust the structure above accordingly.
3. **Add or remove blocks** if your course has more or fewer than five.
4. **Drop source material** into `src/input/` and place processed output in `src/output/`.
5. **Populate each `content/block-*/`** folder with the final teaching material for that block.
6. **Delete this section** ("How to Adapt This Template") once the module is set up.
