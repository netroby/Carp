# Todo

## Critical Bugs
* Ensure 'Array.pop-back' is memory safe and shrinks the array properly.
* Can't define globals of with heap allocated types (String, structs, etc.)
* Arrays can contain references, this will lead to dangling pointers.
* Type declarations inside other modules can't be unqualified even though the outer module is 'use':d
* A program using references to arrays but nothing else produces invalid typedefs (see sum-functions for adding the elements of an array)

## Ugliness
* Just entering '=' at the REPL leads to strange type error.
* The 'range' function is fully generic (for all 'a') but only compiles when 'a' is numeric type
* Remove unnecessary Array-functions and rewrite them in Carp
* Create a proper .c file for the core library C functions
* No need to set unique identifiers on XObj:s in Parse.hs?

## Big Language Features
* Allow evaluation of dynamic functions in the REPL and give access to the Commands from dynamic code
* Platform defines and optional compilation
* Generic data types (apart from Array, which already is)
* Tagged unions (also known as "sum types" or "enums")
* Lambdas (anonymous functions)
* Doc strings

## Smaller Language Features ("niceties")
* All the math functions!
* Good string functions
* Being able to use 'the' in function parameter declarations, i.e. (defn f [(the Int x)] x) to enforce a type
* Allow use of 'the' as a wrapper when defining a variable or function, i.e. (the (Fn [Int] Int) (defn [x] x))
* Quasiquote
* Splicing in macros
* Pattern matching on arguments in macros?

## Language Design Considerations
* What's the correct type of the variable in a set!-form, i.e. (set! &x value) or (set! x value)
* Is some kind of interface/typeclass construct worthwhile?
* How should passing primitive types (that do not care about being referenced) as ref:ed parameters be handled?
* How to handle heap allocated values? Box type with reference count?
* Fixed-size stack allocated arrays would be useful (also as members of structs)
* Look over how many times the function 'annotateOne' in Infer.hs actually needs to be applied to a form
* Macros in modules must be qualified right now, is that a good long-term solution?

## Code generation
* LLVM backend
* Emit #LINE macros in the generated C code

## Tooling
* Warning when changing the type of a function (can create bugs by overriding earlier declarations with the same name)
* Enable printing of typed AST:s at the REPL to help debug unresolved type variables etc.
* Proper error handling when defining invalid struct types (right now it crashes)
* Stop evalutaion of forms after errors to avoid "Trying to refer to undefined symbol" error
* Built in REPL history (without using rlwrap)
* Preserve whitespace to allow saving forms back to disk
* Refactorings at the REPL. Rename, extract function, add/remove parameter?
* Hide instances of templates/generic functions when printing the environment (by default, allow it as a setting)
* Somehow make it possible to enter ":t foo" at the REPL (can't be done now because each atom is evaluated separately)
* Rename type variables from t0, t1, t2 to a, b, c, etc.
