# Requirements

## Phase 1: Nix-native OpenVox agent

- Model system dependency packaging on [Arch Linux's OpenVox package](https://archlinux.org/packages/extra/any/openvox/).
- Compare component coverage with [upstream AIO definitions](https://github.com/OpenVoxProject/openvox/tree/main/packaging).
- Provide the complete agent functionality without bundling a redundant Ruby runtime.
- Support aarch64-darwin, aarch64-linux, and x86_64-linux from the first implementation milestone. aarch64-linux is required for Nix-enabled Apple containers used as development sandboxes.
- Allow arbitrary compatible third-party gems, including ones absent from nixpkgs, through a declarative flake interface. Resolve and pin dependencies reproducibly without requiring users to write Nix packaging code.
- Preserve conventional Puppet CLI, config, SSL, state, and /etc/puppetlabs and /opt/puppetlabs behavior where needed. Determine exact compatibility paths through tests.

## Validation strategy

- Reuse the upstream OpenVox agent test suites as the primary functional and compatibility checks. Run as much as possible against the Nix-native build.
- Investigate upstream RSpec/Rake tests and acceptance tests, including their dependencies and environment assumptions.
- Inspect Arch Linux's OpenVox PKGBUILD, its check() phase (if any), packaging CI, and related validation practices. Reuse useful coverage without assuming Arch CI runs upstream tests.
- Propose patches upstream when they make the same tests usable across package layouts. Avoid a permanent Nix-specific test fork.
- Add focused Nix-only tests for packaging, paths, third-party gems, and installed-agent behavior.
- Run relevant checks on aarch64-darwin, aarch64-linux, and x86_64-linux; document any upstream tests not yet runnable.

## Phase 2: Upstream AIO development

Provide Nix development shells capable of running upstream's actual AIO build workflow. Start with one supported Linux target. Building AIO artifacts and installing Nix-native packages are distinct goals.

## Later ecosystem work

- OpenBolt: independently extensible MRI Ruby environment.
- OpenVox Server: JRuby gem support, including hiera-eyaml, plus NixOS service.
- OpenVoxDB: JVM packaging, PostgreSQL integration, termini, and NixOS service.
- Jig: module development tooling. Existing Puppet module testing typically uses Bundler and does **not** require a packaged agent.
- Vox Pupuli modulesync workflows may be supported separately.

## Engineering constraints

- Package-level functionality must not depend on NixOS modules; Darwin and other Linux distributions are first-class targets.
- NixOS and nix-darwin integrations should consume shared package composition interfaces.
- Do not assume system-wide /opt symlinks can be installed without elevated privileges.
- All repository changes go through pull requests.
