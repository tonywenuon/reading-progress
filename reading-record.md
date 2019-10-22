
### Commmon places:
1. They all have a retriever and a reader.
2. They found that a retriever ranker is helpful for the results.
3. Predict end position on top of start position is helpful (not treat them independently)
4. A passage probability multiply with the predicted start/end position probability, which is helpful


## 1. Reading Wikipedia to Answer Open-Domain Questions (DrQA)

### Good aspect:
This work propose a two-stage pipeline to achive the mechine reading at scale on a single knowledge source, Wikipedia. A document retriever takes responsibility to retrieve from the large-scale Wikipedia data set and a document reader module is in charge of getting the best text span from the retrieved paragraphs. To test the effectiveness, the author conducts the DR models on four data sets. Among them, the SQuAD is used for training and the other three (Curated TREC, WebQuestions and WikiMovies) for testing. This is a kind of distant supervision (train a model on a data set while extracting information from another data set). They claim that by the results, we can observe thte task transfer is occurring. Note: the document retriever select top 5 articles for the document reader.
### Limitations:
1. The document reader treats paragraphs independently (no reasoning).
2. Two DR systems pipeline, which is not an end-to-end system.
3. Start and End position are treated independently. If there are multi-answers in a paragraph, the end position may be located at the second answer span, which is incorrent.

## 2. $R^3$: Reinforced Ranker-Reader for Open-Domain Question Answering

### Good aspects:
It has a similar idea with the DrQA. A Ranker takes responsibility of ranking all of the paragraphs (use reinforcement learning) and a Reader to extract the answer from the paragraphs. The Ranker uses a Match-LSTM to get the relation between the question and the paragraph. The Reader uses all of the potential useful vector to get probabilities of the start position and the end position. Jointly train the two models. Note that the Ranker only choose the most relevant one for the Reader.

### Notion
Match-LSTM: use the attention scores (weights) between the question words and the paragraph words to get the representation of each word in the paragraph. On the other hand, the paragraph word has its own representation. Concate them and take this as the paragraph word representation. (Potentially, the word representation contains the relation between the question and the current paragraph)
### Limitations:
1. The model is far from the oracle performance (upper bound), this can be improved.
2. It doesn't contain the inter-relationship between paragraphs.
3. It only selects the most relevant paragraph so it can't filter noise.
4. Start and End position are treated independently. If there are multi-answers in a paragraph, the end position may be located at the second answer span, which is incorrent.

## 3. Denoising Distantly Supervised Open-Domain Question Answering

### Good aspects:
The author propose a **paragraph selector** and a **paragraph reader**, which are similar to the previous two papers. The different part is the output of the paragraph selector. It obtains all of the potentially useful paragraph, and give each of them a probability that indicates how much the current paragraph relates to the question. This can be considered as a filter. 

### Limitations:
1. The predicted answers can further be re-ranked to get better results.
2. There is no reasoning process between the paragraphs in the model.
3. Start and End position are treated independently. If there are multi-answers in a paragraph, the end position may be located at the second answer span, which is incorrent.

## 4. Has-qa: Hierarchical answer spans model for open-domain question answering. 

### Good aspects:
This work summarises three different aspects between traditional Reading Comprehension (RC) and open-domain QA. 1) RC only contains useful paragraph, omitting paragraphs wittout answer string; 2) RC only considers the first answer span; 3) RC assumes the start position and the end position are independent. They propose a HAS-QA by using four modules. The basic idea is to give different paragraph a probability indicating the quality of the paragraph. And then predicting the end position conditioned on top of the start position. Akin to the paper Denoising Distantly Supervised Open-Domain Question Answering, it can filter noise to some extent.
### Limitations:
1. There is no reasoning process between the paragraphs in the model.

## 5. Multi-passage BERT: A Globally Normalized BERT Model for Open-domain Question Answering

### Good aspects:
Leverage the BERT to extract answer from the background knowledge. It provides that (1) global normalization makes QA model more stable by injecting a large number of parasssages. (2) treat the passage granularity with the passage window length (100) and sliding window with 50, this is helpful for getting all of the information. (3) Leveraging a BERT-based passage ranker improves the performance.
### Limitations:
1. There is no reasoning process (inter-correlation among passages) between the paragraphs in the model.

## 6. Learning to Transform, Combine, and Reason in Open-Domain Question Answering

### Good aspects:
This work adopts Transformer to get the representation. A novel multihop reasoning is used for reasoning between all of the document. With this approach, the model can make use of the low ranking documents. It is robust when injecting more documents.

### Limitations:
1. Keep the retrieval process a black box. They don't explore the retrieval process.
2. The decoder gets access to document-level, not word-level, potentially missing some useful information.

## 7. EVIDENCE AGGREGATION FOR ANSWER RE-RANKING IN OPEN-DOMAIN QUESTION ANSWERING

### Good aspects:
This work proposes re-rank method to improve the performance. After an Open-QA model gets all of the potential answers, the work uses two methods to re-rank them. A strength-based re-ranker (answer overlap count) and a coverage-based re-ranker (whether the evidence is able to cover most of the question).

### Limitations:
1. There is no reasoning process (inter-correlation among passages) between the paragraphs in the model.
2. It relys on the QA model to get the answer candidates.

## 8. Learning Natural Language Inference with LSTM
### Good aspects:
The author proposes a match-LSTM to match the question with another sequence to infer from each other. It belongs to the Natural language inference area. By the match-LSTM, the two sequences can be matched with an RNN and finally get a single vector to be as the match degree. 
### Limitations:
1. It doesn't have paragraph databases in the learning process. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyMTgxNDQzOCwyMDAwNzU5ODI0LDk2NT
A3MjExLC0zMDg0ODgxNzQsMjI2MzUzNTQ4LDEyMTEzMDgzNzcs
NDYxNTQ5NzQ4LDE3MTE2NTY5MCwxNzk2NDY4NzEwLC0xNjcxMD
YxNCwtOTMxOTIyNjg3LDE0MjU3NDc3NjQsNzQ1MjAyNzc4LDE1
MjYxNjk2NjksLTE0NTg0Mjk5MzldfQ==
-->