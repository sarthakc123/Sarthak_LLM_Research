# 🤖 Multi-Agent LLM Proposal Generator: A Research Prototype

This project simulates a team of autonomous LLM agents collaboratively drafting a cross-functional project proposal. It evaluates how well agents like a **Project Manager**, **Technical Lead**, and **Business Analyst** emulate real-world collaboration.

Built using:
- **Mistral-7B Instruct v0.2 (local GGUF)** for fast inference via `llama-cpp-python`
- **AutoGen-style roles**, with shared memory and log analysis
- Full support for **hallucination detection, repetition tracking, and concept growth metrics**

---

## 📚 Research Goals

- Can LLM agents emulate realistic cross-functional decision-making?
- Does reasoning improve across multiple rounds of conversation?
- How prone are autonomous agents to hallucination or topic drift?
- What evaluation strategies can benchmark multi-agent collaboration?

---

## 🛠️ Project Overview

| Component              | Description                                       |
|------------------------|---------------------------------------------------|
| `conversation_log.txt` | Transcript of 5 rounds of agent collaboration     |
| `Sarthak_Research_1.ipynb` | Main notebook with simulation, visualizations   |
| `hallucination_report.csv` | Optional export of hallucination flags         |
| `llm_topics_by_round.csv`  | Optional export of LLM-extracted round topics |

---

## 💬 Agents

- **ProjectManager**: Sets timeline, phases, deliverables
- **TechnicalLead**: Designs architecture, picks tech stack
- **BusinessAnalyst**: Understands user needs, defines KPIs

---

## 🧠 Evaluation Metrics

| Metric              | Description                                                  |
|---------------------|--------------------------------------------------------------|
| 🔁 Repetition        | Detects repeated phrases across agent replies                |
| 🎯 Role Alignment    | Checks if agents stay within their domain keywords           |
| 🧠 New Concepts      | Tracks keyword and topic diversity across rounds             |
| 🚨 Hallucination     | Flags off-topic or unverifiable terms                        |
| 🧩 LLM Topics        | Mistral-based topic summarization per round (semantic view) |

---

## 📊 Visualizations

- Concept growth per round (line chart)
- New concepts per agent/round (bar chart)
- Repetition and hallucination heatmaps
- LLM-generated topic bar chart (stacked horizontal)

> All generated using `matplotlib` in the main notebook

---

## 📦 How to Run

### 1. Clone and Load the Model
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

Place your `mistral-7b-instruct-v0.2.Q4_K_M.gguf` model inside a `/models` folder.

### 2. Install Dependencies
```bash
pip install llama-cpp-python matplotlib
```

### 3. Run Notebook
Open `Sarthak_Research_1.ipynb` in **Jupyter** or **Colab**  
Make sure to point to your model path correctly.

---

## 📊 Sample Output

<p align="center">
  <img src="https://placehold.co/600x300?text=Concepts+Per+Round" alt="New Concepts Graph">
</p>

---

## 📄 License

MIT License — feel free to fork and build upon this!

---

## ✍️ Author

**Sarthak Chandarana**  
LLM Systems Researcher  
Find me on GitHub or LinkedIn for questions or collaborations!
