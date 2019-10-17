
## 1. Reading Wikipedia to Answer Open-Domain Questions (DrQA)

### Good aspect:
This work propose a two-stage pipeline to achive the mechine reading at scale on a single knowledge source, Wikipedia. A document retriever takes responsibility to retrieve from the large-scale Wikipedia data set and a document reader module is in charge of getting the best text span from the retrieved paragraphs. To test the effectiveness, the author conducts the DR models on four data sets. Among them, the SQuAD is used for training and the other three (Curated TREC, WebQuestions and WikiMovies) for testing. This is a kind of distant supervision (train a model on a data set while extracting information from another data set). They claim that by the results, we can observe thte task transfer is occurring.
### Limitations:
1. The document reader treats paragraphs independently (no reasoning).
2. Two DR systems pipeline, which is not an end-to-end system.

## 2. $R^3$: Reinforced Ranker-Reader for Open-Domain Question Answering

### Good aspects:
It has a similar idea with the DrQA. A Ranker takes responsibility of ranking all of the paragraphs (use reinforcement learning) and a Reader to extract the answer from the paragraphs. The Ranker uses a Match-LSTM to get the relation between the question and the paragraph. The Reader uses all of the potential useful vector to get probabilities of the start position and the end position. Jointly train the two models.

### Notion
Match-LSTM: use the attention scores (weights) between the question words and the paragraph words to get the representation of each word in the paragraph. On the other hand, the paragraph word has its own representation. Concate them and take this as the paragraph word representation. (Potentially, the word representation contains the relation between the question and the current paragraph)
### Limitations:
1. The model is far from the oracle performance (upper bound), this can be improved.
2. It doesn't contain the inter-relationship between paragraphs.

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzQ1MjAyNzc4LDE1MjYxNjk2NjksLTE0NT
g0Mjk5MzldfQ==
-->