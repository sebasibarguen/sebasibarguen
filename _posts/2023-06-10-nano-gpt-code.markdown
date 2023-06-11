---
layout: post
title:  "NanoGPT Coder"
date:   2023-06-10 20:17:01 -0600
categories: nanogpt pytorch ai
---
To better understand how Transformers, and the GPT models work, I followed along the incredible [Karpathys series on building GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY). To really push my self a bit, I wanted to use a different dataset and try to make a few twicks beyond what Karpathy covers in his series, so that I really have to understand whats going on. So instead of generating Shakespear, the nanogpt-coder generates python code using the [bigcode/starcode dataset](https://huggingface.co/datasets/bigcode/starcoderdata).

My key learnings over buiding nanogpt-coder:
- How *attention* works
- Understanding how the building blocks fit together
- Manually finding the right `batch_siz`e to train in Colab
- Using *Weights and Biases* to monitor the progress on the loss, as well as samples.
- Save the model weights as checkpoints for further improvements
- Working with GPUs vs CPU vs MPS (mac metal)
- Tweaking the data to obtain a better performance
- Dataset sampling vs using all the dataset


After 15,000 steps or epochs, with 32 batch size, the results started to look pythonic, although still very far from producing working code. 


*Prompt*:
> "def sum(a, b):\n"

*Output*:
{% highlight python %}
def sum(a, b):
    """
    try: B.sigmoid.ormal.clear_mean_values - 1
    fig_order = F.sigmoid
    mean_device = I
{% endhighlight %}
