# GitHub Copilot for VS Code: The Complete Tutorial

> An 8-week hands-on learning plan covering every GitHub Copilot feature in Visual Studio Code, with weekly data science exercises.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Week 1: Setup, Installation & Inline Code Completions](#week-1-setup-installation--inline-code-completions)
- [Week 2: Copilot Chat Fundamentals](#week-2-copilot-chat-fundamentals)
- [Week 3: Inline Chat & Code Transformations](#week-3-inline-chat--code-transformations)
- [Week 4: Agent Mode -- Autonomous Coding](#week-4-agent-mode----autonomous-coding)
- [Week 5: Testing, Debugging & Code Review](#week-5-testing-debugging--code-review)
- [Week 6: Documentation, Custom Instructions & Prompt Files](#week-6-documentation-custom-instructions--prompt-files)
- [Week 7: Advanced Features -- NES, Vision, MCP & CLI](#week-7-advanced-features----nes-vision-mcp--cli)
- [Week 8: Capstone -- End-to-End Data Science Project](#week-8-capstone----end-to-end-data-science-project)
- [Appendix A: Keyboard Shortcut Reference](#appendix-a-keyboard-shortcut-reference)
- [Appendix B: Copilot Settings Reference](#appendix-b-copilot-settings-reference)
- [Appendix C: Troubleshooting Common Issues](#appendix-c-troubleshooting-common-issues)
- [Appendix D: Plans & Pricing Comparison](#appendix-d-plans--pricing-comparison)
- [Appendix E: Glossary of Terms](#appendix-e-glossary-of-terms)

---

## Prerequisites

Before starting this tutorial, make sure you have:

1. **Visual Studio Code** (version 1.99 or later recommended) installed from <https://code.visualstudio.com>
2. **A GitHub account** at <https://github.com>
3. **A GitHub Copilot subscription** (Free, Pro, Business, or Enterprise). Students and open-source maintainers qualify for free access.
4. **Python 3.9+** installed with pip
5. **Familiarity with Python basics** and common data science libraries (pandas, numpy, scikit-learn, matplotlib)

### Recommended Python Environment Setup

```bash
python -m venv copilot-tutorial
# Windows
copilot-tutorial\Scripts\activate
# macOS / Linux
source copilot-tutorial/bin/activate

pip install pandas numpy scikit-learn matplotlib seaborn scipy jupyter pytest flask fastapi uvicorn
```

---

## Week 1: Setup, Installation & Inline Code Completions

### Learning Objectives

By the end of this week you will be able to install and configure GitHub Copilot in VS Code, understand how inline ghost-text suggestions work, and use keyboard shortcuts to accept, reject, and navigate suggestions efficiently.

---

### 1.1 Installing the Extensions

1. Open VS Code.
2. Go to the Extensions view (`Ctrl+Shift+X`).
3. Search for **GitHub Copilot** and click **Install**.
4. Search for **GitHub Copilot Chat** and click **Install** (bundled in newer VS Code versions).
5. After installation, you will see a Copilot icon in the status bar at the bottom of the editor.

### 1.2 Signing In

1. Click the Copilot icon in the status bar, or open the Command Palette (`Ctrl+Shift+P`) and type `GitHub Copilot: Sign In`.
2. Follow the browser-based OAuth flow to authenticate with your GitHub account.
3. Once signed in, the status bar icon changes to indicate Copilot is active.

### 1.3 Verifying Your Subscription

| Plan       | Price             | Key Limits                              |
|------------|-------------------|-----------------------------------------|
| Free       | $0/month          | 2,000 completions + 50 chat messages/mo |
| Pro        | $10/month         | Unlimited completions and chat          |
| Business   | $19/user/month    | Org-level policies, audit logs          |
| Enterprise | $39/user/month    | Fine-tuned models, knowledge bases      |

Check your subscription at: `https://github.com/settings/copilot`

### 1.4 How Inline Suggestions Work

When you type code, Copilot displays **ghost text** (dimmed, inline suggestions) that predict what you are likely to write next. Suggestions can range from a single variable name to an entire function body.

Copilot generates suggestions based on:

- The current file content (code above and below your cursor)
- Open tabs in your editor (neighboring files provide context)
- The file name and language
- Comments and docstrings

### 1.5 Keyboard Shortcuts for Inline Suggestions

| Action                          | Windows / Linux  | macOS           |
|---------------------------------|------------------|-----------------|
| Accept full suggestion          | `Tab`            | `Tab`           |
| Dismiss suggestion              | `Esc`            | `Esc`           |
| Show next suggestion            | `Alt+]`          | `Option+]`      |
| Show previous suggestion        | `Alt+[`          | `Option+[`      |
| Accept next word only           | `Ctrl+Right`     | `Cmd+Right`     |
| Trigger suggestion manually     | `Alt+\`          | `Option+\`      |
| Open completions panel          | `Ctrl+Enter`     | `Ctrl+Return`   |

### 1.6 Toggling Copilot On/Off

- Click the Copilot icon in the status bar to toggle suggestions globally or for specific languages.
- You can disable Copilot for certain file types in `settings.json`:

```json
{
  "github.copilot.enable": {
    "*": true,
    "markdown": false,
    "yaml": false
  }
}
```

### 1.7 Tips for Better Inline Suggestions

1. **Write descriptive comments first.** A comment like `# Load CSV, drop nulls, convert dates` gives Copilot clear intent.
2. **Use meaningful function and variable names.** `def calculate_moving_average(df, window)` yields better suggestions than `def func(a, b)`.
3. **Keep relevant files open.** Copilot reads neighboring tabs for context.
4. **Accept word-by-word** with `Ctrl+Right` when only part of a suggestion is useful.
5. **Cycle through alternatives** with `Alt+]` / `Alt+[` -- the first suggestion is not always the best.

---

### Week 1 Exercises (Data Science)

#### Exercise 1.1: Auto-Complete a DataFrame Loading Function

Create a new file `data_loader.py`. Type the following and let Copilot complete the function body:

```python
import pandas as pd

def load_and_preview(filepath: str, nrows: int = 5) -> pd.DataFrame:
    """Load a CSV file into a DataFrame and print shape, dtypes, and first n rows."""
```

- Press `Enter` after the docstring and wait for Copilot's suggestion.
- Accept with `Tab`. If the suggestion does not include `df.dtypes`, cycle with `Alt+]`.
- Verify the function works by calling `load_and_preview("your_data.csv")`.

**Goal:** Experience how docstrings drive Copilot's suggestions.

---

#### Exercise 1.2: NumPy Array Manipulation

Create `array_utils.py`. Write only the function signatures and docstrings below, then let Copilot fill in the bodies:

```python
import numpy as np

def normalize_array(arr: np.ndarray) -> np.ndarray:
    """Normalize array values to range [0, 1] using min-max scaling."""

def compute_statistics(arr: np.ndarray) -> dict:
    """Return a dict with mean, median, std, min, and max of the array."""

def create_polynomial_features(x: np.ndarray, degree: int) -> np.ndarray:
    """Generate polynomial features up to the given degree for a 1D array."""
```

- Accept each suggestion with `Tab`.
- Test with sample arrays to verify correctness.

**Goal:** Practice letting Copilot generate mathematical operations from clear signatures.

---

#### Exercise 1.3: Generate a Visualization from a Docstring

Create `visualize.py`. Write only the docstring:

```python
import matplotlib.pyplot as plt
import pandas as pd

def plot_correlation_heatmap(df: pd.DataFrame, title: str = "Correlation Matrix") -> None:
    """
    Plot a correlation heatmap for all numeric columns in the DataFrame.
    Use seaborn for styling. Annotate cells with correlation values.
    Save the figure as 'correlation_heatmap.png'.
    """
```

- Let Copilot generate the entire function.
- If `import seaborn` is missing, see if Copilot suggests adding it.
- Run the function on a sample DataFrame.

**Goal:** See how detailed docstrings produce near-complete implementations.

---

#### Exercise 1.4: Multi-Line Data Cleaning Pipeline

Create `data_cleaning.py`. Start typing:

```python
import pandas as pd

def clean_dataset(df: pd.DataFrame) -> pd.DataFrame:
    """
    Clean a raw dataset by:
    1. Dropping duplicate rows
    2. Filling numeric nulls with column median
    3. Filling categorical nulls with mode
    4. Converting date columns to datetime
    5. Resetting the index
    """
```

- Accept Copilot's multi-line suggestion for the entire pipeline.
- If the suggestion is partial, continue pressing `Enter` and accepting line-by-line.

**Goal:** Practice accepting multi-line suggestions and understanding how numbered lists in docstrings produce step-by-step code.

---

#### Exercise 1.5: Partial Acceptance for Model Training

Create `train_model.py`. Type:

```python
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report

def train_random_forest(X, y, test_size=0.2, n_estimators=100, random_state=42):
    """Train a Random Forest classifier and return the model with evaluation metrics."""
```

- When Copilot suggests the body, use `Ctrl+Right` to accept **word-by-word**.
- Modify parts of the suggestion as you accept it partially.
- Try rejecting one suggestion with `Esc`, typing a few characters, and then pressing `Alt+\` to trigger a new suggestion.

**Goal:** Master partial acceptance and manual re-triggering of suggestions.

---

## Week 2: Copilot Chat Fundamentals

### Learning Objectives

By the end of this week you will be able to use Copilot Chat to ask questions, get explanations, use chat participants and variables for targeted queries, and leverage slash commands for common tasks.

---

### 2.1 Opening Copilot Chat

There are three ways to access Copilot Chat:

| Method               | Shortcut          | Description                            |
|----------------------|-------------------|----------------------------------------|
| Chat Panel           | `Ctrl+Alt+I`      | Opens the chat view in the side bar    |
| Quick Chat           | `Ctrl+Shift+I`    | Opens an inline quick chat popup       |
| Inline Chat          | `Ctrl+I`          | Chat within the editor at your cursor  |

The Chat Panel supports three modes, selectable via a dropdown:

- **Ask** -- read-only Q&A; Copilot cannot modify files
- **Edit** -- Copilot can propose edits across files in a working set
- **Agent** -- fully autonomous mode (covered in Week 4)

### 2.2 Chat Participants

Chat participants are invoked with `@` and bring domain-specific expertise into the conversation.

| Participant    | Purpose                                                |
|----------------|--------------------------------------------------------|
| `@workspace`   | Searches your entire workspace for relevant context    |
| `@vscode`      | Answers questions about VS Code settings and features  |
| `@terminal`    | Assists with terminal/shell commands                   |

**Example prompts:**

```
@workspace How is the data pipeline structured in this project?
@vscode How do I change the Python interpreter?
@terminal How do I install tensorflow with GPU support using conda?
```

### 2.3 Chat Variables

Chat variables are prefixed with `#` and inject specific context into your prompts.

| Variable       | What It References                                     |
|----------------|--------------------------------------------------------|
| `#file`        | A specific file (you pick from a file picker)          |
| `#selection`   | The currently selected code in the editor              |
| `#editor`      | The entire visible content of the active editor        |
| `#codebase`    | Semantic search across the full project                |
| `#git`         | Git history, diffs, and branch information             |
| `#terminalLastCommand` | Output of the last terminal command             |
| `#terminalSelection`   | Selected text in the terminal                   |

**Example prompts:**

```
Explain this code: #selection
What does #file:data_loader.py do?
Find all functions related to feature engineering in #codebase
```

### 2.4 Slash Commands

Slash commands are shortcuts for common tasks. Type `/` in the chat input to see the full list.

| Command           | Action                                                 |
|-------------------|--------------------------------------------------------|
| `/fix`            | Suggest a fix for errors in the selected code          |
| `/tests`          | Generate tests for the selected code or file           |
| `/explain`        | Explain what selected code does                        |
| `/doc`            | Generate documentation for selected code               |
| `/new`            | Scaffold a new project or file                         |
| `/newNotebook`    | Create a new Jupyter Notebook                          |
| `/clear`          | Clear the chat history                                 |
| `/setupTests`     | Set up a testing framework for the project             |
| `/fixTestFailure` | Analyze and fix a failing test                         |

### 2.5 Asking Effective Questions

Follow these patterns for better chat responses:

1. **Be specific:** Instead of "fix this code," say "fix the `KeyError` on line 23 in `data_loader.py`."
2. **Provide context:** Use `#file` or `#selection` so Copilot knows exactly what you mean.
3. **State constraints:** "Optimize this function to use no more than O(n) time complexity."
4. **Ask follow-ups:** Chat remembers the conversation -- ask "Can you also add type hints?" after getting an initial answer.

### 2.6 Conversation Management

- `/clear` resets the conversation history.
- You can rename conversations for later reference.
- Conversations are saved and accessible from the chat history panel.
- Each new conversation starts with a clean context.

---

### Week 2 Exercises (Data Science)

#### Exercise 2.1: Explore a Project with @workspace

Make sure you have several Python files from Week 1 in your workspace. Open Copilot Chat and type:

```
@workspace Describe the structure of this project. What does each Python file do?
```

Then follow up with:

```
@workspace Which functions handle data cleaning, and where are they defined?
```

**Goal:** Learn how `@workspace` searches across all your project files to answer structural questions.

---

#### Exercise 2.2: Explain Code with #selection

Open `data_cleaning.py` from Week 1. Select the entire `clean_dataset` function body. In Copilot Chat, type:

```
Explain this code step by step: #selection
```

Then select just the line that fills nulls and ask:

```
Why is median used instead of mean for filling numeric nulls? #selection
```

**Goal:** Practice using `#selection` for targeted explanations of specific code blocks.

---

#### Exercise 2.3: Create a Jupyter Notebook with /newNotebook

In Copilot Chat, type:

```
/newNotebook Create an EDA notebook for a customer churn dataset with sections for:
1. Data loading and shape inspection
2. Missing value analysis
3. Distribution plots for numeric features
4. Correlation analysis
5. Target variable (churn) distribution
```

- Copilot will generate a complete `.ipynb` file.
- Open the notebook and review the generated cells.
- Run the cells with a sample churn dataset (or generate synthetic data).

**Goal:** Experience how `/newNotebook` scaffolds complete Jupyter notebooks from natural language.

---

#### Exercise 2.4: Terminal Help with @terminal

Open Copilot Chat and ask:

```
@terminal How do I create a conda environment named 'ml-project' with Python 3.11, pandas, scikit-learn, and jupyter?
```

Follow up with:

```
@terminal How do I export this conda environment to a YAML file for reproducibility?
```

Copy the suggested commands and run them in your terminal.

**Goal:** Use `@terminal` for environment management commands without leaving VS Code.

---

#### Exercise 2.5: Learn an ML Algorithm via Chat

Open Copilot Chat and have a learning conversation:

```
Explain the XGBoost algorithm. How does it differ from Random Forest?
```

Follow up:

```
Show me a Python code example comparing Random Forest and XGBoost on a classification task using scikit-learn compatible APIs.
```

Then:

```
What hyperparameters should I tune for XGBoost, and what are typical value ranges?
```

Copy the code into a new file and run it.

**Goal:** Use Copilot Chat as an interactive learning resource for data science concepts.

---

## Week 3: Inline Chat & Code Transformations

### Learning Objectives

By the end of this week you will be able to use Inline Chat for in-place code edits, perform code transformations (refactoring, type hints, error handling), and use multi-file editing for coordinated changes.

---

### 3.1 Inline Chat

Inline Chat (`Ctrl+I`) lets you give natural language instructions to edit code directly in the editor, right at your cursor position.

**How to use it:**

1. Place your cursor on a line, or select a block of code.
2. Press `Ctrl+I` -- a small input box appears inline.
3. Type your instruction (e.g., "add error handling", "make this async").
4. Copilot generates a diff preview showing the proposed changes.
5. Review the diff, then click **Accept** or **Discard**.

### 3.2 Common Inline Chat Commands

| Instruction                      | What It Does                                              |
|----------------------------------|-----------------------------------------------------------|
| "Add type hints"                 | Adds Python type annotations to function signatures/bodies|
| "Add error handling"             | Wraps code in try/except blocks                           |
| "Refactor into smaller functions"| Breaks a long function into helper functions               |
| "Optimize for performance"       | Suggests vectorized or more efficient implementations     |
| "Add logging"                    | Inserts logging statements at key points                  |
| "Convert to list comprehension"  | Transforms for-loops into comprehensions                   |
| "Make this a class method"       | Converts a standalone function into a class method         |
| "Add docstring"                  | Generates a documentation string                           |

### 3.3 Multi-File Editing (Copilot Edits)

Multi-file editing allows coordinated changes across multiple files:

1. Open the Chat Panel and switch to **Edit** mode.
2. Add files to the **Working Set** by clicking "Add Files" or dragging them in.
3. Describe the change you want across those files.
4. Copilot shows diffs for every affected file.
5. Review each diff and accept or reject individual changes.

**Use cases for multi-file editing:**

- Renaming a function and updating all call sites
- Adding a new parameter to a function and updating all callers
- Splitting a module into multiple files
- Applying a consistent code pattern across files

### 3.4 Editor Context Menu (Smart Actions)

Right-click on selected code to access Copilot actions:

- **Copilot > Explain This** -- get an explanation
- **Copilot > Fix This** -- suggest a fix
- **Copilot > Generate Docs** -- add documentation
- **Copilot > Generate Tests** -- create test cases

### 3.5 Reviewing Diffs

When Copilot proposes changes (via Inline Chat or Edit mode), it shows a side-by-side diff:

- Green highlighted lines are additions.
- Red highlighted lines are deletions.
- Click **Accept** to apply, or **Discard** to reject.
- In Edit mode, you can accept/reject changes per-file.

---

### Week 3 Exercises (Data Science)

#### Exercise 3.1: Refactor a Messy Function

Create `messy_analysis.py` with this deliberately messy code:

```python
import pandas as pd

def analyze(path):
    d = pd.read_csv(path)
    d = d.dropna()
    d = d[d['age'] > 0]
    d = d[d['salary'] > 0]
    avg_salary = d.groupby('department')['salary'].mean()
    max_salary = d.groupby('department')['salary'].max()
    count = d.groupby('department')['salary'].count()
    result = pd.DataFrame({'avg': avg_salary, 'max': max_salary, 'count': count})
    result = result.sort_values('avg', ascending=False)
    result.to_csv('department_stats.csv')
    print(result)
    return result
```

- Select the entire function.
- Press `Ctrl+I` and type: `Refactor this into clean, well-named functions with proper variable names and type hints`
- Review the diff and accept.

**Goal:** Experience how Inline Chat transforms code structure while preserving functionality.

---

#### Exercise 3.2: Add Type Hints to a Pipeline

Open `data_loader.py` from Week 1 (or create one without type hints). Select the functions and use Inline Chat:

```
Add comprehensive type hints to all functions, including return types and parameter types. Use typing module for complex types.
```

- Review the proposed type annotations.
- Accept the changes.

**Goal:** Practice using Inline Chat for systematic code quality improvements.

---

#### Exercise 3.3: Multi-File Refactoring

You should have `data_loader.py`, `data_cleaning.py`, `array_utils.py`, and `visualize.py` from Weeks 1-2.

1. Open the Chat Panel and switch to **Edit** mode.
2. Add all four files to the Working Set.
3. Type: `Create a main.py that imports and calls functions from all four modules in a logical data pipeline order: load, clean, transform, visualize. Add a __main__ block.`
4. Review the generated `main.py` and any updates to the other files.

**Goal:** Experience coordinated multi-file editing through Copilot Edits.

---

#### Exercise 3.4: Convert Procedural Code to OOP

Create `ml_pipeline_procedural.py`:

```python
import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

def load_data(path):
    return pd.read_csv(path)

def preprocess(df, target_col):
    X = df.drop(columns=[target_col])
    y = df[target_col]
    X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
    scaler = StandardScaler()
    X_train = scaler.fit_transform(X_train)
    X_test = scaler.transform(X_test)
    return X_train, X_test, y_train, y_test, scaler

def train(X_train, y_train):
    model = RandomForestClassifier(n_estimators=100)
    model.fit(X_train, y_train)
    return model

def evaluate(model, X_test, y_test):
    preds = model.predict(X_test)
    return accuracy_score(y_test, preds)
```

Select the entire file. Press `Ctrl+I` and type:

```
Convert this procedural code into a class called MLPipeline with methods for each step, storing state (scaler, model, metrics) as instance attributes
```

**Goal:** Learn how Copilot restructures code from one paradigm to another.

---

#### Exercise 3.5: Add Error Handling to a CSV Parser

Create `csv_parser.py`:

```python
import pandas as pd

def parse_csv(filepath, date_columns=None, required_columns=None):
    df = pd.read_csv(filepath)
    if date_columns:
        for col in date_columns:
            df[col] = pd.to_datetime(df[col])
    if required_columns:
        df = df[required_columns]
    return df
```

Select the function. Use Inline Chat:

```
Add comprehensive error handling: FileNotFoundError, empty file check, missing required columns validation, date parsing errors, and return informative error messages
```

**Goal:** See how Copilot wraps code with appropriate exception handling and validation logic.

---

## Week 4: Agent Mode -- Autonomous Coding

### Learning Objectives

By the end of this week you will understand how Agent Mode works as an autonomous coding assistant, how to activate it, how to review its proposed changes, and how to guide it to build complete features.

---

### 4.1 What Is Agent Mode?

Agent Mode is Copilot's most powerful feature. Unlike regular chat, Agent Mode:

- **Autonomously plans** multi-step tasks
- **Searches your workspace** for relevant files and context
- **Edits multiple files** without you adding them to a working set
- **Runs terminal commands** (with your approval) -- installs dependencies, runs tests, executes scripts
- **Self-corrects** by monitoring lint errors, compile errors, and test failures
- **Iterates** until the task is complete

Think of it as a pair programmer that can independently work through a task while keeping you informed.

### 4.2 Activating Agent Mode

1. Open the Chat Panel (`Ctrl+Alt+I`).
2. Click the mode dropdown at the top (defaults to "Ask").
3. Select **Agent**.
4. Type your task description and press Enter.

### 4.3 How Agent Mode Executes Tasks

```
Your Prompt --> Agent Plans Steps --> Searches Codebase --> Edits Files --> Runs Commands --> Checks Results --> Iterates
```

At each step, you can:

- **Review file edits** as inline diffs
- **Approve or reject terminal commands** -- Agent asks before running commands
- **Confirm command execution** with `Ctrl+Enter`
- **Edit suggested commands** before running them
- **Undo/redo** individual file edits within the response

### 4.4 Writing Effective Agent Mode Prompts

Good prompts for Agent Mode are:

- **Goal-oriented:** "Build a REST API that serves predictions from a trained model"
- **Specific about requirements:** "Use FastAPI, add input validation with Pydantic, include health check endpoint"
- **Context-aware:** "The model is saved as `model.pkl` in the `models/` directory"

Avoid:

- Vague prompts: "Make it better"
- Overly long prompts with every detail (Agent will figure out implementation details)

### 4.5 Terminal Command Approval

When Agent Mode needs to run a command, it shows the command and waits for approval:

- Press `Ctrl+Enter` to approve and run
- Click the command to edit it before running
- Reject if the command looks unsafe

Agent Mode may run commands like:

- `pip install <package>` to install dependencies
- `python <script.py>` to test code
- `pytest` to run tests
- `mkdir` to create directories

### 4.6 Auto-Correction

Agent Mode monitors its own output:

- If edited code produces lint errors, it automatically attempts to fix them.
- If a test fails after changes, it reads the error and iterates.
- If a terminal command fails, it adjusts the approach.

### 4.7 Multiple Agent Sessions

You can run multiple agent sessions simultaneously:

- Each session runs in its own chat thread.
- Use this for parallel tasks (e.g., one agent writes code while another writes tests).
- Background agents can continue working while you do other things.

---

### Week 4 Exercises (Data Science)

#### Exercise 4.1: Generate a Complete EDA Script

Switch to Agent Mode and type:

```
Create a complete exploratory data analysis script called `eda_analysis.py` that:
1. Loads a CSV file (path passed as command-line argument)
2. Prints dataset shape, dtypes, and basic statistics
3. Analyzes missing values (count and percentage per column)
4. Plots distributions for all numeric columns (histograms)
5. Plots value counts for categorical columns (bar charts)
6. Generates a correlation heatmap
7. Saves all plots to an 'eda_plots/' directory
8. Prints a summary report to console

Use argparse for CLI arguments. Use matplotlib and seaborn for plots.
```

- Let Agent Mode create the file, install any missing packages, and test it.
- Provide a CSV file path when Agent asks or test with a sample dataset.

**Goal:** Experience Agent Mode building a complete, runnable script from a detailed specification.

---

#### Exercise 4.2: Build a Prediction API

Make sure you have a trained model from Week 1 exercises (or ask Agent to train one first). Then prompt:

```
Build a FastAPI prediction API that:
1. Loads a trained scikit-learn model from 'model.pkl'
2. Has a POST /predict endpoint accepting JSON with feature values
3. Has a GET /health endpoint returning status
4. Includes input validation using Pydantic models
5. Returns predictions with confidence scores
6. Add a requirements.txt with all dependencies
7. Include a README with usage instructions

Create the project structure with src/ and tests/ directories.
```

- Agent Mode will create multiple files, install FastAPI, and may even start the server for testing.

**Goal:** See Agent Mode handle project scaffolding, multi-file creation, and dependency management.

---

#### Exercise 4.3: Add Production Features to Existing Code

With your existing pipeline files, prompt Agent Mode:

```
Add production-quality features to the existing Python files in this project:
1. Add structured logging (using Python's logging module) to all functions
2. Add error handling with custom exception classes
3. Create unit tests for every function using pytest
4. Add a configuration file (config.yaml) for file paths and parameters
5. Update any existing imports as needed
```

- Watch as Agent Mode navigates across files, adds imports, creates new files, and runs tests.

**Goal:** Experience Agent Mode enhancing existing code across multiple files.

---

#### Exercise 4.4: Project Structure Setup

Start with an empty directory. Prompt Agent Mode:

```
Set up a professional data science project structure with:
- src/ directory with __init__.py, data/, features/, models/, visualization/ subpackages
- tests/ directory mirroring src/ structure
- configs/ directory with a sample config.yaml
- notebooks/ directory with a template notebook
- requirements.txt with common DS libraries
- setup.py or pyproject.toml for package installation
- .gitignore for Python projects
- Makefile with targets: install, test, lint, clean
```

**Goal:** Use Agent Mode to bootstrap a full project in seconds.

---

#### Exercise 4.5: Notebook to Production Migration

Create a messy Jupyter notebook (`exploration.ipynb`) with mixed EDA, preprocessing, and modeling code. Then prompt Agent Mode:

```
Migrate the code in exploration.ipynb into production-ready Python modules:
1. Extract data loading into src/data/loader.py
2. Extract feature engineering into src/features/engineering.py
3. Extract model training into src/models/trainer.py
4. Extract visualization into src/visualization/plots.py
5. Create a main.py that orchestrates the full pipeline
6. Keep the notebook as a thin wrapper that imports from these modules
7. Add proper error handling and logging to all modules
```

**Goal:** See Agent Mode decompose a monolithic notebook into clean, modular code.

---

## Week 5: Testing, Debugging & Code Review

### Learning Objectives

By the end of this week you will be able to generate tests with Copilot, debug failing code, and use Copilot's code review capabilities to identify bugs and improvements.

---

### 5.1 Generating Tests

Copilot offers multiple ways to generate tests:

**Method 1: Slash Command**
```
/tests Generate tests for the clean_dataset function in data_cleaning.py
```

**Method 2: Context Menu**
- Right-click on a function > **Copilot** > **Generate Tests**

**Method 3: Inline Chat**
- Select a function, press `Ctrl+I`, type: `Write pytest tests for this function`

**Method 4: Agent Mode**
- Ask Agent Mode: `Write comprehensive tests for all functions in this project`

### 5.2 Setting Up Test Frameworks

Use the `/setupTests` command:

```
/setupTests Set up pytest with the following configuration:
- conftest.py with common fixtures
- pytest.ini with test discovery settings
- Sample test file demonstrating the project's testing patterns
```

Copilot will create configuration files and sample test structures.

### 5.3 Fixing Failing Tests

When a test fails, use `/fixTestFailure`:

1. Run your tests: `pytest --tb=short`
2. If a test fails, copy the error output.
3. In chat, type: `/fixTestFailure` and paste the error.
4. Copilot analyzes the failure and suggests a fix (either in the test or the source code).

### 5.4 Debugging with Copilot

**Explaining errors:**
```
I'm getting this error: ValueError: could not convert string to float: 'N/A'
The error occurs in #file:data_cleaning.py on line 15.
How do I fix this?
```

**Using /fix on selected code:**
1. Select the problematic code.
2. Type `/fix` in chat, or press `Ctrl+I` and type "fix the bug in this code."

**Debugging with terminal output:**
```
#terminalLastCommand
Explain this error and suggest a fix.
```

### 5.5 Code Review with Copilot

Ask Copilot to review your code for:

- **Bugs:** `Review #file:ml_pipeline.py for potential bugs`
- **Performance:** `Identify performance bottlenecks in #selection`
- **Security:** `Check this code for security vulnerabilities`
- **Best practices:** `Review this code against Python best practices and PEP 8`

Copilot will annotate specific lines with issues and suggest improvements.

### 5.6 Smart Actions

Right-click selected code to access quick actions:

| Action             | What It Does                                          |
|--------------------|-------------------------------------------------------|
| Explain This       | Provides a line-by-line or block explanation          |
| Fix This           | Identifies and fixes bugs                              |
| Generate Docs      | Creates docstrings or comments                         |
| Generate Tests     | Writes test cases for the selected code                |

---

### Week 5 Exercises (Data Science)

#### Exercise 5.1: Generate Tests for Feature Engineering

Create `feature_engineering.py`:

```python
import pandas as pd
import numpy as np

def add_age_bins(df: pd.DataFrame, col: str = "age", bins: list = None) -> pd.DataFrame:
    if bins is None:
        bins = [0, 18, 35, 50, 65, 100]
    labels = [f"{bins[i]}-{bins[i+1]}" for i in range(len(bins)-1)]
    df[f"{col}_bin"] = pd.cut(df[col], bins=bins, labels=labels)
    return df

def add_rolling_mean(df: pd.DataFrame, col: str, window: int = 7) -> pd.DataFrame:
    df[f"{col}_rolling_{window}"] = df[col].rolling(window=window).mean()
    return df

def encode_categorical(df: pd.DataFrame, columns: list) -> pd.DataFrame:
    return pd.get_dummies(df, columns=columns, drop_first=True)

def add_interaction_features(df: pd.DataFrame, col1: str, col2: str) -> pd.DataFrame:
    df[f"{col1}_x_{col2}"] = df[col1] * df[col2]
    df[f"{col1}_div_{col2}"] = df[col1] / df[col2].replace(0, np.nan)
    return df
```

Select all functions and use:
```
/tests Generate comprehensive pytest tests for all functions, including edge cases: empty DataFrames, missing columns, null values, and type errors
```

**Goal:** See how Copilot generates test cases that cover happy paths and edge cases.

---

#### Exercise 5.2: Debug a Failing Transformation

Create `buggy_transform.py` with intentional bugs:

```python
import pandas as pd

def transform_sales_data(df: pd.DataFrame) -> pd.DataFrame:
    # Bug 1: Wrong column name
    df['total_revenue'] = df['quantity'] * df['unit_price']

    # Bug 2: Incorrect date parsing
    df['order_date'] = pd.to_datetime(df['order_date'], format='%Y-%m-%d')

    # Bug 3: Division by zero not handled
    df['avg_price_per_unit'] = df['total_revenue'] / df['quantity']

    # Bug 4: Modifying original DataFrame
    monthly = df.groupby(df['order_date'].dt.month)['total_revenue'].sum()

    return df, monthly
```

Create test data that triggers the bugs, then:
1. Run the function and observe errors.
2. Select the error traceback, then use `/fix`.
3. Let Copilot identify and fix each bug.

**Goal:** Practice using `/fix` for systematic debugging.

---

#### Exercise 5.3: Code Review for ML Best Practices

Create `model_training.py` with common ML anti-patterns:

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score

def train_model(filepath):
    df = pd.read_csv(filepath)

    # Anti-pattern: scaling before split
    scaler = StandardScaler()
    X = scaler.fit_transform(df.drop('target', axis=1))
    y = df['target']

    # Anti-pattern: no train/test split
    model = LogisticRegression()
    model.fit(X, y)

    # Anti-pattern: evaluating on training data
    preds = model.predict(X)
    print(f"Accuracy: {accuracy_score(y, preds)}")

    return model
```

Ask Copilot:
```
Review #file:model_training.py for machine learning best practice violations. Identify anti-patterns and suggest corrections.
```

**Goal:** Learn how Copilot identifies domain-specific best practice violations (data leakage, overfitting, etc.).

---

#### Exercise 5.4: Edge Case Tests for Data Validation

Create `data_validator.py`:

```python
import pandas as pd

def validate_dataset(df: pd.DataFrame, schema: dict) -> dict:
    """
    Validate a DataFrame against a schema.
    Schema format: {'column_name': {'type': str, 'nullable': bool, 'min': float, 'max': float}}
    Returns dict with 'valid' (bool) and 'errors' (list of strings).
    """
    errors = []
    for col, rules in schema.items():
        if col not in df.columns:
            errors.append(f"Missing column: {col}")
            continue
        if not rules.get('nullable', True) and df[col].isnull().any():
            errors.append(f"Null values in non-nullable column: {col}")
        if 'min' in rules and (df[col] < rules['min']).any():
            errors.append(f"Values below minimum in column: {col}")
        if 'max' in rules and (df[col] > rules['max']).any():
            errors.append(f"Values above maximum in column: {col}")
    return {'valid': len(errors) == 0, 'errors': errors}
```

Use Inline Chat: `Generate edge case tests including: empty DataFrame, empty schema, columns with all nulls, mixed types, schema with only some columns present, boundary values at min/max`

**Goal:** Learn to prompt Copilot for thorough edge-case test coverage.

---

#### Exercise 5.5: Identify Memory Issues

Create `large_data_processor.py`:

```python
import pandas as pd
import numpy as np

def process_large_dataset(filepath: str) -> pd.DataFrame:
    df = pd.read_csv(filepath)
    results = []
    for idx, row in df.iterrows():
        processed = {
            'original': row.to_dict(),
            'squared': {col: val**2 for col, val in row.items() if isinstance(val, (int, float))},
            'normalized': {col: val/df[col].max() for col, val in row.items() if isinstance(val, (int, float))}
        }
        results.append(processed)
    all_squared = pd.DataFrame([r['squared'] for r in results])
    all_normalized = pd.DataFrame([r['normalized'] for r in results])
    final = pd.concat([df, all_squared.add_suffix('_sq'), all_normalized.add_suffix('_norm')], axis=1)
    return final
```

Ask Copilot:
```
Review this function for memory efficiency and performance issues. It needs to handle datasets with millions of rows. Suggest an optimized version using vectorized operations.
```

**Goal:** Use Copilot to identify and fix performance anti-patterns (iterrows, unnecessary copies, unvectorized operations).

---

## Week 6: Documentation, Custom Instructions & Prompt Files

### Learning Objectives

By the end of this week you will be able to generate documentation with Copilot, configure custom instructions for your project, create reusable prompt files, and select different AI models for different tasks.

---

### 6.1 Generating Documentation

**Docstrings:**
- Select a function, press `Ctrl+I`, type: `Add a NumPy-style docstring`
- Or right-click > **Copilot** > **Generate Docs**

**README generation:**
```
@workspace Generate a comprehensive README.md for this project including:
- Project overview
- Installation instructions
- Usage examples
- API documentation
- Contributing guidelines
```

**Inline comments:**
- Select complex code, use Inline Chat: `Add comments explaining the non-obvious logic`

### 6.2 Custom Instructions

Custom instructions tell Copilot how to behave for your specific project. They persist across sessions and apply to all interactions.

**Repository-level instructions:**

Create a file at `.github/copilot-instructions.md`:

```markdown
## Project Context
This is a data science project for customer churn prediction.

## Coding Standards
- Use Python 3.11+ features
- Follow PEP 8 and Google Python Style Guide
- Use type hints for all function signatures
- Use NumPy-style docstrings
- Prefer pandas vectorized operations over loops
- Use pathlib instead of os.path

## Libraries
- pandas for data manipulation
- scikit-learn for modeling
- matplotlib/seaborn for visualization
- pytest for testing

## Testing
- Write tests using pytest
- Use fixtures for common test data
- Aim for >80% code coverage
```

Copilot reads this file automatically and adjusts its suggestions accordingly.

### 6.3 Path-Specific Instructions

Create instruction files under `.github/instructions/` with YAML frontmatter to target specific paths:

**`.github/instructions/test-conventions.instructions.md`:**

```markdown
---
applyTo: "tests/**"
---
- Use pytest with fixtures from conftest.py
- Name test files as test_<module>.py
- Name test functions as test_<function>_<scenario>
- Use parametrize for multiple test cases
- Include docstrings describing what each test verifies
```

**`.github/instructions/data-processing.instructions.md`:**

```markdown
---
applyTo: "src/data/**"
---
- Always validate input DataFrames before processing
- Use logging instead of print statements
- Return copies of DataFrames, never modify in place
- Handle missing values explicitly
- Include timing decorators for performance monitoring
```

### 6.4 Prompt Files

Prompt files (`.prompt.md`) are reusable prompt templates stored in your project. Enable them in settings:

```json
{
  "chat.promptFiles": true
}
```

Create `.github/prompts/eda-template.prompt.md`:

```markdown
# EDA Template

Generate an exploratory data analysis for the given dataset:

1. Basic statistics (shape, dtypes, describe)
2. Missing value analysis with visualization
3. Distribution analysis for numeric features
4. Categorical feature analysis
5. Correlation analysis with heatmap
6. Outlier detection using IQR method
7. Target variable analysis (if applicable)

Use matplotlib and seaborn. Save all plots. Print summary findings.
```

Reference it in chat by typing `#prompt` and selecting the file.

### 6.5 VS Code Settings for Copilot

Key settings in `settings.json`:

```json
{
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": true,
    "yaml": true
  },
  "github.copilot.nextEditSuggestions.enabled": true,
  "github.copilot.chat.localeOverride": "en",
  "github.copilot.chat.codeGeneration.useInstructionFiles": true,
  "chat.promptFiles": true
}
```

### 6.6 Model Selection

In Copilot Chat, you can choose different AI models for different tasks:

| Model         | Best For                                          |
|---------------|---------------------------------------------------|
| GPT-4o        | General coding, explanations, fast responses       |
| Claude 3.5    | Long-context reasoning, detailed analysis          |
| o3-mini       | Complex logic, mathematical reasoning              |

Change the model by clicking the model name in the chat panel header.

---

### Week 6 Exercises (Data Science)

#### Exercise 6.1: Generate NumPy-Style Docstrings

Open `feature_engineering.py` from Week 5. Select all functions and use Inline Chat:

```
Add comprehensive NumPy-style docstrings to every function including Parameters, Returns, Raises, and Examples sections
```

Verify the docstrings follow this format:

```python
def add_age_bins(df: pd.DataFrame, col: str = "age", bins: list = None) -> pd.DataFrame:
    """
    Bin a continuous age column into categorical ranges.

    Parameters
    ----------
    df : pd.DataFrame
        Input DataFrame containing the age column.
    col : str, default "age"
        Name of the column to bin.
    bins : list, optional
        Bin edges. Defaults to [0, 18, 35, 50, 65, 100].

    Returns
    -------
    pd.DataFrame
        DataFrame with an additional '{col}_bin' column.

    Raises
    ------
    KeyError
        If the specified column does not exist in the DataFrame.

    Examples
    --------
    >>> df = pd.DataFrame({'age': [25, 45, 70]})
    >>> result = add_age_bins(df)
    >>> result['age_bin'].tolist()
    ['18-35', '35-50', '65-100']
    """
```

**Goal:** Practice generating standardized documentation across an entire module.

---

#### Exercise 6.2: Create Custom Instructions

Create `.github/copilot-instructions.md` in your project root with these instructions:

```markdown
## Project: Customer Churn Prediction

### Tech Stack
- Python 3.11
- pandas, numpy, scikit-learn, xgboost
- matplotlib, seaborn, plotly
- pytest, pytest-cov

### Code Style
- All functions must have type hints
- Use NumPy-style docstrings
- Maximum function length: 30 lines
- Use pathlib for file paths
- Use logging module, never print()
- Prefer f-strings over .format()

### Data Conventions
- Raw data in data/raw/
- Processed data in data/processed/
- Models in models/
- Plots in reports/figures/
```

After saving, create a new Python file and write a function. Observe how Copilot now follows your custom instructions (e.g., using logging instead of print, pathlib instead of os.path).

**Goal:** Experience how custom instructions shape Copilot's behavior project-wide.

---

#### Exercise 6.3: Path-Specific Instructions

Create two instruction files:

**`.github/instructions/source-code.instructions.md`:**
```markdown
---
applyTo: "src/**/*.py"
---
- Use defensive programming: validate all inputs
- Log function entry and exit at DEBUG level
- Use custom exceptions defined in src/exceptions.py
- Return immutable results where possible
```

**`.github/instructions/test-code.instructions.md`:**
```markdown
---
applyTo: "tests/**/*.py"
---
- Use pytest fixtures from conftest.py
- Use @pytest.mark.parametrize for multiple inputs
- Each test function must have a docstring
- Use assert with descriptive messages
- Test both success and failure cases
```

Now ask Copilot to generate a source file and a test file. Verify it follows different conventions for each.

**Goal:** See how path-specific instructions provide granular control over Copilot's behavior.

---

#### Exercise 6.4: Create Prompt Files

Create the following reusable prompt files:

**`.github/prompts/model-evaluation.prompt.md`:**
```markdown
# Model Evaluation Template

Evaluate the given model with:
1. Train/test accuracy, precision, recall, F1-score
2. Confusion matrix visualization
3. ROC curve and AUC score
4. Feature importance plot (top 20 features)
5. Cross-validation scores (5-fold)
6. Learning curve visualization
7. Summary of findings and recommendations
```

**`.github/prompts/data-quality-report.prompt.md`:**
```markdown
# Data Quality Report

Generate a data quality report:
1. Completeness: percentage of non-null values per column
2. Uniqueness: count of unique values, potential ID columns
3. Consistency: data type mismatches, mixed-type columns
4. Validity: values within expected ranges
5. Timeliness: date range analysis
6. Summary table with quality scores per column
```

Use these in chat with `#prompt:model-evaluation` to generate code following the template.

**Goal:** Build a library of reusable prompts for common data science workflows.

---

#### Exercise 6.5: Generate a Project README

Ask Copilot Chat:

```
@workspace Generate a comprehensive README.md for this project. Include:
1. Project title and description
2. Directory structure diagram
3. Installation and setup instructions
4. How to run the pipeline
5. How to run tests
6. Data dictionary (infer from code)
7. Model performance summary section (template)
8. Contributing guidelines
9. License section
```

Review and refine the generated README.

**Goal:** Use Copilot to generate professional project documentation from existing code.

---

## Week 7: Advanced Features -- NES, Vision, MCP & CLI

### Learning Objectives

By the end of this week you will be able to use Next Edit Suggestions for faster editing, attach images to Copilot Chat, configure MCP servers for external tools, and use Copilot in the terminal.

---

### 7.1 Next Edit Suggestions (NES)

NES predicts **where** and **what** you will edit next based on your recent changes. Unlike inline completions (which suggest new code), NES suggests changes to existing code.

**Enabling NES:**

```json
{
  "github.copilot.nextEditSuggestions.enabled": true
}
```

**How it works:**

1. You make a change (e.g., rename a variable on line 10).
2. A blue arrow appears in the gutter next to another line that needs a related change.
3. Press `Tab` to navigate to that suggestion.
4. Press `Tab` again to accept the change.
5. Continue pressing `Tab` to follow the chain of related edits.

**Common NES scenarios:**

- Rename a parameter -- NES suggests updating all usages in the function
- Change a return type -- NES suggests updating the type hint
- Modify a function signature -- NES suggests updating the docstring
- Fix a typo in one place -- NES catches the same typo elsewhere

### 7.2 Vision (Image Input)

Copilot Chat can accept images as input. This is useful for:

- Reproducing a chart from a screenshot
- Implementing a UI from a mockup
- Debugging from an error screenshot
- Describing a data visualization you want to recreate

**How to attach images:**

1. **Drag and drop** an image into the chat panel
2. **Paste from clipboard** (`Ctrl+V` in the chat input)
3. **Click the attachment icon** in the chat input bar

Supported formats: JPEG, PNG, GIF, WEBP

Vision requires the GPT-4o model to be selected.

### 7.3 Model Context Protocol (MCP)

MCP lets you extend Copilot with external tools and data sources.

**What MCP servers provide:**

- **Tools:** Functions that Copilot can call (e.g., query a database, call an API)
- **Resources:** Data that Copilot can read (e.g., documentation, schemas)
- **Prompts:** Pre-built prompt templates

**Configuring MCP servers in VS Code:**

Add to your `settings.json` or `.vscode/settings.json`:

```json
{
  "mcp": {
    "servers": {
      "my-database": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://localhost/mydb"]
      },
      "filesystem": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-filesystem", "/path/to/data"]
      }
    }
  }
}
```

**Using MCP tools in Agent Mode:**

Once configured, Agent Mode can automatically discover and use MCP tools. For example, with a database MCP server, you can ask:

```
Query the customers table and show the top 10 by total purchases
```

Agent Mode will use the database tool to execute the query.

**Managing MCP servers:**

- Open Command Palette > `MCP: List Servers` to see active servers
- Restart servers if they become unresponsive
- Check server logs for debugging

### 7.4 Copilot in the Terminal

Copilot provides AI assistance directly in the VS Code terminal.

**Terminal Inline Suggestions:**

Start typing a command and Copilot suggests completions, just like in the editor.

**Natural Language to Commands:**

Press `Ctrl+I` in the terminal to describe what you want in plain English:

```
find all CSV files larger than 100MB in the data directory
```

Copilot translates this to the appropriate shell command.

**Using @terminal in Chat:**

```
@terminal How do I run pytest with coverage reporting and generate an HTML report?
```

**Terminal output as context:**

After running a command that produces an error, use `#terminalLastCommand` in chat:

```
#terminalLastCommand Explain this error and how to fix it
```

### 7.5 Commit Messages and PR Summaries

**Auto-generated commit messages:**

1. Stage your changes (`git add`).
2. In the Source Control panel, click the sparkle icon (Copilot) next to the commit message box.
3. Copilot generates a descriptive commit message based on the diff.
4. Edit if needed, then commit.

**Pull Request summaries:**

When creating a PR on GitHub, Copilot can auto-generate the description:

1. Click "Generate" next to the PR description field.
2. Copilot analyzes the diff, commit messages, and related issues.
3. It produces a structured summary with changes, motivation, and testing notes.

### 7.6 Background and Parallel Agent Sessions

**Running agents in the background:**

- Start an Agent Mode task.
- Continue working in the editor while the agent runs.
- Agent notifications appear when tasks complete or need input.

**Parallel sessions:**

- Open multiple chat panels for concurrent agent tasks.
- Each session maintains its own context and history.

---

### Week 7 Exercises (Data Science)

#### Exercise 7.1: Use NES for Iterative Refactoring

Open `feature_engineering.py`. Enable NES if not already enabled.

1. Rename the parameter `col` to `column_name` in the `add_age_bins` function signature.
2. Watch for the blue arrow in the gutter -- NES should suggest updating `col` references inside the function body.
3. Press `Tab` to navigate and accept each suggestion.
4. Now change the default value of `bins` to `[0, 25, 40, 55, 70, 100]`.
5. NES should suggest updating the related labels variable.

Repeat with another function: change a return type and see NES suggest docstring updates.

**Goal:** Experience how NES chains related edits together, reducing manual find-and-replace.

---

#### Exercise 7.2: Reproduce a Chart from a Screenshot

1. Find a chart online (e.g., a bar chart of global CO2 emissions by country, or any data visualization).
2. Save it as a PNG/JPEG.
3. Open Copilot Chat, attach the image.
4. Type: `Reproduce this chart in Python using matplotlib. Generate sample data that matches the approximate values shown.`
5. Run the generated code and compare the output with the original image.

Alternative: Take a screenshot of one of your own matplotlib plots, then ask Copilot to improve it:

```
[attach screenshot]
Improve this chart: add a title, axis labels, gridlines, color palette, and make it publication-ready
```

**Goal:** Use Vision to translate visual references into code.

---

#### Exercise 7.3: Set Up an MCP Server for Data Access

Set up a filesystem MCP server to give Copilot access to your data files:

1. Add to `.vscode/settings.json`:

```json
{
  "mcp": {
    "servers": {
      "project-data": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-filesystem", "./data"]
      }
    }
  }
}
```

2. Create a `data/` directory with some CSV files.
3. In Agent Mode, ask:

```
List the CSV files in the data directory and show me the first 5 rows of each file. Then suggest which files could be joined and on which columns.
```

For a more advanced setup, configure a SQLite MCP server if you have a local database.

**Goal:** Extend Copilot's capabilities with external data sources via MCP.

---

#### Exercise 7.4: Terminal AI for Complex Commands

Use `Ctrl+I` in the terminal for each of these tasks:

1. `Create a Docker command to run a Jupyter notebook server with port 8888 mapped and the current directory mounted`
2. `Generate an AWS CLI command to upload all CSV files in data/ to an S3 bucket called my-ds-project`
3. `Write a DVC command to track the data/ directory and push to remote storage`
4. `Create a cron job expression that runs python pipeline.py every day at 6 AM`

Review each suggested command before running.

**Goal:** Use terminal AI to generate complex CLI commands from natural language descriptions.

---

#### Exercise 7.5: Smart Commit Messages

1. Make several changes across your project files (add a feature, fix a bug, update docs).
2. Stage the changes with `git add`.
3. In the Source Control panel, click the Copilot sparkle icon to generate a commit message.
4. Review the message -- does it accurately describe the changes?
5. Make more changes, stage them, and generate another commit message.
6. Compare the quality of messages for different types of changes (feature vs. bugfix vs. refactor).

**Goal:** Integrate Copilot into your git workflow for descriptive, consistent commit messages.

---

## Week 8: Capstone -- End-to-End Data Science Project

### Learning Objectives

This final week brings everything together. You will build a complete machine learning project from scratch using every Copilot feature learned in Weeks 1-7.

---

### 8.1 Capstone Project: Customer Churn Prediction

**Project overview:**

Build a complete ML pipeline that predicts customer churn for a telecom company. The project must include data loading, cleaning, EDA, feature engineering, model training, evaluation, API serving, testing, and documentation.

**Dataset:** Use the Telco Customer Churn dataset from Kaggle, or generate synthetic data using Copilot.

### 8.2 Best Practices for Prompt Engineering with Copilot

Use these strategies throughout the capstone:

**1. Start with the big picture, then zoom in:**
```
First: "Scaffold a customer churn prediction project"
Then: "Implement the feature engineering module with these specific features: ..."
```

**2. Provide constraints:**
```
"Write a data loader that handles CSV and Parquet files, validates schema against config.yaml, and logs all operations. Maximum function length: 20 lines."
```

**3. Give examples of desired output:**
```
"Generate features like this example:
- tenure_months -> bin into [0-12, 12-24, 24-48, 48+]
- monthly_charges -> log transform
- total_charges / tenure -> average monthly spend"
```

**4. Iterate and refine:**
```
"Good, but also add: cross-validation, hyperparameter tuning with GridSearchCV, and save the best model"
```

**5. Use context effectively:**
```
"Based on #file:config.yaml and #file:src/features/engineering.py, create a training script that uses the configured feature pipeline"
```

### 8.3 When NOT to Rely on Copilot

Be aware of Copilot's limitations:

- **Statistical correctness:** Always verify that statistical methods are applied correctly (e.g., train/test split before scaling).
- **Domain logic:** Copilot does not know your business rules. Validate domain-specific transformations.
- **Data privacy:** Do not paste sensitive data into Copilot prompts.
- **Outdated patterns:** Copilot may suggest deprecated APIs. Check library documentation.
- **Complex algorithms:** For custom algorithms, write them yourself and use Copilot for the boilerplate around them.

### 8.4 Measuring Productivity with Copilot

Track these metrics during the capstone:

- **Time to complete each module** (compare with your estimate without Copilot)
- **Acceptance rate** of suggestions (how many did you accept vs. reject?)
- **Rework rate** (how often did you need to fix Copilot's code?)
- **Test coverage** achieved with Copilot-generated tests

---

### Week 8 Exercises (Capstone Project)

#### Exercise 8.1: Project Scaffolding with Agent Mode

Open Agent Mode and prompt:

```
Create a complete project structure for a Customer Churn Prediction ML pipeline:

Project structure:
- src/data/ (loading, validation)
- src/features/ (engineering, selection)
- src/models/ (training, evaluation, prediction)
- src/visualization/ (EDA plots, model plots)
- tests/ (mirroring src/ structure)
- configs/config.yaml (paths, hyperparameters, feature lists)
- notebooks/ (EDA notebook)
- data/raw/ and data/processed/
- models/ (saved models)
- reports/figures/ (saved plots)
- requirements.txt
- Makefile (install, test, train, predict, lint, clean)
- .gitignore

Use the custom instructions from .github/copilot-instructions.md.
Generate synthetic churn data (1000 rows) if no real data is available.
```

Let Agent Mode build the entire structure. Review the generated files.

**Goal:** Combine Agent Mode with custom instructions for consistent project generation.

---

#### Exercise 8.2: EDA and Feature Engineering with Chat + Inline Chat

1. Open the generated EDA notebook (or create one with `/newNotebook`).

2. Use Copilot Chat to guide your analysis:
```
@workspace Based on the data schema in config.yaml, what EDA steps should I perform for churn prediction?
```

3. For each EDA step, use Inline Chat to write the code:
   - Select the empty notebook cell and press `Ctrl+I`.
   - Type: `Plot the distribution of churn vs. non-churn customers across tenure, monthly charges, and contract type`.

4. After EDA, create the feature engineering module using Chat:
```
Based on the EDA findings in #file:notebooks/eda.ipynb, suggest feature engineering steps for the churn model. Consider interaction features, binning, encoding, and derived metrics.
```

5. Use Inline Chat in `src/features/engineering.py` to implement each suggested feature.

**Goal:** Combine Chat (for planning) with Inline Chat (for implementation) in a real workflow.

---

#### Exercise 8.3: Test Coverage with /tests and Agent Mode

1. First, generate tests for individual modules:
```
/tests Generate comprehensive pytest tests for src/features/engineering.py including:
- Unit tests for each feature function
- Integration test for the full pipeline
- Parametrized tests for edge cases
- Fixtures for sample DataFrames
```

2. Then use Agent Mode for broader test coverage:
```
Analyze all modules in src/ and generate test files for any module that doesn't have tests yet. Include conftest.py with shared fixtures. Aim for >80% code coverage.
```

3. Run the tests and fix any failures:
```
Run pytest with coverage. If any tests fail, fix them. Show me the final coverage report.
```

**Goal:** Achieve comprehensive test coverage using multiple Copilot features.

---

#### Exercise 8.4: Custom Instructions and Prompt Files in Action

1. Verify your `.github/copilot-instructions.md` from Week 6 is in place.

2. Create a prompt file `.github/prompts/model-comparison.prompt.md`:
```markdown
# Model Comparison

Compare at least 3 classification models:
1. Logistic Regression (baseline)
2. Random Forest
3. XGBoost

For each model:
- Train with 5-fold cross-validation
- Report accuracy, precision, recall, F1, AUC
- Plot ROC curves on the same figure
- Plot feature importance for tree-based models
- Generate a comparison summary table
- Recommend the best model with justification
```

3. In Chat, reference the prompt:
```
Using #prompt:model-comparison, implement the model comparison for our churn prediction project. Use the features from src/features/engineering.py.
```

4. Review the code -- does it follow the custom instructions (logging, type hints, docstrings)?

**Goal:** See custom instructions and prompt files working together for consistent, high-quality code.

---

#### Exercise 8.5: Final Code Review, Documentation, and Commit Messages

1. **Code Review:** Ask Copilot to review the entire project:
```
@workspace Review this project for:
- Code quality and consistency
- ML best practices (no data leakage, proper validation)
- Error handling completeness
- Test coverage gaps
- Security issues (hardcoded paths, credentials)
Provide a prioritized list of improvements.
```

2. **Documentation:** Generate final documentation:
```
@workspace Generate a comprehensive README.md with project overview, setup instructions, usage guide, architecture diagram (mermaid), and model performance results.
```

3. **Commit Messages:** Stage all files and use Copilot to generate a commit message for the complete project.

4. **Reflection:** Compare the finished project against what you would have built without Copilot. Note:
   - Which features saved the most time?
   - Where did you need to correct Copilot's output?
   - What is your new workflow going to be going forward?

**Goal:** Complete the capstone with polished documentation, thorough reviews, and a clean git history.

---

## Appendix A: Keyboard Shortcut Reference

### Inline Suggestions

| Action                          | Windows / Linux      | macOS               |
|---------------------------------|----------------------|---------------------|
| Accept suggestion               | `Tab`                | `Tab`               |
| Dismiss suggestion              | `Esc`                | `Esc`               |
| Next suggestion                 | `Alt+]`              | `Option+]`          |
| Previous suggestion             | `Alt+[`              | `Option+[`          |
| Accept next word                | `Ctrl+Right`         | `Cmd+Right`         |
| Trigger suggestion              | `Alt+\`              | `Option+\`          |
| Open completions panel          | `Ctrl+Enter`         | `Ctrl+Return`       |

### Chat

| Action                          | Windows / Linux      | macOS               |
|---------------------------------|----------------------|---------------------|
| Open Chat Panel                 | `Ctrl+Alt+I`         | `Ctrl+Cmd+I`        |
| Open Quick Chat                 | `Ctrl+Shift+I`       | `Cmd+Shift+I`       |
| Open Inline Chat                | `Ctrl+I`             | `Cmd+I`             |

### Next Edit Suggestions

| Action                          | Windows / Linux      | macOS               |
|---------------------------------|----------------------|---------------------|
| Navigate to next NES            | `Tab`                | `Tab`               |
| Accept NES                      | `Tab`                | `Tab`               |
| Dismiss NES                     | `Esc`                | `Esc`               |

### Terminal

| Action                          | Windows / Linux      | macOS               |
|---------------------------------|----------------------|---------------------|
| Inline Chat in terminal         | `Ctrl+I`             | `Cmd+I`             |
| Accept terminal command         | `Ctrl+Enter`         | `Ctrl+Return`       |

---

## Appendix B: Copilot Settings Reference

All settings go in `settings.json` (open with `Ctrl+,` then click the `{}` icon).

### Core Settings

```json
{
  // Enable/disable Copilot globally or per-language
  "github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": true,
    "yaml": true
  },

  // Enable Next Edit Suggestions
  "github.copilot.nextEditSuggestions.enabled": true,

  // Use custom instruction files
  "github.copilot.chat.codeGeneration.useInstructionFiles": true,

  // Enable prompt files
  "chat.promptFiles": true,

  // Override locale for Copilot Chat
  "github.copilot.chat.localeOverride": "en",

  // Enable Copilot for Jupyter notebooks
  "github.copilot.chat.notebook.enabled": true
}
```

### MCP Server Configuration

```json
{
  "mcp": {
    "servers": {
      "server-name": {
        "command": "command-to-start-server",
        "args": ["arg1", "arg2"],
        "env": {
          "ENV_VAR": "value"
        }
      }
    }
  }
}
```

### Editor Settings That Improve Copilot Experience

```json
{
  // Show inline suggestion details
  "editor.inlineSuggest.enabled": true,

  // Show suggestions only on demand (less intrusive)
  "editor.inlineSuggest.showToolbar": "onHover",

  // Tab completion mode (important for NES)
  "editor.tabCompletion": "on"
}
```

---

## Appendix C: Troubleshooting Common Issues

### Copilot Not Showing Suggestions

| Issue                               | Solution                                        |
|-------------------------------------|-------------------------------------------------|
| No ghost text appears               | Check status bar icon -- click to re-enable      |
| Suggestions appear for wrong language | Check `github.copilot.enable` in settings       |
| Slow suggestions                    | Check internet connection; Copilot needs network |
| Extension not activating            | Sign out and sign back in via Command Palette    |
| Subscription expired                | Check github.com/settings/copilot               |

### Chat Not Working

| Issue                               | Solution                                        |
|-------------------------------------|-------------------------------------------------|
| Chat says "Copilot is not available"| Update VS Code to latest version                |
| Agent Mode not visible              | Ensure VS Code >= 1.99                          |
| MCP servers not connecting          | Run `MCP: List Servers` and restart failed ones  |
| Slow chat responses                 | Try a different model (GPT-4o is fastest)        |

### Common Error Messages

| Error                                   | Meaning and Fix                              |
|-----------------------------------------|----------------------------------------------|
| "You don't have access to Copilot"      | Subscription issue -- check billing          |
| "Rate limit exceeded"                   | Free tier limit reached -- wait or upgrade   |
| "Unable to connect to Copilot"          | Network issue -- check proxy/firewall        |
| "Extension host terminated unexpectedly"| Restart VS Code; update extensions           |

### Reset Copilot

If Copilot behaves unexpectedly:

1. Open Command Palette (`Ctrl+Shift+P`)
2. Type: `GitHub Copilot: Sign Out`
3. Restart VS Code
4. Sign back in: `GitHub Copilot: Sign In`

---

## Appendix D: Plans & Pricing Comparison

| Feature                    | Free          | Pro ($10/mo)  | Business ($19/mo) | Enterprise ($39/mo) |
|----------------------------|---------------|---------------|--------------------|--------------------|
| Code completions           | 2,000/month   | Unlimited     | Unlimited          | Unlimited          |
| Chat messages              | 50/month      | Unlimited     | Unlimited          | Unlimited          |
| Agent Mode                 | Limited       | Yes           | Yes                | Yes                |
| Model selection            | Limited       | GPT-4o, Claude, o3-mini | All models | All models + fine-tuned |
| Custom instructions        | Yes           | Yes           | Yes                | Yes                |
| MCP support                | Yes           | Yes           | Managed by admin   | Managed by admin   |
| Organization policies      | No            | No            | Yes                | Yes                |
| Audit logs                 | No            | No            | Yes                | Yes                |
| Knowledge bases            | No            | No            | No                 | Yes                |
| Fine-tuned models          | No            | No            | No                 | Yes                |
| IP indemnity               | No            | No            | Yes                | Yes                |

*Prices as of early 2026. Students and verified open-source maintainers get Pro-level access free.*

---

## Appendix E: Glossary of Terms

| Term                       | Definition                                                                 |
|----------------------------|---------------------------------------------------------------------------|
| **Ghost Text**             | Dimmed inline code suggestions that appear as you type                     |
| **Inline Chat**            | A chat input that appears directly in the editor at your cursor            |
| **Agent Mode**             | Autonomous mode where Copilot plans, edits, and runs commands independently|
| **NES (Next Edit Suggestions)** | Predictions about where and what to edit next based on recent changes |
| **Chat Participant**       | A domain expert invoked with `@` (e.g., `@workspace`, `@terminal`)        |
| **Chat Variable**          | Context injected with `#` (e.g., `#file`, `#selection`, `#codebase`)      |
| **Slash Command**          | A shortcut command prefixed with `/` (e.g., `/fix`, `/tests`)             |
| **Working Set**            | The set of files added to a multi-file editing session                     |
| **MCP (Model Context Protocol)** | Open standard for connecting AI to external tools and data sources   |
| **Custom Instructions**    | Project-level guidelines stored in `.github/copilot-instructions.md`       |
| **Prompt File**            | Reusable prompt templates stored as `.prompt.md` files                     |
| **Smart Actions**          | Context menu actions (Explain, Fix, Generate Docs, Generate Tests)         |
| **Completions Panel**      | A panel showing multiple alternative suggestions (`Ctrl+Enter`)            |
| **Vision**                 | Ability to attach images to Copilot Chat for visual context                |
| **Coding Agent**           | Asynchronous agent that runs in GitHub Actions and opens PRs               |
| **Background Agent**       | An agent session that continues running while you work on other things     |

---

## Quick Reference Card

```
+------------------------------------------------------------------+
|                    GITHUB COPILOT QUICK REFERENCE                 |
+------------------------------------------------------------------+
|                                                                  |
|  INLINE SUGGESTIONS                                              |
|    Tab .............. Accept    Esc .............. Dismiss        |
|    Alt+] ............ Next     Alt+[ ............ Previous       |
|    Ctrl+Right ....... Word     Alt+\ ............ Trigger        |
|                                                                  |
|  CHAT                                                            |
|    Ctrl+Alt+I ....... Panel    Ctrl+Shift+I ...... Quick Chat    |
|    Ctrl+I ........... Inline   Modes: Ask / Edit / Agent         |
|                                                                  |
|  PARTICIPANTS         VARIABLES          COMMANDS                |
|    @workspace         #file              /fix                    |
|    @vscode            #selection         /tests                  |
|    @terminal          #editor            /explain                |
|                       #codebase          /doc                    |
|                       #git               /newNotebook            |
|                                                                  |
|  AGENT MODE                                                      |
|    Select "Agent" in chat dropdown                               |
|    Ctrl+Enter to approve terminal commands                       |
|                                                                  |
|  NES                                                             |
|    Tab to navigate and accept next edit suggestions              |
|                                                                  |
+------------------------------------------------------------------+
```

---

*Tutorial created for GitHub Copilot in VS Code. Features and pricing are subject to change. Always refer to the official documentation at [code.visualstudio.com/docs/copilot](https://code.visualstudio.com/docs/copilot) and [docs.github.com/copilot](https://docs.github.com/copilot) for the latest information.*
