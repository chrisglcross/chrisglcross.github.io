---
layout: post
title: Bias in Word Embeddings
---
AI has always been centered around objectivity. Mitigating as much human judgement as possible has been the predominant mindset for machine learning algorithms today. However, this mindset ignores a fundamental problem: no matter how much one factors out human judgement, human biases are going to be inherently present in the datasets (especially those in Natural Language Processing) that you train your models on. Case in point: bias in word embeddings. 

Despite the fact that word embeddings are an unsupervised training task, they tend to exhibit significant stereotypes across a range of topics (e.g. gender, race, religion). This is likely due to the fact that the corpuses that they are trained on often reflect the societal biases that scaffold our language. The biases behind these embeddings raises questions as to nature of these biases in our society as well as the integrity of these embeddings. However, before delving into the details behind these biases and the solutions that have been proposed to fix it, we first need to know what word embeddings are and how they encode these biases.
  
## Word Embeddings
Word embeddings arose out of a desire to somehow represent words numerically so that they could be more easily read by more complex models like neural networks. Thus, words were mapped to n-dimensional vector space that were based on the similarities of each word to each other. For instance, this can be seen when one looks at the most similar words (using cosine similarity between word vectors) in an embedding to the word "Stanford" - which unsurprisingly give words like "Harvard", "USC", and "Cal" (booo).

![_config.yml]({{ site.baseurl }}/images/figure1a.png) | ![_config.yml]({{ site.baseurl }}/images/figure1b.png)

However, another useful characteristic of this vectorized representation is that the different relationships across words are still preserved in the multi-dimensional space. In other words, embeddings are able to capture similarities across a wide spectrum of characteristics (e.g. location, part-of-speech, synonym, etc). For example, if you were to focus on some "geographical" dimension, one could see parallels in how capital cities and countries relate to each other.

![_config.yml]({{ site.baseurl }}/images/figure2.png)

The figure on the left is actually very relevant to how bias can be encoded in these representations. Using that figure as an example, one is able to take advantage of simple vector arithmetic for tasks like word analogies. Using the equation below, one is able to find equivalent pairings between two separate words (in this case, "man" and "woman") based on their meanings.

![_config.yml]({{ site.baseurl }}/images/figure3.png)

However, if one experiments with this general setup for a variety of different inputs, an glaring problem arises:

![_config.yml]({{ site.baseurl }}/images/figure4.png)

For some gender neutral words that should presumably be equivalent across genders (such as "programmer"), the analogous word that is outputted ("homemaker") represents a clear example of how one occupation could be inaccurately leaned towards a specific gender. It was this particular example that used in Bolukbasi's _Man is to Computer Programmer as Woman is to 58Homemaker?  Debiasing  Word  Embedding_, which highlighted this way of showing how word embeddings could represent the implicit sexism in a dataset
