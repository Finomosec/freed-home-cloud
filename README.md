[English](README.md) · [Deutsch](README.de.md)

# Freed Home Cloud

> *"This is my data, and I'm keeping it to myself."*

A modular, self-hosted home cloud — free from Google, Microsoft and the other
hyperscalers. Privacy first, encrypted, multi-user, and designed to run on
hardware that sits in your own home.

> **Status: concept.** There is no usable code here yet. This repository holds
> the vision, the architecture notes and the open questions while the design is
> worked out. The name is reserved; development starts from here.

## Why

Every year more of our private life ends up on servers we neither own nor
control: documents, photos, calendars, passwords, conversations. Moving away
from that today means assembling a dozen separate self-hosting projects, each
with its own login, its own update story and its own backup gap — a full-time
hobby rather than a product.

Freed Home Cloud aims to be the package that removes that hurdle: one coherent
system, one login, one backup strategy, one place where everything is findable.

**Guiding values:** freedom · sovereignty · taking back control · personal
responsibility · local · independence.

## What it is meant to become

A modular platform whose components can be switched on as needed:

- **Portal** — a dashboard that makes every service discoverable
- **Single sign-on** — locally hosted, one login for all components
- **Multi-user** — built for families and small groups, not just one admin
- **Encrypted storage** — data at rest is encrypted on local disks
- **Layered backups** — snapshots, local mirroring, off-site redundancy

## Planned modules

The services that make the platform worth running, switchable per household:

- **Files, calendar and contacts** — the core of everyday digital life, synced across every device
- **Music streaming** — your own library, streamed at home and on the road
- **Password manager** — credentials stay on your own hardware
- **Device sync** — continuous file sync between PCs, phones and tablets
- **PDF toolbox** — merge, split, sign and convert without an upload to a stranger
- **Ad filtering** — network-wide, at DNS level, for every device in the house
- **Metrics and monitoring** — see what the system is doing and when it needs attention
- **Mail** — your own mailbox, optionally under your own domain
- **Local AI assistant** — a model running on your hardware, for support and automation

Wherever a good open-source project already exists, it gets integrated rather
than reinvented.

## The hard part: distributed backup

Most of the above is integration work. One piece is genuinely unsolved and is
the research core of this project:

**Storing your encrypted data redundantly on other users' machines — and keeping
it reliably available even though those machines are ordinary home PCs that go
offline whenever their owner feels like it.**

The sketch: data is split into encrypted, anonymised chunks and distributed
under software control; erasure coding keeps the storage overhead sane; and each
client measures how well-replicated a chunk still is and re-seeds it when
redundancy drops below a threshold — so the system heals itself without a
central coordinator.

The open questions are exactly the interesting ones: how a client reliably
measures network-wide chunk availability among transient nodes, how to avoid
over- and under-replication and thundering-herd effects, how to prove that a
remote node actually still holds what it claims, and how to enforce fairness.

### Prior art

This is not virgin territory, and pretending otherwise would be dishonest.
[Tahoe-LAFS](https://tahoe-lafs.org/), [Storj](https://www.storj.io/) and
[Sia](https://sia.tech/) all distribute encrypted, erasure-coded data — but they
lean on always-on professional or paid nodes and central repair services. The
projects that tried it with unreliable consumer machines — Symform, CrashPlan's
friend-to-friend backup, BuddyBackup — have all been discontinued. That gap is
the part worth working on.

## Roadmap (rough)

1. **Foundation** — portal, SSO, multi-user, encrypted storage, a first set of
   integrated services, sane update and monitoring story
2. **Backup** — layered local backups, then the distributed redundancy layer
3. **Assistance** — local AI for support and self-healing of the system

## Name

"Freed" as in *liberated* — the point is getting your data out of the big
clouds. This project is **not affiliated with** [FreedomBox](https://freedombox.org/),
Freenet or any similarly named project.

## Contributing

It is too early for code contributions. Ideas, criticism and pointers to prior
art are very welcome — please open an issue.

## License

[GNU AGPL-3.0](LICENSE) — if you run a modified version as a service, the users
of that service get the source. That seems like the right default for software
whose entire purpose is keeping people in control of their own systems.
