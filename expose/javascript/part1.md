# Part 1 - Variables & Scoping

## var declaration

1. **What is printed by line 9?**
   `values added: 20`
   The function is called with `add = true`, so it enters the `if` block. `result` is declared with `var` and assigned 0, then reassigned to `num1 + num2 = 20`. Line 9 logs `values added: 20`.

2. **What is printed by line 13?**
   `final result: 20`
   Because `result` was declared with `var`, it has function scope (not block scope). It is still accessible outside the `if` block, so line 13 prints `final result: 20`.

3. **Why should you not use `var`? Explain why.**
   `var` has function scope (not block scope), which causes bugs when variables leak out of `if`/`for`/`while` blocks. It is also hoisted and initialized as `undefined`, can be redeclared in the same scope without error, and does not respect the temporal dead zone. `let` and `const` are block-scoped and safer, making code easier to reason about and reducing the chance of accidental variable reuse.

## let declaration

4. **What is printed by line 9?**
   `values added: 20`
   Same as before — inside the `if` block, `result` is declared with `let`, set to 0, then reassigned to 20.

5. **What is printed by line 13?**
   Nothing is printed — the code throws a `ReferenceError: result is not defined`.
   `let` is block-scoped, so `result` only exists inside the `if` block. Outside the block (on line 13), it is no longer defined.

## const declaration

6. **What is printed by line 9?**
   Nothing is printed — line 9 is never reached. The code throws a `TypeError: Assignment to constant variable.` on line 7 when it tries to reassign `result` (originally `const result = 0`).

7. **What is printed by line 13?**
   Nothing is printed — same reason as Q6. The function errors out on line 7 before reaching line 13.
