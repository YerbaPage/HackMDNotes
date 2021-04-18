### Consistency of a Recurrent Language Model With Respect to Incomplete Decoding

#### Ideas and Q:

- [x] What is length bias?

  "Encoder-decoder models exhibit a bias towards short sequences that surprisingly gets worse with increasing beam size."

  > Length bias in Encoder Decoder Models and a Case for Global Conditioning
  
- [ ] why are the methods like nucleus sampling called "incomplete"? because they have cut some "tails"?

- [ ] what does " 'inconsistency': can yield infinite length sequence **with zero probability**" mean? It has zero prob but happens?

#### Abstract

models trained with maximum likelihood performs well in many tasks but have problems like **"length bias"** and **"degenrate repetition"**

define **'inconsistency'**: can yield infinite length sequence with zero probability.

proved that popular decoding algorithms are inconsistent

proposed remedies:

-  consistent variants of top-k 
- self-terminating recurrent language models