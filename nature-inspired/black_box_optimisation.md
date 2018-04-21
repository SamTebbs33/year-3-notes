# Black box optimisation
The evolutionary algorithm may not always know the details of the fitness function, which acts like a black box mapping inputs to outputs.

## Cost of an algorithm
Cost of an algorithm `A` on fitness function `f`:

```
T(A, f) = min[t e N](t | f(x(t)) >= f(y))
```
This gives the minimum time point that has an optimum search point.

Average case of expected runtime:
```
E(T(A, f)) = Sum[f e F](P(f) * E(T(A, f)))
```

## Algorithm
1. Choose some probability distribution `p0` on `X`
2. Sample a search point `x0 e X` according to `p0`
3. `R0 = {x0}`
4. Evaluate the fitness of `x0 = f(x0)`
5. For `t = 1` to `|X|`:
  6. `Ht = (x0, f(x0)), ..., (x(t-1), f(x(t-1))`
  7. Given `Ht` choose a prob. distribution `pt` on `X \ R(t-1)`
  8. Sample a search point `xt e X \ R(t-1)` according to `pt`
  9. `Rt = {x0, ..., xt}`
  10. Evaluate the fitness of `xt = f(xt)`
