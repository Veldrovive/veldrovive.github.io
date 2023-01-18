---
layout: post
title: 'DALLE2 PyTorch'

code_url: 'https://github.com/lucidrains/DALLE2-pytorch'
---

The modern transformer architecture has been a huge success in a multitudes of fields and has been the backbone of many state of the art models. However, in order to achieve the amazing results we are seeing all over the internet, we need to throw ungodly amounts of gpu time at the problem. The LAION organization in conjunction with along with a team of independent open source developers has made an effort to combat the trend toward only the most powerful having access to large models by replicating and training open source version using donated compute time. This project is a part of that effort.

DALLE2-PyTorch was trained using the StabilityAI HPC for <a href="https://wandb.ai/veldrovive/dalle2_train_decoder/runs/2yea5t0u?workspace=user-veldrovive" target="_blank">150k steps</a>.

#### My Contribution
DALLE2-PyTorch was primarily a collaboration between myself, <a href="https://github.com/lucidrains" target="_blank">lucidrains (Phil Wang)</a>, and <a href="https://github.com/nousr" target="_blank">nousr</a>. I was responsible for the decoder training code, distributed training, and configuration management.

{% include wip.html %}