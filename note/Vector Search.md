

When a § section is ingested, it is not stored as plain text alone.
It is first passed through an embedding model
  (gemini-embedding-001) which reads the text and converts its
  meaning into a list of 768 numbers. This list is called a vector.
  Think of it like a GPS coordinate — just as a coordinate captures
  where something is in physical space, a vector captures where a
  piece of text sits in meaning space. Short or long, every text gets
   compressed into the same fixed size of 768 numbers. The model is
  trained to place texts with similar meaning close together in this
  space, and texts about different topics far apart.

  These 768-number vectors are stored in PostgreSQL using an
  extension called pgvector, which adds the ability to store and
  search vectors efficiently. Without pgvector, PostgreSQL would only
   understand exact matches — it has no built-in notion of
  similarity. pgvector adds a special operator (<=>) and an index
  that allows the database to quickly find the closest stored vectors
   to any given query vector.

  When a user asks a question, the same embedding model converts the
  question into its own 768-number vector. pgvector then compares
  this vector against every stored chunk vector and returns the top 5
   closest matches. Closeness is measured by the angle between the
  vectors — a small angle means similar meaning, a large angle means
  different meaning. This similarity is expressed as a relevance
  percentage in the UI: 90%+ means the chunk is very likely about
  exactly what was asked, below 70% means it was the best available
  but may not be a perfect match.

  The 5 retrieved chunks are then passed to gemini-2.5-flash
  alongside the user's question. Gemini reads the chunks and uses
  them as the sole source of truth to write the answer. It is
  explicitly instructed never to invent rules or section numbers — it
   can only explain what the retrieved chunks say.

  The same embedding model is used at both stages — ingestion and
  query — which is what makes the comparison meaningful. The question
   and the chunks are encoded in the same numerical language, so
  similar meanings produce similar vectors and the right chunks
  surface.