# Security Policy

## Reporting a Vulnerability

To report a security vulnerability, use
[GitHub's private vulnerability reporting](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)
on the affected repository. Please do not open a public issue for suspected security vulnerabilities.

For critical vulnerabilities affecting multiple amatos repositories, report to the
[.github repository](https://github.com/amatos/.github/security/advisories/new).

Report security concerns through GitHub's private vulnerability reporting when it
is enabled on the affected repository. If that is not available, contact the
repository owner directly through the contact method listed on the relevant
project profile or README.

When reporting, include:

- The affected repository, package, or deployed service.
- A clear description of the issue and likely impact.
- Steps to reproduce, proof of concept, or affected versions when available.
- Any suggested mitigation if you already have one.

## Response Expectations

I triage security reports as time permits. Personal projects may not have formal
service-level commitments, but credible reports will be prioritized over normal
feature work.

## Accepted Risks

### nix-devenv uses `nixpkgs-unstable`

Intentional. Dev shells need latest tool versions (terraform, ansible, kubectl).
nix-devenv is never consumed by nix-darwin at build time — it provides independent
`nix develop` entry points outside the system build graph.

### Nix Flake Alignment (`follows` Pattern)

nix-darwin uses `inputs.nixpkgs.follows` to force companion repos to use the same
nixpkgs at build time, regardless of their own `flake.lock`. This means
flake.lock drift between repos is cosmetic for the system build but matters
for standalone development and CI.

## Supported Versions

Unless a repository says otherwise, only the latest released version or the
default branch is considered supported.
