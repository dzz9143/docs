## Has
Check if `key` is a direct property of `object`(direct means not in the prototype chain)

use `object.prototype.hasOwnProperty` for direct properties

use `value in object` for all properties

## double equal to null
the only values that null is loosely equal to are `undefined` and itself

use `object != null` to match both not equal to `null` and `undefined`

## Get
the whole algorithm is like: 

```javascript

function get(object, pathString) {
    const componentArray = getComponent(pathString);
    let index = 0;
    const len = componentArray.length;
    let o = object;

    while(o != null && index < len) {
        o = o[componentArrary[index++]];
    }

    return (index && index == length) ? object : undefined
}
```
