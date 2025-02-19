# RAG-Faith-Embed
CS646 Final Project - The Impact of Embedding Methods on Faithfulness of Retrieval-Augmented Generation (RAG)

This study was performed for CS646 as a final project in the Fall 2024 semester. The project was worked on as a group of three members.

Overview
-----------
The intuition of the project is to explore the relationship between embedding techniques and faithfulness when using Retrieval-Augmented Generation(RAG) models. Thus, our study embarked to answer one question - Which embedding technique best maintains faithfulness
in responses produced by RAG models on a domain-specific dataset?
Specifically, we evaluated three embedding models -- **bge-small-en-v1.5, MedEmbed-small-v0.1, and all-MiniLM-L6-v2** on the **RAG-Mini-BioASQ** dataset. Our findings indicate that general-purpose embeddings can outperform domain-specific ones in maintaining faithfulness in generated responses.

Repo Structure
--------------
- files/ - Contains presentation files, reports, and diagrams
- generated-data/ - Contains a copy of the generated data in our study
- contributions/ - A file describing each author's contribution
- RAG_12_04.ipynb - The Jupiter notebook tracking our source code in the project
- README.md - This document

Installation
-------------
To replicate this work, you need to first visit the hugging-face website and create user logins. Then, you need to create login tokens for use. After those steps, you can follow the instructions in RAG_12_04.ipynb to run the processes. You may also need a Google account and mount to a Google Drive to run everything successfully, this is optional and can be bypassed by feeding paths to directories. If you're having trouble generating data, a copy of our generated data can be found in the corresponding folders. 

Details/Procedures
-------------------
Refer to files/overview_diagram.png, the start data is fed into three embedding models listed, which gives in result a vector database. The vector database is then fed into the RAG pipeline using the Milvus library. The top three contexts produced by this pipeline are then fed into Mistral AI (an LLM), where the answers with contexts are then fed into our faithfulness evaluation(Unsloth). Each embedding model receives a faithfulness score out of 100, and the results are listed below:

<div align="center">
  
| Model                     | Faithfulness Score |
|---------------------------|--------------------|
| bge-small-en-v1.5         | 97%                |
| MedEmbed-small-v0.1       | 93%                |
| all-MiniLM-L6-v2          | 92%                |

</div>

Results
-----------
The general-purpose bge-small-en-v1.5 outperformed the domain-specific MedEmbed-small-v0.1 in terms of faithfulness. Faithfulness evaluation using DeepEval showed that retrieved contexts play a significant role in reducing hallucinations.

Future Work
-----------
Future work should explore alternative LLMs, prompt engineering, and additional evaluation metrics. Expanding dataset coverage and incorporating larger models can provide deeper insights into embedding model selection.
