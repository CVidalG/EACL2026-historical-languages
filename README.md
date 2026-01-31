### Lemmatization and POS-tagging of historical languages using LLM

This repository contains the experimental framework and code for the paper:

"Under-resourced studies of under-resourced languages: lemmatization and POS-tagging with LLM annotators for historical Armenian, Georgian, Greek and Syriac" (Vidal-Gorène et al., 2025).

**Abstract**: Low-resource historical languages pose persistent challenges for NLP tasks such as lemmatization and part-of-speech (POS) tagging. This project investigates the capacity of Large Language Models (LLMs), including GPT-4 variants and open-weight Mistral models, to address these tasks in zero-shot and few-shot settings. We focus on four diverse languages: Ancient Greek, Classical Armenian, Old Georgian, and Syriac.

#### Repository structure

```
├── data
│   ├── corpus              # Train/Test TSV files (in-domain and out-of-domain)
│   ├── prompt-templates    # Text templates for zero-shot and few-shot (5, 50, 500)
│   └── tagsets             # Language-specific POS tagsets
├── pie-baseline            # Configuration and models for the PIE baseline mentioned in the paper
├── results                 # Raw outputs of the paper
├── scripts                 # Core logic
│   ├── config.py           # Configuration (API keys, task definitions)
│   ├── main.py             # Execution script
│   └── utils.py            # Helper functions
├── requirements.txt
└── README.md
```

#### Getting started

1. Installation 
```bash
git clone https://github.com/anonymous/EACL2026_historical_languages.git
cd EACL2026_historical_languages
pip install -r requirements.txt
```

2. Configuration
Edit the config.py file to include your API keys, select models and define your local file paths:

```json
OPENAI_API_KEY = "your_key_here"
MISTRAL_API_KEY = "your_key_here"

TASKS = [
    {
        "name": "Zero Shot Armenian",
        "template": "path/to/template.txt",
        "test_file": "path/to/test.tsv",
        "tagset": "path/to/tagset.txt",
        "models": [
            {"provider": "openai", "name": "gpt-4o-mini"},
            {"provider": "mistral", "name": "mistral-large-latest"}
        ]
    }
]
```

To adapt the code to your language, you will have to update the `tagset`, the `prompt` and samples to provide.

3. Usage
Run the main script to start the annotation process:
```bash
python main.py
```

#### How to cite

TBD

#### Acknowledgements
This research was supported by the French National Research Agency (ANR), grant ANR-21-CE38-0006 (DALiH project), and conducted as part of the PSL Research University's Major Research Program CultureLab. We thank the GREgORI lab for data access.