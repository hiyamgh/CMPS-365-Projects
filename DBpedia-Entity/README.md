# DBpedia-Entity

DBpedia-Entity is a widely used test collection for evaluating entity search over the DBpedia knowledge base. It is designed to assess retrieval systems that return a ranked list of entities (DBpedia URIs) in response to free-text user queries.

The first version of the collection, DBpedia-Entity v1, was introduced in 2013 and was based on DBpedia v3.7. It was developed by compiling search queries from various entity-oriented benchmarking initiatives and linking relevant results to DBpedia entities.

A second version, DBpedia-Entity v2, was released in 2017 as part of a collaborative effort involving the IAI group at the University of Stavanger, the Norwegian University of Science and Technology, Wayne State University, and Carnegie Mellon University.

## Knowledge base

The test collection requires entities to have both a title and abstract (i.e., `rdfs:label` and `rdfs:comment` predicates)--this effectively  filters out category, redirect, and disambiguation pages. Note that list pages, on the other hand, are retained.  In the end, there are 4.6 million entities, each uniquely identified by its URI.  We use a simplified prefixed format:  `http://dbpedia.org/resource/Albert_Einstein` => `<dbpedia:Albert_Einstein>`.


## Queries

The collection consists of a set of heterogeneous entity-bearing queries, assembled from various benchmarking campaigns (see the paper for details). Queries are categorized into four groups:

| Category | Description | Examples |
| --- | --- | --- |
| `SemSearch_ES` | Named entity queries | "brooklyn bridge", "08 toyota tundra" |
| `INEX-LD` | IR-style keyword queries | "electronic music genres" |
| `QALD2` | Natural language questions | "Who is the mayor of Berlin?" |
| `ListSearch` | Queries that seek a particular list of entities | "Professional sports teams in Philadelphia" |

All queries are prefixed with the name of the originating benchmark.  `SemSearch_ES`, `INEX-LD`, and `QALD2` each correspond to a separate category; the rest of the queries belong to the `ListSearch` category.


## Relevance judgments

Relevance judgments are collected using crowdsourcing. To ensure high quality, we obtained further expert annotations for cases with substantial disagreement.
In total, over 49K query-entity pairs are labeled using a three-point scale (0: irrelevant, 1: relevant, and 2: highly relevant).


## Files

The **DBpedia-Entity v2** collection can be found under `collection/v2` and is organized as follows:

  - `queries-v2.txt`: The set of 467 queries, where each line contains a query ID and query text pair.
  - `queries-v2_stopped.txt`: The same queries, with stop patterns and punctuation marks removed.
  - `qrels-v2.txt`: Relevance judgments in standard TREC format.
  - `folds/`: Partitioning of queries for 5-fold cross validation. This is provided to make results directly comparable by using the same partitioning for supervised approaches. A separate file is provided for each query subset; if training is done over the set of all queries, use the `all_queries.json` file.
  - `annotator_agreements.tsv`: Inter-annotator agreements between crowd workers (and expert annotators, if applicable) for each query-entity pair. The agreement scores are computed according to the Fleiss' kappa index (i.e., Eq (3) of [its Wikipedia article](https://en.wikipedia.org/wiki/Fleiss%27_kappa)). This information may be used as a proxy for query difficulty.

## Download the Collection
You can find the collection [here on OneDrive](https://mailaub-my.sharepoint.com/:f:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/DBPedia-Entity?csf=1&web=1&e=SFVM6q)
