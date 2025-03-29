# Scientific claim verification
Fact-checking – a task in which the veracity of an input claim is verified against a corpus of
documents that support or refute the claim – has been studied to combat the proliferation of 
misinformation in political news, social media, and on the web.

## The Archive

We are interested in the task of scientific claim verification to evaluate the veracity of  scientific claims against a scientific corpus.

This archive includes an expert-annotated dataset of 1,409 scientific claims, 
each paired with abstracts that either support or refute the claim. Each claim
is also annotated with rationales explaining the SUPPORTS / REFUTES decision.

To construct this dataset, we introduce a new annotation protocol where annotators
reformulate naturally occurring claims from scientific literature—specifically, 
citation sentences—into atomic scientific claims. Using citation sentences as the 
basis for claims helps accelerate the claim generation process while ensuring that the dataset covers topics representative of research literature. Additionally, citation links provide direct references to documents likely containing the evidence needed to verify each claim.

## Task Formulation
The inputs to our task are a scientific claim $c$ and a corpus of abstracts $A$. All abstracts $a \in A$ are labeled as $y(c, a) \in {SUPPORTS,
REFUTES, NOINFO }$ with respect to a claim $c$. The abstracts that either SUPPORT or REFUTE $c$
are referred to as evidence abstracts for $c$, denoted as $E(c)$. 
Each evidence abstract $a \in E(c)$ is annotated with rationales. A single rationale $R_i$ is
a collection of sentences ${r_1(c, a), . . . , r_m(c, a)}$,
where $m$ is the number of sentences in the rationale $R_i$ .
We denote the set of all rationales as $R(c, a) =
{R_1(c, a), . . . , R_n(c, a)}.$

Given a claim $c$ and a corpus $A$, the system
must predict a set of evidence abstracts $\hat{E}(c)$. For
each abstract $a \in \hat{E}(c)$, it must predict a label
$\hat{y}(c, a)$, and a collection of rationale sentences
$\hat{S}(c, a) = {\hat{s_1}(c, a), . . . , \hat{s_l}(c, a)}$. 
Note that although the gold annotations may contain multiple
separate rationales, to simplify the prediction task, we only require the model to predict a single collection of rationale sentences; these sentences may
encompass multiple gold rationales.

The task is to select abstracts from the research literature containing evidence that SUPPORTS or REFUTES a given scientific claim, and to identify rationales justifying each decision.

## The Data
A dataset of 1.4K expert-written scientific claims paired with evidence-containing abstracts annotated with labels and rationales.

You can find the archive [here on OneDrive](https://mailaub-my.sharepoint.com/:u:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/scientific-claim-verification-data.zip?csf=1&web=1&e=zJyVIo)

The data formats and code used to visualize and work with the data are described below.

### Outline

- [Claims](#claims)
- [Corpus](#corpus)

#### Claims
The claims are split into `claims_train.jsonl`, `claims_dev.jsonl`, and `claims_test.jsonl`, one claim per line. The claim and dev sets contain labels, while the test set is unlabeled. The corpus of evidence documents is `corpus.jsonl`, one evidence document per line.

The schema for the claim data is as follows:

`claims_(train|dev|test).jsonl`
```python
{
    "id": number,                   # An integer claim ID.
    "claim": string,                # The text of the claim.
    "evidence": {                   # The evidence for the claim.
        [doc_id]: [                 # The rationales for a single document, keyed by S2ORC ID.
            {
                "label": enum("SUPPORT" | "CONTRADICT"),
                "sentences": number[]
            }
        ]
    },
    "cited_doc_ids": number[]       # The documents cited by this claim's source citation sentence.
}
```

NOTE: In our dataset, the labels for all rationales within a single abstract will be the same. We provide a label annotation for each rationale in case future versions of the data have conflicting rationales within a single abstract.

An example is below. This claim was written based on a citation with 3 cited documents, of which only two were found to have evidence. Document `11328820` contradicts the claim, and has 1 rationale consisting of two sentences. Document `30041340` also contradicts the claim. It has two rationales: one with two sentences, and another with a single sentence.
```python
{
  "id": 263,
  "claim": "Citrullinated proteins externalized in neutrophil extracellular traps act indirectly to disrupt the inflammatory cycle.",
  "evidence": {
    "11328820": [
      { "sentences": [7, 9],
        "label": "CONTRADICT" }
    ],
    "30041340": [
      { "sentences": [0, 1],
        "label": "CONTRADICT" },
      { "sentences": [11],
        "label": "CONTRADICT" }
    ]
  },
  "cited_doc_ids": [
    11328820,
    30041340,
    14853989
  ]
}
```
** Note: you will not need the 5-fold cross validation split since we are not doing machine learning, but rather, information retrieval**
After unzipping the tarball, the data will organized like this:
```
data
| corpus.jsonl
| claims_train.jsonl
| claims_dev.jsonl
| claims_test.jsonl
| cross_validation
  | fold_1
    | claims_train_1.jsonl
    | claims_dev_1.jsonl
  ...
  | fold_5
    | claims_train_5.jsonl
    | claims_dev_5.jsonl
```

##### Explanation of `cited_doc_ids`

SciFact claims are generated by re-writing _citation sentences_ into atomic claims. The `cited_doc_ids` are the documents mentioned in the citation sentence used to generate a given claim. Cited documents containing evidence are annotated in the `evidence` field. For instance, in the example above, three documents were cited. Annotators found evidence in the abstracts of `11328820` and `30041340` but not in `14853989`.

#### Corpus

Below are the schema for evidence abstracts, along with an example.

Schema
```python
{
    "doc_id": number,               # The document's S2ORC ID.
    "title": string,                # The title.
    "abstract": string[],           # The abstract, written as a list of sentences.
    "structured": boolean           # Indicator for whether this is a structured abstract.
}
```

Example
```python
{
  "doc_id": 4983,
  "title": "Microstructural development of human newborn cerebral white matter assessed in vivo by diffusion tensor magnetic resonance imaging.",
  "abstract": [
    "Alterations of the architecture of cerebral white matter in the developing human brain can affect cortical development and result in functional disabilities.",
    ...
  ],
  "structured": false
}
```

