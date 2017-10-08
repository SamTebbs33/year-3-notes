# LR parsing stack machine
Assuming a context-free grammar. The top of the stack is on the right.

```
<\r, a w> shift -> <\r a, w>
<\r \a, w> reduce -> <\r A, w>      If there is a rule A -> \a
```

Where `\r` is the stack and `w` is the input.

If the right hand side of a rule is on the top of the stack then reduce it to its left hand side. Else shift the top of the input to the stack.

```
<\e, w>     Is the initial state for input w
<S, \e>     Is the accepting state
```

## Example
```
S -> A
S -> B
D -> a
A -> a b
B -> a c
```

Initial state is `<\e, a b>`

1. Shift: `<a, b>`
2. Shift: `<a b, \e>`
3. Reduce: `<A, \e>`
4. Reduce: `<S, \e>`

## Non-determinism
For some grammars there may be:
* **shift/reduce conflicts**: Either step can be carried out at some machine step
* **reduce/reduce conflicts**: When the top of the stack could be reduced to one of multiple rules
