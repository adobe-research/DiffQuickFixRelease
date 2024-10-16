# DiffQuickFixRelease : Model Editing for Text-to-Image Diffusion Models

This Jupyter notebook implements the DiffQuickFix algorithm (ICLR '24 - https://arxiv.org/abs/2310.13730) which edits the text-encoder in Diffusion models to remove copyrighted concepts. 


![Removing the style of Van Gogh and Monet from an Image](./assets/teaser.png)

### Introduction 

Text-to-Image Diffusion Models such as Stable-Diffusion and Imagen have achieved unprecedented quality of photorealism with state-of-the-art FID scores on MS-COCO and other generation benchmarks. Given a caption, image generation requires fine-grained knowledge about attributes such as object structure, style, and viewpoint amongst others. Where does this information reside in text-to-image generative models? In our paper, we tackle this question and understand how knowledge corresponding to distinct visual attributes is stored in large-scale text-to-image diffusion models. We adapt Causal Mediation Analysis for text-to-image models and trace knowledge about distinct visual attributes to various (causal) components in the (i) UNet and (ii) text-encoder of the diffusion model. In particular, we show that unlike generative large-language models, knowledge about different attributes is not localized in isolated components, but is instead distributed amongst a set of components in the conditional UNet. These sets of components are often distinct for different visual attributes. Remarkably, we find that the CLIP text-encoder in public text-to-image models such as Stable-Diffusion contains only one causal state across different visual attributes, and this is the first self-attention layer corresponding to the last subject token of the attribute in the caption. This is in stark contrast to the causal states in other language models which are often the mid-MLP layers. Based on this observation of only one causal state in the text-encoder, we introduce a fast, data-free model editing method Diff-QuickFix which can effectively edit concepts in text-to-image models. DiffQuickFix can edit (ablate) concepts in under a second with a closed-form update, providing a significant 1000x speedup and comparable editing performance to existing fine-tuning based editing methods.


## Citation

If you use our code in your research, do cite us!

```bibtex
@inproceedings{
basu2024localizing,
title={Localizing and Editing Knowledge In Text-to-Image Generative Models},
author={Samyadeep Basu and Nanxuan Zhao and Vlad I Morariu and Soheil Feizi and Varun Manjunatha},
booktitle={The Twelfth International Conference on Learning Representations},
year={2024},
url={https://openreview.net/forum?id=Qmw9ne6SOQ}
}
```
