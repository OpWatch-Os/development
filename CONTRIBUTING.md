# Contributing

Useful contributions identify an exact source revision and device/software baseline, explain the change or finding, and include reproducible validation. Start with the open milestones in [ROADMAP.md](docs/ROADMAP.md).

Keep research, successful compilation, offline compatibility checks, and hardware-tested behavior clearly distinguished. A port proposal should name its missing inputs rather than supply guessed partition sizes, boot headers, AVB values, or vendor compatibility claims.

Publish original code and documentation that you have permission to contribute. Preserve licenses and provenance when third-party code is introduced. Do not add stock firmware, proprietary blobs, SDK images, private device dumps, packet captures, serial numbers, network credentials, account data, or signing keys.

Use relative paths in shared documentation. Record public commits and artifact hashes where they make a finding reproducible. Kernel work belongs in the appropriate source-history-preserving fork, with links from this development repository.

There is currently no supported build, flashing, or installation procedure. A contribution introducing one must document prerequisites, validation, exact supported device/build, and the verified stock restoration path.
