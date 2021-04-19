### Metrics for evaluation

#### Ideas and Q:

- [ ] Wow to choose the n in BLEU?

- [x] What is **self-**bleu in some papers? "lower Self-BLEU scores imply higher diversity"

  calculate the BLEU scores by choosing each sentence in the set of generated sentences as hypothesis and others as reference, and then take an average of BLEU scores. [7]
  
- [ ] what is "probability assigned by the language model" in HUSE? difference between HUSE and BLEURT? (secondary)

> from https://towardsdatascience.com/how-to-evaluate-text-generation-models-metrics-for-automatic-evaluation-of-nlp-models-e1c251b04ec1
>
> **codes are provided on the page**

**Compared with human texts, the closer, the better**

#### Perplexity

**lower is better**

to evaluate efficacy of generative models, normalized on the length of sentences

$perplexity =\prod_{t=1}^{T}\left(\frac{1}{P_{\mathrm{LM}}\left(\boldsymbol{x}^{(t+1)} \mid \boldsymbol{x}^{(t)}, \ldots, \boldsymbol{x}^{(1)}\right)}\right)^{1 / T}$

some other forms: $P P(S)=2^{-\frac{1}{N} \sum \log \left(P\left(w_{i}\right)\right)}$ where $w_i$ stands for the i^{th}$ bigram 

- "more training data, less perplexity" [5]
- stop words and punctuation marks influence perplexity a lot some times [5]BLEURT

#### BLEU: Bilingual Evaluation Understudy Score

**higher is better**

$B L E U=B P \times \exp \left(\sum_{n=1}^{N} w_{n} \times \log p_{n}\right)$

where 

- BP (brevity penalty) to penalize situation where length of reference and generated are very different $B P=\left\{\begin{array}{ll}1 & \mathrm{c}>\mathrm{r} \\ e^{1-r / c} & \mathrm{c} \leq \mathrm{r}\end{array}\right.$ r stands for length of reference
- $w_n$ is a weight (ususlly $1/N$)
- $p_n$ for 'how many word pieces (n-lengthed) in c are the same as r': $p_{n}=\frac{\sum_{C \in \text { candidates }} \sum_{n-\operatorname{gram} \in C} \operatorname{Count}_{c l i p}(n-g r a m)}{\sum_{C^{\prime} \in \text { candidates }} \sum_{n-g r a m \in C^{\prime}} \operatorname{Count}(n-g r a m)}$ (repeated n-grams will only be counted once)

codes can be found in [2] with `nltk`

#### Rouge: Recall Oriented Understudy for Gisting Evaluation 

BLEU is percision oriented: compare n-grams in c with r, but Rough compares n-grams in r with c

and there is a rough-L: $\frac{L C S(\text { candidate }, \text { reference })}{\text { len }(\text { reference })}$ focusing on the "longest common subsequence"

there are also variants like range-w with designed weights

codes can be found in [2] with `itertools` there also seems to be a package named `rough`

#### BLEURT (Bilingual Evaluation Understudy with Representations from Transformers)

let's train a model to evaluate! [6]

#### Zipf coefficient (distributional statistical evaluation)

**closer to one is better**

"Zipf’s law suggests that there is an exponential relationship between the rank of a word and its frequency in text" 

#### Repetition

**lower is better**

#### HUSE: Human Unified with Statistical Evaluation [8]

**higher is better**

computed by **training a discriminator** to distinguish between text drawn from the human and model distributions based on two features:

- probability assigned by the language model
- human judgements of typicality of generations

a combined human and statistical evaluation

#### Other metrics:

some semantic based (reading ease score...), grammar based metrics, ...

TER: Translation Edit Rate: ![img](https://miro.medium.com/max/426/1*dn5rJIrKwSNuJzb53DkFmg.png)

#### Related: 

[1] [**New Evaluation Metrics for Text Generation**](https://52paper.github.io/slides/20200514_rickywchen.pdf) (new ones)

[2] https://towardsdatascience.com/how-to-evaluate-text-generation-models-metrics-for-automatic-evaluation-of-nlp-models-e1c251b04ec1

[3] https://www.bilibili.com/video/av64670877/ (old ones and new ones)

[4] https://blog.csdn.net/codename_cys/article/details/108654792

[5] https://blog.csdn.net/index20001/article/details/78884646

[6] [BLEURT: Learning Robust Metrics for Text Generation](https://arxiv.org/abs/2004.04696)

[7] [Texygen: A Benchmarking Platform for Text Generation Models](https://arxiv.org/abs/1802.01886)

[8] [Unifying human and statistical evaluation for natural language generation](https://www-nlp.stanford.edu/pubs/hashimoto2019unifying.pdf)