# FieldStation42 Media Organization Strategy

This document outlines the organizational strategy for **commercials** and **bumpers** for FieldStation42 stations. It is designed to maintain consistency across networks and shows while supporting seasonal and time-specific rotations.

---

## Commercials

Commercials are organized by **era**, **audience**, **network**, and **season**, allowing flexible rotation without duplication.

### Commercial Guidelines

- **Generic directories** contain ads not specific to a network, e.g., Saturday morning cereals, general kids’ products.  
- **Network directories** contain station-specific ads for ABC, CBS, NBC, or FOX.  
- **Seasonal directories** are used for special holidays or events (e.g., October for Halloween, December for Christmas).  
- **Symlinks** may be used to include shared content across multiple networks or eras without duplication.  
- **Time-specific ads** (like Saturday morning cereals) live in `generic/morning` and are included only during scheduled cartoon hours (typically 7–11 AM).

---

## Bumpers

Bumpers are simpler: they are either **network-specific** or **show-specific**.

### Bumper Directory Structure

### Bumper Guidelines

- **Network bumpers**: branding stingers, station IDs, or general network branding.  
- **Show-specific bumpers**: intros, outros, or recurring show identifiers.  
- No need for seasonal or era-specific subdirectories unless a bumper is intentionally reused across multiple networks/shows.  
- Each schedule entry points to the appropriate `bump_dir` depending on context (network vs show-specific).

---

### Full Directory Structure

```shell
├── kids_80s
│   ├── generic
│   │   ├── afternoon
│   │   │   ├── abc -> ../../network/abc
│   │   │   ├── cbs -> ../../network/cbs
│   │   │   ├── fox -> ../../network/fox
│   │   │   ├── nbc -> ../../network/nbc
│   │   │   └── seasonal -> ../../seasonal
│   │   └── morning
│   │       ├── abc -> ../../network/abc
│   │       ├── cbs -> ../../network/cbs
│   │       ├── fox -> ../../network/fox
│   │       ├── nbc -> ../../network/nbc
│   │       └── seasonal -> ../../seasonal/
│   ├── network
│   │   ├── abc
│   │   ├── cbs
│   │   ├── fox
│   │   └── nbc
│   └── seasonal
│       ├── December
│       └── October
├── kids_90s
│   ├── generic
│   │   ├── afternoon
│   │   │   ├── abc -> ../../network/abc
│   │   │   ├── cbs -> ../../network/cbs
│   │   │   ├── fox -> ../../network/fox
│   │   │   ├── nbc -> ../../network/nbc
│   │   │   └── seasonal -> ../../seasonal
│   │   └── morning
│   │       ├── abc -> ../../network/abc
│   │       ├── cbs -> ../../network/cbs
│   │       ├── fox -> ../../network/fox
│   │       ├── nbc -> ../../network/nbc
│   │       └── seasonal -> ../../seasonal
│   ├── network
│   │   ├── abc
│   │   ├── cbs
│   │   ├── fox
│   │   └── nbc
│   └── seasonal
│       ├── December
│       └── October
├── standard_80s
│   ├── generic
│   │   ├── afternoon
│   │   │   ├── abc -> ../../network/abc
│   │   │   ├── cbs -> ../../network/cbs
│   │   │   ├── fox -> ../../network/fox
│   │   │   ├── nbc -> ../../network/nbc
│   │   │   └── seasonal -> ../../seasonal
│   │   ├── late
│   │   │   ├── abc -> ../../network/abc
│   │   │   ├── cbs -> ../../network/cbs
│   │   │   ├── fox -> ../../network/fox
│   │   │   ├── nbc -> ../../network/nbc
│   │   │   └── seasonal -> ../../seasonal
│   │   ├── morning
│   │   │   ├── abc -> ../../network/abc
│   │   │   ├── cbs -> ../../network/cbs
│   │   │   ├── fox -> ../../network/fox
│   │   │   ├── nbc -> ../../network/nbc
│   │   │   └── seasonal -> ../../seasonal
│   │   └── primetime
│   │       ├── abc -> ../../network/abc
│   │       ├── cbs -> ../../network/cbs
│   │       ├── fox -> ../../network/fox
│   │       ├── nbc -> ../../network/nbc
│   │       └── seasonal -> ../../seasonal
│   ├── network
│   │   ├── abc
│   │   ├── cbs
│   │   ├── fox
│   │   └── nbc
│   └── seasonal
│       ├── December
│       └── October
└── standard_90s
    ├── generic
    │   ├── afternoon
    │   │   ├── abc -> ../../network/abc
    │   │   ├── cbs -> ../../network/cbs
    │   │   ├── fox -> ../../network/fox
    │   │   ├── nbc -> ../../network/nbc
    │   │   └── seasonal -> ../../seasonal
    │   ├── late
    │   │   ├── abc -> ../../network/abc
    │   │   ├── cbs -> ../../network/cbs
    │   │   ├── fox -> ../../network/fox
    │   │   ├── nbc -> ../../network/nbc
    │   │   └── seasonal -> ../../seasonal
    │   ├── morning
    │   │   ├── abc -> ../../network/abc
    │   │   ├── cbs -> ../../network/cbs
    │   │   ├── fox -> ../../network/fox
    │   │   ├── nbc -> ../../network/nbc
    │   │   └── seasonal -> ../../seasonal
    │   └── primetime
    ├── late
    │   ├── abc -> ../../network/abc
    │   ├── cbs -> ../../network/cbs
    │   ├── fox -> ../../network/fox
    │   ├── nbc -> ../../network/nbc
    │   └── seasonal -> ../../seasonal
    ├── network
    │   ├── abc
    │   ├── cbs
    │   ├── fox
    │   └── nbc
    └── seasonal
        ├── December
        └── October
```

