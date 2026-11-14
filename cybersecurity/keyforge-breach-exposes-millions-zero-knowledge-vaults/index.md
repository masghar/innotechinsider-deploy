# How the KeyForge Breach Exposed 38 Million Zero-Knowledge Vaults

> A devastating supply-chain intrusion at KeyForge has exposed 38 million encrypted vaults, proving that zero-knowledge architectures still have a glaring human flaw.

By InnotechInsider Staff · Cybersecurity · Oct 21, 2026
Canonical URL: https://innotechinsider.com/cybersecurity/keyforge-breach-exposes-millions-zero-knowledge-vaults/

> **TL;DR** A sophisticated continuous-deployment compromise has handed state-sponsored attackers 38 million encrypted KeyForge vaults, revealing that zero-knowledge cryptographic designs remain terrifyingly vulnerable to metadata leaks, legacy hashing schemes, and developer-pipeline attacks.

The marketing pitch behind zero-knowledge password managers has always rested on an absolute mathematical bargain: *Even if our servers are ripped out of our data centers, your secrets remain unreadable math.*

Over the weekend, that bargain met its most brutal stress test yet.

San Francisco-based KeyForge—one of the fastest-growing enterprise and consumer credential platforms of the past four years—confirmed that an unauthorized third party breached its cloud production snapshot environment. Attackers exfiltrated complete database backups containing approximately 38.2 million customer vaults. The incident compromises accounts ranging from everyday consumers to system administrators at Fortune 500 defense contractors, cloud infrastructure giants, and government agencies.

While KeyForge executives were quick to issue a boilerplate statement insisting that customer master passwords were "never stored on our servers" and that zero-knowledge architecture remains unbroken, security researchers and incident response teams are painting a far darker picture. The breach did not just capture encrypted credential blobs; it exfiltrated completely unencrypted customer metadata, vault modification dates, IP access logs, and billing addresses.

Crucially, it captured millions of legacy vaults that were never upgraded to modern key-derivation standards. The mathematical fortress has not fallen, but the walls have been hauled away to a hostile server farm where supercomputing clusters are already chipping away at the mortar.

