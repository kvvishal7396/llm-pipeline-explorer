# LLM Pipeline Explorer

An interactive, visual, single-file teaching tool for exploring how Large Language Models process text — from tokenization and vocabulary construction to 3D embedding spaces and semantic similarity.

## Features

- **Part 1: Tokenizer**
  - **Vocabulary Builder**: Tokenizes training sentences, cleans/isolates punctuation, computes frequencies, and assigns token IDs (with `[UNK]` reserved for unknown words).
  - **Interactive Word-Keeping Slider**: Dynamically prune vocabulary to top $N$ words and watch subword splitting happen live.
  - **Color-coded Token Chips**: Consistent HSL pastel coloring per token ID with automatic subword breakdown (`##` prefix) for out-of-vocabulary terms.
  - **Detailed Statistics**: Real-time character counts, token counts, and compression ratio (characters per token).

- **Part 2: Embeddings in 3D**
  - **Spelling-Based Embedding**: Character 3-gram hashing into 64-dimensional normalized vectors.
  - **Meaning-Based Embedding**: Optional in-browser neural embeddings via Transformers.js (`Xenova/all-MiniLM-L6-v2`) with automatic fallback.
  - **Interactive 3D Scatter Plot**: Dimensionality reduction (PCA via power iteration in plain JavaScript) visualized using Plotly.js.
  - **Closest Pairs Table**: Top cosine similarity rankings across full vector representations.
  - **Custom Sentence Exploration**: Tokenize and project custom sentences into the 3D space with dedicated highlight markers and nearest-neighbor calculations.

## How to Run

Because this is built with zero dependencies, you can run it directly:

1. Clone the repository:
   ```bash
   git clone https://github.com/kvvishal7396/llm-pipeline-explorer.git
   cd llm-pipeline-explorer
   ```

2. Open `index.html`:
   - **Spelling-based mode**: Simply double-click `index.html` to open it in any web browser.
   - **Meaning-based mode**: To enable in-browser Transformers.js neural embeddings, serve over HTTP:
     ```bash
     python3 -m http.server 8000
     ```
     Then navigate to `http://localhost:8000`.

## Architecture & Constraints

- Single-file web app (`index.html` with inline CSS and JS).
- Zero npm dependencies, no build steps, no backend, and no API keys required.
- Beginner-friendly commented code explaining each stage of the pipeline.
