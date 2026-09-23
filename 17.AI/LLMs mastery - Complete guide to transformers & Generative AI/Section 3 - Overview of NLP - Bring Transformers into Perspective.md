# Rule Based Systems Era (not imp)
It has limitations

# Statistical Era (not imp - but read it)
After the previous era, researchers were on a mission to overcome the limitations of rule-based systems, and they started looking into statistical methods as a way to improve natural language processing capabilities.
The statistical NLP era was a game-changer, because it marked a big perspective shift from relying on manually-crafted rules to embracing data-driven approaches.
Instead of spending hours and hours creating and tweaking rules, researchers leverage the power of probability and statistics to analyze and generate text.
What made statistical techniques so great was their ability to better handle language ambiguity, the hard task of making sense of words or phrases that can have multiple meanings depending on the context(Rule based era problem).
These techniques also allowed NLP systems to adapt to new language patterns without needing someone to constantly update the rules.
This new approach to NLP was a huge advancement in the field.
It laid a foundation for many of the NLP techniques we are familiar with today,

Let's see some useful concepts and key methods that emerged during this exciting period.
So during the statistical NLP era, tools like n-grams and probabilistic language models emerged as superstars, 
as they were making it easier to predict word sequences.
An n-gram is simply a sequence of n-words that are right next to each other in a text.
And breaking up texts like this helps spot keywords and patterns.
By looking at how often n-grams showed up in huge collections of text, researchers could estimate the probability of specific word sequences happening.

DRAWBACKS OF STATISTICAL NLP -
Statistical NLP techniques definitely made some big leaps in language processing,
but they also ran in quite a few limitations.
One major challenge they faced was data sparsity.
In real world texts, there are a lot of possible word combinations that we don't see very often.
This made it tough for statistical models to accurately estimate probabilities for these rare occurrences, which naturally led to predictions that weren't always on point.
Another limitation was that statistical models didn't have a great grasp of semantics or the meaning behind words. Sure, these models could pick up on patterns and relationships between words based on how often they appear together, but they often had a hard time understanding the deeper meaning and context behind these words.
This made it very difficult for statistical NLP systems to tackle tasks that needed a more nuanced understanding of language. So these challenges got researchers thinking about new techniques that could overcome such limitations.

# Machine Learning Era
Building upon the progress made in statistical NLP, researchers started incorporating machine learning techniques in order to push natural language processing even further.
The machine learning era marked a big shift as these techniques allowed NLP systems to learn patterns and relationships within language data more effectively, tackling some big limitations faced by the statistical methods.
Machine learning algorithms like Naive Bayes, Support Vector Machines and neural networks were used to handle a wide range of NLP tasks, such as sentiment analysis, question answering, and machine translation.
Furthermore, these new approaches also help NLP systems deal with large-scale data, thus also aiding in the second limitation this field had until now, scalability.

Let's check out some of the most useful key machine learning techniques that emerged during this era.
Naive Bayes and Support Vector Machines became popular algorithms for NLP tasks like text classification, sentiment analysis, spam detection.
Both Naive Bayes and Support Vector Machines laid the groundwork for more complex techniques like neural networks.
So, needless to say, the introduction of neural networks was a game changer for natural language processing, offering a more flexible and powerful approach to language understanding.

Neural networks could automatically learn the meaningful features and representations from raw text data, finally getting rid of the need for manual feature engineering.

Let me stress this point again because it's really important. 
Neural networks have changed the way we work with raw text data.
Instead of relying on manual feature engineering, which was both time consuming and very error prone, these networks can automatically learn meaningful features and representations directly from the text, completely removing the need for feature engineering altogether.
This advancement has not only simplified the process, but also led to more accurate and powerful mode It was quite a milestone in the field of natural language processing.

Okay, so neural networks were applied to a wide range of NLP tasks, like machine translation, sentiment analysis, and text summarization, resulting in significant improvements in both performance and scalability.
Let's look at some examples and applications.
One popular architecture was the recurrent neural network, or RNN. RNNs are a specialized type of neural network. Later LSTMs were introduced.

# Embeddings Era
Researchers started thinking to represent text. They started thinking of words as continuous vectors in a high dimensional space. This helped understanding text way better than before.
So popular word embeddings techniques came up in this era - word2vec and glove.
Than later contextualized word embeddings line ELMO unlike traditional techniques which gives one one fixed vector representation, contextualised word embeddings gave dynamic representation to each word based on entire context of the sentence. This gave more accurate representations because words can give different meanings how they used in a sentence, so this was the big step as previous old era struggle with this situation. 

Limitations of embeddings era - 
1. fixed-length representations - 
2. lack of transfer learning - each time model needs to be trained from scratch for each new task, which can be time consuming and computationally expensive. This limitation prevents the efficient use of pre-existing knowledge, slowing down the development and deployment of NLP models.

Next it Transformer models that took to the next level. Finally enabling deep contextual understanding of long sequences. 

![[Pasted image 20260527141303.png]]