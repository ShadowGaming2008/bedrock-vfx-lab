# Best way to give this research to Claude

Use **direct attachments**, not the archive, for normal agent work. A zip must be opened before its contents can be searched; uploading the key files directly removes that step.

Create one Claude Project (or one shared agent workspace) and upload these files once:

1. `bedrock-particles-safe-overrides.skill` — installs the safe vanilla-hook and emitter rules.
2. `particle_catalog_full.json` — the complete source-derived corpus: all 1,056 parsed particle definitions, including their raw JSON.
3. `particle_spawn_graph.csv` — event-to-child-effect chains.
4. `block_face_and_orientation_index.csv` — block gates, offsets, directions, and billboard-facing behavior.
5. `integrity_and_trigger_report.json` — validation findings and source-level links.

Attach `particles.zip` only when the task needs original whitespace, textures, entities, animations, manifest data, or other non-particle files. It is not needed for ordinary particle design or review.

For every task, add this short instruction:

> Use the attached Bedrock particle corpus and safe-overrides skill. Cite the exact particle identifier and file for every claim. Preserve generic vanilla effects unless a global replacement is explicitly requested. For a block-bound effect, use a gated custom emitter rather than replacing a generic vanilla visual.

## Handoff rule for multiple agents

Each agent should return: the affected identifiers, source files used as evidence, changed/added vanilla hooks, block conditions, expected trigger, and any runtime check still required. Merge those reports; do not ask later agents to recreate a broad summary of the corpus.
