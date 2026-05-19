# TKLTA Core 100 Sentence Embeddings

Kindly find the key for languages with currently available datasets and their TKLTA language codes here: https://www.talkalotta.com/languages

---

This repository provides a collection of precomputed sentence embeddings for the **Talkalotta Core 100** corpora.  Each JSON file corresponds to one language variety and contains embeddings for 100 sentences.  The embeddings were generated with the [`sentence-transformers/LaBSE`](https://huggingface.co/sentence-transformers/LaBSE) model and are 768-dimensional floating point vectors.

## Repository contents

There are 50 JSON files named `TKLTA_*_100_MBDS.json`.  The code in each filename identifies the language or language variety.

## JSON formats

```json
{
  "Sentence 1": [0.12, -0.34, ...],
  "Sentence 2": [ ... ]
}
```

---

Some files use native scripts or region‑specific orthographies. Lines may not be strictly normalized, so minor formatting differences are expected.

---

These datasets are provided "as is" without warranty. They are intended for language learning, linguistics research, and natural language processing experiments.
