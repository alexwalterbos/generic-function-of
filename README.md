# generic-function-of
Reproduction of bug in babel-eslint

Babel-eslint parses a generic function just fine:
```JS
function someGenericFunction<R>(args: R): Array<R> {
  return [args];
}
```

It fails to parse that same function when it is named `of`, however:
```JS
function of<R>(args: R): Array<R> {
  return [args];
}
```
```
/path/to/index.js
  5:12  error  Parsing error: Unexpected token, expected "("

  3 | }
  4 | 
> 5 | function of<R>(args: R): Array<R> {
    |            ^
  6 | 	return [args];
  7 | }
  8 | 

✖ 1 problem (1 error, 0 warnings)

error Command failed with exit code 1.
```
