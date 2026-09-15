# ADR App Builder Generated Repository

Packaging profile: `split-git`

This repository contains the runtime application definition and persisted runtime Dataset. The applicable Ruleset is external.

## Runtime components

- application: `application.json` (file)
- dataset: `dataset` (tree)

## Initialization inputs

`init-config/` contains byte-for-byte copies of the four App Builder CLI input files that created this repository. Those files reproduce the original build invocation; they are not runtime application, Ruleset, or Dataset authority.

## Provenance

`provenance.json` records the exact ADR and App Builder construction commits as immutable lineage and upgrade anchors. It is not application, Ruleset, Dataset, or active-session authority.

## Working state and save

Active application working state may be newer than the persisted Dataset. Governed edits do not automatically persist. A user-requested or user-accepted save writes current governed working state to the runtime Dataset while preserving non-Dataset realization material.

## Ruleset realization binding

`binding.json` determinately identifies the exact external Ruleset realization bound to this application instance. It is realization metadata, not Ruleset semantic authority, construction provenance, Git history, or Dataset state. For `ruleset_authority.kind` equal to `content-sha256`, reproduce the identity by parsing the supplied Ruleset JSON, serializing that parsed value as UTF-8 JSON with object keys sorted recursively, compact separators, and non-ASCII characters preserved, with no trailing whitespace, then taking SHA-256 of those bytes. Before ordinary initialization, compare that supplied Ruleset identity with this bound identity. An exact match establishes binding alignment; a mismatch must be resolved by Ruleset-owned compatibility, migration, acceptance, refusal, recovery, or rebinding semantics before ordinary application operation proceeds.
