# Repository guidance

## Owner-maintained checkout guidance

<!-- fork: local governance reference; inherited project guidance is preserved. -->
For substantive work, read the shared project standards at `~/Project standards/README.md`, then its `Owner approval.md` and `Delivery gates.md`, followed by this repository's guidance. Use an authorized local or mounted copy; this reference grants no access. Owner approval is limited to infrastructure additions/deletions, permission changes and production deployments; independent agent review covers other changes. Report a refusal without another tool, route or identity.

This is a fork of operational Chia and Linux/storage scripts. The default tree does not prove current owned deployment or permission to execute host commands. No automatic workflow or credential-free repository-wide runner is established. Treat storage/harvester/provisioning commands as operational instructions requiring their actual task authority; do not run them as CI.

Keep evidence dated with source/version/hash and actual outcomes; distinguish source checks, CI and runtime acceptance. Never record credentials or private runtime stores in evidence. Standards compliance and settings gaps are tracked separately; this file does not authorize a deployment or settings write.
