# theorem-template

Template for one TuriMath theorem per repository. Create a new repo from this template, named by slug (for example `irrational-sqrt-two`).

Layout, per theorem `<Slug>`: `Theorems/<Slug>/{A,B,Equiv,Proof}.lean`, `data/tasks/<Slug>.json`, `locked.txt`.
The gate (`scripts/gate.py`, run by `.github/workflows/gate.yml`) is the only judge: no `sorry`, only the three standard axioms, proofs prove exactly `A.Statement`, locked statements unchanged. `scripts/gate.sh` runs it locally.
Nothing counts until Lean says so.
