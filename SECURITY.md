# Security policy

Report vulnerabilities privately via GitHub's **Report a vulnerability** feature where enabled; otherwise contact the maintainers through the organization's private channels. Do not disclose secrets or personal information in public issues.

## Supported releases

Only deployed and explicitly tagged production releases receive production support. Development branches and examples are not production-ready.

## Baseline security controls

- No committed secrets, tokens, proxies with credentials, or personal contact lists.
- Use least privilege, repository rulesets, and required CI checks.
- Protect service-to-service tokens and validate untrusted URLs; network retrieval must defend against SSRF and redirects.
- Restrict extraction to permitted sources and implement robots, terms and rate limiting at fetch boundaries.
- Implement POPIA lawful basis, minimization, retention, deletion and Do-Not-Contact suppression prior to any outreach.
