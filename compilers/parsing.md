# Parser
A parser for a grammar is a program such that for any input string `w` produces a parse tree or raises a syntax error when the string doesn't match the grammar.

# Parsing Dyck language with a stack machine
1. If '[' then consume and push ']' onto stack

2. If ']':

  If same ']' is on stack then pop stack and consume

  Else stop and reject

3. If input is empty:

  If stack is empty: accept

  Else: reject

# Determinism vs non-determinism
* **Finite automata**: can always construct DFA to NFA
* **Pushdown automata**: *not always* possible to make deterministic
* **Polynomial-time Turing machines**: There are no deterministic P-time algorithm for NP-complete problems

# Parsing stack machines
A state comes in the form `<\s, w>`

* \s is the stack, a string of symbols (perhaps non-terminals)
* w is the remaining input, no non-terminals

Transitions come in the form

```
<\s1, w1> -> <\s2, w2>
```

# LL and LR
L means that the input is read from left to right.

**LL** machine step == leftmost derivation
**LR** machine step == rightmost derivation in reverse

**LL(1)** LL with one symbol lookahead
**LL(k)** LL with `k` symbols lookahead
**LL(*)** LL(k) with a large enough `k`
**LR(0)** LR with 0 symbols lookahead
**LALR(1)** variant of LR(1) with less memory consumption
**LR(k)** for `k` > 1 is not needed as LR(1) is powerful enough

In LL the stack has a prediction of what the parser expects to see in the input. In LR the stack has a reduction of what the parser has already seen in the input.

LR is more powerful than LL as it only deals with what has been seen, rather than making chance predictions about future input.
