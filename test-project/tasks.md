# Manual test checklist

Use this checklist when validating the extension in Zed.

## Setup

- [ ] Install as dev extension from `/home/anton/zed-latex-plugin`
- [ ] Open `test-project/main.tex`

## Task presets

- [ ] Run `latexmk (current file)`
- [ ] Run `latexmk (watch current file)` and confirm rebuild on save
- [ ] Run `pdflatex (single pass)`
- [ ] Run `lualatex (single pass)`
- [ ] Run `xelatex (single pass)`
- [ ] Run `tectonic`

Expected for each: no hard error, PDF generated, diagnostics reasonable.

## Root-aware build

- [ ] Open `test-project/sections/intro.tex`
- [ ] Run `latexmk (!TEX root aware)`

Expected: build is performed for `main.tex` due to `% !TEX root = ../main.tex`.

## Snippets

In `main.tex`, validate these prefixes expand:

- [ ] `sec`
- [ ] `beg`
- [ ] `eq`
- [ ] `ali`
- [ ] `fig`
- [ ] `tab`
- [ ] `thm`
- [ ] `prf`
- [ ] `cite`

In `references.bib`, validate:

- [ ] `art`
- [ ] `book`
- [ ] `inpro`
- [ ] `misc`

## Diagnostics quality

- [ ] In `main.tex`, set `\\brokendiagnosticstrue`
- [ ] Build with `latexmk (current file)`
- [ ] Confirm error points to `\\thiscommanddoesnotexist`
- [ ] Set `\\brokendiagnosticsfalse` and rebuild

Expected: clear file+line diagnostics and successful build after reverting.
