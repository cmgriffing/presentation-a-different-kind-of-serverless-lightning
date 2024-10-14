---
transition: fade-out
layout: intro
---

# WASM History

---
transition: fade-out
layout: intro
---

## WASM Timeline

- 2011: Emscripten library started
- 2011: Google Native Client (NaCL) started
- 2013: asm.js introduced
- 2015: WASM first announced
- 2017: NaCL deprecated in favor of WASM
- 2017: Broad browser support
- 2019: WebAssembly System Interface (WASI) announced

---
transition: fade-out
layout: intro
---

## asm.js

- a precursor to WASM
- a strict subset of JavaScript

---
transition: fade-out
---

## asm.js: Example

```js
function asmModule(stdlib, foreign, heap) {
  "use asm";

  // shared variables
  var sin = stdlib.Math.sin;
  var heap32 = new stdlib.Float32Array(heap);
  var size = 0;

  // function declarations
  function complexCalculation(size, factor) {
    size = size|0;
    factor = +factor
    ...
  }

  // export function
  return { complexCalculation: complexCalculation }
}
```

<!--
- "use asm"
- size|0 - int - 32-bit integer
- +factor - double - 64 bit floating point type

Syntax not allowed
- for-in (Objects and strings are not allowed)
- try-catch-finally
- Change the scope with {}
- Any ES6 syntax
-->


---
transition: slide-left
---

## The Birth and Death of JavaScript (2014)

https://www.destroyallsoftware.com/talks/the-birth-and-death-of-javascript

![](/images/birth-and-death-of-js.png)
