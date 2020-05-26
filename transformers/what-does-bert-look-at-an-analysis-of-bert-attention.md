### Contribution
Methods for analyzing the attention mechanisms of pre-trained models (applied to BERT) are proposed. Findings show that BERT's attention heads exhibit patterns such as attending to delimiter tokens (SEP, CLS), specific positional offsets (previous, current and next tokens), or broadly attending over the whole sequence (CLS token). Attention heads in the same layer often exhibit similar behaviors (shown via clustering heads in one layer, and JSD of attention distributions of pairs of heads). Results conclude that substantial syntactic information is encoded in BERT.

### Key points
- Most heads put little attention on the current token, but there are heads that specifically attend to next or previous tokens especially in the earlier layers of the network
- A substantial amount of BERT's attention focuses on only a few tokens (SEP, CLS, period and comma)
- Attending to SEP token is used as a no-op step (when an attention head's function is not applicable)
- Using gradient-based measures (measuring the impact of changing the attention for a token on the model's outputs), it is shown that attending more or less to SEP does not substantially change the outputs (further evidence that SEP token is used as a no-op)
- Attention heads in lower layers have very broad attention distributions (roughly leading to a bag-of-vectors representation of the sentence)
- Entropy of the attention heads in the last layer from only the CLS token shows that it has a very broad attention distribution (CLS token in last layer encodes the entire sentence and is thus used for further classification tasks)
- Model's overall knowledge about syntax is distributed across multiple attention heads. However, many heads can be pruned away without damaging the performance.

### Code
- https://github.com/clarkkev/attention-analysis