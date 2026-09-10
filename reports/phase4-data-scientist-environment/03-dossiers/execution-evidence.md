# Execution evidence

Profile-local interpreter:
`C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\.venv\Scripts\python.exe`

Captured validation output:

```text
--- pip check ---
No broken requirements found.
--- import-and-model-smoke ---
PYTHON=3.14.3
EXECUTABLE=C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\.venv\Scripts\python.exe
IMPORTS=numpy,pandas,scipy,statsmodels,sklearn
SEED=20260908
DATA_SHAPE=(6, 2)
SCIPY_TTEST_STAT=4.146139914483856
STATSMODELS_PARAMS=2.000000,3.000000
STATSMODELS_R2=1.000000
SKLEARN_INTERCEPT=2.000000
SKLEARN_COEF=3.000000
SMOKE_TEST=PASS
--- requested versions ---
numpy==2.5.3
pandas==3.0.5
scipy==1.18.1
statsmodels==0.15.0
scikit-learn==1.9.0
--- required file hashes ---
f5b19a7b2398ba9476a57d11fde836ccbdf5f6aab73fcb9eef09eb5a1ea1ef18 *C:/Users/EvanMoore/AppData/Local/hermes/profiles/data-scientist/requirements-data-science.lock
a5fd74465273e5ecb1bca890b4a54352672a7e710d8a661d5da715c1af489f97 *profiles/data-scientist/README.md
--- scoped source diff validation ---
15\t0\tprofiles/data-scientist/README.md
```

Resolved lock pins:

```text
cloudpickle==3.1.2
formulaic==1.2.2
interface_meta==2.0.1
joblib==1.6.0
narwhals==2.26.0
numpy==2.5.3
packaging==26.3
pandas==3.0.5
patsy==1.0.3
python-dateutil==2.9.0.post0
scikit-learn==1.9.0
scipy==1.18.1
six==1.17.0
statsmodels==0.15.0
threadpoolctl==3.6.0
typing_extensions==4.16.0
tzdata==2026.3
wrapt==2.4.1rc1
```

SOURCES (LAYER 3 PROVENANCE)
C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\requirements-data-science.lock
 -> Profile-local, secret-free lock file installed and verified by the executable above.

profiles/data-scientist/README.md
 -> Source guidance change that specifies explicit use of the profile-local interpreter.
