# Welcome to Vallabh's Portfolio

This website exists primarily to share my data science projects and learnings with anyone who's willing to listen to my ramblings. But it may evolve over time.

## About Me

My name is Vallabh Reddy. I have a bachelor's in Computer Science and a master's in Business Analytics. I have been working in the Data Science field since 2015 across a few domains, namely, fintech, healthcare and retail. Mu Sigma, a decision sciences firm to which companies outsource their analytics and problem solving, was my first company. After which I worked at Amazon's Last Mile department. I'm a 2020 University of Cincinnati grad. Yes, I'm one from the Coronavirus wave of Bearcats.

In my free time I like to read non-fiction works detailing natural and man-made systems and I play squash and videogames. Also, I'm always willing to try new board games.

# Portfolio
Below is a list of complete and ongoing public Data Science projects of mine. 

1. [Image Classification on the Fashion MNIST dataset using Convolutional Neural Networks](#fashion_MNIST)
2. [Multilingual Toxic Comments Classification with only English training data - RoBERTa NLP Transformer](#multilingual_RoBERTa)
3. [USA Foreign Trade Analysis](#US_trade_analysis)
4. [Kickstarter Campaign Success Prediction](#Kickstarter)


 
## 1. Image Classification on the Fashion MNIST dataset using Convolutional Neural Networks <a name = 'fashion_MNIST'></a>

Github does not represent certain features of a jupyter notebook well, such as the intra notebook anchors, so here's a link to open the notebook through **[NBViewer](https://nbviewer.jupyter.org/github/VallabhReddy/Image-Classification-Fashion-MNIST-CNN/blob/master/Fashion%20MNIST%20Image%20Classification.ipynb)**.

Here is the **[Github link](https://github.com/VallabhReddy/Image-Classification-Fashion-MNIST-CNN/blob/master/Fashion%20MNIST%20Image%20Classification.ipynb)** for the same notebook.

### Introduction
The objective of this project was to build an image classifier that could recognize the category of apparel in the photo fed into it.

### Dataset
The model is trained and tested on the [Fashion MNIST dataset](https://github.com/zalandoresearch/fashion-mnist). The dataset is provided by the research branch of Zalando, a European e-commerce company. The dataset is made up of 28x28 grayscale images of 10 categories of apparel. There are 60,000 observations in the training set and 10,000 observations in the test set. The mapping for the 10 categories of apparel is given below.

<table>
<thead>
<tr>
<th>Label</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>0</td>
<td>T-shirt/top</td>
</tr>
<tr>
<td>1</td>
<td>Trouser</td>
</tr>
<tr>
<td>2</td>
<td>Pullover</td>
</tr>
<tr>
<td>3</td>
<td>Dress</td>
</tr>
<tr>
<td>4</td>
<td>Coat</td>
</tr>
<tr>
<td>5</td>
<td>Sandal</td>
</tr>
<tr>
<td>6</td>
<td>Shirt</td>
</tr>
<tr>
<td>7</td>
<td>Sneaker</td>
</tr>
<tr>
<td>8</td>
<td>Bag</td>
</tr>
<tr>
<td>9</td>
<td>Ankle boot</td>
</tr>
</tbody>
</table>

### Methodology 
Using Keras for Python, the model is built of Convolutional Neural Networks(CNN) which are especially effective in image comprehension. The notebook contains several architectures of CNNs and their performance is compared. I used the GPU implementation of TensorFlow since this increases the speed of deep learning model training exponentially, but the drawback is that the results are not perfectly reproducible and setting a seed does not work for the randomizing operations performed by the GPU.

### Results
I was able to achieve a 91-93% accuracy of classifications on the test set using a 13 layer network.

## 2. Multilingual Toxic Comments Classification <a name = 'multilingual_RoBERTa'></a>
This project was a kaggle submission, and can be found [here](https://www.kaggle.com/vallabhreddy/eda-and-roberta-using-huggingface-trasformers)

### Introduction 
The Conversation AI team, a research initiative founded by Google and Jigsaw, is tasked with improving the vigilance against online toxicity in conversation. The goal of [this competition](https://www.kaggle.com/c/jigsaw-multilingual-toxic-comment-classification/overview) is to be able to predict the toxicity of multilingual comments using only English comments as our training data. 

Excerpts from the competition are given below.

>It only takes one toxic comment to sour an online discussion. The Conversation AI team, a research initiative founded by Jigsaw and Google, builds technology to protect voices in conversation. A main area of focus is machine learning models that can identify toxicity in online conversations, where toxicity is defined as anything rude, disrespectful or otherwise likely to make someone leave a discussion. If these toxic contributions can be identified, we could have a safer, more collaborative internet.
>
>In the previous 2018 Toxic Comment Classification Challenge, Kagglers built multi-headed models to recognize toxicity and several subtypes of toxicity. In 2019, in the Unintended Bias in Toxicity Classification Challenge, you worked to build toxicity models that operate fairly across a diverse range of conversations. This year, we're taking advantage of Kaggle's new TPU support and challenging you to build multilingual models with English-only training data.
>
>Jigsaw's API, Perspective, serves toxicity models and others in a growing set of languages (see our documentation for the full list). Over the past year, the field has seen impressive multilingual capabilities from the latest model innovations, including few- and zero-shot learning. We're excited to learn whether these results "translate" (pun intended!) to toxicity classification. Your training data will be the English data provided for our previous two competitions and your test data will be Wikipedia talk page comments in several different languages.
>
>As our computing resources and modeling capabilities grow, so does our potential to support healthy conversations across the globe. Develop strategies to build effective multilingual models and you'll help Conversation AI and the entire industry realize that potential.
>
>*Disclaimer: The dataset for this competition contains text that may be considered profane, vulgar, or offensive.*

### Datasets
We are given the following datasets.

**Training set 1**
An all English dataset.
<table>
<thead>
<tr>
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Comment_text</td>
<td>Contains the string that represents the comment.</td>
</tr>
<tr>
<td>Toxic</td>
<td>A boolean value, 1 = toxic, 0 = non-toxic.</td>
</tr>
</table>

**Training set 2**
An all English dataset.
<table>
<thead>
<tr>
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Comment_text</td>
<td>Contains the string that represents the comment.</td>
</tr>
<tr>
<td>Toxic</td>
<td>A value between 0 and 1 representing the probability of the comment being toxic. </td>
</tr>
</table>


**Validation Set**
Has a few languages aside from English.
<table>
<thead>
<tr>
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Comment_text</td>
<td>Contains the string that represents the comment.</td>
</tr>
<tr>
<td>Toxic</td>
<td>A boolean value, 1 = toxic, 0 = non-toxic.</td>
</tr>
<tr>
<td>Lang</td>
<td>Two letter representation of the language of the comment. 'es'= Espaniol, 'it' = Italian etc.</td>
</tr>
</table>

**Test Set**
Has multiple languages outside of English or what was available in the validation set.
<table>
<thead>
<tr>
<th>Column</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>Comment_text</td>
<td>Contains the string that represents the comment.</td>
</tr>
<tr>
<td>Lang</td>
<td>Two letter representation of the language of the comment. 'es'= Espaniol, 'it' = Italian etc.</td>
</tr>
</table>

### Methodology
I employed transfer learning here. Which means I made use of a model that is pretrained at language comprehension and trained it to identify toxic comments. The specific model I used is Facebook's RoBERTa which is a version of a BERT Transformer. The Transformer is a deep learning NLP model introduced in the 2017 that is able to make sense of a word within the context of the sentence, i.e., it reads the entire sentence of words from left to right as well as right to left before making final interpretations of the word. 

The model consists of components called Encoder and Decoder which, well, encode words into intermediate representations, and decode this representation in a language respectively. This is precisely what makes the Transformer models multilingual. If the encoder is trained in multiple languages, they can all be reduced to the same intermediate representation, further the Decoder can be used to output a whole different language thus enabling the Transformer to be used as a translation tool. More specific to our problem, this feature is what let's us get away with using an all English training dataset to classify toxic comments from other languages. The Transformer has already been trained to interpret the different languages in our test and validation sets.

### Results
I was able to achieve a test accuracy of 92.9%.

## 3. USA Foreign Trade Analysis <a name = 'US_trade_analysis'></a>
Here is the link to the notebook hosted on github but opened through **[NBViewer](https://nbviewer.jupyter.org/github/VallabhReddy/US-Trade-Analysis/blob/master/Notebooks/US%20Trade%20Analysis.ipynb)**.
Here is the **[Github link](https://github.com/VallabhReddy/US-Trade-Analysis/blob/master/Notebooks/US%20Trade%20Analysis.ipynb)**.

### Introduction
The nature of this project was simply exploratory. I find the economy and its workings fascinating and wanted to look into how US foreign trade has varied over time. This analysis was conducted for the years 1998-2018.

### Datasets
     1. [US Trade Data](https://usatrade.census.gov) - from USA Trade online hosted by the US Department of Commerce.
     2. [USD CPI Data](https://www.bls.gov/cpi/) - from the Bureau of Labor Statistics website hosted by the United States Department of Labor.

### Methodology

