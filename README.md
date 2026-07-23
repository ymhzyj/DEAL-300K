## **DEAL-300K**: Diffusion-based Editing Area Localization with a 300K-Scale Dataset and Frequency-Prompted Baseline



## Description


This is the official repository for DEAL-300K. The DEAL-300K dataset and editing instructions are publicly available through the links below. The SAM-CD and Qwen-VL checkpoints, MFPT checkpoints, and full implementation are planned for a later release.





## Release Status
- [x] Release DEAL-300K dataset.
- [ ] Release SAM-CD pre-trained weights.
- [ ] Release Qwen-VL pre-trained weights.
- [ ] Release MFPT pre-trained weights.
- [ ] Release full code.

## Overview
Diffusion-based image editing provides intuitive semantic editing capabilities but also lowers the barrier to producing realistic local manipulations. DEAL-300K is a benchmark for diffusion-based image manipulation localization (DIML) containing 340,468 images: 119,371 source images and 221,097 edited images with pixel-level masks. Its construction pipeline uses a multimodal large language model for image-conditioned editing instructions, a mask-free diffusion editor for manipulated-image generation, and active-learning change detection for scalable pixel-level annotation. We also present Multi-Frequency Prompt Tuning (MFPT), a frequency-prompted localization baseline built on a frozen Visual Foundation Model. Under the evaluation protocol reported in the paper, MFPT achieves 82.48% pixel-level F1 on the DEAL-E edited-only test subset and 80.88% on CoCoGlide. 

## DEAL-300K dataset

### Download
The dataset is available from both OneDrive and Hugging Face. 

Training Set Images can be downloaded from [train.zip](https://1drv.ms/u/s!AgVmq0AY0Su8gr1DmG-HWFsws_Fkww?e=MOPn47)

Val Set Images can be downloaded from [val.zip](https://1drv.ms/u/s!AgVmq0AY0Su8grxy38macOANthNBfA?e=0jgmly)

Testing Set Images can be downloaded from [test.zip](https://1drv.ms/u/s!AgVmq0AY0Su8grxwCKrru0NLUkf39g?e=DNfNRK)

Labels can be downloaded from [label.zip](https://1drv.ms/u/s!AgVmq0AY0Su8grxx2lnMXYsGYhv79w?e=nGRYJt)

The complete dataset is also available on [Hugging Face](https://huggingface.co/datasets/FlyHorseJ/DEAL-300K).

### Instructions

The edited images are generated with InstructPix2Pix, using instructions produced by the fine-tuned Qwen-VL model. The instructions are available in [instructions](./instructions). The source images originate from MS COCO. 
The word cloud of the editing instructions is shown in the image below.

<!-- ![Word Cloud](assets/wordcloud-page-001.jpg) -->
<div style="text-align: center;">
<img src="assets/wordcloud-page-001.jpg" alt="Word Cloud" width="500">
</div>


### Quantitative comparison of DEAL-300K to existing publicly available DIML datasets

| Dataset | Year | Source Images  | Edited Images | Image Size | Scenario | Generative Model | 
|------------------|-------------------------------------------------------------|---------------------|---------------------|-----|-----|------|
| [CoCoGlide](https://github.com/grip-unina/TruFor) | 2023 | 512                  | 512    | $256 \times 256$  | General   | Glide   | 
| [AutoSplice](https://github.com/shanface33/AutoSplice_Dataset)| 2023 | 2,273                 | 3,621 | $256 \times 256 - 4232 \times 4232$  | General   | DALL-E2   |
| [MagicBrush](https://github.com/OSU-NLP-Group/MagicBrush)| 2023 | 5,313               | 10,388  | $1024 \times 1024$  | General   | DALL-E2   |
| [Repaint-P2/CelebA-HQ](https://github.com/bit-ml/dolos) | 2024 | 10,800  | 41,472   | $256 \times 256$   | Face   | Repaint   |
| DEAL-300K | 2024 Apr. | 119,371  | 221,097       | $128 \times 512 - 512 \times 576$  | General  | InstructPix2Pix   |

### Visualization

Some random examples from the training set
<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000000009_qwen120.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000000009.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000000009_qwen120.png" alt="Image ori 2" width="300">
</div>

<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000000459_qwen120.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000000459.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000000459_qwen120.png" alt="Image ori 2" width="300">
</div>


<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000436603_qwen120.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000436603.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000436603_qwen120.png" alt="Image ori 2" width="300">
</div>

<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000436647_qwen120.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000436647.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000436647_qwen120.png" alt="Image ori 2" width="300">
</div>

<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000436795_qwen180.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000436795.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000436795_qwen180.png" alt="Image ori 2" width="300">
</div>

<div style="display: flex; justify-content: center;">
    <img src="assets/examples/000000436797_qwen180.jpg" alt="Image ori 1" width="300">
    <img src="assets/examples/000000436797.jpg" alt="Image ori 2" width="300">
    <img src="assets/examples/000000436797_qwen180.png" alt="Image ori 2" width="300">
</div>

## Acknowledgments
Our work is built upon the foundational work of [MS COCO](https://cocodataset.org/), [InstructPix2Pix](https://github.com/timothybrooks/instruct-pix2pix), [Qwen-VL](https://github.com/QwenLM/Qwen-VL), [ISAT](https://github.com/yatengLG/ISAT) and [SAM-CD](https://github.com/ggsDing/SAM-CD/tree/main).

