# Transform Source Input to Markdown

Transform the raw source files in `src/input/` into clean, structured markdown files in `src/output/`.

## Instructions

1. **Scan `src/input/`** for all files and subfolders.

2. **Naming scheme** — use zero-padded two-digit prefixes to preserve order:

   | Input layout | Output path |
   |---|---|
   | `src/input/file.pdf` | `src/output/01-file.md` |
   | `src/input/topic-a/intro.pdf` | `src/output/01-topic-a/01-intro.md` |
   | `src/input/topic-a/details.docx` | `src/output/01-topic-a/02-details.md` |

   - Top-level items (files or folders) are numbered `01`, `02`, … in the order they appear.
   - Files inside a subfolder are numbered independently starting at `01`.
   - Strip the original file extension and kebab-case the name: `My File (v2).pdf` → `03-my-file-v2.md`.
   - Folder names follow the same kebab-case convention.

3. **Folder = source parent** — when input is a folder:
   - Create a matching folder under `src/output/`.
   - Add a `00-index.md` file inside that folder with a heading derived from the folder name (e.g., `# Topic A`) and a table-of-contents listing every chapter file.
   - Each file in the subfolder becomes a chapter / content section.

4. **Content transformation rules:**
   - Extract or convert the full textual content of each source file into markdown.
   - Use proper markdown heading hierarchy: `#` for the document title, `##` for major sections, `###` for subsections, etc.
   - Preserve lists, tables, code blocks, and emphasis where present in the source.
   - If the source contains images, note them as `<!-- image: description -->` placeholders.
   - Do **not** invent content — only restructure and format what exists in the source.

5. **Do not overwrite** existing files in `src/output/` unless the user explicitly asks to regenerate.

6. After transformation, print a short summary listing every generated file and its source.
