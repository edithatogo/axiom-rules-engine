# Implementation plan: Conductor planning: qualify maintained YAML adapter without changing RuleSpec semantics

- [ ] Freeze exact source tree/Cargo.lock, fixture corpus and public `serde_yaml::Value` exposure; note repository owner and open work.
- [ ] Compare maintained YAML parsers with isolated fixtures for valid/invalid ProgramSpec and RuleSpec, duplicate keys, anchors/tags, numeric coercion, Unicode, nested maps, path resolution and hard error cases; document loss and error differences.
- [ ] Model source/API compatibility: if a public `Value` type or error type changes, require versioned API, downstream Python/RuleSpec adapters and migration fixtures. Do not blindly rename the crate in Cargo.
- [ ] If qualified, implement one bounded opt-in parser swap PR with verified source/compiled behaviour and a removal of redundant code; else record no-go without replacing dependencies.
- [ ] Run `cargo test`, `cargo test --features schema`, installed Python tests, independent law/policy oracles and exact-head security, MSRV and schema-conformance review; never claim legal correctness from successful deserialization.
