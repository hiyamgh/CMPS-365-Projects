# Patient to Article & Patient-to-Patient IR
Retrieval-based Clinical Decision Support (ReCDS) can aid clinical workflow by providing relevant literature and similar patients for a given patient. However, the development of ReCDS systems has been severely obstructed by the lack of diverse patient collections and publicly available large-scale patient-level annotation datasets. A novel dataset of patient summaries and relations is created to benchmark two ReCDS tasks: **Patient-to-Article Retrieval (ReCDS-PAR)** and **Patient-to-Patient Retrieval (ReCDS-PPR)**. Specifically, patient summaries from medical articles using simple heuristics, utilizing citations graph to define patient-article relevance and patient-patient similarity. The archive contains 167k patient summaries with 3.1M patient-article relevance annotations and 293k patient-patient similarity annotations, serving as one of the largest-scale resources for ReCDS and also one of the largest patient collections.

## Choice of Task
For your project, you could choose either the **Patient to Article** or the **Patient-to-Patien** tasks.

## Dataset Link
You can find the dataset [here on OneDrive](https://mailaub-my.sharepoint.com/:u:/r/personal/hg31_aub_edu_lb/Documents/CMPS-365-Projects/patient2patient_patient2article.zip?csf=1&web=1&e=fsJIVO)

## Datasets
All files listed below have train, dev, and test splits.

The ``dataset/`` directory contains the following:

### PMC-Paitents_train.json

PMC-Patients-training/test/dev, each of which is a list of dict with keys:
- `patient_id`: string. A continuous id of patients, starting from 0.
- `patient_uid`: string. Unique ID for each patient, with format PMID-x, where PMID is the PubMed Identifier of source article of the note and x denotes index of the note in source article.
- `PMID`: string. PMID for source article.
- `file_path`: string. File path of xml file of source article.
- `title`: string. Source article title.
- `patient`: string. Patient note.
- `age`: list of tuples. Each entry is in format `(value, unit)` where value is a float number and unit is in 'year', 'month', 'week', 'day' and 'hour' indicating age unit. For example, `[[1.0, 'year'], [2.0, 'month']]` indicating the patient is a one-year- and two-month-old infant.
- `gender`: 'M' or 'F'. Male or Female.

Note that `PMC-Patients_human.json` present ground-truth patient notes, their ages, and genders. The `human_patient_id` and `human_patient_uid` are different from those in `PMC-Patients` since it's difficult to align human annotations with automatic annotations.


### patient2patient_retrieval/PPR_train.json

A dict where the keys are `patient_uid` of queries and each entry is a list of `patient_uid`, representing similar patients to the query patient.

### patient2article_retrieval/PAR_train.json

A dict where the keys are `patient_uid` of queries and each entry is a list of `PMID`, representing articles relevant to the query.

### PPR_PAR_human_annotations.json

Ground-truth of patient-patient similarity and patient-article relevance of top 5 results given by BM25 on human-annotated patient notes.

The keys are `human_patient_id` and each entry is a dict with `PMID`s and `patient_uid`s as keys, representing articles and patients, respectively, and numbers as values indicating type of relevance/similarity. For details, see our paper.

## Meta data
The ``meta_data/`` directory consists of the following files.

### PMIDs.json

PMIDs of articles from which PMC-Patients are extracted.
List of string, length 140,897.

### train_PMIDs.json & dev_PMIDs.json & test_PMIDs.json & human_PMIDs.json

PMIDs of articles in PMC-Patients-train/dev/test/human.
List of string.

### train_patient_uids.json & dev_patient_uids.json & test_patient_uids.json & human_patient_uids.json

Patient_uids of notes in PMC-Patients-train/dev/test/human.
List of string.

### PMC-Patients.json

PMC-Patients dataset, which is a list of dict with keys:
- `patient_id`: string. A continuous id of patients, starting from 0.
- `patient_uid`: string. Unique ID for each patient, with format PMID-x, where PMID is the PubMed Identifier of source article of the note and x denotes index of the note in source article.
- `PMID`: string. PMID for source article.
- `file_path`: string. File path of xml file of source article.
- `title`: string. Source article title.
- `patient`: string. Patient note.
- `age`: list of tuples. Each entry is in format `(value, unit)` where value is a float number and unit is in 'year', 'month', 'week', 'day' and 'hour' indicating age unit. For example, `[[1.0, 'year'], [2.0, 'month']]` indicating the patient is a one-year- and two-month-old infant.
- `gender`: 'M' or 'F'. Male or Female.

### patient2article_relevance.json

Full patient-to-article dataset.
A dict where the keys are `patient_uid` of queries and each entry is a list of `PMID`, representing articles relevant to the query.

### patient2patient_similarity.json

Full patient-to-patient similarity dataset.
A dict where the keys are `patient_uid` of queries and each entry is a list of `patient_uid`, representing similar patients to the query.


### PMID2keywords.json & PMID2Mesh.json

Dict of PMIDs to keywords/MeSH terms of the article.

