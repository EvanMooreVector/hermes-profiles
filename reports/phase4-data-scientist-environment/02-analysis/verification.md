# Verification analysis

The environment is profile-local: `C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\.venv\Scripts\python.exe`. This is distinct from the Hermes runtime interpreter and the installation used no global Python packages.

Validated requested package versions are NumPy 2.5.3, pandas 3.0.5, SciPy 1.18.1, statsmodels 0.15.0, and scikit-learn 1.9.0. `pip check` found no broken requirements. The smoke test used a fixed seed (20260908), a six-row pandas frame with `y = 2 + 3x`, SciPy's one-sample t-test, statsmodels OLS, and scikit-learn linear regression. It asserted frame shape, the SciPy statistic, OLS parameters/R-squared, and scikit-learn intercept/coefficient before reporting PASS.

Changed source guidance: `profiles/data-scientist/README.md`; SHA-256 `a5fd74465273e5ecb1bca890b4a54352672a7e710d8a661d5da715c1af489f97`. The new runtime lock: `C:\Users\EvanMoore\AppData\Local\hermes\profiles\data-scientist\requirements-data-science.lock`; SHA-256 `f5b19a7b2398ba9476a57d11fde836ccbdf5f6aab73fcb9eef09eb5a1ea1ef18`.

Limitations: the lock is intentionally pin-based and was resolved for CPython 3.14.3 on Windows x86_64; it contains no wheel hashes and should be regenerated with the explicit local interpreter for a different Python version, architecture, or platform. The lock includes `wrapt==2.4.1rc1` because that was the resolver-selected compatible dependency. The source branch already contains the upstream Phase 2–3 changes and report files; this task changed only the listed README among source profile files.

SOURCES (LAYER 3 NAVIGATION)
../03-dossiers/execution-evidence.md
 -> Verbatim captured validation output, resolved lock pins, executable path, and source diff count.
