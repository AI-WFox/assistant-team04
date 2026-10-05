# Smart Virtual Assistant — Team 04

A student project for CSC10014 at HCMUS. The assistant helps students find
university offices, rooms, and opening hours through a Python command-line
interface. This repository currently contains a rule-based starter; it does not
use an AI model or provide a web interface yet.

## Requirements

- Python 3.10 or newer, available as `python` (or `python3` on macOS/Linux).
- Git, available as `git`.
- Internet access to clone the repository and install Python dependencies.

## Setup

Clone the team repository and enter its root directory:

```sh
git clone https://github.com/Computational-Thinking-Project/assistant-team04.git
cd assistant-team04
```

Create and activate a virtual environment using the commands for your platform.

**Windows PowerShell:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

If PowerShell blocks activation, run the following in the current terminal,
then retry activation. The policy change applies only to this session.

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned
.\.venv\Scripts\Activate.ps1
```

**macOS/Linux:**

```sh
python3 -m venv .venv
source .venv/bin/activate
```

With the environment activated, install the test dependency and the package:

```sh
python -m pip install -r requirements.txt
python -m pip install -e .
```

The editable installation makes `assistant` importable from the `src/` layout.
Run the following commands from the repository root. Use `deactivate` when
finished with the virtual environment.

## Run

Check a greeting:

```sh
python -m assistant "hi"
```

Expected response:

```text
Hello! Ask me where an office is, or when it opens.
```

Start an interactive session:

```sh
python -m assistant
```

Type `quit` or `exit` to leave. Office questions use office names from
[`data/offices.csv`](data/offices.csv), for example:

```sh
python -m assistant "Where is the Training Office?"
```

Expected response:

```text
Training Office: room I.101, open Mon-Fri 07:30-16:30.
```

The responder reads the root-level `data/offices.csv` relative to its source
file. Keep that CSV in the cloned repository when using the editable install.

## Test and environment checks

```sh
python -m pytest -q
python scripts/check_env.py
```

The four smoke tests cover greetings, office lookup, unknown questions, and
empty input. A successful test run reports `4 passed`.

The environment checker checks Python, virtual-environment activation, pytest,
Git, repository metadata, `.gitignore`, README completeness, Git email, and a
greeting response. It checks only a greeting; run the smoke tests as well to
verify office lookup. The starter currently lacks
`.gitignore`, which the configuration owner must add. Until then, keep `.venv/`
and generated caches out of commits by staging only the intended files.

If the checker reports a missing Git email, set your own commit identity inside
this repository:

```sh
git config user.name "Your Name"
git config user.email "your-email@example.com"
```

## Project structure

```text
assistant-team04/
|-- README.md                 # Project overview and developer setup
|-- pyproject.toml            # Package metadata and pytest configuration
|-- requirements.txt          # Test dependency
|-- src/assistant/
|   |-- __init__.py           # Package version
|   |-- __main__.py           # Single-question and interactive CLI
|   `-- rules.py              # Rule-based replies and CSV loading
|-- scripts/check_env.py      # Developer environment checks
|-- data/offices.csv          # Starter office directory
|-- tests/test_smoke.py       # Four baseline behavior tests
|-- ui/README.md              # Future UI plan
`-- docs/
    |-- README.md            # Documentation index
    `-- team.md              # Team roster and responsibilities
```

## Behavior and limitations

The responder normalizes input, checks a small set of greetings, loads office
records from CSV, and returns the first office whose full name occurs in the
question. Questions without a matching name receive a fallback response.
This is a deterministic baseline, with no fuzzy matching or
language-model integration. Starter room numbers and hours must be verified
with the university before being presented as authoritative information.

For CSV size `B`, `N` offices, question length `L`, and maximum office-name length
`K`, loading costs O(B) time and space. A conservative substring-matching bound
is O(NLK) time. A non-greeting reply that loads its own data therefore uses
O(B + NLK) time and O(B + L) space; the starter reloads the CSV for each such
question.

Before expanding the assistant, validate that students can obtain accurate
office information and that a campus staff member can maintain the data.
Future AI and UI work should follow demonstrated user needs.

## Team and contribution workflow

See the [team roster](docs/team.md) and [documentation index](docs/README.md).
Each member works on their assigned feature branch and opens a pull request
against this repository's `main` branch for review. Contributors without write
access can push their branch to a personal fork and open a PR into the team
repository. Member 7's documentation branch is `feat/docs` and covers
`README.md`, `docs/README.md`, and `docs/team.md`.

After all seven assigned PRs are reviewed and merged, the project manager can
create the setup milestone tag `v0.1-setup`.
