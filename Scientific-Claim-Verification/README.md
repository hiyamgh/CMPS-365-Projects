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

## The Dataset
A dataset of 1.4K expert-written scientific claims paired with evidence-containing abstracts annotated with labels and rationales.

