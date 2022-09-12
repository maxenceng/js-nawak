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
