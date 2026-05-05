 What embedding dimensions are            
	  When you turn text into an embedding, you get a list of numbers — the length of that list is the "dimension." Think of it as how many
	  different aspects of meaning the model captures.
	
	  "§ 5-2 bebygd areal"  →  [0.12, -0.84, 0.33, ... 768 numbers total]
	
When you search, you compare that list against all stored chunk vectors to find the       most similar ones. The dimension affects three things:

![[Pasted image 20260502134454.png|537]]

For tens of thousands of regulation chunks, storage and speed differences are negligible at MVP scale. The meaningful question is search
  quality.


What matters more for your use case

  TEK17/SAK10 text is structured and formal. Chunks will be things like "§ 5-2. Bebygd areal (BYA)" — precise, consistent, short sections. For
  this kind of text, chunk quality and metadata matter more than extra dimensions. A well-structured 768-dim chunk will outperform a
  poorly-chunked 3072-dim one.

  Also: your content is in Norwegian. This is the most important factor when choosing a model.


 Relevant Gemini embedding models
![[Pasted image 20260502134605.png]]

recommendation for the app at this stage

  Use text-multilingual-embedding-002 with 768 dimensions.

  Reasons:
  - Norwegian is the primary language of your sources — using a multilingual model built for this is the right call
  - 768 dims is well-established, stable, and the schema in your document already uses VECTOR(768) — no changes needed
  - Free tier accessible
  - The structured chunking strategy (one section per chunk) is the bigger quality driver anyway
  - Easy to swap later if a better model becomes available
