# Evaluation of different Embedding Models based on a SAP-specific German Dataset with mock questions

## It does matter which embedding model to choose when using RAG!

The evaluation structure can be seen in the Jupyter Notebook (embedding_evaluation.ipynb).

## RAG(E)

Retrieval Augmented Generation (RAG) plays an important role in the evaluation of various embedding models. 

RAG provides the grounding for today's chatbots and digital assistants and can thus clearly demonstrate how well and securely different models generate embeddings and how well they can be accessed.

RAG for enterprises is called RAGE and currently means a lot for the use of digital assistants based on specific business data of the company in which the digital assistant is used.

## Evaluation Metrics

The results of the evaluation are based on the RAG algorithm, which was written for each model. First, the next best answer (k-nearest-neighbors in vector space of the embeddings --> k = 1) is taken and we see how well it can generate the answer based on the data set of 100 questions of SAP-specific knowledge and how often it is wrong.

In the 2nd part of the evaluation, k is set to 3 to see how RAG works for each of the 3 nearest embeddings for the different models and how well they perform when considering multiple neighbor embeddings.

## Evaluation Results

### Result for Top 1 answers (RAG including next neighbor):

- Failure Score Mistral Embedding Model (mistral-embed):          7   => 93 %
- Failure Score OpenAI Embedding Model (text-embedding-ada-002):  13  => 87 %
- Failure Score OpenAI Embedding Model (text-embedding-3-small):  15  => 85 %
- Failure Score OpenAI Embedding Model (text-embedding-3-large):  7   => 93 %

Best model (for this dataset in German): mistral-embed, text-embedding-3-large

### Result for Top 3 answers (RAG including next 3 neighbors):

- Failure Score Mistral Embedding Model (mistral-embed):          4   => 96 %
- Failure Score OpenAI Embedding Model (text-embedding-ada-002):  3   => 97 %
- Failure Score OpenAI Embedding Model (text-embedding-3-small):  4   => 96 %
- Failure Score OpenAI Embedding Model (text-embedding-3-large):  2   => 98 %

Best model (for this dataset in German): text-embedding-3-large

### Result for Top 5 questions (RAG including next 5 question-neighbors):

- Failure Score Mistral Embedding Model (mistral-embed):          2   => 98 %
- Failure Score OpenAI Embedding Model (text-embedding-ada-002):  2   => 98 %
- Failure Score OpenAI Embedding Model (text-embedding-3-small):  2   => 98 %
- Failure Score OpenAI Embedding Model (text-embedding-3-large):  2   => 98 %

Best model (for this dataset in German): all equal

Here you can see very clearly that different models perform differently as soon as you use several neighbors as comparison vectors for answers and questions. If you now connect an LLM and compare the 3 answers based on the input prompt and the LLM decides, the accuracy of the answers would be greatly improved.

### If you got any questions or feedback regarding this research, please reach out to me anytime via Teams or Mail (niklasdziwisch@web.de)
