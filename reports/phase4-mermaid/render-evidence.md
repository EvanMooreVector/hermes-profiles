# Phase 4 Mermaid rendering evidence

## Result

PASS. Mermaid CLI was installed profile-locally and rendered a minimal standard Mermaid flowchart to SVG.

- Renderer package: `@mermaid-js/mermaid-cli@11.17.0`
- Verified command output: `11.17.0`
- Render command output: `Generating single mermaid chart`
- Output SVG is non-empty: 11,014 bytes and begins with an SVG `flowchart-v2` document.

## Installation scope

The renderer is local to the active technical-architect profile:

`C:\Users\EvanMoore\AppData\Local\hermes\profiles\technical-architect\tools\mermaid-renderer`

No global npm install was performed. No Terraform/OpenTofu/Pulumi/Helm/Ansible/Tailscale/Traefik tooling, provider configuration, secrets, state, or gateway state was changed.

The Windows shell supplied a stale `NODE_OPTIONS` preload reference. Commands below use `env -u NODE_OPTIONS` only for the npm/mmdc subprocesses; this avoids the stale preload and does not persistently alter environment configuration.

## Commands exercised

```text
env -u NODE_OPTIONS "C:/Program Files/nodejs/npm.cmd" install --prefix "C:/Users/EvanMoore/AppData/Local/hermes/profiles/technical-architect/tools/mermaid-renderer" --no-audit --no-fund @mermaid-js/mermaid-cli@11.17.0
env -u NODE_OPTIONS "C:/Users/EvanMoore/AppData/Local/hermes/profiles/technical-architect/tools/mermaid-renderer/node_modules/.bin/mmdc.cmd" --version
env -u NODE_OPTIONS "C:/Users/EvanMoore/AppData/Local/hermes/profiles/technical-architect/tools/mermaid-renderer/node_modules/.bin/mmdc.cmd" -i "C:/Users/EvanMoore/Documents/GitHub/hermes-profiles/reports/phase4-mermaid/minimal-flowchart.mmd" -o "C:/Users/EvanMoore/Documents/GitHub/hermes-profiles/reports/phase4-mermaid/minimal-flowchart.svg"
```

Observed results:

```text
added 190 packages in 27s
11.17.0
Generating single mermaid chart
```

## Evidence hashes (SHA-256)

```text
e8bf4424ca9d96d37cf2ba25682798ddeb8075d2b6875e3b8f17834d245df3b6  minimal-flowchart.mmd
e358d00b152d46a8a78671af2c957e2e77361b4be682ce498dff38f43ebd9661  minimal-flowchart.svg
87270cf06ad4fb3943afa1b62806348b6d91be210354dd450b05c73572b4a753  profile-local renderer package.json
ee7cb59279ee5e5b3afae83dc76f3cf95cd84c773725a0655de7f30c0f2ef278  profile-local renderer package-lock.json
```

## Source-profile posture

No Phase 4 behavioral source edit was needed because the corrected guidance already makes rendering conditional on a verified renderer:

- `profiles/technical-architect/AGENTS.md:18`
- `profiles/technical-architect/SOUL.md:108`

Current source hashes:

```text
8cc69b1d2a83914ef99c6586544200b4b0a5592d57f8a9fbcc2d6d0c8a96c5fd  profiles/technical-architect/AGENTS.md
cf493fa7d546efc508cb572770976eb3798e01730772aa253ccaddda9e113648  profiles/technical-architect/SOUL.md
```

These two source files were already modified by the completed upstream Phase 2-3 task; this Phase 4 task made no behavioral source changes. The only repository files created by this task are the render evidence files in this directory.

## Limitations

The validation proves that this host can render the supplied minimal standard `flowchart TD` source using the installed renderer. It does not certify every Mermaid diagram type, every Mermaid version, GitHub's renderer, or experimental C4 Mermaid syntax. C4 plugin syntax remains conditional on renderer/plugin compatibility; standard Mermaid flowcharts remain the portable default.

## SOURCES

`C:\Users\EvanMoore\Documents\GitHub\hermes-profiles\reports\phase4-mermaid\minimal-flowchart.mmd`
-> Exact minimal Mermaid source passed to mmdc.

`C:\Users\EvanMoore\Documents\GitHub\hermes-profiles\reports\phase4-mermaid\minimal-flowchart.svg`
-> Durable SVG output emitted by mmdc for the source diagram.

`C:\Users\EvanMoore\AppData\Local\hermes\profiles\technical-architect\tools\mermaid-renderer\package.json`
-> Profile-local renderer dependency declaration.

`C:\Users\EvanMoore\AppData\Local\hermes\profiles\technical-architect\tools\mermaid-renderer\package-lock.json`
-> Locked profile-local dependency tree used for the rendered result.

`C:\Users\EvanMoore\Documents\GitHub\hermes-profiles\profiles\technical-architect\AGENTS.md`
-> Source guidance specifying conditional rendering behavior.

`C:\Users\EvanMoore\Documents\GitHub\hermes-profiles\profiles\technical-architect\SOUL.md`
-> Source profile policy carrying the same conditional rendering behavior.
