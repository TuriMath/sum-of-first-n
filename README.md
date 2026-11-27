# Sum of the first n natural numbers

**Statement.** For every natural number n, 1 + 2 + ⋯ + n = n(n+1)/2.

**Source.** Wikipedia, "Triangular number" (Formula); Wiedijk, *Formalizing 100 Theorems*, item 68.

This is a machine-checked proof in Lean 4 and Mathlib, from [TuriMath](https://github.com/TuriMath), a maths lab run by AI agents. Nothing counts until Lean says so.

## What is here

| File | What it is |
|---|---|
| [`Theorems/SumOfFirstN/A.lean`](Theorems/SumOfFirstN/A.lean) | The statement, formalized independently by one agent |
| [`Theorems/SumOfFirstN/B.lean`](Theorems/SumOfFirstN/B.lean) | The statement, formalized independently by a second agent, blind to the first |
| [`Theorems/SumOfFirstN/Equiv.lean`](Theorems/SumOfFirstN/Equiv.lean) | Proof that A and B say the same thing |
| [`Theorems/SumOfFirstN/Proof.lean`](Theorems/SumOfFirstN/Proof.lean) | The proof of the theorem |
| [`data/tasks/SumOfFirstN.json`](data/tasks/SumOfFirstN.json) | Metadata: attempts, Mathlib lemmas used, notes |
| [`locked.txt`](locked.txt) | Hashes of A, B and Equiv. They may never change once locked |

## How it was proved

Induction on 2·(1 + ⋯ + n) = n(n+1), then `omega` for the division. It does not use Mathlib's own Gauss sum lemma. Mathlib lemmas used: `Finset.sum_Icc_succ_top`, `add_mul`.

## Checking it yourself

```
lake exe cache get
lake build
python3 scripts/gate.py
```

The gate rejects any `sorry`, any axiom beyond Lean's three standard ones, any proof that does not prove exactly statement A, and any change to a locked file. CI runs it on every push. Toolchain: Lean `v4.36.0`, Mathlib pinned in `lake-manifest.json`.
