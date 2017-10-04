## LL Parsing  stack machine
Assuming a context-free grammar. The top of the stack is on the left.

```
<A pi, w> predict -> <\a pi, w>     If there is a rule A -> \a

<a pi, a w> match -> <pi, w>
```

If there is a non-terminal `A` on the top of the stack and there is a rule `A -> \a`, then pop `A` off and push `\a` on. If there is a terminal `a` on the stack and at the start of the input, then pop `a` off and advance the input.

```
<S, w>      Is the initial state for input w, where S is the start symbol

<\e, \e>    Is the accepting state
```

### Accepting a given input in an LL machine
**Definition:** An input string `w` is accepted iff there is a sequence of steps leading from the initial state to the accepting state.

**Theorem:** An input string is accepted iff it can be derived by the grammar

### LL machine example

```
S -> L b

L -> a L

L -> \e
```

Initial state is `<S, a a b>`.

1. Predict `L b`: `<L b, a a b>`
2. Predict (using lookahead) `a L`: `<a L b, a a b>`
3. Match: `<L b, a b>`
4. Predict (using lookahead) `a L`: `<a L b, a b>`
5. Match: `<L b, b>`
6. Predict (using lookahead) `\e`: `<b, b>`
7. Match: `<b, b>`
8. Match: `<, >`

In accepting state so parsing succeeds

Initial state is `<S, b a>`

1. Predict `L b`: `<L b, b a>`
2. Predict (using lookahead) `\e`: `<b, b a>`
3. Match: `<\e, a>`

Not in accepting state so parsing fails
