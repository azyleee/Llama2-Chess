# Llama2-Chess

<p align="center">
  <img src="https://github.com/azyleee/Llama2-Chess/blob/main/images/llamachess4.jpeg" alt="llama playing chess" width=500/>
</p>

LLaMA 2 is an open source Large Language Model (LLM) developed by Meta AI. Its special tokens are publically available. This project used these tokens to create a dataset of chess moves using data from professional chess tournaments. 

Moves from a chess match are stored as a string which contains a unique key for each piece, file (vertical position), rank (horizontal position) and capturing. By replacing each of these unique keys with a unique token, we translate the highly structured data into what the language that the LLM understands best: tokens.


# Preliminary Results

Llama 2 was 4-Bit quantised then trained with QLoRA using the Transformers library on the first 33% of the dataset. The fine-tuned model was initially able to produce valid moves, but produces illegal moves as the game progresses. This is mostly likely due to the fundamental operation of an LLM. It is provided a string and predicts the most likely tokens that follow. There are a near infinite number of possible strings that can be produced in a chess game. When the fine-tuned model encounters a new string, it does not know the rules of chess, so while it might provide a move that _can_ be legal, it was not able to "think" analytically to generate a move that _is_ legal.
