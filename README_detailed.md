# 🧠 LLM Agent Research: AI-Driven Project Proposal Generation

This project demonstrates how multiple autonomous LLM agents can collaborate to draft a detailed project proposal — specifically for an AI-powered fitness and wellness app for seniors. The system tracks their interactions, evaluates performance, and visualizes behavior using a local Mistral model.

---

## 🚀 Project Goals

- Simulate cross-functional reasoning using LLM agents (PM, Tech Lead, BA)
- Track reasoning flow across multiple conversation rounds
- Evaluate output diversity, hallucination, topic drift, and role alignment
- Compare outputs with a single-agent GPT baseline
- Visualize how ideas emerge, repeat, or drift over time

---

## 🧰 Technologies Used

| Tool/Library            | Purpose                                           |
|-------------------------|---------------------------------------------------|
| `llama-cpp-python`      | Load and run the Mistral 7B GGUF model locally    |
| `matplotlib`            | Visualization of concept growth and agent behavior|
| `AutoGen-style logic`   | Structured group chat simulation via code         |
| `re`, `collections`     | Text processing and keyword extraction            |

---

## 📁 Key Files

| File                          | Description                                             |
|-------------------------------|---------------------------------------------------------|
| `Sarthak_Research_1.ipynb`    | Main notebook with logic, LLM prompts, and visualizations |
| `conversation_log.txt`        | Raw transcript of all agent responses                    |
| `hallucination_report.csv`    | Flags topic drift and hedging terms                      |
| `README.md`                   | Full documentation                                       |

---

## 🤖 Agents Involved

1. **ProjectManager** – defines timelines, deliverables, and project phases
2. **TechnicalLead** – outlines architecture, tech stack, integration plans
3. **BusinessAnalyst** – analyzes user needs, personas, KPIs, and success metrics

Each agent contributes over 5 rounds of conversation.

---

## 📦 Code Breakdown

### ✅ Log Extraction & Round Grouping

```python
with open("/content/conversation_log.txt") as f:
    blocks = f.read().strip().split("\n\n")
```
- Filters out non-agent entries
- Groups every 3 replies into one "round"

---

### ✅ Keyword-Based Concept Growth

```python
def extract_keywords(text):
    return set(re.findall(r'\b[a-zA-Z]{4,}\b', text.lower()))
```
- Uses regex to pull 4+ letter words as concepts
- Tracks newly introduced concepts per round

---

### ✅ LLM-Based Topic Summarization

```python
def extract_topics(text):
    prompt = f"""The following is a transcript..."""
    response = llm(prompt)
```
- Sends each round's content to Mistral
- Returns 3–6 short semantic topics

---

### ✅ Hallucination Detection

- Scans each response for:
  - ❌ Off-topic drift terms (e.g., "quantum", "aliens")
  - 🤔 Hedging phrases (e.g., "studies show", "people say")
- Results are logged to CSV for analysis

---

### ✅ Repetition & Redundancy Check

```python
seen_phrases = set()
def check_repetition(content):
    phrases = content.lower().split(". ")
    repeats = [p for p in phrases if p in seen_phrases]
```

---

### 📊 Visualizations

1. **Concept Growth per Round** (line chart)
2. **New Concepts per Agent or Round** (bar chart)
3. **LLM-Extracted Topics per Round** (stacked horizontal chart)
4. **Hallucination + Repetition flags** (optional CSV or heatmap)

---

## 🧪 Evaluation Highlights

| Metric               | Description                                        |
|----------------------|----------------------------------------------------|
| Role Alignment       | Keywords matched per agent domain (PM/TL/BA)       |
| Concept Growth       | How many new ideas emerged in each round           |
| Hallucinations       | Off-topic drift or unverifiable statements         |
| Repetition           | Reused phrases/sentences across rounds             |
| LLM Topics           | Semantic summaries of each round’s discussion      |

---

## 📤 How to Run

### 1. Install Dependencies
```bash
pip install llama-cpp-python matplotlib
```

### 2. Place Your Model
Download from Hugging Face:
`mistral-7b-instruct-v0.2.Q4_K_M.gguf` → `/models/` folder

### 3. Open and Run
Run `Sarthak_Research_1.ipynb` in Colab or Jupyter with GPU enabled.

---

## 📄 License

MIT License – free to use, remix, or adapt for research or learning.

---

## 👤 Author

**Sarthak Chandarana**  
LLM Evaluation | Open-Source Researcher  
GitHub: sarthakc123 | LinkedIn: sarthak-chandarana123
