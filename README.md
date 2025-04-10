# CMPS 365 Projects

Please choose one project from the list below. Each project includes a detailed description and links to download the associated archive files.

## Cross-Language Information Retrieval 
Cross-language Information Retrieval (CLIR) has been studied for more than twenty years. Prior to the application of deep learning, strong statistical approaches were developed that work well across many languages. As with most other language technologies though, neural computing has led to significant performance improvements in information retrieval. Incorporation of neural advances into CLIR is now well underway.

Here, we present a cross-language information retrieval challenge. Topics are written in English, and three target language collections in _Chinese, Persian, and Russian_, are provided. Topics are written in the following format: a short title and a sentence-length description. Systems are to return a ranked list of documents for each topic.

### Single-Language News CLIR Tasks
The main task is ad hoc cross-language news retrieval.  Systems will receive a document collection in Chinese, Persian, or Russian, and a set of topics in English. For each topic, the system will return a ranked list of 1000 documents drawn from the document collection, ordered by likelihood of relevance to the topic.

Topics will be available in Chinese, Persian and Russian. In addition to CLIR runs with English queries (the main task), you are welcome t present submissions in which the query language is the same as the document language (i.e., monolingual runs), and submissions from systems in which the query language is neither English nor the document language (non-English CLIR runs).

Note: While queries are provided in multiple languages, we encourage the use of a single query language throughout a given retrieval pipeline; this is especially encouraged when queries are ingested by multiple systems for a single run.

Read more [here](./CLIR-Single-Language/).

### Multilingual News Retrieval (MLIR) Tasks
This task is identical to the Ad Hoc CLIR-Single-Language task, with the exception that for each query, systems must search all three news document collections and produce a single ranked list. That is, systems should treat the entirety of the `NeuCLIR1` collection (see below) across all three languages as a single corpus. The topics for the multilingual retrieval task will be identical to those of the ad hoc CLIR task. Participants should be aware that there is no guarantee that the set of relevant documents for a query will include documents from all three languages.

Read more [here](./CLIR-Multiple-Languages/).

## IR-COVID
The **IR-COVID** dataset is an **information retrieval benchmark** developed to evaluate search systems on **COVID-19-related scientific literature**. Based on a collection of research papers on **COVID-19, SARS-CoV-2, and related coronaviruses**, sourced from repositories like **PubMed, bioRxiv, and medRxiv**. The dataset consists of multiple **query topics**, such as *"What are the long-term effects of COVID-19?"*, along with **relevance judgments** manually assigned by experts. These judgments help determine whether a document is **relevant or not** to a given query. The dataset was released in **five rounds**, with each round introducing new queries and refined relevance assessments. 

Read more [here](./IR-COVID/).

## Medical Information Retrieval

Read more [here](./Medical-Information-Retrieval/).

## Non-Factoid Question-Anwering
Researchers have been increasingly interested in answer sentence and passage retrieval, particularly for non-factoid questions—which are open-ended and require complex answers, such as descriptions, opinions, or explanations. Unlike factoid questions that seek precise facts (e.g., “At what age did Rossini stop writing opera?”), non-factoid questions, such as “What is the reason for life?”, require more detailed responses, often at the passage level. These questions are crucial for improving question-answering systems, as current technologies are more advanced for factoid questions than for non-factoid ones.

To advance research in non-factoid question answering, we introduce a novel dataset containing 2,626 questions sourced from Yahoo! Answers, a community question-answering (CQA) platform.

To ensure high-quality data, we conducted a carefully designed crowdsourcing process involving multiple iterations, automatic and manual quality checks, and four-level relevance judgments.

Overall, the dataset provides 34,011 question-answer pairs, making it significantly larger than many comparable datasets and a valuable resource for evaluating term-matching and neural retrieval models.

Read more [here](./Non-Factoid-QA/).

## Patient to Article & Patient-to-Patient IR
Retrieval-based Clinical Decision Support (ReCDS) can aid clinical workflow by providing relevant literature and similar patients for a given patient. However, the development of ReCDS systems has been severely obstructed by the lack of diverse patient collections and publicly available large-scale patient-level annotation datasets. A novel dataset of patient summaries and relations is created to benchmark two ReCDS tasks: **Patient-to-Article Retrieval (ReCDS-PAR)** and **Patient-to-Patient Retrieval (ReCDS-PPR)**. Specifically, patient summaries from medical articles using simple heuristics, utilizing citations graph to define patient-article relevance and patient-patient similarity. The archive contains 167k patient summaries with 3.1M patient-article relevance annotations and 293k patient-patient similarity annotations, serving as one of the largest-scale resources for ReCDS and also one of the largest patient collections.

Read more [here](./Patient-to-Article-and-Patient-to-Patient-IR/). 

## Scientific claim verification
Fact-checking – a task in which the veracity of an input claim is verified against a corpus of
documents that support or refute the claim – has been studied to combat the proliferation of 
misinformation in political news, social media, and on the web.

We are interested in the task of scientific claim verification to evaluate the veracity of  scientific claims against a scientific corpus.

Read more [here](./Scientific-Claim-Verification/).  

## DBpedia-Entity

DBpedia-Entity is a widely used test collection for evaluating entity search over the DBpedia knowledge base. It is designed to assess retrieval systems that return a ranked list of entities (DBpedia URIs) in response to free-text user queries.

The first version of the collection, DBpedia-Entity v1, was introduced in 2013 and was based on DBpedia v3.7. It was developed by compiling search queries from various entity-oriented benchmarking initiatives and linking relevant results to DBpedia entities.

A second version, DBpedia-Entity v2, was released in 2017 as part of a collaborative effort involving the IAI group at the University of Stavanger, the Norwegian University of Science and Technology, Wayne State University, and Carnegie Mellon University.

Read more [here](./DBpedia-Entity/).  