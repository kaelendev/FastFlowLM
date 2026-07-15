---
layout: docs
title: MiniCPM
nav_order: 8
parent: Models
---

## 🧩 Model Card: [MiniCPM5-8B](https://huggingface.co/OpenBMB)

- **Type:** Text-to-Text
- **Think:** No
- **Tool Calling Support:** Template-dependent (fallback to plain chat output if tool-call markers are not emitted)
- **Base Model:** OpenBMB/MiniCPM5 family
- **Quantization:** Q4_1 (FastFlowLM NPU package)
- **Max Context Length:** 32k tokens  
- **Default Context Length:** 32k tokens ([change default](https://fastflowlm.com/docs/instructions/cli/#-change-default-context-length-max))  
- **[Set Context Length at Launch](https://fastflowlm.com/docs/instructions/cli/#-set-context-length-at-launch)**

▶️ Run with FastFlowLM in PowerShell:  

```shell
flm run minicpm5:8b
```

---

## Notes

- MiniCPM5 is integrated through FastFlowLM's standard LLM route:
  - model family detection in `all_models.hpp`,
  - model registry/manifest in `src/model_list.json`,
  - tokenizer + chat template loading via `AutoModel::_shared_setup_tokenizer`.
- The current implementation uses the existing LLaMA-compatible NPU execution path.
- If a MiniCPM5 package diverges from the expected tensor/layout contract, load may fail; in that case use an FLM-converted MiniCPM5 package.

