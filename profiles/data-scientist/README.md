# Data-Scientist — Hermes Profile

PhD-level data scientist — statistical modeling, causal inference, experimental design, machine learning, and reproducible research.

## Installation

```bash
git clone https://github.com/magnus919/hermes-profiles.git ~/hermes-profiles
ln -s ~/hermes-profiles/profiles/data-scientist ~/.hermes/profiles/
hermes --profile data-scientist
```

## Scientific Python Environment

Run statistical and modeling code through the profile-local interpreter, not a
shell-activated or global Python. On Windows, with `HERMES_HOME` set to the
data-scientist profile directory:

```bash
"$HERMES_HOME/.venv/Scripts/python.exe" -m pip install -r "$HERMES_HOME/requirements-data-science.lock"
"$HERMES_HOME/.venv/Scripts/python.exe" analysis.py
```

The profile-local `requirements-data-science.lock` pins NumPy, pandas, SciPy,
statsmodels, scikit-learn, and resolved dependencies. Regenerate the lock with
the explicit interpreter if the Python version or platform changes.

## Skill Dependencies

| Skill | Provides |
|---|---|
| `artifact-pyramids` | Progressive disclosure output format |

## Output Format

Artifact pyramid. Response is the absolute path to `00-index.md`.
