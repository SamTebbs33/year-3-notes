# Algorithms

## Types
* Divide and conquer (e.g quicksort)
* Dynamic programming
* Mathematical programming
* Search and enumeration
  * Brute force
  * Improved brute force (not exploring candidate solutions that will most definitely not work)
  * Heuristic algorithms
    * Experience-based: experimental, less theoretical and systematic
    * Usually non-optimal but satisfactory
    * Faster alternative to brute forcing

## Heuristic algorithms
A usually simple algorithm that produces a good enough solution for a problem in a reasonable time frame. Has a tradeoff between completeness/accuracy/optimality/precision for speed.

## Deterministic Algorithms
An algorithm that will always produce the same output for a particular input, e.g a deterministic finite state automaton.

## Randomised algorithms
An algorithm that makes random choices during its execution. Immune to data ordered in a detrimental way as they don't work based on the order of the data.

Two categories:
* Using random numbers to find a solution to a problem
* Using random numbers to improve a solution to a problem

### Las Vegas algorithm
Selects a random element and checks if it matches, else continues Guaranteed to be correct but time is not controlled.
```
repeat
  a = random element
until a is correct
```

## Monte Carlo algorithm
Checks random elements a restricted number of times, if it doesn't find the correct element it returns a random one. Not guaranteed to be correct but time is controlled.
```
i = 0
k = 1000 // arbitrary limit
repeat
  a = random element
  i++
until a is correct or i == k
```

### Applications
RIP

### Advantages
* Usually simple and easy to implement
* For many problems, they produce near-optimum solutions with high probability.

### Disadvantages
* It's difficult the analyse the performance and complexity due to its non-determinism.
