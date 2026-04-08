# LaTeX Smart test project

This project is designed to validate the new extension features quickly.

## Files

- `main.tex`: root document used for most task tests
- `sections/intro.tex`: subfile with `% !TEX root = ../main.tex` for root-aware task testing
- `references.bib`: bibliography entries for citation/bib workflow

## Quick test flow

1. Open `main.tex` in Zed.
2. Run these tasks from the Run button:
   - `latexmk (current file)`
   - `pdflatex (single pass)`
   - `lualatex (single pass)`
   - `xelatex (single pass)`
   - `tectonic`
3. Confirm PDF output and diagnostics are shown.
4. Open `sections/intro.tex` and run `latexmk (!TEX root aware)`.
   - Expected: it builds `main.tex`, not `intro.tex`.

## Diagnostics checks

In `main.tex`, set `\\brokendiagnosticstrue` and build again.

Expected:
- build fails fast
- diagnostics point to file/line of `\\thiscommanddoesnotexist`

Then set `\\brokendiagnosticsfalse` again.
