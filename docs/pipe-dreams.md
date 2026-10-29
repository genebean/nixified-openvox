# Pipe dreams

Ideas that a Nix-native OpenVox ecosystem might enable someday. These are **not roadmap commitments** and should not distract from packaging the agent, supporting upstream AIO development shells, or other practical ecosystem work.

## Nix-specific Puppet providers

Explore providers for Nix-managed resources. They could let Puppet work with parts of a Nix-based system that are outside its normal resource model.

## A Puppet package provider for nixpkgs

The ambitious idea: manage packages from nixpkgs through Puppet's package resource.

Open questions include how to select package sets and versions, handle profiles or generations, and avoid conflicts with NixOS, nix-darwin, or Home Manager. There is no proposed implementation yet.

## Integrations with Nix configuration tools

A future integration could use Puppet to extend what is managed declaratively on:

- NixOS, for carefully delegated resources.
- nix-darwin, potentially in a role analogous to nix-homebrew.
- Home Manager-only installations.
- Non-NixOS Linux hosts with Nix installed.

These would need explicit ownership boundaries so Puppet and Nix do not fight over the same resources.

## What is not a pipe dream

Making OpenFact aware of Nix environments and exploring contributions to [facterdb](https://github.com/voxpupuli/facterdb) is practical follow-on work tracked in [issue #9](https://github.com/genebean/nixified-openvox/issues/9).
