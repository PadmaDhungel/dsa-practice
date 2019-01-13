## Arithmetic Operator
| Operator       | Expression  & Result a=10, b=3 | Description                                           |
| -------------- | -------------------- | ----------------------------------------------------- |
| Addition       | `a + b` → `13`       | Adds two values.                                      |
| Subtraction    | `a - b` → `7`        | Subtracts the second value from the first.            |
| Multiplication | `a * b` → `30`       | Multiplies two values.                                |
| Division       | `a / b` → `3.333...` | Divides the first value by the second (float result). |
| Floor Division | `a // b` → `3`       | Divides and rounds down to the nearest integer.       |
| Modulo         | `a % b` → `1`        | Returns the remainder of the division.                |
| Exponentiation | `a ** b` → `1000`    | Raises the first value to the power of the second.    |


### Operator precedence (Order of operations)

*Python follows PEMDAS/BODMAS rules:*

Parentheses > Exponents > Multiplication/Division > Addition/Subtraction

```
result = 10 + 2 * 3        # 10 + 6 = 16
result = (10 + 2) * 3      # 12 * 3 = 36
```
### Compound Assignment Operators

These compound assignment operators are shorthand for their longer equivalents and make code mroe concise and readable.
| Expression | Equivalent To | Description             |
| ---------- | ------------- | ----------------------- |
| `x += y`   | `x = x + y`   | Add and assign          |
| `x -= y`   | `x = x - y`   | Subtract and assign     |
| `x *= y`   | `x = x * y`   | Multiply and assign     |
| `x /= y`   | `x = x / y`   | Divide and assign       |
| `x %= y`   | `x = x % y`   | Modulo and assign       |
| `x //= y`  | `x = x // y`  | Floor divide and assign |
| `x **= y`  | `x = x ** y`  | Exponentiate and assign |


### Useful math functions

| Function Name & Syntax     | Expression & Result         | Remarks                                             |
| -------------------------- | --------------------------- | --------------------------------------------------- |
| `abs(x)`                   | `abs(-10)` → `10`           | Returns absolute (positive) value                   |
| `round(x, ndigits)`        | `round(3.1415, 2)` → `3.14` | Rounds number to `ndigits` decimal places           |
| `pow(base, exp)`           | # `pow(2, 3)` → `8` <br> # `pow(2, 3.5) `→ `11.3137` <br> #  `pow(2, -3)` → `0.125` <br>  # `pow(-9, 0.5)` → `3j`         | # base(int) and exp(int) → int <br>  # base(float) or exp(float) →  float <br> # exp(-ve) →  float <br> # base(-ve) and exp(not int) → complex  |
| `max(iterable or args...)` | `max(3, 7, 5)` → `7`        | Returns the largest item                            |
| `min(iterable or args...)` | `min(3, 7, 5)` → `3`        | Returns the smallest item                           |
| `sum(iterable)`            | `sum([1, 2, 3])` → `6`      | Adds all values in the iterable                     |

### Useful math constants

| Constants     | Expression & Result         | Remarks                                             |
| -------------------------- | --------------------------- | --------------------------------------------------- |
| `math.pi`                  | `math.pi` → `3.14159...`    | The mathematical constant π                         |
| `math.e`                   | `math.e` → `2.71828...`     | Euler's number (the base of natural logarithms)     |



### Useful math functions (from math module)

import math
| Function Name & Syntax | Expression & Result      | Remarks                                  |
| ---------------------- | ------------------------ | ---------------------------------------- |
| `math.sqrt(x)`         | `math.sqrt(16)` → `4.0`  | Always returns a float                   |
| `math.pow(base, exp)`  | `math.pow(2, 3)` → `8.0` | Always Returns float; `2 ** 3` gives `8` as int |
| `math.floor(x)`        | `math.floor(3.9)` → `3`  | Rounds **down** to nearest whole number  |
| `math.ceil(x)`         | `math.ceil(3.1)` → `4`   | Rounds **up** to nearest whole number    |


### More on floor, ceil, round and int()
| Function        | Example                 | Description                            |
| --------------- | ----------------------- | -------------------------------------- |
| `math.floor(x)` | `math.floor(2.9)` → `2` | ALways Rounds **down** to the nearest integer |
| `math.ceil(x)`  | `math.ceil(2.1)` → `3`  | Always Rounds **up** to the nearest integer   |
| `round(x)`      | `round(2.5)`→ `2` <br> `round(3.5)`→ `4 `     | Rounds to the nearest **even** integer |
| `int(x)`        | `int(2.9)` → `2`        | Removes the decimal part (no rounding) |
