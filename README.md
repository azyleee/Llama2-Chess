# Llama2-Chess

![llama playing chess]([https://via.placeholder.com](https://github.com/azyleee/Llama2-Chess/blob/main/images/llamachess4.jpeg)/500x500)

LLaMA 2 is an open source Large Language Model (LLM) developed by Meta AI. Its special tokens are publically available. This project used these tokens to create a dataset of chess moves using data from professional chess tournaments. 

Moves from a chess match are stored as a string which contains a unique key for each piece, file (vertical position), rank (horizontal position) and capturing. By replacing each of these unique keys with a unique token, we translate the highly structured data into what the language that the LLM understands best: tokens.
