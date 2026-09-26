# Validation record

Validated locally on 2026-09-26.

| Check | Result |
| --- | --- |
| Queue, API and agent suite on SQLite and PostgreSQL 17 | 39 passed |
| Real-process integration | API plus two workers completed both agents; results survived API restart |
| Docker build | Python 3.12 Linux image built with the runtime lockfile |
| Compose deployment | PostgreSQL, API and two workers healthy; migration exited successfully |
| Containerized assignment demo | Task succeeded and stored queued/running/succeeded events |
| Browser console | Headless Edge: authentication, task submission, result/event display, mobile width and disconnect passed |
| Lint | Ruff passed for cloud runtime, cloud tests, shared provider client and demo/setup scripts |
| HTTPS overlay | Compose configuration and Caddy configuration validated locally |
| Agent failure handling | Mocked provider errors propagate; coach stops at the first failed step |

The database suite ran in an isolated temporary PostgreSQL container, separate from the demo data. The temporary test container was removed afterward. The demo stack uses a persistent named volume.

The complete suite ran before the final display-character and fail-fast planning changes; the affected agent tests and browser checks were repeated after those changes.

Not validated here: real Gemini billing/provider access, a public cloud deployment, public certificate issuance, remote GitHub Actions execution, throughput benchmarks, or the legacy supervisor and unrelated experimental agents.

The screenshot in this directory is a real local mock-mode run, not a design mockup.
