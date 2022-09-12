# Pousser le JS à ses limites : Coder sans jamais utiliser un seul chiffre ou une seule lettre

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

## Qu'en faire ? Sortir des nombres et des lettre comme on veut !
```js
const oneTwoThree = +((+!![] + []) + (!![]+!![]) + (!![]+!![]+!![]+[])) // 123
const s = ([] + ![])[+!![]+!![]+!![]]  // "s"
const o = ([] + {})[+!![]] // "o"
const sortString = ([] + ![])[+!![]+!![]+!![]] + ([] + {})[+!![]] + (!![]+[])[+!![]] + (!![]+[])[+[]] // "sort"
const constructorString = ([] + {})[+!![]+!![]+!![]+!![]+!![]] // "c"
  + ([] + {})[+!![]] // "o"
  + ([][+[]]+[])[+!![]] // "n"
  + ([] + ![])[+!![]+!![]+!![]] // "s"
  + (!![]+[])[+[]] // "t"
  + (!![]+[])[+!![]] // "r"
  + (!![]+[])[+!![]+!![]] // "u"
  + ([] + {})[+!![]+!![]+!![]+!![]+!![]] // "c"
  + (!![]+[])[+[]] // "t"
  + ([] + {})[+!![]] // "o"
  + (!![]+[])[+!![]] // "r"
const filter = (![]+[])[+[]] // "f"
  + ([][+[]]+[])[+!![]+!![]+!![]+!![]+!![]] // "i"
  + (![]+[])[+!![]+!![]] // "l"
  + (!![]+[])[+[]]// "t"
  + ([][+[]]+[])[+!![]+!![]+!![]]// "e"
  + (!![]+[])[+!![]]// "r"
const name = ([][+[]]+[])[+!![]] // "n"
  + (![]+[])[+!![]] // "a"
  + ((+[])[constructorString]+[])[+!![]+(+!![]+[])] // "m"
  + (!![]+[])[+!![]+!![]+!![]] // "e"
const toString = (!![]+[])[+[]]+({}+[])[+!![]]+([]+[])[constructorString][name] // "toString"
/* On peut même chercher n'importe quoi */
const e1000 = +!![]+(!![]+[])[+!![]+!![]+!![]]+(+!![]+(+![]+[])+(+![]+[])+(+![]+[])) // "1e1000"
const infinity = +e1000 // Infinity
```

## Faire appel à n'importe quel fonction et arriver à eval pour contourner les sécurités faibles et faire passer n'importe quoi sur un site
```js

const arrayFn = [][constructorString] // [Function: Array]
const filterFn = [][filter][constructorString] // [Function: Function]
const v = (+((+!![]+!![]+!![])+(+!![]+[])))[toString]((+!![]+!![]+!![])+(+!![]+!![]+[])) // "v" avec Number.toString() avec une base 32
const evalString = ([][+[]]+[])[+!![]+!![]+!![]] // "e"
  + v
  + (![]+[])[+!![]] // "a"
  + (![]+[])[+!![]+!![]] // "l"

const returnString = (!![]+[])[+!![]] // "r"
  + ([][+[]]+[])[+!![]+!![]+!![]] // "e"
  + (!![]+[])[+[]]// "t"
  + (!![]+[])[+!![]+!![]] // "u"
  + (!![]+[])[+!![]] // "r"
  + ([][+[]]+[])[+!![]] // "n"

const space = ({} + [])[+!![]+!![]+!![]+!![]+!![]+!![]+!![]] // " "

const returnEval = returnString + space + evalString // "return eval"

const evalFn = [][filter][constructorString](returnEval)() // [Function: eval]
```

### References :
[Hack Ebay](https://blog.checkpoint.com/2016/02/02/ebay-platform-exposed-to-severe-vulnerability/)

[Sources JSFuck](https://github.com/aemkei/jsfuck)

[Différentes méthodes d'accès aux élements](https://stackoverflow.com/questions/63673610/alternative-way-to-get-c-letter-in-jsfuck/63713987#63713987)

