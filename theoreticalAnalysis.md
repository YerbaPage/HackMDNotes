### A Theoretical Analysis of the Repetition Problem in Text Generation

#### Ideas and Q:


 - [ ] "repetition is cause by language itself", why not our models (or does it mean our language itself have many common words and this is the reason? )? We can design other ways (mixed) to improve diversity?

#### Abstract

there is no existing theoretical analysis to show why repetition happens and how it is resolved


"repetition is cause by language itself"


- many pieces predicts the same next word "high inflow"


- derived a concentration bound of the average repetition probability


- proposed a rebalanced approach to alleviate high inflow problem and reduce the upper bound


works well for translation and language modeling task

finds that most existing methods are minimizing the upper bound (explicitly or implicitly)
