# Provisioning outcome

The data-scientist profile has an isolated CPython 3.14.3 environment at `C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\.venv`, with all requested scientific packages importable and `pip check` reporting no broken requirements.

The reproducible lock at `C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\requirements-data-science.lock` pins the requested stack and its resolved dependencies. The source README now instructs use of the explicit profile-local interpreter rather than activation or global Python.

The deterministic statistics/modeling smoke test passed using SciPy, pandas, statsmodels, and scikit-learn; the downstream Phase 5–7 child may proceed once its other Phase 4 dependency also completes.

SOURCES (LAYER 2 NAVIGATION)
../02-analysis/verification.md
 -> Paths, package-version evidence, source and lock hashes, validation meaning, and known constraints.
