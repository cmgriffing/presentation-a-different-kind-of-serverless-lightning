---
transition: fade-out
layout: intro
---

# WASM Basics

---
transition: fade-out
layout: intro
---

# What is WASM?

- WebAssembly
- an open standard
- aims to support any language on any operating system

---
transition: fade-out
layout: center
---

## WAT!?

Textual Representation

```lisp
(module
  (func (export "main")
        (result i32)
    i32.const 42
    return))
```

---
transition: fade-out
layout: center
---

## WASM Binary

That same program:

```
00000000: 0061 736d
00000004: 0100 0000
00000008: 0105 0160
0000000c: 0001 7f03
00000010: 0201 0007
00000014: 0801 046d
00000018: 6169 6e00
0000001c: 000a 0701
00000020: 0500 412a
00000024: 0f0b
```

---
transition: fade-out
layout: center
---

## The first couple lines

```
; Wasm magic number (\0asm)
0000000: 0061 736d

; version
0000004: 0100 0000
```

---
transition: fade-out
layout: center
---

## WASM Modules

```
; section "type" (ID 1)
0000008: 01

; section size (5 bytes)
0000009: 05
```

<!--
In Wasm, modules are organized into sections (type section, function section, export section, etc.). The first byte of each section represents the section ID (1 for the section “type”) and section size (5 following bytes)
-->

---
transition: fade-out
layout: center
---

## Types

```
; number of types (1)
0000000a: 01

; func
0000000b: 60

; number of parameters (0)
0000000c: 00

; number of results (1)
0000000d: 01

; result type i32
0000000c: 7f
```

<!--
The type section contains function signatures. Our example has one function with zero parameters and one return result of type i32 (32-bit integer)
-->

---
transition: fade-out
layout: center
---

## The function signature

```
; section "function" (ID 3)
0000000f: 03

; section size (2 bytes)
00000010: 02

; number of functions (1)
00000011: 01

; index of the function (0)
00000012: 00
```

<!--
After five bytes (the section size) a new section begins. In our example, ID 3 stands for a function section. The section stores indexes of the function signature
-->

---
transition: fade-out
layout: center
---

## The export section

```
; section "export" (ID 7)
0000013: 07

; section size (8 bytes)
0000014: 08

; number of exports (1)
0000015: 01

; length of the export name (4 bytes)
0000016: 04

; export name ("main")
0000017: 6d61 696e

; export kind (0 for function)
000001b: 00

; index of the exported function (0)
000001c: 00
```

<!--
Next, the export section (ID 7) follows. The section defines the export name with the index to our function
-->

---
transition: fade-out
layout: center
---

## The function section

```
; section "code" (ID 10)
000001d: 0a

; section size (7 bytes)
000001e: 07

; number of functions (1)
000001f: 01

; function body size (5 bytes)
0000020: 05

; number of local declarations (0)
0000021: 00
```

<!--
The next section is a code section (ID 10) that represents the actual code of the function
-->

---
transition: fade-out
layout: center
---

## The logic section

```
; instruction i32.const
0000022: 41

; i32 literal (42)
0000023: 2a

; return
0000024: 0f
```

<!--
In our example, a numeric constant 42 (the answer) is pushed onto the stack and returned as the result
-->

---
transition: fade-out
layout: center
---

## The end

```
; end of the function code
0000025: 0b
```

<!--
The very last byte is simply the end of the function code
-->

---
transition: fade-out
layout: center
---

## Pseudocode

The whole program as pseudocode would read as follows

```
Wasm magic number
version

section "type"
  func
  result type: i32

section "function"
  index of the function: 0

section "export"
  export name: "main"
  export kind: function
  index of the function: 0

section "code"
  i32.const
  i32 literal: 42
  return
```

---
transition: slide-left
layout: center
---

## Binary Specification

To learn more about the binary format, check the spec:

https://webassembly.github.io/spec/core/binary/
