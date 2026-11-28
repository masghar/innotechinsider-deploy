# I Ditched Immich After Two Years: Why Ente Is Now My Top Pick

> Immich spent years dominating the self-hosted photo scene, but Ente’s hardened security, zero-knowledge encryption, and lean footprint won over my homelab.

By InnotechInsider Staff · Data & Security · Sep 19, 2026
Canonical URL: https://innotechinsider.com/data-security/immich-vs-ente-self-hosted-google-photos-2026/

> **TL;DR** Immich revolutionized self-hosted photo backup, but its heavyweight microservices footprint and lack of zero-knowledge encryption eventually took a toll; switching to self-hosted Ente Photos delivered rock-solid stability, audited end-to-end encryption, and seamless mobile syncing.

For anyone who spent the early 2020s trying to de-Google their digital lives, [Immich](https://immich.app/) felt like an absolute miracle. It brought a pixel-perfect clone of Google Photos straight into Docker, complete with fluid mobile scrubbing, instant timeline scrubbing, and local machine learning models that could recognize your dog across a decade of holiday snapshots. When the project secured funding back in 2024, the self-hosting community celebrated what felt like a permanent victory over proprietary cloud lock-in.

I was right there in the front row. I deployed Immich on my primary unRAID server in late 2023, pointed it at a dedicated 4TB NVMe cache pool, and faithfully updated the container stack every two weeks. For more than two years, it backed up every photo taken by my partner and me across three generations of smartphones.

Yet last month, I permanently spun down my Immich stack. In its place sits [Ente Photos](https://ente.io/), an open-source, end-to-end encrypted photo platform that has quietly matured into the most resilient personal cloud tool available in 2026. The migration took a weekend, but the peace of mind it restored to my home server was immediate.

![high end smartphone displaying photo gallery app](https://images.unsplash.com/photo-1567985944845-cb4d1e598822?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxoaWdoJTIwZW5kJTIwc21hcnRwaG9uZSUyMGRpc3BsYXlpbmclMjBwaG90byUyMGdhbGxlcnklMjBhcHB8ZW58MHwwfHx8MTc4OTgxMTg4Nnww&ixlib=rb-4.1.0 "high end smartphone displaying photo gallery app — Photo by Josh Power on Unsplash")

## The Honeymoon and the Hangover with Immich

To understand why I walked away, you first have to understand the operational weight of running Immich. Immich is ambitious—perhaps too ambitious. It was built to replicate Google Photos feature-for-feature, which means it doesn't just store pictures; it indexes them with multi-model vector embeddings, transcribes background video audio, and performs facial clustering locally.

That sophistication comes with severe architectural overhead. A standard Immich stack isn't a single executable; it is a sprawling orchestration of services. You have the core server, the microservices container, a dedicated Redis instance for job queues, an isolated machine-learning pipeline running PyTorch or ONNX runtimes, and a heavily extended PostgreSQL database using extensions like `pgvector`.

For homelab hobbyists who love monitoring dashboard dials, this is fun. But as a production system housing two decades of irreplaceable family memories, it proved exhausting:

* **Resource voracity:** Even with hardware transcoding on an Intel QuickSync processor, background jobs frequently pegged CPU utilization across multiple cores whenever my family uploaded 500 photos from a vacation.
* **Fragile update paths:** While the Immich development team is remarkably talented, the blistering pace of releases frequently introduced breaking database migrations. Skipping three minor versions meant carefully reading changelogs to avoid schema locks or corrupted vector indices.
* **Zero at-rest encryption:** Immich stores files on your disk in plain directory structures. If someone gains unauthorized root access to your server or steals an offsite backup drive, your entire visual life is wide open. In an era where personal [data security](/data-security/) hygiene requires zero-trust assumptions even inside local networks, plain-file storage felt increasingly outdated.

I didn't want to manage an enterprise-grade AI cluster just to back up my smartphone's camera roll. I wanted an impenetrable, lightweight vault.

## Enter Ente: Cryptographic Rigor Meets Homelab Reality

Ente approached the photo problem from the opposite direction. Instead of starting with Google’s feature set and trying to self-host it, Ente’s creators started with cryptography. Designed from the ground up around zero-knowledge architecture, Ente was initially recognized primarily as a commercial hosted service for privacy purists. But its entire codebase—server, web, desktop, and mobile clients—is open-source under the AGPLv3 license.

By early 2026, the self-hosted deployment of Ente reached absolute parity with its managed offering. Running `ente-server` locally requires little more than a Go binary (or a single lightweight container), a standard PostgreSQL instance, and an S3-compatible storage backend, such as MinIO or even an offsite Backblaze B2 bucket.

The defining difference lies in where the trust resides. In Ente, encryption happens entirely on the client before data ever touches your local network interface. Using [XChaCha20-Poly1305](https://en.wikipedia.org/wiki/ChaCha20-Poly1305) authenticated encryption, your photos, metadata, and album structures are scrambled on your phone or laptop. The server only ever sees encrypted blobs.

Independent penetration testing firms like [Cure53 have audited Ente's cryptography](https://ente.io/architecture/cure53-audit.pdf), verifying that even a fully compromised server instance reveals nothing about the user's photos or identity. For those of us keeping a keen eye on modern [cybersecurity](/cybersecurity/) threats, running a service where server compromise equals zero data loss is transformative.

![compact nas server sitting on modern wooden desk](https://images.unsplash.com/photo-1759986452774-be47f7db2362?ixid=M3w5MDk5NzB8MHwxfHNlYXJjaHwxfHxjb21wYWN0JTIwbmFzJTIwc2VydmVyJTIwc2l0dGluZyUyMG9uJTIwbW9kZXJuJTIwd29vZGVuJTIwZGVza3xlbnwwfDB8fHwxNzg5ODExODg2fDA&ixlib=rb-4.1.0 "compact nas server sitting on modern wooden desk — Photo by Thuan Tran on Unsplash")

## Head-to-Head: Immich vs. Ente in 2026

Both platforms represent the pinnacle of open-source engineering, but they serve completely different philosophies. Here is how they stack up across the metrics that actually matter after years of real-world use:

| Feature / Metric | Immich (v1.11x+) | Ente Photos (Self-Hosted) |
| :--- | :--- | :--- |
| **Primary Architecture** | Node.js, Redis, Postgres (pgvector), Python ML | Go backend, Postgres, S3-compatible object storage |
| **Container Count** | 4 to 6 active containers | 1 server container + 1 DB (or external DB) |
| **Encryption Model** | Plaintext at rest; optional disk-level encryption | Client-side End-to-End Encryption (E2EE) |
| **Independent Security Audit** | Community-reviewed | Audited by Cure53 & Symbolic Software |
| **AI / Semantic Search** | Server-side CLIP embeddings & facial recognition | On-device machine learning (client-side indexing) |
| **Idle RAM Footprint** | ~2.5 GB to 4.5 GB (with ML running) | ~250 MB to 450 MB |
| **Storage Portability** | Relies heavily on DB links; raw files visible | Pure S3 abstraction; painless distributed replication |
| **Background Mobile Sync** | Excellent, but battery-heavy during initial sync | Native background sync, battery-optimized |

The architectural contrast shows up immediately in system overhead. Where Immich routinely consumed 3 GB of RAM idling on my server while waiting to compute image embeddings, Ente’s Go daemon barely sips 300 MB.

## The Trade-Offs: What You Give Up

Switching to Ente isn't without compromises. Immich’s server-side approach allows for some truly jaw-dropping capabilities that Ente simply cannot match due to its cryptographic boundaries.

Because Immich has unencrypted access to your photos on your server, it can run heavy server-side [ai apps](/ai-apps/) workflows. It can churn through 50,000 photos overnight using a dedicated GPU, categorizing faces, detecting geographic landmarks, and letting you search for hyper-specific natural language queries like "receipts on a wooden table."

Ente cannot do this on the server. Doing so would violate zero-knowledge architecture. Instead, Ente performs machine learning tasks—such as on-device face recognition and object classification—directly on your client devices (your phone or desktop). While modern smartphone neural engines handle this surprisingly well in 2026, the initial index of a massive library takes longer and requires your phone to be plugged in overnight to parse the library locally.

Furthermore, Immich’s public album sharing feels more like modern web software. You can send a link to relatives, let them upload their own photos into your shared album, and view live updates instantly. Ente supports sharing, but because it relies on cryptographic key exchange, sharing albums with non-Ente users requires viewing a decryptor web client that can feel marginally slower on older browsers.

## How I Handled the Migration

Moving away from Immich was simpler than I feared, largely because I had maintained Immich’s external library feature alongside its upload directory.

1. **Database Export:** First, I ran Immich's database backup routines to ensure I retained all tag and favorite metadata in a JSON dump.
2. **Exporting Master Files:** Using the Immich CLI, I exported all original assets without transcode artifacts, ensuring raw EXIF metadata remained untouched.
3. **Deploying Ente Server:** I spun up the official Ente Docker compose template, mapping it to a dedicated MinIO bucket hosted on my network-attached storage.
4. **Desktop CLI Ingestion:** Rather than trying to push 400 GB of high-resolution photos and 4K video clips through a mobile Wi-Fi connection, I used the `ente-cli` desktop utility on a wired 10GbE connection. The CLI handled client-side encryption locally on an M-series Mac before streaming the encrypted chunks directly into my local MinIO endpoint.

The entire 400 GB library uploaded in less than two hours. Once uploaded, opening the Ente mobile app on my phone and entering my recovery passkey populated my entire timeline within seconds.

## The Verdict: Reliability Trumps Novelty

Immich is an astonishing technical feat. If your primary goal is having an exact, uncompromised replacement for Google Photos with bleeding-edge AI search running on your own hardware, Immich remains the undisputed champion.

However, after years of homelabbing, my priorities have shifted from chasing features to demanding operational stability. A personal photo archive is not a media server like Plex or Jellyfin; if a media server crashes or corrupts a database, you lose some watch history. If your photo vault hiccups during an unannounced schema migration, you risk losing irreplaceable documentation of your family's life.

Ente treats photos not as data points to be fed into machine-learning vectors, but as private property requiring mathematically sound protection. It uses a fraction of the system resources, eliminates breaking maintenance cycles, and ensures that my family's private moments stay private—even from my own home server's root account. In 2026, that makes it the best self-hosted photo tool money can't buy.
