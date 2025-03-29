# IR-COVID
The **IR-COVID** dataset is an **information retrieval benchmark** developed to evaluate search systems on **COVID-19-related scientific literature**. Based on a collection of research papers on **COVID-19, SARS-CoV-2, and related coronaviruses**, sourced from repositories like **PubMed, bioRxiv, and medRxiv**. The dataset consists of multiple **query topics**, such as *"What are the long-term effects of COVID-19?"*, along with **relevance judgments** manually assigned by experts. These judgments help determine whether a document is **relevant or not** to a given query. The dataset was released in **five rounds**, with each round introducing new queries and refined relevance assessments. 

## Download the Archive
You can find the archive [here on OneDrive](https://mailaub-my.sharepoint.com/:u:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/IR-Covid-archive.zip?csf=1&web=1&e=wSShn2)

## Archive Description

### Queries (queries.jsonl)

A set of user queries related to COVID-19.

Each query has an ID, a textual question, and metadata that includes a reformulated search query and a narrative explaining the intent.

Example:
```
{
  "_id": "1",
  "text": "what is the origin of COVID-19",
  "metadata": {
    "query": "coronavirus origin",
    "narrative": "seeking range of information about the SARS-CoV-2 virus's origin, including its evolution, animal source, and first transmission into humans"
  }
}
```

### Document Corpus (corpus.jsonl)

A large collection of scientific research articles related to COVID-19.

Each document includes a unique ID, a title, the full text, and metadata (such as PubMed IDs and URLs).

Example:
```
{
  "_id": "ug7v899j",
  "title": "Clinical features of culture-proven Mycoplasma pneumoniae infections...",
  "text": "OBJECTIVE: This retrospective chart review describes...",
  "metadata": {
    "url": "https://www.ncbi.nlm.nih.gov/pmc/articles/PMC35282/",
    "pubmed_id": "11472636"
  }
}
```
### Relevance Judgments (qrels/test.tsv)

A ground truth relevance file mapping queries to documents.

Each row contains a query ID, a document ID, and a score indicating how relevant the document is to the query.

Example:
```
query-id  corpus-id  score
1         005b2j4b   2
1         00fmeepz   1
1         047xpt2c   0
```

#### Relevance Scores
* Score 2 → Highly relevant
* Score 1 → Partially relevant
* Score 0 → Not relevant