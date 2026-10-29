# nixified-openvox

Nix-native packaging for the [OpenVox](https://github.com/OpenVoxProject/openvox) ecosystem, with familiar Puppet behavior.

## Roadmap

1. **Nix-native agent:** complete, Arch-style package with system-managed dependencies.
2. **AIO build shells:** let upstream developers build official AIO artifacts using Nix tooling.
3. **Ecosystem:** OpenBolt, OpenVox Server, OpenVoxDB, and Jig.

The initial platforms are **aarch64-darwin** and **x86_64-linux**; aarch64-linux follows. x86_64-darwin is out of scope.

See [project requirements](docs/requirements.md) and [open issues](https://github.com/genebean/nixified-openvox/issues).

## Status

Planning and initial implementation. No working package is provided by this repository yet.

## Contributing

All changes go through pull requests. See [AGENTS.md](AGENTS.md) for contributor and agent guidance.

Licensed under Apache-2.0; see [LICENSE](LICENSE).
