# Contributing to axiom-rules-engine

Axiom Rules Engine implements a Rust runtime and Python bindings for Axiom RuleSpec. Contributions should improve generic execution, diagnostics, schemas, interoperability and independently reproducible tests.

## Before you start

Read [README.md](README.md), [DECISIONS.md](DECISIONS.md) and the relevant RuleSpec documentation before changing semantics. Check open issues and pull requests. Production jurisdiction policy belongs in its jurisdiction repository; this engine keeps policy documents as test fixtures. Explain compatibility effects across reference, compiled, explain, fast and dense execution paths.

For bugs, provide the affected version or commit, environment, minimal reproduction, expected result and observed result. For a substantial proposal, describe the use case and compatibility impact before expanding implementation scope. Use existing issue templates when offered.

## Development and validation

Follow the existing [Cargo configuration](Cargo.toml), lockfile and Python package setup. The README documents:

```sh
cargo test
cargo test --features schema
python -m pytest -q python/tests
```

The schema-enabled run includes fidelity, golden-file and optional external jurisdiction checks. Report a skipped external checkout explicitly; its absence is not conformance evidence. Install Python test prerequisites in an isolated environment using the package's existing configuration.

Add independently expected results for temporal boundaries, invalid input and changed rule behaviour. Preserve authoritative JSON Schemas in `schemas/` and test their agreement with deserialization. Changes to currency rounding or compiled artifacts need parity evidence across the affected paths and clear compatibility documentation. Keep production policy content out of engine infrastructure and do not infer legal correctness from a passing fixture.

## Pull requests

Create a focused branch from the current `main` branch and submit a pull request to this repository. Link the relevant issue or existing project task, explain the resulting behaviour, and update affected examples and documentation. Keep unrelated changes in separate pull requests.

Report executed commands, outcomes and the commit they validate. Identify unavailable checks and remaining limitations explicitly. Follow the repository's existing review and automated-check requirements; retain required gates and current ownership. Address findings and verify the final head before integration. Repository changes do not themselves authorise a release or external operational action.

## Security, rights and conduct

Follow the [security policy](https://github.com/edithatogo/.github/blob/main/SECURITY.md). Use private vulnerability reporting if available; otherwise request a private contact without publishing vulnerability details. Keep credentials, personal information and restricted source material out of issues, fixtures, logs and artifacts.

Read the [existing licence](LICENSE) and preserve attribution and third-party terms. Follow the [code of conduct](https://github.com/edithatogo/.github/blob/main/CODE_OF_CONDUCT.md) and keep technical discussions respectful.

## Basis for this guide

This guide follows [GitHub's contribution-guideline guidance](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors) and the contribution-process and testing principles in [OpenSSF Best Practices](https://www.bestpractices.dev/en/criteria). It does not assert certification.
