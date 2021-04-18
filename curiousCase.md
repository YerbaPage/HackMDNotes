### THE CURIOUS CASE OF NEURAL TEXT DeGENERATION

#### Ideas & Q:


- improve training? predict more tokens(2,3,..) and then back-prop?
- need codes for evaluation (for each metric)
- reminds me of similar states: " the animal was found by fishermen off the coast of Bundaberg", "fishing vessel off
the coast of Bundaberg" and "fishermen off the coast of
Bundaberg" (and how to detect them automatically? by fractions of sentence?)
- need to search and take notes for the metrics (e.g. perplexity)

#### Abstract


likelihood works well for training but maximization-based decoding methods leads to 'degeneration': bland, incoherent repetitive output text


Nucleus Sampling: truncating the unreliable tail of prob distribution and than sample

#### Metrics:

- likelihood ("surprising"), diversity and repetition

#### Results:


- maximization is inappropriate

- current best models still have unreliable tails to be truncated

- nucleus sampling is 'good' and diverse

#### Main body: 

b=32: repetition, b>64, prefer to stop

beam search text is not "surprising"


probability of 'I don't know' increases during the loop


it can be observed from table1 that topk=640 repeats the least


Zipf's law: there is an exponential relationship between the rank of a word and its frequency in text
