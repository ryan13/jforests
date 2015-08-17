# Introduction #

The aim of risk-sensitive retrieval is to reduce the _risk_ that the system could perform worse than a baseline (e.g. BM25) for a given query.

Wang et al. (1) proposed that LambdaMART could be adapted to be more robust, or risk-sensitive, by adaptation of the loss-function. In particular, their URisk measure, which weights decreases in effectiveness (e.g. in terms of NDCG) more strongly than gains can be integrated into LambdaMART. The alpha >0 parameter defines how must emphasis down-side risk (losses compared to the baseline) obtain compared to relative gains.

Dincer et al (2) proposed new _adaptive_ risk-sensitive measures for LambdaMART based on the t-test statistic, namely SARO & FARO: Semi-Adaptive Risk-sensitive Optimisation (SARO) weights more strongly the alpha value for topics which exhibit significant downside risk. On the other hand, for Fully-Adaptive Risk-sensitive Optimisation (FARO), the alpha value for topics is varied according to the amount of risk (down-side or up-side) observed for the topic.

As of version 0.5, Jforests supports URisk, SARO & FARO.

# Usage #

**NB:** Citation: If you use the risk-sensitive evaluation in Jforests, please cite (2): B.T Dincer, C Macdonald, I Ounis. Hypothesis Testing for Risk-Sensitive Evaluation of Retrieval Systems. In Proceedings of SIGIR 2014.

To deploy URisk with alpha=1, based on the NDCG evaluation measure, the ranking.properties should be altered as follows:
```
#learning.evaluation-metric=NDCG
learning.evaluation-metric=URiskAwareEval:1:NDCG
```

To deploy SARO:
```
#learning.evaluation-metric=NDCG
learning.evaluation-metric=TRiskAwareSAROEval:1:NDCG
```

To deploy FARO:
```
#learning.evaluation-metric=NDCG
learning.evaluation-metric=TRiskAwareFAROEval:1:NDCG
```

# References #
(1) L Wang, P N Bennett, and K Collins-Thompson. Robust ranking models via risk-sensitive optimization. In Proceedings of SIGIR 2012. http://doi.acm.org/10.1145/2348283.2348385

(2) B T Dincer, C Macdonald, I Ounis. Hypothesis Testing for Risk-Sensitive Evaluation of Retrieval Systems. In Proceedings of SIGIR 2014.