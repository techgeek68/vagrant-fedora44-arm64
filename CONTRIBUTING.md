# Contributing

Thank you for your interest in contributing to the documentation and support repository for `techgeek68/fedora44-arm64`. Contributions of all kinds are welcome, including documentation improvements, bug reports, and feature suggestions.

Please review our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing.

## How to Contribute

### Reporting Issues

If you find a bug, a documentation error, or unexpected behavior:

1. Search [existing issues](../../issues) first, to avoid duplicates.
2. If none match, open a new issue using the appropriate [issue template](.github/ISSUE_TEMPLATE).
3. Include as much detail as possible: your host OS, VirtualBox version, Vagrant version, box version, and the exact steps to reproduce the problem.
4. Do not include secrets, tokens, passwords, or private infrastructure details in issue reports. Redact anything sensitive before posting.

### Suggesting Enhancements

Feature and documentation improvement suggestions are welcome. Open an issue using the feature request template, and describe:

- The problem you are trying to solve
- Your proposed solution
- Any alternatives you considered

### Submitting Changes

1. Fork this repository.
2. Create a new branch for your change:
   ```
   git checkout -b docs/improve-installation-guide
   ```
3. Make your changes. Keep documentation changes focused and scoped to a single topic where possible.
4. Follow the [Documentation Style Guide](#documentation-style-guide) below.
5. Commit your changes with a clear, descriptive message.
6. Push your branch and open a pull request using the [pull request template](.github/PULL_REQUEST_TEMPLATE.md).

### Documentation Style Guide

- Use clear, plain language. Prefer short sentences over long, complex ones.
- Use fenced code blocks with the appropriate language tag for all commands and code.
- Use relative links when referencing other files in this repository.
- Do not include real IP addresses, hostnames, credentials, tokens, or any other sensitive values, even as examples. Use clearly labeled placeholders such as `YOUR_USERNAME` or `example.com`.
- Keep one command per code block where practical, so readers can copy and run commands individually.
- Mark any assumption or inferred detail clearly, rather than presenting it as a confirmed fact.

## What We Cannot Accept

- Changes that introduce real credentials, private infrastructure details, or internal system information
- Provisioning scripts that reveal internal, non public implementation details
- Content that violates the [Code of Conduct](CODE_OF_CONDUCT.md)

## Questions

If you are not sure whether a contribution fits, open an issue first to discuss it before submitting a pull request.
