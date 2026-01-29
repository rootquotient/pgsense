# Security Policy

## Supported Versions

`pgsense` is currently under active development.

Security fixes will be applied to:

- The `main` branch
- The latest tagged release (once releases are published)

Older versions may not receive security updates.

---

## Reporting a Vulnerability

If you discover a **security vulnerability**, please **do not open a public GitHub issue**.

Instead, follow the responsible disclosure process below.

### How to Report

Send a private report via:

- GitHub Security Advisories

Your report should include:

- A clear description of the vulnerability
- Steps to reproduce (proof-of-concept if possible)
- Affected versions or commit hashes
- Potential impact (data exposure, privilege escalation, DoS, etc.)
- Any suggested mitigations (optional)

Incomplete or vague reports may be delayed.

---

## What Qualifies as a Security Issue

Examples include:

- SQL injection in generated queries
- Unsafe handling of database credentials
- Privilege escalation beyond documented requirements
- Leakage of sensitive metadata or query contents
- Unsafe defaults in managed/cloud environments
- Any behavior that violates the stated safety principles

Performance issues, incorrect recommendations, or false positives are **not** security issues — open a normal issue instead.

---

## Disclosure Process

Once a valid report is received:

1. **Acknowledgement** within 72 hours
2. **Initial assessment** and severity classification
3. **Fix development** in a private branch or advisory
4. **Coordinated disclosure** once a fix is available
5. **Public advisory** with mitigation steps

We aim to resolve critical issues as quickly as possible, but **no fixed SLA is guaranteed**.

---

## Expectations from Reporters

We ask that you:

- Act in good faith
- Avoid exploiting the issue beyond proof-of-concept
- Do not disclose the vulnerability publicly before coordination
- Give reasonable time for remediation

Failure to follow responsible disclosure may result in reports being ignored.

---

## Security Design Principles

`pgsense` is designed with security in mind:

- Read-only database access by default
- No automatic schema changes
- No execution of generated SQL
- Minimal privilege requirements
- Cloud-safe and RLS-aware behavior

Security reports that contradict documented behavior should reference the exact deviation.

---

## Out of Scope

The following are out of scope for security reports:

- PostgreSQL core vulnerabilities
- Misconfigured user databases
- Third-party extensions not used by `pgsense`
- Issues requiring superuser access that `pgsense` does not request

---

## Acknowledgements

Valid security reports may be acknowledged in release notes or advisories, unless anonymity is requested.

---

## Policy Changes

This security policy may evolve as the project matures.  
Significant changes will be documented in the repository history.
