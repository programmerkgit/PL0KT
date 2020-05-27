# PL0KT
My first language written by kotlin.

## BNF
```kotlin
/**
 * program := block .
 * block := [constDecl|varDecl|funcDecl] statement
 * constDecl := const identifier = number{, identifier = number } ;
 * varDecl := var identifier{, identifier};
 * funcDecl := function ident ([ident{, ident}]) {block};
 * statement := identifier = expression
 *              | begin statement{; statement} end
 *              | if ( condition ) { statement }
 *              | while (condition) do { statement }
 *              | return expression
 *              | write expression
 *              | writeln
 * condition := expression =|<>|<|>|<=|>= expression
 * expression := [+|-] term {+ term}
 * term := factor {(*|/) factor }
 * factor := ident
 *          | number
 *          | ident ([expression{, expression}])
 *          | ( expression )
 *
 */
```
## Example

```kotlin
        val l = Lexer(
            """
function fibonacci(n) { 
    if(n == 0) {
        return 0
    }
    if (n == 1) {
        return 1 
    }
    return fibonacci(n -1) + fibonacci(n - 2)
}
var i
const n = 3
i = 0
while(i < 10) do { 
    write fibonacci(i) 
    writeln
    i = i + 1 
}
        """.trimIndent()
        )
        val p = Parser(l)
        p.parse()
        Executor(p.codes).execute()
```

Output

```
0
1
1
2
3
5
8
13
21
34
```