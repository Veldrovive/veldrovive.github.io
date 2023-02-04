---
layout: post
title: "Semantic Search with Pre-Trained Sentence Encoders"

code_url: 'https://github.com/Veldrovive/QuestionContext'
demo_url: 'https://wandb.ai/veldrovive/QuestionContext?workspace=user-veldrovive'
demo_url_text: 'Wandb Project'
---

For as long as search has existed, it has been an acquired skill. You need to have an understanding of how the search algorithm is using the words you type to find the most relevant results. This was especially true in the very early days of search engines when lexical search was the main method used. However, with the rise of neural networks in natural language processing, effective semantic search has become a reality. Semantic search uses the meaning of the query instead of the word content to find the most relevant results which means we can apply our years of experience in formatting questions to other people to improve our search results.

In parallel with improvements in semantic search, there have been massive strides in unsupervised representation learning for both natural language and vision. Current state of the art for both of these tasks is achieved by the <a href="https://openai.com/blog/clip/" target="_blank">CLIP model</a>. CLIP uses a variant of contrastive learning to learn a shared representation for both language and vision. This means that we can use the same model to encode both text and images into a common (aligned in cosine similarity) space. This is a huge advantage because it means we can use the same model for both text and image search. CLIP has also shown impressive robustness on many downstream tasks, not least of which is the <a href="https://openai.com/dall-e-2/" target="_blank">DALLE2 model</a> which can generate images from text.

However, in this post I want to explore a separate downstream task, semantic search. Semantic search is currently dominated by models such as <a href="https://huggingface.co/sentence-transformers/msmarco-distilbert-base-v4" target="_blank">`msmarco-distilbert-base-v4`</a> which are trained end to end for semantic search. This is very effective for performance, but means that massive amounts of data and compute are required to train these models. In contrast, we could also use pre-trained sentence encoders as a frozen backbone and cheaply train a mlp projection head on top of it. This approach is vastly cheaper in compute required and also converges better with much smaller datasets, but at the cost of performance. In order to train this model, we use the same approach as the original CLIP training except that we replace both encoders with a small projection model.

<!-- Insert figure of CLIP training diagram -->
{% include image.html image="projects/semantic-search-pretrained/clip_qa.svg" text="" %}


For testing, we use a combined set of the <a href="https://rajpurkar.github.io/SQuAD-explorer/" target="_blank">SQuaD</a> and <a href="https://quac.ai/" target="_blank">QuaC</a> datasets, two question answering in context datasets. SOTA models achieve a top 1 score of 41.3% out of 500 examples on this dataset, meaning that they select the correct context for 41.3% of the questions. They also achieve a top 10 score of 81.1% out of 500 examples. These scores are very impressive given the fact that the context provided is very short and often does not have enough information to be 100% sure of the correct answer even as a human.

Our model that uses a 2 layer MLP with a hidden dimension of 1024 and a backbone of the openclip's CLIP-H model achieves a top 1 score of 29.4% and a top 10 score of 79%. This is a significant drop in performance, but vastly better than I expected beginning this project. There is more to the story though. Since clip works for semantic search as is with no projection head, we can also compare the projected embedding to the same task without projection. Without projection, CLIP-H achieves a top 1 score of 21.3% and a top 10 score of 63.4%. From this, we can see that the projection head is responsible for a large performance improvement. This validates that the approach of projecting the sentence embeddings into a new space is an effective way to improve performance on semantic search tasks.

<!-- Insert 10 top and top 1 figures -->
{% include image.html image="projects/semantic-search-pretrained/top_10_score.png" text="Top 10 Score" %}
{% include image.html image="projects/semantic-search-pretrained/top_1_score.png" text="Top 1 Score" %}

Using this method, we do not achieve SOTA, but given that we are using a small fraction of the compute required for SOTA and a much smaller dataset, I think this shows that as representation learning further improves methods similar to this one will become more and more viable. It is silly to continue to train models on massive datasets when we can use pre-trained models and train a small projection head on top of them. This is especially true when the pre-trained model is already very good at the task. This is a very exciting time for NLP and I am excited to see what the future holds.