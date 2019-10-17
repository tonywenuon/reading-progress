
## 1. Reading Wikipedia to Answer Open-Domain Questions (DrQA)

### Good aspect:
This work propose a two-stage pipeline to achive the mechine reading at scale on a single knowledge source, Wikipedia. A document retriever takes responsibility to retrieve from the large-scale Wikipedia data set and a document reader module is in charge of getting the best text span from the retrieved paragraphs. To test the effectiveness, the author conducts the DR models on four data sets. Among them, the SQuAD is used for training and the other three (Curated TREC, WebQuestions and WikiMovies) for testing. This is a kind of distant supervision (train a model on a data set while extracting information from another data set). They claim that by the results, we can observe thte task transfer is occurring.
### Limitations:
1. The document reader treats paragraphs independently (no reasoning).
2. Two DR systems pipeline, which is not an end-to-end system.

## $R^3$: Reinforced Ranker-Reader for Open-Domain Question Answering

### Good aspects:
It has a similar 
### Limitations:

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NTg0Mjk5MzldfQ==
-->