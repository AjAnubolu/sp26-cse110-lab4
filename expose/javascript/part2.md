# Part 2 - Variables, Data Types, Operators, Loops, Functions

## Variables continued

1. **Question 1 — Line 12:** Prints `3`.
   `i` was declared with `var` in the `for` loop, so it has function scope. After the loop ends, `i = 3` (the value that failed the `i < prices.length` check). It is still accessible at line 12.

2. **Question 2 — Line 13:** Prints `150`.
   `discountedPrice` was declared with `var` inside the loop body, but `var` has function scope, so it persists after the loop. Its last assigned value was `300 * (1 - 0.5) = 150`.

3. **Question 3 — Line 14:** Prints `150`.
   `finalPrice` was declared with `var` at the top of the function, so it is accessible. Its last value (from the last iteration) is `Math.round(150 * 100) / 100 = 150`.

4. **Question 4 — What will the function return?**
   Returns `[50, 100, 150]`.
   Each iteration pushes the rounded discounted price onto `discounted`: `100*0.5=50`, `200*0.5=100`, `300*0.5=150`.

5. **Question 5 — Line 12:** Throws `ReferenceError: i is not defined`.
   `i` was declared with `let` in the `for` loop initializer, so it is block-scoped to the loop. It does not exist at line 12.

6. **Question 6 — Line 13:** Throws `ReferenceError: discountedPrice is not defined`.
   `discountedPrice` was declared with `let` inside the loop body. It is block-scoped to that block and does not exist outside the loop.

7. **Question 7 — Line 14:** Prints `150`.
   `finalPrice` was declared with `let` at the top of the function (not inside a block), so it is accessible. Its last value is `150`.

8. **Question 8 — What will the function return?**
   Returns `[50, 100, 150]`. Same behavior as Q4 — `let` does not change what gets pushed to the array.

9. **Question 9 — Line 11:** Throws `ReferenceError: i is not defined`.
   `i` was declared with `let` in the `for` loop, so it is block-scoped and does not exist at line 11.

10. **Question 10 — Line 12:** Prints `3`.
    `length` is a `const` declared at the top of the function (`const length = prices.length`), so it is accessible. `prices.length === 3`.

11. **Question 11 — What will the function return?**
    Returns `[50, 100, 150]`. The function pushes each `discountedPrice` into `discounted` and returns it.

## Data Types

12. **Object access notation:**
    A. `student.name`
    B. `student['Grad Year']` (bracket notation required because the key has a space)
    C. `student.greeting()`
    D. `student['Favorite Teacher'].name`
    E. `student.courseLoad[0]`

## Basic Operators & Type Conversion

13. **Arithmetic:**
    A. `'3' + 2` → `'32'` (string concatenation — `+` with a string converts the other operand to a string)
    B. `'3' - 2` → `1` (`-` only does arithmetic, so `'3'` is coerced to the number `3`)
    C. `3 + null` → `3` (`null` is coerced to `0`)
    D. `'3' + null` → `'3null'` (string concatenation; `null` is coerced to `'null'`)
    E. `true + 3` → `4` (`true` is coerced to `1`)
    F. `false + null` → `0` (`false` → `0`, `null` → `0`)
    G. `'3' + undefined` → `'3undefined'` (string concatenation)
    H. `'3' - undefined` → `NaN` (`undefined` cannot be coerced to a valid number)

14. **Comparison:**
    A. `'2' > 1` → `true` (string is coerced to number `2`, and `2 > 1`)
    B. `'2' < '12'` → `false` (both strings — compared lexicographically; `'2'` comes after `'1'`)
    C. `2 == '2'` → `true` (loose equality coerces the string to a number)
    D. `2 === '2'` → `false` (strict equality — types differ, so `false`)
    E. `true == 2` → `false` (`true` is coerced to `1`, and `1 != 2`)
    F. `true === Boolean(2)` → `true` (`Boolean(2)` is `true`, both are booleans of the same value)

15. **Difference between `==` and `===`:**
    `==` is loose (abstract) equality — it coerces operands to the same type before comparing values, so `2 == '2'` is `true`.
    `===` is strict equality — it requires both the type and the value to match without any coercion, so `2 === '2'` is `false`.
    You should generally prefer `===` to avoid surprising coercion behavior.

## Loops

16. See `part2-question16.js` in this directory.

## Functions

17. **`modifyArray([1, 2, 3], doSomething)` returns `[2, 4, 6]`.**
    `modifyArray` creates an empty array `newArr`, then loops through `[1, 2, 3]` and calls `callback(array[i])` on each element, pushing the result.
    `doSomething(num)` returns `num * 2`. So `doSomething(1) = 2`, `doSomething(2) = 4`, `doSomething(3) = 6`. `newArr` becomes `[2, 4, 6]` and is returned.

## setInterval, setTimeout, clearTimeout

18. See `part2-question18.js` in this directory.

19. **Output of the `printNums()` code:**
    ```
    1
    4
    3
    2
    ```
    Walkthrough:
    - `console.log(1)` runs synchronously → prints `1`.
    - `setTimeout(..., 1000)` schedules `console.log(2)` for ~1 second later.
    - `setTimeout(..., 0)` schedules `console.log(3)` for the next tick (still queued, not synchronous).
    - `console.log(4)` runs synchronously → prints `4`.
    - The event loop then runs the `0`ms callback → prints `3`.
    - After ~1 second, the `1000`ms callback fires → prints `2`.
