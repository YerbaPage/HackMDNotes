## Why do (neural) LMs repeat themselves

- mainly due to decoding algorithms and is not specific to neural nets.
- still produce repetitive sequence even if we don't impose decoding algorithms (i.e. sampling)

### My ideas:

- there are similiar states for models

### N-gram LM

> EOS: end of sequence?

Markov chain: $s_{t}=x_{t-n: t}$, transition prob $p\left(\cdot \mid s_{t}\right)$

$p(EOS \mid c)=0$ for most algorithms [2]

### Greedy  decoding

guaranteed to repeat, but to be ovserved:

- cycle should be short

- hitting part of the cycle early

  > if more states transit to states in , then the expected hitting time is shorter

### Tempered sampling

**Q:** what is 'sampling with temperature'?

assume $p>0$, $M$ is irreducible and aperiodic, there will be a $\pi$ 

**Q:** why "once the chain enters any state in a cycle there is a small chance of leaving it"?  What is a cycle?

> to avoid repetition, the decoder should not produce very peaky distributions.

### Generalization to RNNs

approximate it with n-gram where n is large [3]

### Decoding algorithms to avoid repetition

- avoid peaky distributions: give sufficent probability to leave the cycle
- using [2] to end generation before cycling (unclear for long-text generation)

### Natural text

if revisiting happens frequently in natural texts, of course algorithms will revisit frequently.

### TODOs

- repetition in n-gram models 
- state revisits in human-generated text 
- expected hitting time 
- how to find cycles given an LM

[1] The Curious Case of Neural Text Degeneration.

[2] Consistency of a Recurrent Language Model With Respect to Incomplete Decoding.

[3] Sharp Nearby, Fuzzy Far Away: How Neural Language Models Use Context

[4] A Theoretical Analysis of the Repetition Problem in Text Generation





