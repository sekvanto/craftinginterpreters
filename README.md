A place for the code from the Crafting Interpreters book (https://craftinginterpreters.com/contents.html)

# jlox
Minor extensions:
* Supports C-style `/*...*/` block comments (not nested)
* Comma expressions
* C-style ternary operator `?:`
* Supports concatenation of strings with other types via addition `+`
* Detects and reports a runtime error when division by zero occurs
* Supports `break` statement inside loops

# clox
Minor extensions:
* Arity checking for native functions
* Extended native function system for reporting runtime errors. Example:
```c
static bool callValue(Value callee, int argCount) {
    if (IS_OBJ(callee)) {
        switch (OBJ_TYPE(callee)) {
            case OBJ_NATIVE: {
                if (AS_NATIVE_ARITY(callee) != argCount) {
                    runtimeError(false, "Expected %d arguments but got %d.", AS_NATIVE_ARITY(callee), argCount);
                    return false;
                }
                /*...*/
                return true;
            }
            /*...*/
        }
    }
}
```
