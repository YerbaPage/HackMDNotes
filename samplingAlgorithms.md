# How to sample from language models

#### Q: 

- how are generation models trained? what are the different techniques? "During generation it is forced to complete its own automatically-generated context, a setting it has not considered during training." 

  [1]  [Adversarial Text Generation without Reinforcement Learning](https://arxiv.org/abs/1810.06640) 

  [2]  [RL-based idea](https://becominghuman.ai/generative-adversarial-networks-for-text-generation-part-2-rl-1bc18a2b8c60)

- performance of maximum likelihood sampling?

> from https://towardsdatascience.com/how-to-sample-from-language-models-682bceb97277#

"Humans often choose words that **surprise** language models (Holtzman et al 2019,  [The Curious Case of Neural Text *De*generation](https://arxiv.org/abs/1904.09751))"

<img src="https://miro.medium.com/max/1341/1*9sEpLZF8lV5OXwUQUMVZlg.png" alt="img" style="zoom: 33%;" />

- this generation often either gets stuck in repetitive loops or forgets the subject and goes off topic
- Sampling the the most likely word, the standard language model training objective causes us to get stuck in loops like “I don’t know. I don’t know. I don’t know.”

Popular sampling methods for generation are based on sampling from the distribution, and temperature and topk are adapted to avoid unrecoverable error by egregiously wrong tokens

#### Temperature sampling

"scaling"

```python
a = torch.tensor([1,2,3,4])
F.softmax(a/temperature, dim=0) # e.g. temp=1e-6, we get: [0, 0, 0, 1]
```

![img](https://miro.medium.com/max/469/0*pgyestIdYz0aNzX0)

"Lower temperatures make the model increasingly confident in its top choices, while temperatures greater than 1 decrease confidence. 0 temperature is equivalent to argmax/max likelihood, while infinite temperature corresponds to a uniform sampling."

#### Topk

removing the tail

but only taking top k doesn't work well for "Board distribution"

<img src="https://miro.medium.com/max/1284/0*J37qonVPJvKZpzv2" alt="img" style="zoom: 33%;" />

so here comes the **top p sampling** (aka nucleus sampling) to control the cumulative distribution

#### Why doesn’t maximum likelihood sampling work?

In the training process, there’s never a chance to see compounding errors: The model is trained to predict the next token based on a human-generated context. If it gets one token wrong by generating a bad distribution, the next token uses the “correct” human generated context independent of the last prediction. During generation it is forced to complete its own automatically-generated context, a setting it has not considered during training.

#### Fix training

- "could we train some kind of discriminator to punish the model when it generates whole sequences that don’t look human?"
- It’s not straightforward how to apply a GAN architecture to non-continuous domains
-  [Adversarial Text Generation without Reinforcement Learning](https://arxiv.org/abs/1810.06640) and an [RL-based idea](https://becominghuman.ai/generative-adversarial-networks-for-text-generation-part-2-rl-1bc18a2b8c60) but "have not yet become mainstream"

