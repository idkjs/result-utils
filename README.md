[ResultUtils.re](https://github.com/adnelson/requery/blob/master/src/utils/ResultUtils.re)

 Apply a function, returning `Ok(result)`. If an exception is
 thrown by the function, return `Error(exception)`. This can be
 used to build an error boundary around code which might fail.

```reason
exception BadNumber(int)
let badFunction = n => n == 3 ? raise(BadNumber(n)) : n + 1
expect(12->catchExn(badFunction)).toEqual(Ok(13))
expect(3->catchExn(badFunction)).toEqual(Error(BadNumber(3)))
```
