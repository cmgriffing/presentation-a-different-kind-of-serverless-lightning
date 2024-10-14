---
transition: fade-out
layout: intro
---

# Whisper.cpp

---
transition: fade-out
layout: intro
---

## Whisper

Robust Speech Recognition via Large-Scale Weak Supervision

https://github.com/openai/whisper

- Open Source
  - MIT License
- by OpenAI
- Written in Python
- CLI or Python

---
transition: fade-out
layout: intro
---

## Whisper Models

|  Size  | Parameters | English-only model | Multilingual model | Required VRAM | Relative speed |
|:------:|:----------:|:------------------:|:------------------:|:-------------:|:--------------:|
|  tiny  |    39 M    |     `tiny.en`      |       `tiny`       |     ~1 GB     |      ~32x      |
|  base  |    74 M    |     `base.en`      |       `base`       |     ~1 GB     |      ~16x      |
| small  |   244 M    |     `small.en`     |      `small`       |     ~2 GB     |      ~6x       |
| medium |   769 M    |    `medium.en`     |      `medium`      |     ~5 GB     |      ~2x       |
| large  |   1550 M   |        N/A         |      `large`       |    ~10 GB     |       1x       |

<!-- The .en models for English-only applications tend to perform better, especially for the tiny.en and base.en models. We observed that the difference becomes less significant for the small.en and medium.en models. -->

---
transition: fade-out
layout: intro
---

## Whisper.cpp

- Plain C/C++ implementation without dependencies
- Apple Silicon first-class citizen - optimized via ARM NEON, Accelerate framework, Metal and Core ML
- AVX intrinsics support for x86 architectures
- Zero memory allocations at runtime
- Support for CPU-only inference
- Efficient GPU support for NVIDIA
- C-style API

---
transition: slide-left
layout: intro
---

## Wiring it up

In index.html

```html
<script>
  let recentResult = [];
  const bracketRegex = new RegExp("^\\[.*?\\]");
  const blankAudioRegex = new RegExp("\\[BLANK_AUDIO\\]$");
  const whisperTimingRegex = new RegExp("^whisper_print_timings: ");

  window.Module = {
    print: function (message) {
      if (bracketRegex.test(message) && !blankAudioRegex.test(message)) {
        recentResult.push(message.replace(bracketRegex, "").trim());
      }
    },
    printErr: function (message) {
      if (whisperTimingRegex.test(message) && recentResult.length > 0) {
        window.dispatchEvent(
          new CustomEvent("whisperResult", {
            detail: recentResult.join(" "),
          })
        );
        recentResult = [];
      }
    },
  };
</script>
```
