### Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context

Ideas & Q:



#### Abstract 

study role of context with ablation studies: the increase in perplexity when prior context are shuffled, replaced, or dropped

-  the model is capable of using about 200 tokens of context on average, but sharply distinguishes nearby context (recent 50 tokens) from the distant history
- highly sensitive to the order of words within the most recent sentence, ignores longer (>50)
- caching model [1] especially helps the LSTM to copy words from within this distant context



[1] IMPROVING NEURAL LANGUAGE MODELS WITH A CONTINUOUS CACHE