# Syllabus
* LL and LR parsing using stack machines
* Compiling a C-like language (stack frames and x86 assembly)
* Compiling a functional language

# Conventions
* Greek letters for strings of symbols (could be made of both terminals and non-terminals) (denoted by forward slash followed by letter)
* Epsilon: empty string
* Uppercase letters: non-terminals
* Lowercase letters: terminals
* X, Y, Z: strings of non-terminals and/or terminals

# Derivations
* If `A -> a` then `b A c => b a c`

* A string `w` consisting of only terminals is *generated* by the grammar if there's a sequence of derivation steps leading to it from start symbol `S`

  ```
  S *=> w
  ```

  The Kleene star `*` on `*=>` means "any number of steps"

* Given `A -> \a` we have leftmost derivation steps

  ```
  w A \c l=> w a \c
  ```

  and rightmost derivation steps

  ```
  \b A z r=> \b a z
  ```

  Where `r=>` means rightmost derivations and `l=>` means leftmost derivations.

# Encoding regex
* `\a | \b`   is  
  ```
  A -> \a
  A -> \b
  ```
* `\a*`  is  
  ```
  A -> \a A
  A ->
  ```

# Ambiguity
A grammar is ambiguous if an input string can have more than one resulting parse tree. These are useless for compilers as a unique parse tree is needed for compilation.

Ambiguity =/= non-determinism
