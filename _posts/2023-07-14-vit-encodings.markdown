---
layout: post
title:  "VIT - Visual Transformer Encodings"
date:   2023-07-15 20:17:01 -0600
categories: nanogpt pytorch ai
---

How do Visual Transformers work? In this post I'll explore the first, but crucial step, of how the Visual Transformer Encodings work.

A bit of context, Transformers are born for text-to-text translation, like english to french for example, and more recently they are used as text generators. Naturally, they've employed text encoders, which work as a first step to transform the text into a vector representation, which is then used by the Transformer to generate the text.

The Visual Transformer is a Transformer that works with images, and it's been used for image classification, image generation, and image segmentation. The Visual Transformer Encodings are the first step of the Visual Transformer, and they work as a first step to transform the image into a vector representation, which is then used by the Visual Transformer to generate the image.

The paper for Visual Transformer is [An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale](https://arxiv.org/abs/2010.11929), and the paper for Visual Transformer Encodings is [Training data-efficient image transformers & distillation through attention](https://arxiv.org/abs/2012.12877).

In the paper, the encoding method used, described in steps:
1. Resize the image to 224x224 pixels
2. Break the image into 16x16 patches, which is 14x14 patches
3. Flatten the patches into vectors using a linear projection, which is a matrix multiplication that reduces the dimensionality of the patch because each patch is a 16x16x3 tensor, and the linear projection reduces it to a 768 vector
4. Add a learnable position embedding to each patch, which is a vector of 768 elements
5. Add a learnable class embedding to the first patch, which is a vector of 768 elements
6. Concatenate the position embedding and the class embedding to the patch vector

The result is a 768 vector for each patch, and the number of patches is 14x14, which is 196 patches, so the result is a 768x196 matrix.

The intuition behind the encoding method is that the patches are the words, and the position embedding is the position of the word in the image, and the class embedding is the class of the image. The class embedding is the same for all patches, and the position embedding is different for each patch. 

Compared to text embeddings, here we don't have to create a vocabulary or a tokenizer, because image representations are already numbers. In a sense the patching is the tokenizer, and the linear projection is the vocabulary. The linear projection just makes sure that the patch vector is a vector of numbers that the Transformer can understand.

