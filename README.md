# DM42 Matrices & Linear Algebra Handbook

A calculator-first guide to matrices, vectors, linear systems, numerical reliability, and applied linear algebra on the SwissMicros DM42.

This repository contains the finished handbook PDF and its reproducible LuaLaTeX source. It is written for DM42 users who want both the underlying mathematics and the exact calculator workflow, from first matrix entry through advanced numerical applications.

## Download

[Download the handbook PDF](./DM42_Matrices_Linear_Algebra_Handbook.pdf)

## What the handbook covers

- Matrix creation, naming, editing, resizing, and indexed access
- Vectors, dot products, cross products, norms, and transformations
- RPN stack order and DM42 matrix-division semantics
- Determinants, inverses, square systems, and the SIMQ application
- Singular, inconsistent, underdetermined, and ill-conditioned systems
- Least-squares fitting and residual-based verification
- Real and complex matrices, including transpose versus conjugate transpose
- Engineering, electronics, physics, chemistry, finance, logistics, game-theory, Markov-chain, astronomical, and sensor-fusion examples
- Constructed advanced methods, capability boundaries, troubleshooting, and a compact command atlas

## DM42-specific approach

The handbook distinguishes carefully between normal calculator operation and program entry. In normal mode, `XEQ` executes a named command or program. In `PRGM` mode, pressing `XEQ` inserts an `XEQ` instruction into the current program line; it does not execute the instruction while the program is being entered.

Calculator keys, soft keys, display mock-ups, diagrams, circuit drawings, plots, and matrix annotations are generated from reusable LaTeX macros or native TikZ, Circuitikz, and PGFPlots code. The pages are not flattened images.

## Building the PDF

The source requires a reasonably complete TeX Live installation with LuaLaTeX, BibTeX, MakeIndex, `latexmk`, TikZ, Circuitikz, PGFPlots, and the packages referenced by `preamble.tex`.

Build the handbook with:

```sh
make
```

The build runs LuaLaTeX together with the required bibliography and index passes and produces `main.pdf`.

To build directly:

```sh
latexmk -lualatex -bibtex -interaction=nonstopmode -halt-on-error main.tex
```

## Verifying the numerical examples

Representative numerical results are independently checked with NumPy:

```sh
python3 verification/verify_examples.py
```

The verification suite covers matrix-product order, real and complex network solves, least-squares coefficients and orthogonality, Markov-chain results, stationary distributions, and a constrained KKT solve.

## Repository layout

```text
.
├── main.tex
├── preamble.tex
├── references.bib
├── Makefile
├── chapters/
│   ├── 01-foundations.tex
│   ├── 02-native.tex
│   ├── 03-operations.tex
│   ├── 04-systems.tex
│   ├── 05-applications.tex
│   ├── 06-advanced.tex
│   └── 07-reference.tex
└── verification/
    └── verify_examples.py
```

## Reference baseline

The command descriptions and calculator behaviour were checked against the contemporary SwissMicros DM42 documentation and the DM42/Free42 implementation available when this edition was prepared. Menu placement and labels may change in later firmware, while the underlying mathematical explanations remain applicable.

## Contributions

Corrections, reproducible counterexamples, clearer keystroke sequences, and additional well-verified applications are welcome. When reporting a calculator-specific issue, please include the DM42 firmware version, stack configuration, input matrices, exact key sequence, observed result, and expected result.

