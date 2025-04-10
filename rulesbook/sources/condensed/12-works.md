# Literature review

Here's a table that summarizes the main differences between the works in the literature.

## Rule sets in "symbolic" style

These works use rule sets to describe a given concept. Could potentially work without negative examples.

| **Work**                                                                                                                                                                          | **Year** | **Model** | **Learning**        | **Scalability**    | **Continuous data** | **TL;DR**                                 |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|-----------|---------------------|--------------------|---------------------|-------------------------------------------|
| [AQ18](https://drive.google.com/open?id=1fd1mClBe7Tea6SQl44CesAQHsO3gBoUy&usp=drive_fs) , [AQ20](https://drive.google.com/open?id=181Mprx_QriVWs3PCiZb5jn3fmxIKD8af&usp=drive_fs) | 1999     | Rule set  | Sequential covering | High $\sim O(N^3)$ | No                  | Seed examples are useful                  |
| [BRS](https://drive.google.com/open?id=1ip1mkmxtPLsu10CSFjrCfxUR0Pd0MHVV&usp=drive_fs)                                                                                            | 2016     | Rule set  | MCMC                | Medium-high        | No                  | Bayesian approaches extended to rule sets | 

## Rule lists in "symbolic" style

Rule lists are the most common way to group rules. They are historically learned with a sequential covering strategy,
even if more recent works explore the space more exhaustively.

| **Work**                                                                                  | **Year** | **Model** | **Learning**        | **Scalability**      | **Continuous data** | **TL;DR**                                 |
|-------------------------------------------------------------------------------------------|----------|-----------|---------------------|----------------------|---------------------|-------------------------------------------|
| [RIPPER](https://drive.google.com/open?id=17LqhbVQSimejk4McNcDayQ6wfmmqP1ug&usp=drive_fs) | 1995     | Rule list | Sequential covering | Medium $\sim O(N^2)$ | Yes (thresholds)    | Pruning controls overfitting              |
| [BRL](https://drive.google.com/open?id=14I5GcJe5uStIT4QQkgeYPhWHP7K66D4B&usp=drive_fs)    | 2015     | Rule list | MCMC                | Medium-high          | No                  | Bayesian approaches can work              |
| [SBRL](https://drive.google.com/open?id=107c4MRmaoyi61WkbzkPsEwCuaEIw-6J4&usp=drive_fs)   | 2017     | Rule list | MCMC                | Medium               | No                  | Higher scalabilty for bayesian approaches |
| [CORELS](https://drive.google.com/open?id=1G_xfJ0zo9W63z4sCCb6t_ERyOBrLrlkg&usp=drive_fs) | 2018     | Rule list | Exhaustive search   | Medium               | No                  | Search spaces can be reduced              |
| [SIRUS](https://drive.google.com/open?id=1uymiboSjddHlOmqVu5fUX3Bu_N5ytc9S&usp=drive_fs)  | 2020     | Rule set  | Algorithmic         | High                 | From RF             | Rules are extracted from Random Forests   |

## Deep rule networks in "symbolic" style

Few works attempt to learn deep rules without gradient-based optimization. The following work uses a mini-batch hill
climbing algorithm.

| **Work**                                                                                                                                                                           | **Year** | **Model**        | **Learning** | **Scalability** | **Continuous data** | **TL;DR**                                         |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|------------------|--------------|-----------------|---------------------|---------------------------------------------------|
| [DRNC](https://drive.google.com/open?id=1GUHn_Imi_Z2o6F8EwK6ymTpCY_vJP1BJ&usp=drive_fs), [DRNCv2](https://drive.google.com/open?id=15Y2jb9ehxeK3THjd_cs7IyRKUbHYC5yr&usp=drive_fs) | 2020     | Multilayer rules | Greedy       | Low             | No                  | Multilayer rules can be optimized combinatorially |

## Rule sets, gradient-based optimization

Flat rule sets can be learnt via gradient-based optimization, with different strategies.

| **Work**                                                                                  | **Year** | **Model** | **Learning**    | **Scalability** | **Continuous data** | **ILP** | **TL;DR**                                    |
|-------------------------------------------------------------------------------------------|----------|-----------|-----------------|-----------------|---------------------|---------|----------------------------------------------|
| [DR-Net](https://drive.google.com/open?id=1_HrjncdOWKnJR_yhjtvaEmCcgmivf8Hl&usp=drive_fs) | 2021     | Rule set  | Backpropagation | High            | Yes                 | No      | Flat rule sets learned with gradient descent |
| [FRR](https://drive.google.com/open?id=1QOApDKLLBqEwVWW5l7lwVPXKWAeD1S7G&usp=drive_fs)    | 2025     | TODO      |                 |                 |                     |         |                                              |

## Rule lists, gradient-based optimization

Rule lists can be encoded (e.g., with ternary schemes) and optimized with gradient-based optimization.

| **Work**                                                                                    | **Year** | **Model** | **Learning**    | **Scalability** | **Continuous data** | **ILP** | **TL;DR**                                                              |
|---------------------------------------------------------------------------------------------|----------|-----------|-----------------|-----------------|---------------------|---------|------------------------------------------------------------------------|
| [RL-Net](https://drive.google.com/open?id=18akcNVRNoqxx8NseHrJtVaweINshC0hh&usp=drive_fs)   | 2023     | Rule list | Backpropagation | High            | Yes                 | No      | Rule lists can be learned with gradient descent using a ternary scheme |
| [NEURULES](https://drive.google.com/open?id=116NDRTi-T2sfwNz5b-Ks_xWrv4Fdoxt4&usp=drive_fs) | 2024     | TODO      |                 |                 |                     |         |                                                                        | 

## Multilayer rules, gradient-based optimization

Multilayer networks can be used to learn rules. The following works use gradient-based optimization to learn rules.

| **Work**                                                                                                                                                                         | **Year** | **Model**           | **Learning**                   | **Scalability** | **Continuous data** | **ILP** | **TL;DR**                                                |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|---------------------|--------------------------------|-----------------|---------------------|---------|----------------------------------------------------------|
| [MLLP](https://drive.google.com/open?id=1uMuaQpDvZoXAMkl6fGUscGUTXsQR9rCf&usp=drive_fs)                                                                                          | 2020     | Multilayer rules    | Backpropagation, combinatorial | High            | No                  | No      | Random binarization helps to learn multilayer rules      |
| [RRL](https://drive.google.com/open?id=1T0iCeQjsuCixWrx_gaMkc_3JvH7Ig5Au&usp=drive_fs), [@IEEE](https://drive.google.com/open?id=1TDyqfhvSXsp4WDFUlfq5sJT7ZPssNqNW&usp=drive_fs) | 2021     | Weighted Rule Lists | Backpropagation                | High            | Yes                 | No      | Weighted rule lists can be learned with gradient descent |

## Explainability and logic-inspired networks

There are some works which focus on providing explanations (e.g., in concept-based models), or use loosely some logic
operators, e.g., to augment neural networks.

| **Work**                                                                                   | **Year** | **Model**                     | **Learning** | **Scalability** | **Continuous data** | **TL;DR**                                                                                |
|--------------------------------------------------------------------------------------------|----------|-------------------------------|--------------|-----------------|---------------------|------------------------------------------------------------------------------------------|
| [Net-DNF](https://drive.google.com/open?id=1S4on6jtKWaqcGrISZtvjFI1oLNxi6MBe&usp=drive_fs) | 2018     | Neural network                | GD           | High            | Yes                 | DNF structure is a valid inductive bias for a model                                      |
| [DDLGN](https://drive.google.com/open?id=15ZSBYS2C3g2C5J9kT5UkM7vRIbuNhkqB&usp=drive_fs)   | 2022     | Neural network                | GD           | High            | Yes                 | All logical functions with two arguments are useful as activation functions              |
| [KAN](https://drive.google.com/open?id=1M2gsh0RUt986fQDHphOpZr-BAg3xAQDk&usp=drive_fs)     | 2024     | Kolgomorov-Arnold network     | GD           | Medium          | Yes                 | Symbolic computation can be embedded into a network, together with spline approximations |

interepretable concept memory reasoner! 

## Inductive logic programming with gradient-based optimization

Some works integrate inductive logic programming to learn rules that put in relationship different predicates.

| **Work**                                                                                                                                                                       | **Year** | **Model**      | **Learning**    | **Scalability** | **Continuous data** | **ILP** | **TL;DR**                                                  |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|----------------|-----------------|-----------------|---------------------|---------|------------------------------------------------------------|
| [NLN](https://drive.google.com/open?id=11glJ_mjKoNAH_IpoMSAZDe3PVKK30PcT&usp=drive_fs), [dLN](https://drive.google.com/open?id=12QDCmL83TYb2gfm6G5iWnpiZYGZ0w-Bc&usp=drive_fs) | 2019     | Logic Programs | Backpropagation | High            | Yes                 | Yes     | First occurence of differentiable logic for learning rules |
| [DLM](https://drive.google.com/open?id=1Y59Ig3wEffCCQDhC3a6bcnMEjtsCHM2i&usp=drive_fs)                                                                                         | 2023     | Neural network | Backpropagation | High            | Yes                 | Yes     | ILP programs used for RL                                   |
| [FRE](https://drive.google.com/open?id=1xjTcq1Mn7plI3NzWDAJO_9PHfKzR76Cq&usp=drive_fs)                                                                                         | 2024     | TODO           |                 |                 |                     |         |                                                            |

## Related works in discrete optimization in backpropagation

Some works are widely cited for their contributions to optimize these discrete structures via gradient descent.

| **Work**                                                                                                | **Year** | **Model**       | **Learning**    | **Scalability** | **Continuous data** | **ILP** | **TL;DR**                                                              |
|---------------------------------------------------------------------------------------------------------|----------|-----------------|-----------------|-----------------|---------------------|---------|------------------------------------------------------------------------|
| [BNN](https://drive.google.com/open?id=10IkhRZHQwM-GXr2w-r0-Gto1NzS9H-DE&usp=drive_fs)                  | 2016     | Neural network  | Backpropagation | High            | Yes                 | No      | Binary neural network can be efficiently optimized                     |
| [GXNOR](https://drive.google.com/open?id=1t_SsiWY-gJAPUvzV14BvC88xUn2Shafu&usp=drive_fs)                | 2018     | Neural network  | Backpropagation | High            | Yes                 | No      | Ternary neural network can be efficiently optimized                    |
| [DFL](https://drive.google.com/open?id=1I_2aPVFpFQdxm_wIdGTatFARXREvNgpe&usp=drive_fs)                  | 2021     | N/A             | Backpropagation | High            | Yes                 | No      | Differentiable logic can be used to encode logical relationships       |
| [Binarize Cont. Feat.](https://drive.google.com/open?id=1W9TwYaOsSFEC7dHrC9BE9dlw5Wkciexq&usp=drive_fs) | 2023     | Neural networks | Backpropagation | High            | Yes                 | No      | Binarization of continuous features can be embedded in neural networks |

## Concept-based learning

A relevant research direction considers concept extraction and manipulation in order to create more robust and actionable models. Here's a (non-exhaustive) list of works. You can also refer to a more exhaustive survey on the topic from the [Neuro-symbolic AI journal](https://neurosymbolic-ai-journal.com/system/files/nai-paper-743.pdf), or from [the guys from Turin](https://arxiv.org/pdf/2312.12936). 

| **Work**                                                                                   | **Year** | **Model**                     | **Learning**    | **Scalability** | **Continuous data** | **TL;DR**                                                                 |
|--------------------------------------------------------------------------------------------|----------|-------------------------------|-----------------|-----------------|---------------------|---------------------------------------------------------------------------|

| [TCAV](https://drive.google.com/open?id=1sEpF52j8K5avLhryVEQPVhx12qx2bKGi&usp=drive_fs) | 2018 | Neural network                | GD              | High            | Yes                 | Labeled concepts used to distinguish what's happening in a hidden layer of a network |
| [CBM](https://drive.google.com/open?id=1wrbpmlth8RF6th555cbRJTU0rfaKY2jb&usp=drive_fs) | 2020 | Neural network                | GD              | High            | Yes                 | Labeled concepts are predicted to make predictions actionable and more robust |
| [LEN](https://drive.google.com/open?id=1d5v0Ng4vun6-qYZF5JdRFk6kXi_zlS2e&usp=drive_fs)     | 2023     | Neural network, concept-based | GD           | High            | Yes                 | Based on extracted (labeled) concepts, it is possible to extract FOL rules.              |
| [CBM-AUC](...) | todo | todo | todo | todo | todo | todo |
| [GlanceNets](...) | todo | todo | todo | todo | todo | todo |
| [ICBMR](...) | todo | todo | todo | todo | todo | todo |
