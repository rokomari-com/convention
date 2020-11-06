# code blocks
- use `4` spaces for block indentation.
- Use a single blank line to separate sections with the same logic or semantics.

### braces `{}`
- A space before opening brace.
- No line break before the opening brace.
- Line break after the opening brace.
- Line break before the closing brace.
- Line break after the closing brace, only if that brace terminates a statement or terminates the body of a method, constructor, or named class. For example, there is no line break after the brace if it is followed by else or a comma.
```
return () -> {
    while (condition()) {
        method();
    }
};

class MyClass() {

    @Override
    public void method() {
        if (condition()) {
            try {
                something();
            } catch (ProblemException e) {
                recover();
            }
        } else if (otherCondition()) {
            somethingElse();
        } else {
            lastThing();
        }
    }
}
```
- always use braces for single-line blocks.
    ```
    if (condition()) {
        statement();
    } 
    ```
- for empty blocks, block should be closed in the next line.
  ```
  if (condition()) {
  }
  ```

## parentheses `()`
- No space is used between the `(` character and its following character. Same for the `)` character and its preceding character.
  ```
  statement(Integer i);
  ```
- if method has multiple parameters, their should be a space between them in the method declaration & metthod calling
  ```
  void statement(Integer i, String st, Status status) {
      ...
  }

  statement(1, "Hello", Status.FINISHED);
  ```
- There must be one space between keywords, such as if/for/while/do/switch/try/catch/finally etc, and parentheses.
---

## operator
- There must be one space at both left and right side of operators, such as `=`, `&&`, `+`, `-`, ternary operator, etc.
  ```
  Integer i = 10;
  Boolean b = false;
  if (i == 10 && b == true) {
      i = i + 1 ? 0 : -10;
      i++;
  }
  ```

## control statetments
- In a `switch` block, each case should be finished by *break/return*. If not, a note should be included to describe at which case it will stop. Within every `switch` block, a default statement must be present, even if it is empty.

## variable
- avoid using premitive data type if the language provide equivalent reference type. (Ex: for **Java** use `Integer` instead of ~~int~~)
- for Array, use `[]` after type, instead of variable name. (Ex: use `String[] names;` instead of ~~String names[]~~ )
- for `Long` value use `L` instead of ~~l~~, & for `Double` value use `D` instead of ~~d~~. use these literals when ever possible.
- if language supports, use `under_score` between big integer value for easy reading purpose.
    ```
    Integer money = 1_00_000;
    ```

## class
- for ***OOP*** languages, every file should contains `1` top level class.
- source file should contains followings **in order**
  1. License or copyright information, if present
  2. Package statement
  3. Import statements
  4. Exactly one top-level class
   
  **Exactly one blank line** separates each section that is present.

- inside the class, following conventions should be followed **in order**
  1. final variables
  2. static variables
  3. public variables (P.S: using getter/setter of a private veriable instead is recommendend)
  4. private variables
  5. static methods
  6. constructors (default constructor at the first)
  7. public methods & thier dependent private methods
  8. inner static class
  9. inner class

  **Exactly one blank line** separates each section that is present.

  **Exactly one blank line** before first section that is present.

- use different classes for configurations/utilities/constants based on their type. Avoid using one big file for all types. Ex ->
  > wallet related constant should go to WalletConstants.
   Account related constant should go to Account Constansts.

  > Dagger Library config should go to DaggerConfig.
   Swagger Library config should go to SwaggerConfig.

   > Validation related utilities should go to ValidationUtils.
    Convertion related utilities should go to ConvertionsUtils.
