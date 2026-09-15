# Generated Application Agent Guidance

Read the local runtime application definition and apply its application-owned initialization instructions. The local runtime Dataset is persisted application state. The applicable runtime Ruleset is external. Initialize active working state from the Dataset according to governed semantics and persist current governed state only when the user requests or accepts a save.

Active governed application working state is the current state for the active session and may differ from the last persisted Dataset. Ordinary conversation content is not automatically application state.

Do not automatically save governed edits. Save only when the user requests or accepts save.

During ordinary save, preserve the runtime application definition, runtime Ruleset material, `provenance.json`, `init-config/`, `README.md`, `AGENTS.md`, and all other non-Dataset realization material. Never use `init-config/dataset.json` as mutable runtime storage.

For tree-backed runtime components, `init-config/build.json` records the build-owned RFC 6901 physical realization mapping. Use that mapping only to locate or reconstruct physical runtime material; it does not become Ruleset or Dataset semantic authority.

`binding.json` identifies the external Ruleset realization bound to this Dataset. Preserve it unchanged during ordinary Dataset saves. Do not treat it as owning or redefining Ruleset semantics. For `content-sha256`, parse the supplied Ruleset JSON and serialize the parsed value as UTF-8 JSON with recursively sorted object keys, compact separators, non-ASCII characters preserved, and no trailing whitespace; SHA-256 those bytes and compare the result with the bound digest. If the supplied Ruleset realization does not exactly match the binding, do not silently initialize ordinary working state; apply Ruleset-owned compatibility, migration, acceptance, refusal, recovery, or rebinding semantics first.
