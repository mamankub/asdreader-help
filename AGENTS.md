# Repository instructions

## CI runner policy (owner instruction, 2026-11-10)

All CI must execute on the owner's self-hosted runners. Never use GitHub-hosted
runners or a hosted fallback, including matrix jobs and reusable workflows.
Before triggering CI or pushing a change that triggers it, verify runner labels,
repository access, OS/architecture and tools. If a required runner is unavailable,
report the missing platform; do not silently skip required tests or switch hosting.
See CI-RUNNERS.md for routing and provisioning requirements. This owner instruction
supersedes inherited guidance to track external reusable workflows at @main.

## Temporary CI platform scope (owner instruction, 2026-11-10)

Run CI only on the owner's Linux x64 and Windows x64 runners for now. macOS,
ARM64, FreeBSD and RISC-V platform jobs are paused; do not report them as tested.
Keep web/portable checks that execute on Linux/Windows x64. Restore additional
platform coverage only after owner approval and verification of matching owned
runners. No GitHub-hosted fallback is permitted.
