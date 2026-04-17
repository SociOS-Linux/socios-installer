# Fog Install Entrypoint in socios-installer

This document captures the intended **installation entrypoint role** of `socios-installer` for the Fog layer.

The platform layering is:
- contracts in `SourceOS-Linux/sourceos-spec`
- substrate invariants in `SociOS-Linux/SourceOS`
- first-boot realization in `SociOS-Linux/socios-ignition`

`SociOS-Linux/socios-installer` is where an operator should be able to select and install a **fog-capable node profile** without manually hand-assembling those layers.

## Responsibilities of this repo for the Fog layer

### 1. Installation profile selection

This repo should expose an install path that can select a fog-capable profile, such as:
- workstation fog node
- edge fog node
- cluster fog worker

### 2. Ignition/profile embedding

The installer lane should be able to:
- reference the appropriate ignition profile
- embed or attach the correct first-boot configuration
- keep disk selection and install safety explicit

### 3. Safety-first operator entrypoint

A fog installer flow should make the dangerous parts legible:
- target disk/device confirmation
- profile identity and provenance
- expected storage substrate behavior
- whether enrollment into optional automation is off by default

### 4. Boundary preservation

This repo should not redefine:
- typed contracts
- substrate semantics
- first-boot systemd logic
- opt-in automation rules

It should act as the operator-facing install entrypoint that composes those already-defined layers.

## Follow-up expected here

Future PRs should add:
1. fog install profiles / profile descriptors
2. ignition attachment flows for fog-capable installs
3. operator docs for workstation vs edge install paths
4. safety checks / confirmations for fog node installation
