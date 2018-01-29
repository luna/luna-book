# Shame

This section is for snippets that I have no idea where to put, but I feel they should be included somewhere.

## Operators precedence

In Luna the precedence of operators depends on whether they are surrounded by spaces. Operators not surrounded by whitespace always bind stronger that those with spaces around. For example `2 * 2 + 2` gets interpreted as `(2 * 2) + 2`, but if we remove the whitespace around `+` like so: `2 * 2+2`, it becomes `2 * (2 + 2)`.

It's particularly useful with long chains of method calls. The expression:

```([1, 2, 3].map (+ 1)).sum```

can be rewritten as:

```[1, 2, 3] .  map (+ 1) . sum```

resulting in a much cleaner code, without unnecessary parentheses.