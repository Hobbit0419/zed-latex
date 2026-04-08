# LaTeX Smart for Zed

LaTeX Smart is a Zed extension focused on practical authoring workflow improvements:

- stronger default build flags for clearer diagnostics
- task presets for `latexmk`, `tectonic`, and single-pass engines
- root-aware build task for `% !TEX root = ...` projects
- writing snippets for common environments and bibliography entries

It is based on the existing `zed-latex` extension and keeps Texlab integration for language intelligence and PDF sync features.

## What is included in v1

- Texlab language server support (auto-download fallback if not on `PATH`)
- Build-on-save defaults (when not explicitly overridden in user settings)
- Better default diagnostics flags for TeX builds
- Runnable LaTeX tasks tagged as `latex-build`
- Snippets for `latex` and `bibtex`

## Build and diagnostics defaults

The extension sets default Texlab build args only when you have not explicitly set them:

- `-file-line-error`
- `-interaction=nonstopmode`
- `-halt-on-error`
- `-synctex=1`

These produce cleaner file/line diagnostics in the editor and fail fast on hard errors.

## Built-in tasks

From the run button in LaTeX files, you can use:

- `latexmk (current file)`
- `latexmk (watch current file)`
- `latexmk (!TEX root aware)`
- `pdflatex (single pass)`
- `lualatex (single pass)`
- `tectonic`

The `!TEX root aware` task reads `% !TEX root = ...` from the current file before building.

## Snippets

This extension provides snippet files via:

- `snippets/latex.json`
- `snippets/bibtex.json`

Examples include sectioning, theorem/proof environments, figure/table templates, list templates, and bibliography entry skeletons.

## User configuration examples

Disable build-on-save:

```json
{
  "lsp": {
    "texlab": {
      "settings": {
        "texlab": {
          "build": {
            "onSave": false
          }
        }
      }
    }
  }
}
```

Use `tectonic` for Texlab build:

```json
{
  "lsp": {
    "texlab": {
      "settings": {
        "texlab": {
          "build": {
            "executable": "tectonic",
            "args": [
              "-X",
              "compile",
              "%f",
              "--untrusted",
              "--synctex",
              "--keep-logs",
              "--keep-intermediates"
            ]
          }
        }
      }
    }
  }
}
```
