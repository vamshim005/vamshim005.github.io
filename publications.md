---
layout: page
title: My Explorations
subtitle: Notes, diagrams, and personal takeaways from my learning journey
---

Welcome to **My Explorations**! This is where I share:

1. Summarized notes from my lectures
2. Diagrams or explanations of difficult concepts
3. My personal takeaways or analogies that helped me understand things better

---

## 🖼️ Image-Augmentation Playbook

*Author: Vamshi Maya*  
*Course: Deep Learning Explorations*

### Introduction
Image augmentation is a set of techniques used to artificially expand the size and diversity of a dataset by creating modified versions of images. This is especially useful in deep learning, where more data can lead to better model generalization. In this playbook, we'll walk through a hands-on, code-driven approach to image augmentation using PyTorch and TorchVision, including advanced methods like CutOut, MixUp, CutMix, AutoAugment, and RandAugment.

---

### How to Reproduce This Playbook

**Phase 1 — Generate the notebook file**
1. Create a new file: `augmentation_playbook.py`
2. Use the following authoring prompt in Cursor chat:

> Create a Jupyter‑style Python script called augmentation_playbook.py that contains the following cells:
> - Cell 0 (markdown): Title '🖼️ Image‑Augmentation Playbook', author line, course info.
> - Cell 1 (code): install & import torch, torchvision, imageio (use pip install -q).
> - Cell 2 (code): load 8 sample CIFAR‑10 images into a tensor imgs.
> - Cell 3 (markdown): subsection header 'Basic Transforms Gallery'.
> - Cell 4 (code): define basic transform pipeline, loop 15 iterations, write basic.gif with imageio.mimsave, and also show a single frame.
> - Cell 5 (markdown): header 'CutOut · MixUp · CutMix'.
> - Cell 6 (code): helper functions for cutout, mixup, cutmix; loop to export cutout.gif, mixup.gif, cutmix.gif plus static previews.
> - Cell 7 (markdown): header 'AutoAugment & RandAugment'.
> - Cell 8 (code): apply AutoAugment & RandAugment, preview grids.
> - Cell 9 (markdown): short note explaining how to download the GIFs.
> Keep every code cell wrapped in # %% markers, and make sure the script runs top‑to‑bottom without missing imports.

**Phase 2 — Install dependencies & run cells**
- In the terminal, run: `pip install torch==2.1 torchvision==0.16 imageio==2.34 -q`
- Open `augmentation_playbook.py` and run all cells (Cmd/Ctrl+Shift+Enter)
- You'll see PNG previews and GIFs (basic.gif, cutout.gif, etc.) in your file explorer.

**Phase 3 — Export & embed in your portfolio**
- Download the GIFs and move them to your website's `/assets/` folder.
- Use Cursor to generate HTML `<figure>` tags to embed `basic.gif` and `cutmix.gif` with captions, using the relative path `/assets/`.

---

### Example Embeds

<figure>
  <img src="/assets/basic.gif" alt="Basic Transforms Gallery">
  <figcaption>Basic Transforms Gallery: See how simple augmentations can diversify your dataset.</figcaption>
</figure>

<figure>
  <img src="/assets/cutmix.gif" alt="CutMix Augmentation">
  <figcaption>CutMix: A powerful augmentation that mixes images and labels for robust training.</figcaption>
</figure>

---

### Further Exploration
- Refactor cutout, mixup, cutmix into a single transform class with a mode switch for a cleaner, reusable API.
- Create a `requirements.txt` from the imports in this file.
- Write a README explaining how to run `augmentation_playbook.py` step-by-step.
- Plot learning-rate and momentum curves for a One-Cycle schedule in a new file `one_cycle_demo.py`.

#### References
- [TorchVision "Illustration of Transforms" notebook](https://pytorch.org/vision/stable/auto_examples/plot_transforms_gallery.html)
- [TorchVision "How to use CutMix & MixUp" example](https://pytorch.org/vision/stable/auto_examples/misc/plot_cutmix_mixup.html)
- [Cursor Jupyter‑style workflow guide](https://www.cursor.so/docs/jupyter-style-workflow)
- [Cursor feature list](https://www.cursor.so/docs/features)

---

## Topic-Based Image Caption Generation

- **Conference:** Arabian Journal for Science and Engineering (AJSE)
- **Publication Date:** 15th November 2019
- **Authors**: Sandeep Kumar Dash, Shantanu Acharya, Partha Pakray, Ranjita Das and Alexander Gelbukh
- **Link:** https://link.springer.com/article/10.1007/s13369-019-04262-2

<br/>

## Every Child Should Have Parents: A Taxonomy Refinement Algorithm Based on Hyperbolic Term Embeddings

- **Conference:** Association for Computational Linguistics (ACL)
- **Publication Date:** 5th June 2019
- **Authors**: Rami Aly, _Shantanu Acharya_, Alexander Ossa, Arne Köhn, Chris Biemann and Alexander Panchenko
- **Link:** https://arxiv.org/abs/1906.02002

---
