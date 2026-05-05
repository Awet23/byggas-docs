#### High quality data
	1. What kind of data are we dealing with(text, image, tabular)?
	2. Data source and implications around getting it?
	3. what needs to be done to the data so that it can be used to train a model?
		1. What steps are involved? What are the best practices?
		2. What tests can be performed on the data to ensure its quality?
	4. What process is involved in training a model?
	5. What options of methods do exist?
	6. What tools do we need?
	7. Are there opensource tools?
#### Compute
	1. What compute resource are needed to train a model?
	2. What are the options?
	3. What is our situation?
		1. How much can we afford?
		2. What is our capability? 
	4. Developing and testing vs deployment?
#### Software and Frameworks
	1. Gathering data?
	2. Cleaning the data?
	3. Tesing quality?
	4. Training model?
	5. Testing model?
	6. Does opensource tools exist?



### Training
#### Prompt Engineering & RAG
	1. How it works?
		- RAG is part of the backend logic. It searches and retrives relevant resource               from database. It is the process of searching the database, selecting the                 right sources, feeding them to the LLM and generating a grounded answer.
		- Builds propt with retreived context
		- Send prompt to LLM
		- Returns answer + resources
	2. pros and cons?
		- PROS
			- RAG is good because it can use **your own data**, keep answers more **up                  to date**, and return **source references**. You can update the database                  without retraining the model. It also makes it easier to control what                     information the LLM is allowed to use.
		- CONS
			- RAG depends heavily on the quality of retrieval. If the system retrieves                  the wrong sources, the LLM may give a weak or wrong answer. It also                       requires extra work: data ingestion, chunking, embeddings, metadata,                      search ranking, and source management. It is not just “connect data and                   it works perfectly.”
			
	3. How it fits our project?
		- Our data is based on **rules, regulations, guidance pages, and earlier                    **construction decisions**. Application serving such data must be: 
			- accurate
			- traceable
			- source-based
			- updated when data source change
			
#### Fine-Tuning / LoRA
	1. How it works?
	2. pros and cons?
	3. How it fits our project?

#### Pre-training from Scratch
	1. How it works?
	2. pros and cons?
	3. How it fits our project?



forskrifter: [[§ 11-1. Sikkerhet ved brann - Direktoratet for byggkvalitet](https://www.dibk.no/regelverk/byggteknisk-forskrift-tek17/11/i/11-1?_t_q=brann)](https://www.dibk.no/regelverk/byggteknisk-forskrift-tek17)