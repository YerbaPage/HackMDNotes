### Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context

#### Ideas & Q:

- [ ] Haven't understood local order and global order, any example? Does it mean order of words and order of sentences respectively? (maybe I'll understand after reading again later)
- [ ] What is "copy"? "success of copy mechanisms such as attention and caching" "can LSTMs copy any words from context without relying on external copy mechanisms" I'd better search for some materials (or use one referenced in the paper) about cache-based models?

#### Abstract 

study role of context with ablation studies: the increase in perplexity when prior context are shuffled, replaced, or dropped

-  the model is capable of using about 200 tokens of context on average, but sharply distinguishes nearby context (recent 50 tokens) from the distant history
- highly sensitive to the order of words within the most recent sentence, ignores longer (>50)
- caching model [1] especially helps the LSTM to copy words from within this distant context



#### How much context is used?

analyzed using **increase in loss**

- LSTM: 200, changing hyperparameters doesn't influence this

- infrequent words need more context
- content words(nouns, verbs, adjs) need more than functional words (prepositions, determiners (only 10 tokens)).

#### Does word order matter?

**shuffle or reverse**

- **local order** (within 20-token permutable spans )matter for 20 recent tokens

- **global order** (local spans to include all the farthest tokens) matter for 50 

content words matter more than functional words

#### About cache

while LSTMs are aware of which words appear in their context, the awareness still degrades after long distance $\rightarrow$ "copy mechanisms such as attention and caching"

- LSTMs can regenerate words seen nearby

**[HAVEN'T FINISHED READING]**

[1] IMPROVING NEURAL LANGUAGE MODELS WITH A CONTINUOUS CACHE