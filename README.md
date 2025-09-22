# 🛍️ E-Commerce Product Categorization Multi Agent System

This project implements an **agentic pipeline for e-commerce product classification** using **LangGraph, Pydantic, and LLMs**.
The system uses **Generator, Evaluator, and Mediator agents** to propose, review, and finalize product category assignments, ensuring higher accuracy and consistency than single-shot classification, such as the HDBSCAN clustering method.

---

## 🚀 Features

* **Agent-based architecture** (Generator → Evaluator → Mediator → Finalizer)
* **Schema enforcement with Pydantic** to guarantee valid JSON responses
* **Chunked classification pipeline** for handling large datasets efficiently
* **Category knowledge integration** for consistent taxonomy-based decisions
* **Fallback to mediator agent** when Generator and Evaluator disagree
* **Confidence scoring** for downstream analysis

---

## 🧠 How It Works

1. **Generator Agent**

   * Proposes a category for a product.
   * Uses taxonomy knowledge and product description.

2. **Evaluator Agent**

   * Accepts or rejects the Generator’s proposal.
   * Provides a counterproposal if rejected.

3. **Mediator Agent**

   * Resolves conflicts between Generator and Evaluator.
   * Makes the **final categorization decision**.

4. **Finalizer**

   * Logs and stores the final classification.

---

## 📊 Example Taxonomy

| Category              | Definition                                  | Example Products                        |
| --------------------- | ------------------------------------------- | --------------------------------------- |
| Home & Kitchen        | Household, cooking, or decor items          | Cookware sets, wall art, bedding        |
| Party Supplies        | Products for celebrations                   | Balloons, banners, party hats           |
| Festive Supplies      | Seasonal holiday products                   | Christmas ornaments, Halloween costumes |
| Clothing & Apparel    | Wearable items for men, women, and children | T-shirts, jeans, dresses                |
| Toys & Games          | Play and educational items                  | Dolls, puzzles, LEGO sets               |
| Jewelry & Accessories | Fashion and decorative items                | Necklaces, handbags, belts              |
| Office Supplies       | Products for workplaces and schools         | Pens, notebooks, printers               |
| Garden & Outdoor      | Gardening and outdoor living equipment      | Planters, lawn mowers, outdoor lights   |

---

## ⚙️ Installation

### 1. Clone the repo

```bash
git clone https://github.com/JavieraAlmendrasVilla/Multi-agent-system-product-classification.git
cd Multi-agent-system-product-classification
```

### 2. Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate   # On Linux/Mac
.venv\Scripts\activate      # On Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Usage

### Run classification on a sample

```python
test_result = agent_classify_sample(final_df, taxonomy, sample_size=30)
```

### Run full pipeline on a dataset

```python
final_result = run_pipeline_chunked(final_df, taxonomy, chunk_size=50)
```

---

## 🛠️ Technologies

* [LangGraph](https://www.langchain.com/langgraph) – stateful agent orchestration
* [LangChain](https://www.langchain.com/) – LLM interaction and prompting
* [Pydantic v2](https://docs.pydantic.dev/) – schema validation
* [Ollama](https://ollama.ai/) – LLM inference locally
* Python 3.11

---

## 📈 Example Output

```
🟢 Generator Agent running for product: "pink paper parasol"
🔎 Evaluator Agent checking product: "pink paper parasol", proposed category: Party Supplies
🤝 Mediator Agent resolving conflict for: "pink paper parasol"
✅ Finalized classification for product: pink paper parasol -> Party Supplies
```

Final dataframe includes:

* **Category** → Final category
* **Reason** → Explanation for decision
* **Confidence** → Confidence score (0.5–0.7 default)

---

## 🧪 Roadmap

* [ ] Improve taxonomy coverage (electronics, automotive, etc.)
* [ ] Add vector similarity fallback (cosine/HNSW) for ambiguous cases
* [ ] Deploy as API for batch processing
* [ ] Extend with multilingual product classification

---

## 🤝 Contributing

Pull requests are welcome! For major changes, open an issue first to discuss what you’d like to add.

---

## 📜 License

MIT License. See [LICENSE](LICENSE) for details.


