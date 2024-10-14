---
# You can also start simply with 'default'
theme: excali-slide
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: A Different Kind of Serverless
info: |
  ## A Case Study for SQLite and Whisper.cpp running purely in the browser

  Using WASM, we can do so much more than we used to. We can run a full version of SQLite alongside Whisper.cpp without the need for any server-side logic.
# apply unocss classes to the current slide
# class: text-center
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# https://sli.dev/guide/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/guide/syntax#mdc-syntax
mdc: true
fonts:
  serif: Gochi Hand
---

# A Different Kind of Serverless

A Case Study for SQLite and Whisper.cpp running purely in the browser

---
src: ./pages/intro.md
---

---
src: ./pages/wasm-basics.md
---

---
src: ./pages/wasm-history.md
---

---
src: ./pages/wasm-support.md
---

---
src: ./pages/wasm-usage.md
---

---
src: ./pages/wasm-limitations.md
---

---
src: ./pages/wasm-security.md
---

---
src: ./pages/orderly.md
---

---
src: ./pages/sqlocal.md
---

---
src: ./pages/whisper.md
---

---
src: ./pages/hosting.md
---

---
src: ./pages/wrapping-up.md
---


<style>
.slidev-layout.cover h1, .slidev-layout.intro h1, .slidev-layout.center h1 {
    font-size: 3.75rem;
    line-height: 1;
    line-height: 5rem;
}
</style>