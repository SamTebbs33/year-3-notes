# Niching
The formation of groups of individuals in a population. Individuals within a group are similar to each other, while individuals from different groups are very different from each other.

* Helps to maintain population diversity, and thus explore the search space better.
* Helps to optimise multiple objectives simultaneously

## Techniques

### Sharing
Transforms the raw fitness of an individual into that of the shared (often lower). The idea is that there is a limited and fixed amount of resources (i.e fitness value) available at each niche. Those occupying the same niche will share the same resources.

[![](https://img.youtube.com/vi/4pdiAneMMhU/0.jpg)](https://www.youtube.com/watch?v=4pdiAneMMhU)

The sharing radius ...

* Sharing function
  ```
  sh(d(i, j)) = 1 - (d(i,j) / \s) ^ a, if d(i,j) < \s
               0, otherwise
  ```

  where `d(i,j)` is the distance between individuals `i` and `j`.
* Shared fitness
  The shared fitness of individual `i` can be defined as
  ```
  fshare(i) = fraw(i) / (Sum[1, \u](sh(d(i, j))))
  ```
  where `\u` is the population size.

Sharing can be done at genotypic or phenotypic levels.
* Genotypic level: Hamming distance
* Phenotypic level: Euclidean distance

A too small sharing radius, then diversity will be low as most individuals will be outside the radius. I it is too large, then there will be little niching as most individuals are in one group.

Fitness sharing can be computationally expensive, as with a population size of `x`, there will be `x^2` pairs of individuals, for all of which distance needs to be calculated.

#### Fitness scaling

```
fshare(i) = fraw(i)^\B / (Sum[1, \u](sh(d(i, j))))
```
for some `\B > 1`

Fitness scaling is often needed to make fitness sharing work appropriately.

With a too small scaling factor, individuals won't converge to the real optima as they are not attractive. With a too large scaling factor, "super individuals" in the initial populations will dominate the population quickly and the evolution may not reach all peaks.

Solutions are:
* Large population
* Soft selection
* Annealing `\B`, start from `\B = 1` and increase gradually

### Implicit fitness sharing
[See from page 12](https://canvas.bham.ac.uk/courses/27617/files/4947578?module_item_id=865921)

#### Algorithm
For each test case `i` to be solved, do the following `C` times
1. Select a sample of `\s` individuals from the population
2. Find the individual in the sample that achieves the best performance for solving test case `i`
3. This best individual receives the payoff. Ties are broken evenly (payoff will be shared evenly among all the best individuals if they have the same best performance)

### Crowding
Crowding techniques insert new individuals into the population by replacing similar individuals, and strive to maintain the pre-existing diversity of a population. Don't modify fitness.

#### Deterministic crowding algorithm
```
Initialise P(0)
From t = 1 to G:
  shuffle P(t - 1) into P(t)
  From i = 0 to (population size / 2 - 1):
    set p1 to the (2 * i + 1)th individual of population t
    set p2 to the (2 * i + 2)th individual of population t
    set c1 and c2 to the offspring from recombination of p1 and p2
    mutate c1 and c2 into c1' and c2' respectively
    If distance between p1 and c1' <= distance between p2 and c2' then:
      If fitness of c1' > fitness of p1 then set (2 * i + 1)th individual of population t to c1'
      If fitness of c2' > fitness of p2 then set (2 * i + 2)th individual of population t to c2'
    Else
      If fitness of c2' > fitness of p1 then set (2 * i + 1)th individual of population t to c2'
      If fitness of c1' > fitness of p2 then set (2 * i + 2)th individual of population t to c1'
    End
  End
End
```

Minimal replacement error (replacing an individual very different), few parameters to tune, fewer distance calculations than in fitness sharing, population size must be large enough and should use full crossover (with crossover rate 1.0).
