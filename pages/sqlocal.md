---
transition: fade-out
layout: intro
---

# SQLocal

---
transition: fade-out
layout: two-cols
---

## SQLocal: Basics

https://sqlocal.dallashoffman.com/

- Any SQLite Query
- Threaded
  - won't block the main thread
- Persisted via OPFS
  - faster than indexedDB

::right::

<img src="/images/sqlocal.png" class="w-full h-auto m-0 mt-32">


---
transition: fade-out
layout: intro
---

## OPFS

- Part of File System Access API
- Basic support in all major browsers since late 2021
- Not the actual OS File System
- Not meant to be visible to users
- No permission prompts and security checks
- Browser storage quota restrictions
  - same quota as IndexedDB
- usable from main thread or web worker
  - web workers are allowed to use synchronous operations


---
transition: fade-out
layout: two-cols-header
---

## ORMs

::left::

- Kysely for migrations
  - Used for: creating tables and indexes, and initial db seeding
  - More of a query builder
  - Made by creator of objection.js
  - "No magic, just SQL"
  - No relations

::right::

- Drizzle for queries
  - Full ORM
  - Migrations-run via CLI tool instead of in the browser
  - Type-safe
  - Relation-capable

::bottom::

<div class="h-8 mt-8 mb-8"></div>

---
transition: slide-left
layout: intro
---

## Considerations

- appReady
  - migrations need to run before we can query things and set up jotai
- Suspense needed
  - async reading and writing can cause too many loader moments
  - lots of startTransition
- Optimistic UI and debouncing still needed
