# Cross-Language Information Retrieval 
Cross-language Information Retrieval (CLIR) has been studied for more than twenty years. Prior to the application of deep learning, strong statistical approaches were developed that work well across many languages. As with most other language technologies though, neural computing has led to significant performance improvements in information retrieval. Incorporation of neural advances into CLIR is now well underway.

Here, we present a cross-language information retrieval challenge. Topics are written in English, and three target language collections in _Chinese, Persian, and Russian_, are provided. Topics are written in the following format: a short title and a sentence-length description. Systems are to return a ranked list of documents for each topic.

## Single-Language News CLIR Tasks
The main task is ad hoc cross-language news retrieval.  Systems will receive a document collection in Chinese, Persian, or Russian, and a set of topics in English. For each topic, the system will return a ranked list of 1000 documents drawn from the document collection, ordered by likelihood of relevance to the topic.

Topics will be available in Chinese, Persian and Russian. In addition to CLIR runs with English queries (the main task), you are welcome t present submissions in which the query language is the same as the document language (i.e., monolingual runs), and submissions from systems in which the query language is neither English nor the document language (non-English CLIR runs).

Note: While queries are provided in multiple languages, we encourage the use of a single query language throughout a given retrieval pipeline; this is especially encouraged when queries are ingested by multiple systems for a single run.

## Tasks (Summarized)
| Task                                      | Document Language(s) | Query Language           | Topic Fields                  |
|-------------------------------------------|----------------------|--------------------------|--------------------------------|
| Single Language News                      | fas                  | eng, fas, other         | title, desc, both, other      |
| Single Language News                      | rus                  | eng, rus, other         | title, desc, both, other      |
| Single Language News                      | zho                  | eng, zho, other         | title, desc, both, other      |

You are invited to submit one or more of these tasks.  

## Data

Archive can be found [here on OneDrive](https://mailaub-my.sharepoint.com/:f:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/CLIR?csf=1&web=1&e=IYcArF)

### Data Formats

#### Documents
Documents are distributed in JSONL format, with one document in JSON format on each line. The fields present for each document are:
* id (string): The document ID for the document
* text (string): Complete text of the document
* date (string): YYYY-MM-DD or empty string
* lang (string): ISO 639-3 trigram


#### Input Format (Topics)
Topics are distributed as JSONL, with one topic per line. Each entry has (at least) the following fields:
* topic_id (string): A unique topic ID
* topics (array): A list of objects, each representing a variant of the topic. Each variant has the following fields:
  * lang (string): ISO 639-3 trigram indicating the language of the topic variant.
  * source (string): An indication of how the topic variant was constructed. Possible fillers include original, human_translation, and google_translation. The main task will use the original entry or the google_translation.
  * topic_title (string): A short (two or three words) description of the topic.
  * topic_description (string): A sentence-length description of the topic.
  * topic_narrative (string): A paragraph-long detailed description of what does and does not count as relevant to the topic.
