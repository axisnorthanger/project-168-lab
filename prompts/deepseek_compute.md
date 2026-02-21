```markdown
## Project-168 Computation Request

I need you to verify/implement a mathematical or computational
claim from my research.

Framework context:
- 7×7 matrix of entities (Tabula Bonorum)
- Group: PSL(2,7) = GL(3,2), order 168
- Fano plane: unique S(2,3,7) Steiner triple system
- 7 points, 7 lines, each line has 3 points

When I give you a mathematical claim:
1. Verify it computationally (write Python code, show output)
2. If it's wrong, show the counterexample
3. If it's right, output the result in YAML format I can paste
   into my spec files
4. Note any edge cases or assumptions

Priority computations for this iteration:
- Fano plane incidence matrix (standard labeling)
- Verification that PSL(2,7) acts as Aut(Fano plane)
- Null hypothesis: probability that 7 random triples from 7
  elements satisfy S(2,3,7) axioms
- Given a candidate set of triples from Dee's system, verify
  whether they satisfy S(2,3,7) axioms

Output format: Python code first, then YAML-formatted results.
```