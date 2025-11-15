# ArchMorphSD  
*A ComfyUI workflow for architectural biomimetic morphogenesis*  
Fuyuki, C. (2025) — CAADRIA 2026 Submission

---

## Overview
ArchMorphSD is a custom ComfyUI workflow developed for the study  
**“Generative AI for Biomimetic Texture-Informed Morphogenesis”**,  
which investigates how parameter-efficient fine-tuning (PEFT) methods—LoRA and IP-Adapter—adapt Stable Diffusion XL to architectural design tasks.

This workflow operationalizes the experimental pipeline used in the paper:
- architectural-outline conditioning via **ControlNet**,  
- PEFT modules applied on top of SDXL,  
- hierarchical prompt/tok​en structures for morphogenetic translation,  
- consistent sampling & inference settings for reproducibility.

The workflow enables controlled comparison of:
1. **Baseline (Zero-shot)**  
2. **Shared LoRA (External module transfer)**  
3. **IP-Adapter (Image-referenced conditioning)**  
4. **Fine-tuned LoRA (Tafoni-specific internal adaptation)**  

This repository provides the workflow necessary to reproduce **architectural-scale generation experiments**, without exposing dataset-specific assets.

---

## Repository Contents
/ArchMorphSD_workflow.json # ComfyUI workflow file
/README.md # Documentation (this file)
/sample_outline/ # Example architectural outline silhouettes


> **Note:**  
> The biomimetic dataset (Tafoni textures) and the fine-tuned LoRA weights used in the study  
> **are not included** for ethical and research-integrity reasons.  
> These can be replaced with user-provided datasets.

---

## Requirements
- **ComfyUI** (latest stable build)  
- **Stable Diffusion XL base model**  
- **ControlNet conditioning model (lineart)**  
- Optional:  
  - LoRA loader (for Shared LoRA and Fine-tuned LoRA conditions)  
  - IP-Adapter (Standard version)

---

## How to Use
1. Install ComfyUI.  
2. Place the SDXL checkpoint and ControlNet model into the appropriate folders.  
3. Load `ArchMorphSD_workflow.json` inside ComfyUI.  
4. Replace:
   - `[USER_OUTLINE]` → with your own architectural silhouette  
   - `[USER_PROMPT]` → with one of the hierarchical prompts from the paper  
   - `[IPADAPTER_IMAGE]` → optional natural reference image  
5. Adjust:
   - LoRA strength  
   - IP-Adapter weight  
   - ControlNet influence schedule  
   according to experimental needs.

---

## Inference Settings (as used in the study)
- **Resolution:** 1024 × 784 px  
- **Sampling steps:** 30  
- **Sampler:** Euler ancestral  
- **Scheduler:** SGM Uniform  
- **CFG:** 3.0  
- **ControlNet strength:** 1.0 with 0.0→1.0 influence schedule

---

## Citation
If you use ArchMorphSD in academic work, please cite:

> **Fuyuki, C. (2025).** *ArchMorphSD (a custom ComfyUI workflow for architectural morphogenesis)* [Computer software]. GitHub.

This workflow is part of the methodology of the CAADRIA 2026 paper:

> **Fuyuki, C. & Nagao, S. (2025).** *Generative AI for Biomimetic Texture-Informed Morphogenesis:  
> A Comparative Study of PEFT Methods in Architectural Prototyping.*

---

## Notes on Reproducibility
The workflow is intentionally modular to allow:
- consistent cross-method comparison,  
- controlled PEFT parameter variation,  
- integration of hierarchical prompt tokens (1–9)  
as defined in the paper.

The **MorphEvalBench** evaluation toolkit used in Section 3.4 is available separately here:  
https://github.com/cfuyuki/MorphEvalBench

---

## License
This repository is released under an academic-use license.  
Commercial use requires prior permission from the author.

---

## Contact
For questions regarding reproduction or research usage:  
**cfuyuki@gmail.com**

