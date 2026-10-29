# Contributor and agent guidance

- **Never commit to the default branch.** Use a topic branch and pull request for every change.
- Keep PRs and documentation concise. Prefer small, reviewable changes and focused issues over walls of text.
- Stay within the issue's scope; don't turn agent packaging work into Puppet module development.
- Ask the repository owner before starting additional, unrequested work or changing project direction.
- Prefer Nix-native dependencies over bundling upstream AIO runtimes.
- Treat upstream AIO as a functional reference and Arch Linux packaging as the initial Nix-native reference.
- Support aarch64-darwin and x86_64-linux first; do not add x86_64-darwin.
- Preserve Puppet/OpenVox conventions where practical. Test compatibility rather than assuming path changes are harmless.
- Third-party gems must be usable declaratively in flakes, including gems absent from nixpkgs, without requiring users to write derivations.
- Distinguish packaged agent/Server/OpenBolt gem environments from Bundler-based Puppet module testing. Module development tooling belongs with Jig, not the initial agent work.
- Add or update tests when changing functionality; clearly state what was actually tested in each PR.
