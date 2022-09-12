## La base : le cast d'un type vers un autre
```js
const zero = +[] // 0
const falsy = ![] // false
const truthy = !![] // true
const one = +!![] // 1
const oneString = +!![] + [] // "1"
const nan = +{} // NaN
const nanString = +{} + [] // "NaN"
const objectObject = {} + [] // "[object Object]"
const undef = [][+[]] // undefined
const undefString = [][+[]]+[] // "undefined"
```
