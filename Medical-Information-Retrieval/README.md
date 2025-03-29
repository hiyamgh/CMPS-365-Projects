# Medical Information Retrieval

## Download the Archive
You can find the archive [here on OneDrive](https://mailaub-my.sharepoint.com/:u:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/medical-information-retrieval-archive.zip?csf=1&web=1&e=pIKspH)

## Archive Content

### Root Directory 

Files used for the experiments (lowercased, stop-word filtered, numbers removed, no punctuation, tokenized):
   
* {train,dev,test}.{all,titles,vid-titles,vid-desc,nontopic-titles}.queries     --      Queries in a tab-separated format: ID, TEXT 

* The query types are as constructed from the content fields of a fitness website:
  * **all**             - all fields concatenated: titles, descriptions, topics, transcripts and comments;
  * **titles**          - only all titles of content pages;
  * **nontopic-titles** - titles of all NutritionFacts.org pages except topic pages;
  * **vid-titles**      - titles of video pages;
  * **vid-desc**        - descriptions from videos pages.
  * The latter three types of queries often resemble queries an average user would type.

* {train,dev,test}.docs        --     Documents in a tab-separated format: ID, TEXT

* {train,dev,test}.3-2-1.qrel  --     Relevance files for 4 levels in total: direct links (3), indirect links (2), marginally relevant(1), others (0, not in the files). 
                                      In the TREC format: QUERY_ID, 0, DOC_ID, RELEVANCE_LEVEL
                                      Not used for the experiments, included for reference.

* {train,dev,test}.2-1-0.qrel  --     The same relevance files but for 3 levels in total: direct links (2), indirect links (1), marginally relevant and others (0, not in the files). 
                                      In the TREC format: QUERY_ID, 0, DOC_ID, RELEVANCE_LEVEL
                                      The 2-1-0 files were used for the experiments.

### In the ``raw/`` subdirectory:
* doc_dump.txt                 --      unfiltered dump of the document side of the corpus. 
                                         One line per document in a tab-separated format:
                                            ID, URL, TITLE, ABSTRACT
* nfdump.txt                   --      unfiltered dump of the fitness website site, one line per document in the following format: ID, URL, TITLE, MAINTEXT, COMMENTS, TOPICS_TAGS, DESCRIPTION, DOCTORS_NOTE, ARTICLE_LINKS, QUESTION_LINKS, TOPIC_LINKS, VIDEO_LINKS, MEDARTICLE_LINKS.  Some fields may be empty depending on the content type (i.e., videos, blog posts and Q&A).

* stopwords.large              --      a list of stop-words used for filtering

* {train,dev,test}.docs.ids    --      identificators of documents in the train, dev or test split (80%/10%/10%)

* {train,dev,test}.queries.ids --      identificators of queries in the train, dev or test split

* all_videos.ids               --      identificators of videos to help reconstruct some query types

* nontopics.ids                --      identificators of non-topic pages to help reconstruct some query types
