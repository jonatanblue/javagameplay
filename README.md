# JavaGamePlay recovery

Recovery of **Alien Invasion (v2.0)**, **WarZone**, and **WarZone 2**, Java
applets written by **Ben Librojo** (1996–2000), originally hosted at
`www.tardis.ed.ac.uk/~benl/` and later `www.javagameplay.com`. Both hosts are
long dead. The games were reconstructed from Internet Archive Wayback Machine
captures in July 2026. The bytecode is unmodified (Java 1.0/1.1 class files).

See [`alien-invasion/MANIFEST.md`](alien-invasion/MANIFEST.md) for full
provenance: which capture every file came from, integrity checks, and what
could not be recovered.

## Playing

```
cd alien-invasion
python3 -m http.server 8321
```

Then open <http://localhost:8321/>. The games run in a modern browser via
[CheerpJ](https://cheerpj.com/) (loaded from its CDN, so internet is
required). Alien Invasion and WarZone 2 are complete and verified playable.
WarZone is missing one never-archived class file but plays regardless.

## Status

| Game | Recovered | Verified running |
|---|---|---|
| Alien Invasion (v2.0), 1996 | complete | yes |
| WarZone 2 | complete | yes |
| WarZone | 23/24 classes (`e.class` lost) | yes, no crash observed |

## Copyright

The games (everything under `alien-invasion/ai/`, `alien-invasion/WarZone/`,
`alien-invasion/wz2/`, and the recovered images and archived HTML in
`pages/`) are **Copyright © 1996–2000 Ben Librojo, all rights reserved**.
They are redistributed here without permission, in the spirit of software
preservation, because the original hosts no longer exist. **If you are the
copyright holder and want this taken down (or blessed), please open an
issue and it will be honored promptly.**

The recovery tooling and wrapper files (the HTML runner pages, manifest, and
this README) are trivial and dedicated to the public domain.
