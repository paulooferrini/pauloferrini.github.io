# Paulo Ferrini Artstyle LoRA

<p align="center">
<img src="images/hero.jpg" width="100%">
</p>

This project documents the development of a custom Stable Diffusion 1.5 LoRA trained exclusively on the artwork of Paulo Ferrini.

The objective was to create a lightweight adapter capable of reproducing the characteristic visual language found throughout the artist's portfolio while preserving the flexibility of the underlying Stable Diffusion model. Instead of learning individual artworks, the LoRA was trained to capture recurring stylistic elements including facial structure, composition, lighting, surface appearance and color relationships.

The repository contains the complete training workflow, including dataset preparation, training notebooks, validation experiments and inference examples. Every stage of the process is documented, from the initial dataset to the final LoRA weights.

---

# Abstract

Large text describing the project.

Recent advances in parameter-efficient fine-tuning have made it possible to adapt large diffusion models using only a comparatively small number of training images. LoRA (Low-Rank Adaptation) has become one of the most practical techniques for teaching Stable Diffusion highly specific concepts without modifying the original model.

This project explores the creation of an artistic LoRA trained on a carefully curated dataset of portrait artwork by Paulo Ferrini. Rather than reproducing existing images, the goal is to transfer the visual characteristics of the style into a reusable model capable of generating new compositions while maintaining a coherent artistic identity.

The resulting model produces portraits that preserve the distinctive atmosphere of the original work while remaining compatible with ordinary Stable Diffusion prompting workflows.

---

# Dataset

<p align="center">
<img src="images/download.png" width="90%">
</p>

The training dataset consists of carefully selected artworks representing the visual language developed throughout Paulo Ferrini's portrait work.

Instead of maximizing dataset size, emphasis was placed on stylistic consistency. The selected images share similar composition, lighting, facial proportions and rendering quality while still providing enough variation for the model to generalize beyond the original training examples.

Before training, all images were prepared for Stable Diffusion 1.5 by applying a consistent preprocessing workflow. Maintaining a clean and coherent dataset proved significantly more important than increasing the overall number of training images.

---

# Training Pipeline

The repository contains two Jupyter notebooks covering the complete workflow.

The first notebook focuses on preparing the dataset and creating a structured training environment. Images are collected, verified and prepared for training before the LoRA process begins.

The second notebook performs the complete LoRA training using the Hugging Face Diffusers training scripts. It includes configuration of the training environment, automatic validation during training, generation of comparison images and export of the final LoRA weights.

The overall workflow can be summarized as

```

Dataset

↓

Preprocessing

↓

Training Configuration

↓

Stable Diffusion 1.5

↓

LoRA Fine-Tuning

↓

Validation

↓

Inference

```

The notebooks were designed for Google Colab and provide a complete end-to-end training pipeline that can be reproduced without additional modifications.

---

# Training Configuration

The model was trained using Stable Diffusion 1.5 as the base checkpoint together with the Hugging Face Diffusers training framework.

The notebook provides configurable parameters including learning rate, batch size, number of training steps, image resolution, validation frequency and output management while keeping the overall workflow intentionally simple.

During development multiple configurations were evaluated until a balance between style fidelity and prompt flexibility was achieved.

---

# Validation

Validation images were generated automatically during training in order to monitor the evolution of the learned style.

Rather than relying exclusively on loss values, visual inspection proved to be the most effective method for evaluating stylistic convergence. Intermediate generations allowed training progress to be monitored continuously and made it possible to identify an appropriate stopping point before overfitting occurred.

<p align="center">
<img src="images/validation_grid.jpg" width="100%">
</p>

---

# LoRA Strength

One of the most important parameters during inference is the LoRA weight.

Lower values preserve more of the original Stable Diffusion model while higher values increase the influence of the learned style. The comparison below illustrates how different strengths affect the generated image while keeping prompt and random seed identical.

<p align="center">
<img src="images/strength_comparison.jpg" width="100%">
</p>

For most portrait generations the optimal balance was found around the default strength, providing a strong stylistic influence while preserving prompt responsiveness.

---

# Results

The trained LoRA successfully reproduces many of the visual characteristics present throughout the training dataset.

Across different prompts the model consistently generates portraits with recognizable facial structure, controlled lighting, painterly surface qualities and the overall atmosphere associated with the original artwork.

The examples below demonstrate the versatility of the trained model across different subjects and compositions.

<p align="center">
<img src="images/gallery.jpg" width="100%">
</p>

---

# Additional Experiments

Beyond standard portrait generation, additional experiments were performed to evaluate how robustly the learned style transfers across different prompts and visual scenarios.

These experiments include comparisons using different inference settings, alternative prompts and variations of the LoRA strength while maintaining identical random seeds.

The results demonstrate that the learned representation remains stable across a broad range of generations without losing its characteristic artistic appearance.

<p align="center">
<img src="images/experiments.jpg" width="100%">
</p>

---

# Repository Structure

```
.
├── notebooks
│   ├── SD15_LoRA_Trainer.ipynb
│   └── Dataset_Preparation.ipynb
│
├── images
│   ├── dataset.png
│   ├── gallery.jpg
│   ├── strength_comparison.jpg
│   └── validation_grid.jpg
│
├── README.md
└── LICENSE
```

---

# Acknowledgements

This project is based on the Stable Diffusion ecosystem and makes use of the Hugging Face Diffusers training framework together with the LoRA fine-tuning approach.

The presentation style of this documentation is inspired by the original DreamBooth project while focusing specifically on documenting an artistic LoRA training workflow.

---

# About

**Paulo Ferrini**

Website

https://www.pauloferrini.com

Instagram

https://www.instagram.com/pauliferrino
