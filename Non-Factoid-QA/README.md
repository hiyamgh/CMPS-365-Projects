# Non-Factoid Question-Anwering
Researchers have been increasingly interested in answer sentence and passage retrieval, particularly for non-factoid questions—which are open-ended and require complex answers, such as descriptions, opinions, or explanations. Unlike factoid questions that seek precise facts (e.g., “At what age did Rossini stop writing opera?”), non-factoid questions, such as “What is the reason for life?”, require more detailed responses, often at the passage level. These questions are crucial for improving question-answering systems, as current technologies are more advanced for factoid questions than for non-factoid ones.

To advance research in non-factoid question answering, we introduce a novel dataset containing 2,626 questions sourced from Yahoo! Answers, a community question-answering (CQA) platform.

To ensure high-quality data, we conducted a carefully designed crowdsourcing process involving multiple iterations, automatic and manual quality checks, and four-level relevance judgments.

Overall, the dataset provides 34,011 question-answer pairs, making it significantly larger than many comparable datasets and a valuable resource for evaluating term-matching and neural retrieval models.


## Archive Description
We conducted the following steps for pre-processing: (i) we kept the non-factoid questions of the dataset (which is called the nfL6 dataset), (ii) questions with less than 3 terms were omitted (excluding punctuation marks); (iii) questions with no user selected answer were removed; (iv) duplicate or near-duplicate questions were automatically identified and removed. (v) the questions under the categories of "Yahoo! Products" and "Computers & Internet" were omitted. 
From the remaining non-factoid questions, we randomly sampled 2,626 questions (out of 66,634), and dedicated 2426 questions to the training set, and 200 questions to the test set. 

The dataset contains four files, including 
* ``collection.txt`` 
* ``train-queries.txt`` 
* ``test-queries.txt``
* ``train.qrel`` 
* ``test.qrel``

You can find the archive [here on OneDrive](https://mailaub-my.sharepoint.com/:u:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/non-factoid-qa-dataset.zip?csf=1&web=1&e=dIPxEf)


The ``collection.txt`` file contains all candidate answers that should be considered for answer retrieval. It consists of all human written answers for 66,634 non-factoid questions that we obtained after pre-processing. The file format is tab-separated as follows:
```
CandidateAnswerId1	AnswerText1
CandidateAnswerId2	AnswerText2
```

The ``CandidateAnswerId`` format is ``x_y``, where ``x`` and ``y`` respectively denote the question id and the candidate answer id for the corresponding question. For instance, 2146313_8 shows the 9th candidate question for the question 2146313 (note that the candidate ids start from 0).

The files ``train-queries.txt`` and ``test-queries.txt`` respectively contain the question texts for the train and test splits, with the following tab-separated format:
```
QuestionId1	QuestionText1
QuestionId2	QuestionText2
```

``train.qrel`` and ``test.qrel`` consist of the relevance labels for the train and test queries. We asked 3 Amazon workers to judge each question-answer pair in a scale ranged from 1 to 4.The format of these two files is as follows:
```
QuestionId1	Q0\U0\E0	CandidateAnswerId1	RelevanceJudgement
QuestionId2	Q0\U0\E0	CandidateAnswerId2	RelevanceJudgement
```

where ``Q0`` means that this relevance label was collected via crowdsourcing; ``E0`` means that the crowdworkers did not agree and we could not aggregate their inputs in two rounds of crowdsourcing. Therefore, an expert judge those question-answer pairs. ``U0`` means that the answer was chosen by the asker (author of the question) as the correct answer.

Note that the test relevance labels were obtained through depth-k pooling (k=10). We collected 27,422 annotations for training, and 6,589 annotations for testing.

### Relevance Judgements
* **Label 4**: The answer looks reasonable and convincing. Its quality is on par
with or better than the “Possibly Correct Answer”. Note that
it does not have to provide the same answer as the “Possibly
Correct Answer”.
* **Label 3**: It can be an answer to the question, however, it is not
sufficiently convincing. There should be an answer with much
better quality for the question.
* **Label 2:** It does not answer the question or if it does, it provides an
unreasonable answer, however, it is not out of context. Therefore,
you cannot accept it as an answer to the question. 
* **Label 1**: It is completely out of context or does not make any
sense

To compute the evaluation metrics on this dataset, we recommend the following setting:
1. For the metrics with binary labels (e.g., MAP, MRR, Precision@k, Recall@k, etc.): Assume that labels 1 and 2 are non-relevant, and labels 3 and 4 are relevant.
2. For the metrics with graded relevance labels (e.g., NDCG): Map the 1-4 scale to the 0-3 scale (i.e., subtract all the labels by 1).

Note: The dataset may contain offensive (and noisy) questions and answers. We intentionally did not remove such queries to preserve the nature of the open-domain CQA data. However, if you prefer to omit these questions from your evaluation set, you can use the `test-queries-blacklist.txt` file and remove the mentioned query IDs from the test set.