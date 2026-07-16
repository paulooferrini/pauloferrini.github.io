# Paulo Ferrini Artstyle LoRA

*A Stable Diffusion 1.5 LoRA trained on my personal 3D art style.*

<p align="center">
<img src="https://github.com/user-attachments/assets/95d1441d-f9d7-4b17-a104-13fbaec53f9f"  width="100%"/>
</p>


This project documents the development of a custom Stable Diffusion 1.5 LoRA trained exclusively on my personal artwork. The objective was to investigate whether a relatively small and carefully curated dataset could successfully transfer the distinctive visual characteristics of my art style into a diffusion model.

Rather than reproducing existing artworks, the LoRA was designed to learn the underlying visual language of my work. The resulting model can be used both as a creative tool for experimentation and as a starting point for generating new imagery inspired by my artistic style.

This documentation presents the complete project, including the dataset, evaluation and the custom inference interface developed alongside the LoRA.

---

# Artistic Background

A lot of my artwork has explored themes inspired by body horror, science fiction and dark fantasy. Much of this inspiration comes from practical effects and creature design found in films of the 1980s, particularly works such as The Thing, where physical transformation and organic deformation become part of the visual storytelling.

While the subjects of my images vary, they are connected through a consistent visual language. The artworks combine digitally sculpted faces with physically based materials and cinematic lighting, creating images that oscillate between realistic portraiture and unsettling human deformation.

The motivation behind this project was to investigate whether these visual characteristics could be learned as a coherent artistic style rather than as individual images. Instead of creating a character LoRA or teaching a specific subject, the objective was to capture the overall atmosphere, material qualities and aesthetic identity of my work.

---

# Dataset


The training dataset consists of 33 original artworks created entirely by myself. Every image was produced digitally using Blender together with Substance Painter and rendered with either Cycles or Octane Render.

Instead of assembling a large and diverse dataset, I deliberately selected a relatively small number of images that represent the core visual language of my work. Each image was manually chosen to maintain stylistic consistency across the dataset while still covering different faces, materials, compositions and lighting situations.

All images were prepared at a resolution of 512 × 512 pixels, providing a consistent foundation for training the LoRA.

<p align="center">
<img src="https://github.com/user-attachments/assets/a10ade03-8604-443a-b0ec-cda9a7c9bd8d"  width="100%"/>

</p>

---

# Training 

The LoRA was trained on Stable Diffusion 1.5 using the curated dataset described above. The primary objective was not to reproduce individual artworks, but to capture the overall artistic language shared across the dataset.

Throughout development, validation images were generated repeatedly using identical prompts and fixed random seeds. Additional generations with varying seeds were used to evaluate how consistently the learned style transferred across different subjects.

Rather than relying exclusively on quantitative metrics, the training process was primarily evaluated through visual comparison. This made it possible to monitor the evolution of the learned style and identify when the LoRA began to consistently reproduce the characteristic appearance of my artwork.


*Trigger Phrase : style of pauloferrini
---

# LoRA Strength

One of the most noticeable parameters during inference is the LoRA strength. Lower values preserve more of the original Stable Diffusion model, resulting in only subtle stylistic influence. As the strength increases, the learned characteristics become progressively more dominant.

While stylistic elements are already visible at lower strengths, the characteristic Paulo Ferrini aesthetic only fully emerges around a LoRA strength of 1.2. At this point the material appearance, facial deformation and body horror influences become significantly more pronounced, closely resembling the visual identity found throughout the training dataset.
<p align="center">
<img src="https://github.com/user-attachments/assets/7f87eb46-786d-41d1-92d8-7b8eb54f8bb0"  width="100%"/>
</p>

<p align="center">
<img src="https://github.com/user-attachments/assets/41d266e9-59f1-4fe3-b146-83a4e1d0a9dc"  width="100%"/>
</p>

---

# CFG Scale

Besides the LoRA strength, the CFG Scale also has a noticeable influence on the final appearance. During testing it became apparent that lower CFG values preserve the artistic style more effectively than higher guidance values.

Around a CFG Scale of 3, the generated images retain a much stronger resemblance to my original artwork. Increasing the CFG gradually shifts the generations back towards the underlying Stable Diffusion model, reducing the stylistic influence of the trained LoRA.


<p align="center">
<img src="https://github.com/user-attachments/assets/4f53c696-8425-4d2d-9a70-7c5023d7b7a7" width="100%"/>
</p>


---

# Base Model Comparison

To evaluate how well the trained LoRA generalizes across different checkpoints, the same prompt and identical generation settings were applied to both Stable Diffusion 1.5 and Realistic Vision. The comparison was performed using fixed random seeds while gradually increasing the LoRA strength from 0.0 to 1.2.

Although both checkpoints successfully learned the artistic characteristics of the dataset, their interpretation of the style differs noticeably. Stable Diffusion 1.5 emphasizes the stylized appearance of the original artwork, while Realistic Vision retains a stronger photorealistic foundation before gradually adopting the learned visual language.

The comparison also confirms that the influence of the LoRA increases continuously with higher strength values. At lower strengths the outputs remain close to the underlying checkpoint, whereas around 1.2 the distinctive Paulo Ferrini art style becomes clearly recognizable on both models.

# Stable Diffusion 1.5

<table align="center">
<tr>
<th>0.0</th>
<th>0.5</th>
<th>1.0</th>
<th>1.2</th>
</tr>

<tr>
<td><img src="https://github.com/user-attachments/assets/4054f271-c3ff-48bc-a1d4-1b3719c8432a" width="100%"></td>
<td><img src="https://github.com/user-attachments/assets/b56dbe9f-55ec-44d1-bd60-546d68ac06c5"  width="100%"></td>
<td><img  src="https://github.com/user-attachments/assets/7a61035e-95d5-4432-a72f-18c6ea5ea4ab" width="100%"></td>
<td><img src="https://github.com/user-attachments/assets/bedbea8b-00a3-4349-88db-1b68bd00230c" width="100%"></td>

</tr>
</table>

# Generalization

Although the training dataset also contains environmental renderings, the LoRA clearly specializes in portraits and facial imagery. Human faces consistently produce the strongest and most convincing results, while environments, architectural scenes and animals exhibit considerably weaker stylistic transfer.

Full-body generations also proved more challenging. However, when successful, they often develop the same exaggerated anatomical proportions and organic deformations observed in the facial generations, reinforcing the body horror characteristics of the learned style.

One of the most surprising outcomes of this project was not how accurately the LoRA reproduced individual visual elements, but how strongly it amplified the underlying aesthetic of the dataset. Instead of merely imitating the original images, the model appears to emphasize the recurring visual themes present throughout the training material.

This behavior became particularly evident in portrait generations, where facial structures gradually transform into increasingly uncanny and distorted forms as the LoRA strength increases. Although this effect was not explicitly intended during training, it aligns remarkably well with the artistic influences behind my work and ultimately became one of the defining characteristics of the final model.

---


# About

**Paulo Ferrini**

Website

https://www.pauloferrini.com

Instagram

https://www.instagram.com/pauliferrino
