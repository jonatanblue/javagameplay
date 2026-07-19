# Recovery Manifest — Ben Librojo's Java applet games

Recovered 2026-07-19 from the Internet Archive Wayback Machine, using raw
(`id_`) captures so bytecode was not rewritten. Bytecode is unmodified,
class file format major version 45 (Java 1.0/1.1, compiled ~1996-1999).

## Sources

| Source | Role |
|---|---|
| `www.javagameplay.com/code/{ai,WarZone,wz2}/` (crawl of 2014-03-13, plus 2013-01/2013-08 for a few wz2 files) | Primary: a full open-directory crawl of Ben's `/code/` tree. All class/sfx/gfx/exp files came from here. |
| `www.javagameplay.com/WarZone2/` (crawls of 2000) | Supplied `wz2/f.class`, missing from the 2014 crawl. Build verified identical: `WarZone2/u.class` (2000) is byte-for-byte equal to `code/wz2/u.class` (2013). |
| `www.tardis.ed.ac.uk/~benl/` (crawls 1997–2000) | Original 1996/97 applet HTML pages (`invasion/invasion.html`, `java/warzone/warzone.html`) and `tank4.gif`. |
| `community.fortunecity.ws/olympia/coe/148/` (live mirror) | Page HTML + `titlescr3.jpg` only. Its applet tag points codebase at the dead tardis host; it serves **no** class files (invader.class → 404). |

## Original applet tags

- Alien Invasion: `<applet codebase=.../invasion code=invader.class width=400 height=350>` (identical on tardis 1997 and javagameplay 2007, no `archive=`, no `<param>`s)
- WarZone: `<applet codebase=.../java/warzone/ code=wireframe.class width=400 height=350>`
- WarZone 2: `<applet codebase="WarZone2" code="warzone2.class" width=400 height=350>`

## Recovered — Alien Invasion (`ai/`) — **COMPLETE**

- Classes (15/15): `invader.class`, `a.class`–`n.class` — every class referenced
  in the constant pools is present.
- Graphics (22/22): `gfx/ALIEN-{1,2,3}{A–D}.GIF`, `gfx/earth.gif`,
  `gfx/n_cluster.gif`, `gfx/n_missile.gif`, `gfx/n_player.gif`,
  `gfx/n_player_half.gif`, `gfx/n_tp{2,4,6,8}.gif`, `gfx/pickup.gif`
- Explosion frames (17/17): `exp/exp-01.gif` … `exp/exp-17.gif`
- Sounds (8/8): `sfx/{afterburner,bl,clust,Explosionv3,fire,laser,missile2,pickup}.au`
- Every resource filename string embedded in the bytecode matches a recovered
  file; all magic bytes verified (CAFEBABE / .snd / GIF8).

## Recovered — WarZone 2 (`wz2/`) — **COMPLETE**

- Classes (29/29): `warzone2.class`, `a`–`e`, `g`–`z` (no `j`), `ab`, `bb`, `cb`
  (`f.class` recovered from the 2000-04-08 capture of the old `/WarZone2/`
  path; build identity proven via byte-identical `u.class`).
- Sounds (6/6): `sfx/{bl,boom,clank,explode,fire,fire3}.au`

## Recovered — WarZone (`WarZone/`) — **INCOMPLETE**

- Classes 23/24: `wireframe.class`, `a`–`d`, `f`–`v`.
- Sounds (5/5): `sounds/{bl,exp1,exp3,gun1,gun5}.au`
- **MISSING: `e.class`** — referenced by the bytecode but never captured by
  the Wayback Machine under any known path (`/code/WarZone/`, the old
  `/WarZone/` path, or tardis `~benl/java/warzone/`). In practice the game
  launches and plays anyway (classes load lazily); it will only fail with
  NoClassDefFoundError if/when class `e` is first instantiated.

## Runtime verification (2026-07-19, CheerpJ 4.3, Chrome)

- **Alien Invasion**: launches, title screen, gameplay verified — alien waves,
  enemy fire, explosion animations, lives/score HUD, keyboard controls all
  work under the deprecated Java 1.0 event model.
- **WarZone 2**: launches, animated title, textured software-3D city renders,
  gameplay reached (validates the substituted `f.class`).
- **WarZone**: launches, intro splash, wireframe-3D gameplay reached and
  playable (drive + fire tested); no NoClassDefFoundError observed so far.

## Not found

- "Alien Invasion 2": no page or code directory for such a title exists in
  any crawl of javagameplay.com (2,599 CDX entries checked) or tardis. The
  site's catalog was: Alien Invasion, WarZone, WarZone 2, WarZone 3,
  Orbital Defense, BreakBall, Swarm, Spitfire, Heavy Cannon, Tank Hunter,
  Doomsday, Lunar, Ice Breaker Alpha. "Alien Invasion (v2.0)" appears to be
  the game's own version number, not a sequel.
- Other games above (BreakBall `bb/`, Orbital Defense `od/`, etc.) were also
  fully captured in the 2014 crawl and could be recovered the same way.

## Running

- `index.html` / `invasion.html` / `warzone.html` / `warzone2.html` —
  CheerpJ 4.3 wrappers (needs internet for the CheerpJ CDN loader).
  Serve with `python3 -m http.server` from this directory; file:// won't work.
- Fallback: JDK 8 `appletviewer invasion.html` (appletviewer was removed in
  JDK 11; the deprecated Java 1.0 event model these applets use still works
  on Java 8).
