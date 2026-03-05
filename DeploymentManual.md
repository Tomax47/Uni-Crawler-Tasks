# Deployment & User Manual

This project is optimized for **Google Colab**. Since all modules are interconnected, the user simply needs to execute the notebook cells in order.

## Prerequisites
- A Google account

## How to Run
1. **Open the Notebook:** Import the `.ipynb` file into Google Colab.
2. **Install Dependencies:** Run the first cell to install `pymorphy3`, `nltk`, `gradio`, and `beautifulsoup4`.
3. **Sequential Execution:** Run the cells from Task 1 through Task 5.

---

## Specific Task Instructions

### Task 3: Boolean Search
To test the Boolean search engine (AND, OR, NOT) manually, go to the last code cell of **Task 3** and **uncomment** the following block:

```python
print("Building inverted index...")
inverted_index, all_doc_ids = build_inverted_index(INPUT_DIR)

with open(INVERTED_INDEX_FILE, "w", encoding="utf-8") as f:
    for lemma, docs in sorted(inverted_index.items()):
        doc_list = " ".join(map(str, sorted(list(docs))))
        f.write(f"{lemma}: {doc_list}\n")

print(f"Inverted index saved to {INVERTED_INDEX_FILE}")
files.download(INVERTED_INDEX_FILE)

# < UNCOMMENT THE BELOW CODE  >

# print("\n--- Boolean Search ---")
# print("Operators: AND, OR, NOT, ()")

# user_query = input("Enter your query: ")
# results = search(user_query, inverted_index, all_doc_ids)

# print(f"\nResults for '{user_query}':")
# if results:
#     print(f"Found in documents: {sorted(list(results))}")
# else:
#     print("No documents found.")
```

### Task 5: Web Interface (Gradio)
The final cell launches the Vector Search Engine UI.

Normal Usage: The interface should appear directly inside the Colab cell output.

Troubleshooting: If the interface does not appear or remains blank within the notebook, look at the execution logs. Click the Public URL (ending in .gradio.live) to open the search engine in a new browser tab.

Example log view: `Running on public URL: https://a911180001c520dcfd.gradio.live`

<img src="Screenshot From 2026-03-05 22-57-37.png" alt="Search Engine Demo" width="600">

## Note:
During the demo, please ensure all previous cells have been executed so the doc_vectors and inverted_index variables are loaded into memory.