![cybersecurity engineer analyzing code on monitor screen](https://images.unsplash.com/photo-1669977731132-80652bf93050?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxjeWJlcnNlY3VyaXR5JTIwZW5naW5lZXIlMjBhbmFseXppbmclMjBjb2RlJTIwb24lMjBtb25pdG9yJTIwc2NyZWVufGVufDB8MHx8fDE3OTI1NzkxMjR8MA&ixlib=rb-4.1.0 "cybersecurity engineer analyzing code on monitor screen — Photo by Evgeniy Alyoshin on Unsplash")

## The Attack Vector: Poisoning the Deployment Well

KeyForge’s preliminary post-mortem, quietly released late Monday evening, reveals an intrusion vector that should terrify any security team relying on cloud-native build infrastructure.

The attackers did not crack AES-256-GCM. Instead, they compromised a secondary engineer’s identity through a session-token hijacking technique that bypassed FIDO2 hardware tokens via a compromised local debugging proxy. From that beachhead, the adversaries pivoted through an internal continuous integration and continuous deployment (CI/CD) pipeline on AWS, gaining administrative access to an isolated staging tier used for disaster recovery verification.

This staging tier contained read-only, point-in-time snapshots of the primary vault database, replicated across US and European availability zones. The exfiltrated data spans vaults created and synced between January 2021 and August 2026.

According to a bulletin from the [Cybersecurity and Infrastructure Security Agency (CISA)](https://www.cisa.gov/), the tactics, techniques, and procedures (TTPs) match those of a well-financed threat actor tracked as Bronze Starlight (or Storm-0875), known for deploying automated password-cracking farms against targeted intellectual property holders.

For organizations that have rushed to modernize their  architecture over the past two years, this incident exposes a recurring failure mode: investing millions in client-side cryptography while leaving pipeline access keys exposed to developer credential theft.

## The Metadata Trap: Why Zero-Knowledge Isn't Zero-Risk

The standard public relations response to encrypted vault theft is simple: "Your master password is your shield; if it is strong, you are safe." In practice, this defense ignores the lethal intelligence contained in vault metadata.

Zero-knowledge architectures rarely encrypt operational metadata because the client application needs to parse server-side structures to determine sync states, platform compatibility, and billing tiers without decrypting the entire payload. In KeyForge’s architecture, the following fields were stored in plaintext alongside the encrypted vault blobs:

*   Account creation date, last sync timestamp, and client OS telemetry.
*   The raw number of stored items, categorization tags, and folder names.
*   The fully qualified domain names (FQDNs) and URLs of websites saved within each entry.
*   The key derivation function (KDF) parameters assigned to that specific account, including iteration counts and cryptographic salt values.

Consider what an attacker can do with that metadata. A state-sponsored adversary does not need to crack 38 million vaults. They can instantly filter the database for users who have entries for internal VPN portals, sovereign defense repositories, cloud administration consoles, or critical infrastructure management dashboards.

Once prioritized, the attackers turn their attention to the user’s key derivation configuration. And that is where KeyForge’s historical technical debt turns catastrophic.

| Architectural Parameter | Legacy Vaults (Pre-2023) | Modern Consumer (2024–2026) | Enterprise Managed (Current) |
| :--- | :--- | :--- | :--- |
| **Symmetric Encryption** | AES-256-CBC | AES-256-GCM | XChaCha20-Poly1305 |
| **Key Derivation (KDF)** | PBKDF2-HMAC-SHA256 | Argon2id | Argon2id |
| **KDF Work Factor** | 100,000 Iterations | 3 Passes / 64MB Memory | 5 Passes / 128MB Memory |
| **Offline Cracking Resistance** | Low (GPU/ASIC Vulnerable) | High | Extremely High |
| **Exposed Metadata** | URLs, Timestamps, Tags | URLs, Timestamps | Stripped / Opaque Blobs |

As the comparison demonstrates, KeyForge maintained backwards compatibility for older accounts without forcing a mandatory KDF re-encryption pass. Vaults created prior to early 2023 were secured using PBKDF2 with a mere 100,000 iterations. Modern custom-built ASIC arrays can rip through PBKDF2-HMAC-SHA256 at speeds measured in billions of guesses per second, rendering an 11- or 12-character alphanumeric password crackable in a matter of hours.

While accounts created after late 2024 utilized the memory-hard [Argon2 key derivation standard](https://en.wikipedia.org/wiki/Argon2), an estimated 40% of the exfiltrated database consisted of unmigrated accounts. For those millions of users, their zero-knowledge vault is a vault in name only.

## The Offline Threat: When the Attacker Has All the Time in the World

When a password manager database is breached, the attacker no longer faces defensive rate-limiting. There are no CAPTCHAs, no account lockouts after five failed attempts, no geo-blocking, and no security operations center monitoring anomalous login spikes.

The adversary copies the encrypted blob to an offline computing cluster and runs targeted wordlists, rule-based mutations, and multi-billion-token neural network linguistic models against the PBKDF2 or Argon2 parameters.

This dynamic radically alters consumer  expectations, particularly because users were conditioned to believe that changing their master password *after* a breach announcement resolves the danger.

It does not.

If an attacker holds a copy of your vault as it existed on August 15, 2026, changing your master password on October 21 does nothing to protect the credentials inside that stolen snapshot. If the offline cracker breaks your master password next month, every API token, seed phrase, corporate credential, and private note stored in that snapshot is compromised.

![hardware security key plugged into modern laptop](https://images.unsplash.com/photo-1614064641938-3bbee52942c7?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxoYXJkd2FyZSUyMHNlY3VyaXR5JTIwa2V5JTIwcGx1Z2dlZCUyMGludG8lMjBtb2Rlcm4lMjBsYXB0b3B8ZW58MHwwfHx8MTc5MjU3OTEyNHww&ixlib=rb-4.1.0 "hardware security key plugged into modern laptop — Photo by FlyD on Unsplash")

## The 4-Step Incident Response Plan for Affected Users

If your organization or household uses KeyForge, treating this incident as a routine "change your master password" event is a catastrophic miscalculation. The security posture must assume that your current vault contents are either readable now or will become readable in the near future.

Follow this systematic containment process immediately:

1.  **Triage High-Value Targets First**
    Do not begin by changing Netflix or retail passwords. Identify and rotate credentials for services that provide administrative leverage: primary email accounts, cloud providers (AWS, Azure, GCP), domain registrars, code repositories, and identity providers (Okta, Entra ID).
2.  **Revoke Active Sessions and API Keys**
    A password change alone does not invalidate persistent OAuth refresh tokens or active session cookies stored in secure notes. Log into critical providers and manually terminate all existing sessions, revoke programmatic API access tokens, and invalidate existing SSH keys that were mirrored in your vault.
3.  **Enforce Hardware MFA Out-of-Band**
    If your two-factor authentication (2FA) TOTP seed secrets were stored inside the same KeyForge vault as your usernames and passwords, your multi-factor security is zero. Immediately transition high-value services to hardware-based FIDO2/WebAuthn authenticators or standalone hardware security keys, which cannot be extracted from a compromised vault.
4.  **Migrate to an Audited, High-Memory Vault Architecture**
    Audit your remaining credential store. If you remain on a platform utilizing PBKDF2, verify that your derivation parameters meet or exceed the latest [NIST's Digital Identity Guidelines](https://pages.nist.gov/800-63-3/). Configure your vault client to enforce maximum memory allocation settings under Argon2id.

## The Death of Master Passwords and the Passkey Dilemma

The KeyForge catastrophe lands at an awkward inflection point for the broader cybersecurity industry. For the past three years, the tech sector has evangelized passkeys as the silver bullet that would eliminate credential theft forever. Yet the vast majority of consumers and enterprises manage their passkeys through the exact same cloud-synced vaults that were compromised in this breach.

When an encrypted vault containing a synchronized passkey’s private cryptographic key is exfiltrated, the core premise of FIDO2—that private keys never leave physical hardware—is broken by convenience. Syncing passkeys across cross-platform ecosystems requires storing cryptographic material in cloud-hosted keychains. If the keychain falls, the passkey falls with it.

We cannot continue patching over the structural flaw of the modern web: the belief that outsourcing our entire digital identity to a single cloud-hosted database is safe so long as the company puts "Zero-Knowledge" in its marketing materials.

The KeyForge breach has stripped away that illusion. The mathematics of modern cryptography are solid, but mathematics cannot compensate for unencrypted metadata, forgotten legacy defaults, and CI/CD pipelines governed by human vulnerability. If your security model relies on an offshore cloud provider remaining permanently uncompromised, your model is already broken.
