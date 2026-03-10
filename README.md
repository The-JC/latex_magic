# latex_magic (personal LaTeX snippet collection)

`latex_magic` is your personal repository of reusable LaTeX snippets: macros, styles, and topic-specific subpackages.

## Philosophy

- Keep everything in one repo (`external/`)
- Load only what each document needs (opt-in modules)
- Organize snippets by topic so you can grow the collection safely

## Current structure

- `latex_magic.sty` — top-level module loader
- `styles/wirelesscomm.sty` — wireless communications subpackage
- `styles/matlablisting.sty` — MATLAB listing style
- `macros/communications.tex` — communications math macros

## Basic usage

In your document preamble:

```tex
\makeatletter
\def\input@path{{external/}}
\makeatother
\usepackage[wirelesscomm]{latex_magic}
```

## Module options

Top-level options in `latex_magic`:

- `wirelesscomm` — load the wireless communications subpackage
- `wc-macros` — only wireless communication macros
- `wc-listings` — only wireless listing style
- `none` — load nothing

Backward-compatible aliases:

- `all` = `wirelesscomm`
- `macros` = `wc-macros`
- `listings` = `wc-listings`

## Add your own snippets

1. Add macros in `macros/<topic>.tex`
2. Add styles/subpackages in `styles/<topic>.sty`
3. Expose the module through options in `latex_magic.sty`
4. Load the module from documents via `\usepackage[<module>]{latex_magic}`

## GitHub CI smoke tests

This repository includes a GitHub Actions workflow at `.github/workflows/latex-package-ci.yml`.

It compiles minimal test documents from `tests/` to verify package loadability for:

- `wirelesscomm`
- `wc-macros`
- `wc-listings`
- `none`

The CI job is a smoke test to ensure package options resolve and compile successfully on push and pull requests.
