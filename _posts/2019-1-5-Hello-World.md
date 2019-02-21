---
layout: post
title: Bias in Word Embeddings
---
AI has always been centered around objectivity. Mitigating as much human judgement as possible has been the predominant mindset for machine learning algorithms today. However, this mindset ignores a fundamental problem: no matter how much one factors out human judgement, human biases are going to be inherently present in the datasets (especially those in Natural Language Processing) that you train your models on. Case in point: bias in word embeddings. 

Despite the fact that word embeddings are an unsupervised training task, they tend to exhibit significant stereotypes across a range of topics (e.g. gender, race, religion). This is likely due to the fact that the corpuses that they are trained on often reflect the societal biases that scaffold our language. The biases behind these embeddings raises questions as to nature of these biases in our society as well as the integrity of these embeddings. However, before delving into the details behind these biases and the solutions that have been proposed to fix it, we first need to know what word embeddings are and how they encode these biases.
   
   
## Word Embeddings
Word embeddings arose out of a desire to somehow represent words numerically so that they could be more easily read by more complex models like neural networks. Thus, words were mapped to n-dimensional vector space that were based on the similarities of each word to each other. For instance, this can be seen when one looks at the most similar words (using cosine similarity between word vectors) in an embedding to the word "Stanford" - which unsurprisingly give words like "Harvard", "USC", and "Cal" (booo).

![_config.yml]({{ site.baseurl }}/images/figure1a.png) | ![_config.yml]({{ site.baseurl }}/images/figure1b.png)

![_config.yml]
However, another useful characteristic of this vectorized representation is that the different relationships across words are still preserved in the multi-dimensional space. In other words, embeddings are able to capture similarities across a wide spectrum of characteristics (e.g. location, part-of-speech, synonym, etc). For example, if you were to focus on some "geographical" dimension, one could see parallels in how capital cities and countries relate to each other.
 
 
![_config.yml]({{ site.baseurl }}/images/figure2.png)
 
 
The figure on the left is actually very relevant to how bias can be encoded in these representations. Using that figure as an example, one is able to take advantage of simple vector arithmetic for tasks like word analogies. Using the equation below, one is able to find equivalent pairings between two separate words (in this case, "man" and "woman") based on their meanings.
 
 
![_config.yml]({{ site.baseurl }}/images/figure3.png)
 
 
However, if one experiments with this general setup for a variety of different inputs, an glaring problem arises:
 
 
![_config.yml]({{ site.baseurl }}/images/figure4.png)
 
 
For some gender neutral words that should presumably be equivalent across genders (such as "programmer"), the analogous word that is outputted ("homemaker") represents a clear example of how one occupation could lean towards a specific gender. It was this particular example that used in Bolukbasi's _Man is to Computer Programmer as Woman is to Homemaker?  Debiasing  Word  Embedding_, which highlighted this way of showing how word embeddings could represent the implicit sexism in a dataset
 
 
## Debiasing Methods
The paper was also seminal in introducing a potential method to fixing this problem, which involved modifying the vector space to eliminate this arbitrary "gender"-ing of words while still retaining the "gender"-ing of words in cases like "sister" and "brother" - where gender is important in the core definitions of these words. This "Neutralize and Equalize" technique essentially projected gender neutral words unto this identified gender subspace and maintained the positioning of gender-definitional pairs. Below is a plot that shows the gender divide between words in the Google News Word2Vec dataset using each word vector's cosine similarity to "he" and "she". The plot was generated using the gender-definitional and gender-neutral examples given by the paper itself. The plot next to it shows the same word vector similarities after I applied Bolukbasi's debiasing method.
 
 
![_config.yml]({{ site.baseurl }}/images/figure5a.png) | ![_config.yml]({{ site.baseurl }}/images/figure5b.png)
 
 
The paper also introduced an alternative method to debiasing the word embeddings, instead redefining the problem as an optimization problem that sought to minimize the gender dimension of gender-neutral words while still maximizing this component for gender-definitional pairs. Using a langrangian method in order to find the optimal linear transformation, this "soft" debiasing algorithm serves as a rough equivalent to the aforementioned "hard" method. This method and its associated mathematical equation is outline here below:
 
 
![_config.yml]({{ site.baseurl }}/images/figure6.png)

 
I've now introduced the topic surrounding bias in word embeddings a potential solution to this problem by Bolukbasi. In a following blog post, I will focus on two more alternative methods focused on adversarial training and pre-processing model adjustments made my researchers in the last year. 
