# Llama2-Chess

<p align="center">
  <img src="https://github.com/azyleee/Llama2-Chess/blob/main/images/llamachess4.jpeg" alt="llama playing chess" width=500/>
</p>

[LLaMA 2](https://ai.meta.com/llama/) is a Large Language Model (LLM) developed by Meta AI. As an open source model, its special tokens are publically available. This project used these tokens to create a dataset of chess moves using data from professional chess tournaments. 

This project used chess games played by professional players to create a dataset to train Llama 2 to play chess. The moves were extracted from a free online database of chess tournaments, [Chessgames.com](https://www.chessgames.com), which stores the moves as a string on their webpages. The moves contain a unique key for each piece, file (vertical position), rank (horizontal position) and capturing. By replacing each of these unique keys with a unique token, I translated the highly structured data into what the LLM understands best: tokens.

# Prerequisite Libraries
To generate the dataset, you will need:
* ```bs4``` (for ```BeautifulSoup```)
* ```urllib```
* ```IPython```
* ```re```
* ```csv```
* ```pandas```

There are many options to load and train Llama 2. A popular option is to use the [HF format model](https://huggingface.co/meta-llama/Llama-2-7b-hf) from HuggingFace which is compatible with the well documented [Transformers](https://huggingface.co/docs/transformers/index) library. To use Transformers, you will need:
* ```transformers```
* ```accelerate```
* ```datasets```
* ```peft```
* ```bitsandbytes```
* ```trl```
* ```einops```
* ```sentencepiece```



# Preliminary Results

[Llama 2 7b](https://huggingface.co/meta-llama/Llama-2-7b-hf) was 4-Bit quantised then trained with QLoRA using the Transformers library on the first 33% of the dataset. The fine-tuned model was initially able to produce valid moves, but produces illegal moves as the game progresses. This is mostly likely due to the fundamental operation of an LLM. It is provided a string and predicts the most likely tokens that follow. There are a near infinite number of possible strings that can be produced in a chess game. When the fine-tuned model encounters a new string, it does not know the rules of chess, so while it might provide a move that _can_ be legal (i.e. a valid piece, file and rank), it was not able to "think" analytically to generate a move that _is_ legal.
