# Security Policy

## Reporting a Vulnerability

This repository contains proprietary code implementing hardware-bound security.
Do NOT open public issues for security vulnerabilities.

Report privately to: security@[your-domain].com

Expected response time: 24 hours.

## Security Architecture

See [`docs/architecture/SECURITY_ARCHITECTURE.md`](docs/architecture/SECURITY_ARCHITECTURE.md)

Key protections:
- mTLS 1.3 hardware-bound certificates
- TPM 2.0 / Apple Secure Enclave code binding
- Zero inbound open ports
- eBPF kernel-level anomaly detection
- Automated cryptographic lockout on tamper
- Air-gapped operational fallback
