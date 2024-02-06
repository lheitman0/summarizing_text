# summarizing_text
Summarizing text to improve skills with transformers and hugging face
## Note
Very simple implementation of pre trained bart-large-cnn from hugging face

Most of this README is for my understanding: documenting encoder/decoder technicalities, hidden states
## Next step
Planning on implementing this to my blog2audio project to have nicely formatted summaries of blogs to help the user decide to listen

## Very Basic Definition of an Encoder in Transformers

- **Seq2Seq Models like BART**
    - The encoder processes the input sequence and produces a set of context vectors. These context vectors are used by the decoder to generate the output sequence, effectively capturing the essence of the input and transforming it into a new form (like a summary).

- **Function of an encoder** 
    - Takes the input and 'encodes' it into the format the model is expecting.
    - Captures the semantic and contextual information of the input in a numerical format.

- **Embedding layer**
    - Converts the input of tokens and converts into vectors of a fixed size: embeddings. These embeddings are learned to represent the semantic meanings of the tokens.

- **Self-attention** 
    - For each token in the input, the self-attention mechanism calculates the weights that determine how much attention the model should pay to every other token in the input when understanding and processing that particular token.
    - Attention scores are calculated based on the query (the token being processed), key (all tokens in the input, including the query token), and value (also all tokens in the input) vectors, derived from the input tokens themselves. The scores are then used to create a weighted average of value vectors, resulting in a new representation of each token that carries contextual information from the entire sequence.
    - Allows the model to dynamically focus on different parts of the input sequence as needed, effectively capturing the nuances of context, meaning, and the relationships between tokens, regardless of their position in the input sequence.

- **Positional Encoding**
    - The self-attention layer doesn't consider the position of the words, positional encoding is added to give each word a unique position.
    - Helps the model understand word order, which is important for making sense of sentences.

- **Normalization + Feed-Forward Network**
    - Input undergoes layer normalization which stabilizes training: ensures values don't get too high or low, increases generalization
    - Then, the data passes through the feed-forward network. This network further refines the context of the embeddings by applying the same set of operations to each position independently. It enhances the model's ability to process and transform the information after considering the entire input context.
