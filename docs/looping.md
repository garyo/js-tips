# Looping in Javascript/Typescript

JS has way too many ways to iterate and loop over objects, arrays, and iterables. 
This page tries to collect them and make some sense of them.

| Construct | Effect on array | Effect on object | Effect on iterable (Map, Set) |
|-----------|-----------------|------------------|--------------------|
| `for (let i=0; i<obj.length; i++)` | Iterates over indices | N/A | N/A |
| `for x in obj` | Iterates over indices *and* custom props (incl prototype props), random order | Iterates over enumerable obj props (incl prototype props) | Iterates over `Map` keys; doesn't work for `Set` |
| `for x of obj` | Iterates over values (in order) | N/A | Iterates over values (or `Set` elements) |
| `obj.forEach(x => ...)` | Iterates over values (also passes index & array to callback)| N/A (but can do `Object.keys(obj).forEach(...)`) | Map: iterates over values + keys |

Notes:
* `arr.forEach()` does *not* work properly with `await` calls in the callback, but the others support `await` in the body
* `arr.forEach()` has no way to break out from the middle of the loop; the others support `break` and `continue`
