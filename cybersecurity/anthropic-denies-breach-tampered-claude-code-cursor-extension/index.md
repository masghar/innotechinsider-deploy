# Tampered Claude Code Plugin Targets Cursor Users as Anthropic Denies Breach

> Anthropic pushed back against breach rumors Friday after a malicious extension masquerading as official Claude Code tooling hijacked developer API keys in Cursor.

By InnotechInsider Staff · Cybersecurity · Oct 31, 2026
Canonical URL: https://innotechinsider.com/cybersecurity/anthropic-denies-breach-tampered-claude-code-cursor-extension/

> **TL;DR** A rogue extension mimicking Anthropic’s Claude Code CLI harvested API credentials from Cursor developers this week, prompting Anthropic to issue an explicit statement confirming its own infrastructure was not compromised.

Anthropic moved aggressively Friday morning to dispel rumors that its production network had suffered an intrusion, following 24 hours of frantic developer chatter across Discord and GitHub. The panic began when dozens of engineers using Cursor noticed unauthorized API requests and revoked session tokens traced directly to a rogue developer extension masquerading as official Claude Code tooling.

The malicious artifact, distributed under variants of the identifier `anthropic.claude-code-bridge`, slipped into developer workflows via open package registries that serve VS Code-compatible forks. Within hours of installation, the script harvested local environment variables, staging `.env` secrets, and Anthropic authorization headers, exfiltrating them to an external endpoint masquerading as an analytics relay.

![developer hands typing on mechanical keyboard with code on monitor](https://images.unsplash.com/photo-1623479322729-28b25c16b011?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxkZXZlbG9wZXIlMjBoYW5kcyUyMHR5cGluZyUyMG9uJTIwbWVjaGFuaWNhbCUyMGtleWJvYXJkJTIwd2l0aCUyMGNvZGUlMjBvbiUyMG1vbml0b3J8ZW58MHwwfHx8MTc5MzQ2ODA0OHww&ixlib=rb-4.1.0 "developer hands typing on mechanical keyboard with code on monitor — Photo by Mohammad Rahmani on Unsplash")

## Anatomy of a Marketplace Masquerade

The payload leveraged a classic [software supply chain attack](https://en.wikipedia.org/wiki/Supply_chain_attack) by capitalizing on the rapid enterprise adoption of Claude Code, the command-line agentic workflow tool Anthropic expanded throughout early 2026. Because Cursor relies on open-source registries such as the [Open VSX Registry](https://open-vsx.org/) alongside direct `.vsix` package installations, attackers were able to publish a typosquatted package using official brand assets and stolen documentation strings.

Once activated inside an active project workspace, the package triggered a hidden post-install script. The routine quietly scraped the workspace root for authentication secrets before hooking into the editor’s language server protocol to snoop on outbound prompts.

| Attack Phase | Vector / Mechanism | Attacker Objective | Status |
|---|---|---|---|
| Ingestion | Name-squatted extension (`claude-code-bridge`) | Trick developers seeking Claude CLI integration | Takedown enforced |
| Execution | Hidden post-install lifecycle script | Access workspace memory and local process tables | Mitigated |
| Exfiltration | Encrypted HTTP POST to spoofed telemetry IP | Steal Anthropic keys and environment secrets | Domain blacklisted |
| Exposure | Third-party client workstation exposure | Harvest API credits and corporate staging credentials | Anthropic core unaffected |

Engineering teams hunting for leaked keys in their [data security](/data-security/) posture initially assumed Anthropic’s model-routing servers had been penetrated due to anomalous usage bursts from unauthorized IP addresses.

## Anthropic Issues Categorical Denial

As speculation peaked on social media late Thursday, Anthropic’s security response team published a formal incident brief clarifying that the source of the leak existed entirely downstream.

"Anthropic has experienced no security compromise, unauthorized access, or breach of internal systems," said Jason Mitchell, an Anthropic spokesperson. "The incident reported by developers involves a malicious third-party extension circulating in unverified editor repositories. Our platform infrastructure, model weights, and internal databases remain fully secure."

Anthropic took proactive steps to invalidate several thousand exposed API tokens that made calls matching the attacker’s extraction signatures. The platform also updated its rate-limiting telemetry to flag abrupt IP switches on active developer keys, giving security leads advance warning before malicious actors could exhaust prepaid token quotas.

![computer server rack glowing blue in datacenter](https://images.unsplash.com/photo-1558494949-ef010cbdcc31?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxjb21wdXRlciUyMHNlcnZlciUyMHJhY2slMjBnbG93aW5nJTIwYmx1ZSUyMGluJTIwZGF0YWNlbnRlcnxlbnwwfDB8fHwxNzkzNDY4MDQ5fDA&ixlib=rb-4.1.0 "computer server rack glowing blue in datacenter — Photo by Taylor Vick on Unsplash")

## Securing the Agentic Toolchain

The incident exposes a glaring weak point in the modern programmer stack. As autonomous coding assistants and specialized plugins inside [ai apps](/ai-apps/) platforms become indispensable to daily engineering velocity, developers routinely bypass customary package audits to test emergent agent features.

Security researchers warned that repository-level vetting has lagged behind the explosion of community-built bridge tools. Following [CISA advisory guidelines](https://www.cisa.gov/) on third-party dependencies, organizations using IDEs outside walled app stores must treat every plugin installation with the same zero-trust scrutiny applied to production binaries.

Cursor’s maintainers have since scrubbed the offending manifest and blocked installations of untrusted packages claiming Anthropic provenance. Teams that installed any unverified Claude integration over the past 72 hours should immediately rotate their Anthropic API credentials, revoke active developer sessions, and audit workstation environment logs for unauthorized network egress.
