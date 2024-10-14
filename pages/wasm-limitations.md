---
transition: fade-out
layout: intro
---

# Limitations and Concerns

---
transition: fade-out
layout: intro
---

## WASM Limitations

- In the Browser
  - No DOM access
  - RAM Usage
  - Must run in Web Workers
- Outside the Browser
  - Limited System Access (solved by WASI)

---
transition: slide-left
layout: intro
---

## Security Concerns

- Obfuscation
  - Binary instead of JavaScript
- SharedArrayBuffers
  - Spectre/Meltdown
  - Secure context required
  - CORP required (Cross Origin Resource Policy)
