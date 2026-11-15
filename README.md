# ClaimTrace — NLP Evidence Alignment Explorer

**An interactive Human–AI Interaction research prototype using sentence embeddings to compare response claims with supplied reference material.**

Live demo: https://claimtrace-five.vercel.app/

## What it does

ClaimTrace accepts an AI-generated response and a reference document. It:
1. Splits both texts into sentences.
2. Generates semantic sentence embeddings with the pretrained `Xenova/all-MiniLM-L6-v2` model using Transformers.js.
3. Compares each response sentence with every reference sentence using cosine similarity.
4. Displays the closest passage and a similarity band to help users inspect evidence alignment.

## NLP implementation

- **Model:** all-MiniLM-L6-v2 (sentence-transformer)
- **Runtime:** Transformers.js in the browser
- **Task:** feature extraction / sentence embeddings
- **Similarity:** cosine similarity over normalized embeddings
- **Frontend:** HTML, CSS, vanilla JavaScript

The model is downloaded from a CDN on first use. No application backend or API key is required.

## Run locally

Open `index.html` in a modern browser with an internet connection. The browser loads Transformers.js and the model from their CDNs on first analysis.

## Research limitations

Semantic similarity is not factual verification, textual entailment, or a calibrated probability of support. A high similarity score can occur for a passage that contradicts a claim; a low score can occur for a valid paraphrase or a claim requiring multiple passages. The model may miss context, negation, temporal qualifiers, numerical differences, and domain-specific meaning.

The displayed bands are heuristic UI categories, not empirically validated thresholds. This prototype should be treated as an exploratory evidence-inspection aid—not a hallucination detector and not a tool for consequential decisions.

A research evaluation would need a labelled benchmark, comparison against suitable baselines (lexical overlap and NLI models), error analysis for negation/numbers/paraphrases, and user testing to assess whether the interface improves evidence-checking behaviour.

## Privacy

Pasted text is processed in the browser and is not sent to an application backend or stored by this app. The Transformers.js library and model files are fetched from external CDNs.

## License

Add a license before redistributing. Check the model and dependency licenses before reuse.
