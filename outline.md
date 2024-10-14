# A Different Kind of Serverless

- Introduction

- What is WASM?

- History of WASM

  - asm.js
  - The Birth and Death of JavaScript

- Languages that Support WASM

  - Compilation
    - Rust
    - C#
    - Go
    - more
  - Consuming
    - browser/JS
    - Serverless runtimes (CF Workers)

- Popular usage of WASM

  - Figma
  - Extism

- WASM Limitations

  - No DOM access
  - RAM usage
  - Must run in Web Workers
    - Message Passing vs SharedArrayBuffers
  - Limited System Access
    - WASI to help fix that

- WASM Security Concerns

  - Obfuscation
  - Circumvent browser mitigations for Spectre and Meltdown

- My App: Orderly

  - Goals/Description
  - Demo of the app
  - Architecture
    - React SPA
    - Mantine for UI Components
    - SQLocal for SQlite in the browser
    - Whisper.cpp for Speech-to-text
    - other stuff
      - jotai for state management
      - pdfjs for pdf export
      - dayjs for dates
      - react-arborist for tree logic
        - features (drag and drop, rendering)
        - flaws (absolute positioning)
      - case for converting between different text cases (camelCase, kebab-case, etc)

- SQLocal

  - SQLite in the browser
  - OPFS
  - ORMs: a hybrid approach
    - Kysely for migrations
    - Drizzle for queries and Relations
  - Considerations
    - State and Optimistic UI

- Whisper.cpp

  - Demo of Whisper.cpp from their repo
  - Wiring it up
    - Module Bindings
    - Custom Events

- Hosting

  - Failure: Github Pages
    - SharedArrayBuffer support
      - https://github.com/gzuidhof/coi-serviceworker
      - inconsistent due to loading and order of operations
  - Success: Render
    - Allows adding headers via config

- Wrapping Up
