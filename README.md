# TKLTA Core 100 Sentence Embeddings

This repository provides a collection of precomputed sentence embeddings for the **Talkalotta Core 100** corpora.  Each JSON file corresponds to one language variety and contains embeddings for 100 sentences.  The embeddings were generated with the [`sentence-transformers/LaBSE`](https://huggingface.co/sentence-transformers/LaBSE) model and are 768-dimensional floating point vectors.

## Repository contents

There are 50 JSON files named `TKLTA_*_100_MBDS.json`.  The code in each filename identifies the language or language variety.  Some files contain only a dictionary of sentence-to-embedding mappings, while others include an additional `metadata` section describing the source CSV, generation time and model used.

Example files with metadata include:

```
TKLTA_AFB_100_MBDS.json
TKLTA_ANDA_100_MBDS.json
TKLTA_ANDE_100_MBDS.json
TKLTA_AUEN_100_MBDS.json
... (see repository for full list)
```

Files without the `metadata` block start directly with the sentence keys.  Regardless of format, all embeddings use the same 768‑dimensional representation.

## JSON formats

**Without metadata**
```json
{
  "Sentence 1": [0.12, -0.34, ...],
  "Sentence 2": [ ... ]
}
```

**With metadata**
```json
{
  "metadata": {
    "source_csv": "Path to original CSV",
    "output_json": "Path to this JSON",
    "model_used": "sentence-transformers/LaBSE",
    "generated_on": "YYYY-MM-DDTHH:MM:SS",
    "sentence_count": 100,
    "format_description": "Dict[str, List[float]] - sentence to embedding mapping"
  },
  "embeddings": {
    "Sentence 1": [0.12, -0.34, ...],
    "Sentence 2": [ ... ]
  }
}
```

## Loading embeddings

```python
import json

with open('TKLTA_USEN_100_MBDS.json', 'r', encoding='utf-8') as f:
    data = json.load(f)

# For files with metadata, access the `embeddings` key
embeddings = data.get('embeddings', data)
first_sentence = next(iter(embeddings))
vector = embeddings[first_sentence]
print(len(vector))  # 768
```

## License

All files in this repository are part of the **Talkalotta Corpora** and are released under the [Creative Commons Attribution-ShareAlike 4.0 International License](https://creativecommons.org/licenses/by-sa/4.0/).  When using these embeddings, please credit Talkalotta as follows:

> "**[Name of Specific Dataset]** by **Talkalotta**, part of the Talkalotta Corpora, licensed under [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)"

