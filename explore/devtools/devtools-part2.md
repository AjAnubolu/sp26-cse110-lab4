# DevTools Part 2 - Debugging

## Questions

1. **What was the bug?**
   The values returned by `document.getElementById("num1").value` and `document.getElementById("num2").value` are **strings**, not numbers. When `calculateSum` does `num1 + num2`, JavaScript's `+` operator performs **string concatenation** instead of numeric addition. For example, with inputs `2` and `3`, the page displayed `Sum: 23` instead of `Sum: 5`.

   The watch expressions confirmed this: `typeof num1 === "string"`, `typeof num2 === "string"`, and therefore `typeof result === "string"`.

2. **How would you fix it?**
   Convert each value to a number before adding. The cleanest fix is in `printSum` (so `calculateSum` stays generic):

   ```js
   function printSum() {
       let num1 = Number(document.getElementById("num1").value);
       let num2 = Number(document.getElementById("num2").value);
       document.getElementById("sum").innerHTML = "Sum: " + calculateSum(num1, num2);
   }
   ```

   `Number(...)` converts the string to a numeric value (or `parseInt` / `parseFloat` would also work). Now `calculateSum(2, 3)` returns `5` instead of `"23"`.

   See `expand/screenshots/fix.png` for a screenshot of the fix.

## Screenshots (in `expand/screenshots/`)

- `result-calculateSum.png` — breakpoint set on the `let result = 0` line of `calculateSum`
- `result-dataType.png` — watch expressions for `num1`, `num2`, and `typeof result`
- `fix.png` — screenshot of the corrected code
