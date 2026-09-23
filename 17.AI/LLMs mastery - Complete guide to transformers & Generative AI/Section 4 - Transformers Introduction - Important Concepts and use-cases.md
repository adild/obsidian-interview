# Encoders, Decoders and the attention mechanism 

Motivation for the development of Transformer models - 
1. RNNS and LSTMS limitations - 
	Struggle with long-range dependencies and slow sequential processing.
2. Self-Attention mechanism - 
	Transformers efficiently capture dependencies, regardless of distance in input data.
3. Parallel Computation -
	Transformers process multiple input parts simultaneously , offering faster processing than RNNs and LSTMs during training particular noticing with larger datasets.

Transformer architecture 
![[Pasted image 20260527150636.png]]

Encoder-Decoder
The Transformer's encoder-decoder architecture is ==the foundation for sequence-to-sequence tasks like language translation and text summarization==. The **encoder** processes the input sequence into rich contextual representations, while the **decoder** takes those representations and auto-regressively generates the target output. [](https://machinelearningmastery.com/encoders-and-decoders-in-transformer-models/)

1. The Encoder: Understanding the Input
The encoder reads the entire input sequence at once. Its primary job is to extract the meaning and contextual relationship of every token by comparing it to all other tokens. [](https://machinelearningmastery.com/encoders-and-decoders-in-transformer-models/)
- **Input Embedding & Positional Encoding:** Converts words into numbers (vectors) and adds "positional" information so the model knows the order of the words.
- **Multi-Head Self-Attention:** Allows the model to weigh the importance of different words in the sentence relative to one another (e.g., understanding that "bank" means the side of a river when near the word "water").
- **Feed-Forward Neural Network:** Processes the attention outputs further before passing them to the next layer.
- _Result:_ The encoder outputs a sequence of continuous vectors (or embeddings) that act as a deep, numerical understanding of the input sequence. [](https://www.youtube.com/watch?v=0_4KEb08xrE)

2. The Decoder: Generating the Output
The decoder generates the output sequence one token at a time. It receives information from the encoder and combines it with its own previous outputs to generate the next word. [](https://www.youtube.com/watch?v=zbdong_h-x4)
- **Masked Multi-Head Self-Attention:** The decoder looks at the words it has _already_ generated to predict the next word. It uses a "mask" to prevent the model from looking ahead at future words in the output sequence.
- **Cross-Attention (Encoder-Decoder Attention):** This is the bridge between the two halves. The decoder uses the context representations provided by the encoder to know _what_ to translate or generate (e.g., knowing that the encoded English sentence "Hello" should trigger a French response like "Bonjour").
- **Linear & Softmax Layers:** Converts the decoder's high-dimensional vector into an actual word from the model's vocabulary. [](https://www.reddit.com/r/learnmachinelearning/comments/1g7plvb/why_do_different_architectures_only_need_an/)

How They Work Together
In a translation task (e.g., English to French), the English sentence goes into the **encoder**. The encoder creates a rich "thought vector" or context representation. This representation is handed to the **decoder**, which then generates the French translation word by word until it produces an "end-of-sentence" token. [](https://www.youtube.com/watch?v=0_4KEb08xrE)

# Attention Mechanism
The **Attention Mechanism** is the core idea behind the Transformer (deep learning architecture) model used in modern AI systems like OpenAI GPT models.

Instead of reading words one-by-one like older RNNs/LSTMs, transformers look at **all words together** and decide:

> “Which words should I focus on while understanding this word?”

---
Simple Example

Sentence:

> "The cat sat on the mat because it was tired."

When processing the word **"it"**, the model needs to know:

- Does "it" refer to:
    - cat?
    - mat?

Attention helps the model focus more on **"cat"**.

---
Core Idea

For every word/token:

1. Compare it with all other words
2. Give importance scores
3. Combine useful information

This is called **Self-Attention**.

Intuition -

Imagine reading a paragraph.

When reading one word, your brain automatically focuses on related words nearby or far away.

Attention does the same mathematically.

---
Self-Attention vs Normal Attention -

|Type|Meaning|
|---|---|
|Self-Attention|Words attend to other words in same sentence|
|Cross-Attention|Decoder attends to encoder output|

---

Multi-Head Attention -

Transformers use multiple attention heads.

Instead of one attention:

- Head 1 learns grammar
- Head 2 learns relationships
- Head 3 learns context

etc.

This improves understanding.

---

Why Attention Is Powerful -

Older RNNs had problems:

- hard to remember long context
- sequential processing
- slow training

Attention solves these because:

✅ parallel processing  
✅ long-range relationships  
✅ better context understanding  
✅ scalable

# Positional Encoding

Because transformer looks at everything at once in all direction so they can sometimes lose sense of that direction. Lets see how these models keep words in order with positional encoding, since attention mechanism doesnt capture the position of words in a sequence the transformer model uses a separate positional encoding to provide this information.
Positional encoding is added to the input embeddings before they are fed into the model, ensuring that the model can recognize the order of the words inside the input.
This technique is essential for the transformer to understand the structure and the meaning of sentences. Without it, they would basically see a messy bag of words.

# Feed Forward Network
After attention mechanism has done its job of capturing relationship between words, the output is passed through a feed-forward network. The purpose of feed-forward network is to help the model learn more complex patterns and representations from input data. They operate independently of each position in input sequence, which allows for parallel computation and contributes to the relative compute efficiency of the transformer. 

# Layer Normalization
![[Pasted image 20260602131855.png]]

Finally to improve stability, the training speed of transformer model, its important to know that layer normalization is also applied after both 