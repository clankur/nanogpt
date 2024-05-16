# einygpt

An implementation of a transformer-based language model primarily using `einops` and trained over the TinyStories dataset. It incorporates techniques to reduce computations with the inclusion of a KVCache and improve memory bandwidth using GQA (grouped query attention).

Training a 6.9 million parameter model on a RTX4090 with the GPT2Tokenizer achieves results inline with the findings from the [TinyStories paper](https://arxiv.org/pdf/2305.07759) and gets a perplexity of 1.0001 over the validation set. Additionally, training a 4.3 million parameter model with its [own Byte-Pair Encoding tokenizer](tiny_tokenizer.py) and using GQA w/ 4 groups achieves a comparable perplexity.

Both models produce stories that have a logical flow and have a good grasp of grammar. The custom tokenizer model does have it's drawbacks - it generates less text within the same context length - as a result of the custom tokenizer. You can compare their outputs side by side in this [notebook](perplexity.ipynb).