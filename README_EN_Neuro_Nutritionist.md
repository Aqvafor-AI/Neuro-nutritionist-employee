# 🧠 Neuro‑Nutritionist (RAG bot on GPT‑3.5)

An AI assistant that answers questions about food, calories, vitamins and healthy habits **strictly based on its own knowledge base**.

> Based on the notebook: `Neuro_nutritionist_employee.ipynb` (Google Colab/Jupyter).  
> Demo results are shown on screenshots in the `screenshots/` folder (see below).

---

## 📋 What it does
- Performs **RAG search** over a markdown knowledge base and injects retrieved chunks into the LLM prompt.  
- Answers **only from the database** (“Found facts: … / Answer: …”).  
- Includes a **safety filter** blocking harmful/unsafe queries (e.g., “how to induce vomiting”) and offensive language.  
- Can return short **recipes/tips** for relevant prompts.  
- Provides a minimal **web UI** (input field, `Submit/Clear` buttons, output panel).

---

## 🧩 Key components (from the notebook)
- **Knowledge base:** `neuro-nutrition-products.md` — structured facts (calories, vitamins, possible risks/notes, links).  
- **Vector search:** `vectorstore.similarity_search(query, k=3)` with duplicate chunk removal.  
- **System prompt:** “You are a neuro‑nutritionist; answer **only** from the base… If no answer is found — say it honestly.”  
- **LLM:** `openai.chat.completions.create(model="gpt-3.5-turbo", temperature=0.2)`.  
- **Filtering:** lists `bad_words` and `danger_phrases` + `check_filter(user_input)`.  
- **Main function:** `neuro_nutritionist_bot(user_input)` → (filter → RAG search → generation).

---

## 🧪 Demo (from screenshots)
Sample Q&A:
- “**How many calories in an apple?**” → *52 kcal.*  
- “**Which vitamins are in milk?**” → *Calcium, vitamin D.*  
- “**Write a light smoothie recipe**” → *1 banana, 1 apple, 200 ml water, blend…*  
- “**How much protein in banana?**” → *1.3 g.*  
- “**What’s the benefit of cottage cheese?**” → *Good for muscles.*  
- “**How to induce vomiting?**” → *Politely refused (safety filter triggered).*

Place screenshots into `screenshots/` and commit:
```
prakticeskaa-rabota-2-01.png
prakticeskaa-rabota-2-02.png
prakticeskaa-rabota-2-02 (1).png
prakticeskaa-rabota-2-03.png
prakticeskaa-rabota-2-2.png
prakticeskaa-rabota-2-3.png
prakticeskaa-rabota-2-4.png
prakticeskaa-rabota-2-5.png
prakticeskaa-rabota-2-6.png
prakticeskaa-rabota-2-7.png
prakticeskaa-rabota-2-8.png
prakticeskaa-rabota-2-9.png
```
Mini‑previews (examples):  
`![UI](screenshots/prakticeskaa-rabota-2-09.png)`  
`![RAG search](screenshots/prakticeskaa-rabota-2-6.png)`  
`![Safety filter](screenshots/prakticeskaa-rabota-2-5.png)`

---

## ⚙️ How to run
1. Open `Neuro_nutritionist_employee.ipynb` in Colab/Jupyter.  
2. Make sure `neuro-nutrition-products.md` is available (same folder or adjust path).  
3. Set `OPENAI_API_KEY` environment variable.  
4. Run all cells.  

> A simple web UI (Gradio/Streamlit) can be launched from the corresponding cells in the notebook.

---

## 🗂️ Recommended repo layout
```
Neuro-Nutritionist-Assistant/
├─ Neuro_nutritionist_employee.ipynb
├─ neuro-nutrition-products.md
├─ screenshots/
│   └─ *.png
└─ README.md  (this file)
```

---

## 📝 Output Data
Text responses and retrieved facts from the base (format “Found facts → Answer”).

---

## 📜 License
MIT
