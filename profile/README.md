<p align="center"><img src="banner.png" alt="GEHIRNS · Capability per GiB" width="100%"></p>

<p align="center">
  <a href="https://huggingface.co/GEHIRNS"><img alt="Hugging Face" src="https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-GEHIRNS-FF3B30?style=flat-square"></a>
  <a href="https://gehirns.pages.dev/"><img alt="Website" src="https://img.shields.io/badge/Website-gehirns.pages.dev-0A0A0B?style=flat-square"></a>
  <a href="https://doi.org/10.5281/zenodo.23630199"><img alt="Paper" src="https://img.shields.io/badge/Paper-Where%20the%20Bits%20Go-0A0A0B?style=flat-square"></a>
</p>

**Capability per GiB.** We study how much a language model can do inside a single 12 GB consumer GPU. Every model is scored on a fixed 2,313-task benchmark (12 suites: coding, math, science and knowledge, commonsense, tool calls) with thinking on, and the score is set against the memory the model actually occupies at a 32K context. All numbers come from our own runs on one RTX 5070.

## Latest releases

| Model | Base | Memory at 32K | Score | Density | What it is |
|---|---|---|---|---|---|
| [**magi-1.2-4B**](https://huggingface.co/GEHIRNS/magi-1.2-4B) | Qwen3.5-4B | 2.55 GiB | 81.90% | **0.968** | magi-1.1-4B's weights with bits fitted to the 4B by measurement: 64 MiB smaller at the same score. It thinks 11% more |
| [**magi-1.1-4B**](https://huggingface.co/GEHIRNS/magi-1.1-4B) | Qwen3.5-4B | 2.61 GiB | 81.72% | 0.939 | magi-1.0-4B plus a LoRA that teaches it to finish its thinking. **Recommended 4B** |
| [**magi-1.2-2B**](https://huggingface.co/GEHIRNS/magi-1.2-2B) | Qwen3.5-2B | 1.23 GiB | 67.09% | **1.305** | One round of training against repetition loops, with bits fitted to the 2B. **Recommended 2B** |
| [magi-1.1-2B](https://huggingface.co/GEHIRNS/magi-1.1-2B) | Qwen3.5-2B | 1.36 GiB | 66.06% | 1.149 | The think-less LoRA on Qwen3.5-2B with the magi-1.0 recipe |
| [magi-1.0-2B](https://huggingface.co/GEHIRNS/magi-1.0-2B) | Qwen3.5-2B | 1.36 GiB | 63.48% | 1.071 | The magi-1.0 recipe on Qwen3.5-2B, no training |

How these were measured:
- **Runtime:** llama.cpp with a q4_0 KV cache; memory is `llama-fit-params` at a 32K context.
- **Density:** ρ = −log₂(1 − score) per GiB, that is, how many times the error rate halves per gibibyte.

The training-free first release, [**magi-1.0-4B**](https://huggingface.co/GEHIRNS/magi-1.0-4B) (magi-1.0 in the paper), keeps 96% of Qwen3.5-4B's score in 30% of the GPU memory with an 8-bit KV cache.

## Recipe and paper

- **[GEHIRNS/magi](https://github.com/GEHIRNS/magi):** the build recipe, the importance matrix, and the data behind every table and figure in the paper.
- **Paper:** Eason Sun, [*Where the Bits Go: Sensitivity-Allocated Mixed Precision for a 4B Reasoning Model on a 12 GB Consumer GPU*](https://doi.org/10.5281/zenodo.23630199), Zenodo, 2026. DOI: 10.5281/zenodo.23630199.
- **Collections:** [MAGI 1.2](https://huggingface.co/collections/GEHIRNS/magi-12-6aef8bdfebb37eb4c9c074d2) · [MAGI 1.1](https://huggingface.co/collections/GEHIRNS/magi-11-6aee2751dc26997eb5d16e2c) · [MAGI 1.0](https://huggingface.co/collections/GEHIRNS/magi-10-6adaeeaefd1d999584a8a12d) · [MAGI experimental](https://huggingface.co/collections/GEHIRNS/magi-experimental-6ad6a94511ffd4dabaa7b24a)
