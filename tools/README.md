This folder contains every tool (practice-first and theory-first) used in the AGFORSIM project.

A tool here means any structured way of knowing or designing an ecosystem, including:
	•	practice-first tools
(books, manuals, permaculture patterns, Indigenous methods, guild charts, field sheets)
	•	theory-first models
(ecosystem models, mathematical frameworks, documented simulators)
	•	software repositories
(GitHub/GitLab codebases relevant to ecosystem modelling)
	•	hybrid tools
(things that have both conceptual and computational components)

All tools are stored as individual Markdown files following a standard YAML template:
---
type: tool
kind: practice | theory | hybrid
title: ""
short_id: ""
author: ""
year: ""
format: book | pdf | guide | website | repo | chart | hybrid
domain: ""
region: ""
scale: micro | patch | field | farm | landscape | bioregion
digital: true | false

 # How much of this tool has been computationally implemented?
representation_level: 0   # 0 conceptual, 1 scoring, 2 heuristic, 3 partial model
has_code: false
language: R
code_path: ""              # e.g. src/base_models/permaculture_heuristic.py

 # Benchmark scoring (0 = fails, 1 = meets)
benchmarks:
  overlap: 0
  multilayer: 0
  dynamic: 0
  multiscale: 0
  cultural: 0
  interpretable: 0

status: unreviewed | reviewed | in-progress
links:
  - ""

 # Optional heuristic rules extracted from the tool
heuristic_rules:
  - id: sample-rule
    description: ""
    condition: ""   # e.g. "design.layer_count >= 3"
    weight: 1.0

 # Notes will be written below after the frontmatter
---
**END OF TEMPLATE**

This ensures that all forms of ecological wisdom—from code to Indigenous design heuristics—can be evaluated using the same conceptual benchmark structure.

⸻

How to Add a New Tool
	1.	Copy the contents of tool-template.yaml.
	2.	Create a new note in this folder: (put etal_ after <auth-lastname>_ if more than one)
	•	<auth-lastname>_<pub_year>.md
	3.	Paste the template and fill it out:
	•	metadata (author, domain, kind)
	•	benchmark scores
	•	notes, strengths, limitations
	•	any heuristics that can be expressed computationally
	4.	If the tool has computable elements:
	•	link or create a representation in src/base_models/
	•	note the path in the YAML (code_path)

⸻

Kinds of Tools

Each tool is tagged with:

kind:
	•	practice → design heuristics, patterns, experiential knowledge
	•	theory → formal models, equations, published simulations
	•	hybrid → conceptual + computational mix

representation_level:
	•	0 — conceptual only
	•	1 — scoring function extracted
	•	2 — heuristic engine (rule-based generator)
	•	3 — partial model implementation

This lets you include everything, while only coding what’s feasible.

⸻

Why Everything Lives Together

Instead of splitting practice/books and code/repos, this single folder:
	•	mirrors the fact that both kinds of knowledge shape agroecosystems
	•	allows direct comparison across benchmarks
	•	supports unified loading in Python for:
	•	scoring
	•	ensemble evaluation
	•	design heuristics
	•	acknowledges Indigenous and grassroots knowledge as first-class data
	•	keeps your thesis, code, practice notes, and ecological findings consistent

AGFORSIM works because it draws from plural knowledge traditions.
This folder is the heart of that pluralism.

⸻

Benchmarks

Every tool is evaluated against AGFORSIM’s ecological benchmarks:
	•	B1 Overlap
	•	B2 Multilayer interactions
	•	B3 Dynamics
	•	B4 Multiscale structure
	•	B5 Cultural grounding
	•	B6 Interpretability

These go in the YAML block at the top of each file.

⸻

How This Supports AGFORSIM

The Tools Folder enables:
	•	a review of all ecosystem modelling approaches (theory + practice)
	•	extraction of rules, heuristics, and principles from non-code sources
	•	code integration via lightweight representations
	•	ensemble comparison of:
	•	code models
	•	heuristic models
	•	practice-based scoring models
	•	a transparent, reproducible “functional bibliography” of everything used
	•	a bridge between:
	•	your microscope observations,
	•	farm-level design, and
	•	computational modelling

This folder is essentially the knowledge engine that AGFORSIM is built from.

# Method

To identify existing models, codebases, and tools relevant to AGFORSIM, an initial exploratory search was conducted primarily on **GitHub**, using a wide range of ecosystem-modelling queries. The aim was not to find perfect matches, but to build a **broad landscape scan** of computational approaches, ecological simulators, and modelling techniques that could inform the early benchmarking stage.

The process followed these steps:
### **1. Generate search terms from project themes**

Search queries were derived from the conceptual foundations of AGFORSIM, including:
- food forests
- agroforestry
- ecosystem services
- agent-based modelling
- ecological interactions
- network ecology
- forest dynamics
- soil modelling
- landscape simulation
- plant trait modelling
    
- sustainability simulators
    
- ecosystem productivity models
    
- forest-growth models
    
- microbial or soil-microbiome dynamics
    
- ensemble modelling
    
- multi-scale modelling
    
- complexity science models
    
- ecological networks
    
- succession models
    
- permaculture design tools
    
- environmental modelling frameworks
    

  

(These were iteratively refined as searches progressed.)

---

### **2. Run systematic GitHub searches**

Each term (and combinations of terms) was searched on GitHub.

Repositories were scanned rapidly (“first-glance relevance check”) for:

- presence of runnable code
- domain relevance
- whether the project includes:
    - ecological models
    - plant/forest simulation
    - soil/biome models
    - interaction networks
    - ABMs
    - spatial models
    - trait databases
    - climate/landscape models

  

Only repositories that met _basic relevance criteria_ were saved for cloning and deeper review.

---

### **3. Bookmark & collect candidates for cloning**
All potentially relevant repositories were:

- opened as Safari tabs
    
- visually reviewed for domain match
    
- filtered by:
    
    - code clarity
        
    - ecosystem modelling relevance
        
    - licence openness
        
    - maintainability
        
    - potential to yield reusable components
        
    
- and then saved for structured import into the vault.
    

  

This produced a dataset of **“candidate models”** that may contain:

- code worth adapting
    
- conceptual frameworks worth analysing
    
- benchmarks for comparison
    
- ensemble components
    
- system architectures
    
- modelling patterns
    
- network or spatial logic
    
- useful ecological assumptions or simplifications
    

---

### **4. The repositories that remain = relevant code**

  

After closing irrelevant tabs, the remaining ones are:

  

> **The first-pass filtered set of ecosystem-modelling repositories that appear potentially useful for extraction, benchmarking, or ensemble construction.**

  

These now move into the **AGFORSIM Tools pipeline**:

1. export URLs
    
2. clone repos locally
    
3. create a tool note for each repo using the YAML template
    
4. perform deeper inspection and benchmarking
    
5. extract reusable components where applicable

# Workflow Algorithm

FOR each codebase in repos-github:
    
    1. CLONE/OPEN codebase
    
    2. SCAN for function definitions
       (grep for "function", "def", "fn", etc.)
    
    3. TRIAGE functions:
       - SKIP: trivial utilities, wrappers, I/O only
       - EXTRACT: domain logic, calculations, models
    
    1. CREATE 01_Tools/{codebase_author}.md if not exists
    
    2. FOR each function to extract:
        RUN ExtractComponent algorithm
        INCREMENT counter
        
        IF counter % 10 == 0:
            COMMIT to git
            TAKE BREAK
    
    3. WHEN codebase complete:
        NOTE completion in logs/
        REVIEW tool note for completeness