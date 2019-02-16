---
layout: post
title: Bias in Word Embeddings
---
AI has always been centered around objectivity. Mitigating as much human judgement as possible has been the predominant mindset for machine learning algorithms today. However, this mindset ignores a fundamental problem: no matter how much one factors out human judgement, human biases are going to be inherently present in the datasets (especially those in Natural Language Processing) that you train your models on. Case in point: bias in word embeddings. 

Despite the fact that word embeddings are an unsupervised training task, they tend to exhibit significant stereotypes across a range of topics (e.g. gender, race, religion). This is likely due to the fact that the corpuses that they are trained on often reflect the societal biases that scaffold our language. The biases behind these embeddings raises questions as to nature of these biases in our society as well as the integrity of these embeddings. However, before delving into the details behind these biases and the solutions that have been proposed to fix it, we first need to know what word embeddings are and how they encode these biases.
  
## Word Embeddings
Word embeddings arose out of a desire to more represent words numerically so that they could be more easily read by more complex models like neural networks. Thus, words were mapped to n-dimensional vector space that were based on the similarities of each word to each other. For instance, this can be seen when one looks at the most similar words (using cosine similarity between word vectors) in an embedding to the word "Stanford" - which unsurprisingly give words like "Harvard", "USC", and "Cal" (booo).

![an image alt text]({{ site.baseurl }}/figure1a.png)
![an image alt text]({{ site.baseurl }}/figure1b.png)

![_config.yml]({{ site.baseurl }}/images/config.png)

The easiest way to make your first post is to edit this one. Go into /_posts/ and update the Hello World markdown file. For more instructions head over to the [Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