#### No need for symlinks in bumpers

```shell
└── bumpers
    ├── network
    │   ├── abc
    │   ├── cbs
    │   ├── fox
    │   └── nbc
    └── show-specific
        ├── show_1
        ├── show_2
        └── ...
```

---

## Summary

1. **Commercials** → curated by era, audience, network, and season; supports symlinks for shared content.  
2. **Bumpers** → organized by network or show-specific only; simple hierarchy.  
3. **Time-specific rotations** → enforced via schedule tags and carefully chosen directories.  
4. **Consistency** → All FieldStation42 schedule entries reference these directories to maintain a clean, maintainable media library.

---

```shell
         ┌─────────────────────────┐
         │ Cartoon Show Tag Active │
         │  (7:00 – 11:00 AM)      │
         └───────────┬─────────────┘
                     │
                     ▼
       ┌────────────────────────────┐
       │  Determine Show-Specific   │
       │       Bumpers              │
       │ /media/fs42/bumpers/show-  │
       │ specific/{show_name}       │
       └───────────┬────────────────┘
                   │
                   ▼
       ┌────────────────────────────┐
       │  Determine Network Bumpers │
       │ /media/fs42/bumpers/network│
       │ /{abc,cbs,nbc,fox}         │
       └───────────┬────────────────┘
                   │
                   ▼
         ┌─────────────────────┐
         │ Commercial Rotation │
         └─────────┬───────────┘
                   │
                   ▼
   ┌───────────────────────────────────────────┐
   │ Select from Kids Era / Generic / Morning  │
   │ - /media/fs42/commercials/kids_80s/       │
   │   generic/morning                         │
   │ - /media/fs42/commercials/kids_90s/       │
   │   generic/morning                         │
   └──────────┬────────────────────────────────┘
              │
              ▼
   ┌─────────────────────────────────────┐
   │ Include Seasonal Ads if Any         │
   │ - /media/fs42/commercials/kids_80s/ │
   │   seasonal/October/                 │
   │ - /media/fs42/commercials/kids_90s/ │
   │   seasonal/October/                 │
   └──────────┬──────────────────────────┘
              │
              ▼
   ┌────────────────────────────────────┐
   │ Include Network-Specific Ads       │
   │ - /media/fs42/commercials/kids_80s/│
   │   network/{abc,cbs,nbc,fox}        │
   └──────────┬─────────────────────────┘
              │
              ▼
   ┌─────────────────────────────────────┐
   │ Final Rotation for Slot             │
   │ - Randomized / Shuffled             │
   │ - Center or Side Breaks             │
   │ - Assigned bumpers & breaks         │
   └─────────────────────────────────────┘
```

### Notes

1. **Order of inclusion**:
   - Show-specific bumpers → network bumpers → commercials (generic → seasonal → network).
2. **Shuffling / sequence**:
   - Use `sequence` and `random_tags` from FieldStation42 config to control rotation order.
3. **Time-specific**:
   - You can set morning ads and bumpers to be played between 7–11 AM, afternoon ads during those times, and so forth
4. **Symlinks**:
   - Used to avoid duplicating commercials across networks or seasonal/era variations.
5. **Bumpers**:
   - Always pulled first to frame the shows properly, then commercials.

---
