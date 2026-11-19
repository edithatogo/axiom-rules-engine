# Specification: Conductor planning: qualify maintained YAML adapter without changing RuleSpec semantics

## Current implementation
- `Cargo.toml` declares `serde` derive, `serde_json`, `serde_yaml 0.9.34` and `jsonschema`. `src/spec.rs` parses `ProgramSpec` via `serde_yaml::from_str`, and `src/rulespec.rs` consumes `serde_yaml::Value` in parsed metadata, optional data, discriminator detection and `#[serde(flatten)]` extension fields.
- RuleSpec validation, decimal/rounding semantics, import resolution, legal source identity and schema fidelity are separate from Serde parsing. `serde_yaml::Value` occurs in Rust structures/public-facing APIs; migrating its type is not necessarily source-compatible.
- Because the format adapter is unmaintained, compare maintained Serde-compatible `serde-saphyr` and `yaml_serde` as candidates, with a documented *no-go* if typed or dynamic YAML meaning would change.

## Required compatibility criteria
Keep discriminators (`rulespec/v1`, `axiom.rules.*`), mapping/tag semantics, aliases/anchors, duplicate-key policy, dates, numeric/decimal input, `#[serde(flatten)]` unknown fields, strict schema fidelity, invalid/missing imports and error locations. Preserve source-level path/citation IDs and execution results across explain/fast/dense Rust/Python. Check MSRV, advisories, feature footprint and failures. No policy-law oracle can be replaced by parser equivalence. 
