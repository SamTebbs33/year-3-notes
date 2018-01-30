# Representation

For a given instance of a problem `(S, f)` find a solution `s* e S` that is globally optimal, i.e `f(s*) <= f(s)` for minimisation or `f(s*) >= f(s)` for maximisation for all `s e S`, where `f` is the evaluation function that assigns a score to the solution. For the travelling salesman, S is the set of all possible routes between the cities (e.g. `{{Birmingham, Cardiff, London}, {Cardiff, Birmingham, London}}` etc.)

## Genotype-Phenotype representation
There is a function `h: G -> P` that corresponds a genotype to a phenotype, where the genotype represents the search space and the phenotype represents the solution space.

## Search spaces

* **Binary Genotypes**: `S = {0, 1}^n`
  Pseudo-Boolean function optimisation (`f: {0, 1}^n -> R`), combinatorial problems such as Vertex Cover, SAT and Knapsack
* **Continuous Genotypes**: `S = R^n`
  Continuous function optimisation (`f: R^n -> R`)
* **Permutation Genotypes**: `S = S^n`
  Different ordering for the problem
