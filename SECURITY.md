# Security Policy

## Supported Versions

The `main` branch is the supported version.

## Reporting A Vulnerability

This repository contains prompt and skill instructions. It should not include credentials, private data, or executable code that handles secrets.

If you find a security issue, please use GitHub's private vulnerability reporting if it is enabled for this repository. If private reporting is not available, open a minimal public issue asking for a private disclosure channel and do not include exploit details or sensitive data in the issue body.

## Before Publishing Changes

Run:

```bash
rg -n "Users/|api[_-]?key|token|secret|password" .
```

Do not commit local paths, tokens, credentials, private prompts, or unpublished third-party content.
