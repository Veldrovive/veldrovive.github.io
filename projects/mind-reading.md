---
layout: post
title: 'Voxel - Image Clip Alignment'

code_url: 'https://github.com/Veldrovive/open_clip'
code_url_text: 'Voxel Clip'
---

CLIP is a model that learned the relationships between text and images using contrastive loss. It turned out to be a very powerful for multiple tasks including image generation as proved by the DALLE2 model. The idea behind CLIP is much more powerful though.

The <a href="https://arxiv.org/pdf/2111.07991.pdf" target="_blank">LIT paper</a> showed that by freezing one encoder model, you can substitute out the other for a new encoder and still get good results after training. Taking this idea a step further, we propose substituting one encoder for an encoder using an entirely different modality. In this case, we use a 3D voxel representation of brain region activation measured using an MRI.

For the dataset we use the <a href="https://naturalscenesdataset.org/" target="_blank">natural scenes dataset</a> which contains image - MRI pairs. For each image there are multiple MRI samples so we need to be careful to confine each set into one of the train or validation dataset or we risk allowing the network to cheat.

{% include wip.html %}