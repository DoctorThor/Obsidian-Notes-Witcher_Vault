# 📁 The Witcher Campaign — Vault Structure

A hybrid structure organized by **type** at the top level, with **region-based subfolders** where it makes sense. Built for a 5e Witcher campaign set on the Continent c. 1240–1260.

---

## Recommended Folder Layout

```
📂 The Continent/
│
├── 📂 World/
│   ├── 📂 Regions/
│   │   ├── 📂 Cintra/
│   │   │   ├── _Cintra Overview.md
│   │   │   ├── 📂 Locations/
│   │   │   └── 📂 Factions/
│   │   ├── 📂 Verden/
│   │   ├── 📂 Brokilon/
│   │   ├── 📂 Temeria/
│   │   └── 📂 [Other Regions]/
│   ├── The Continent Timeline.md
│   ├── The Northern Kingdoms — Political Overview.md
│   ├── Nilfgaard — The Empire.md
│   └── The Conjunction of the Spheres.md
│
├── 📂 NPCs/
│   ├── 📂 Cintra & Surrounds/
│   ├── 📂 Witchers/
│   ├── 📂 Mages & Sorceresses/
│   ├── 📂 Non-Human Communities/
│   └── 📂 Nobility & Rulers/
│
├── 📂 Sessions/
│   ├── Session 001 - [Title].md
│   └── _Session Template.md
│
├── 📂 Quests/
│   ├── 📂 Witcher Contracts/
│   │   ├── 📂 Active/
│   │   ├── 📂 Completed/
│   │   └── 📂 Available/
│   ├── 📂 Bulletin Board/
│   │   ├── 📂 Active/
│   │   ├── 📂 Completed/
│   │   └── 📂 Available/
│   └── 📂 Main Story/
│
├── 📂 Bestiary/
│   ├── 📂 Cursed Ones/
│   ├── 📂 Necrophages/
│   ├── 📂 Vampires/
│   ├── 📂 Draconids/
│   ├── 📂 Hybrids/
│   ├── 📂 Insectoids/
│   ├── 📂 Elementa/
│   ├── 📂 Relicts/
│   └── 📂 Ogroids/
│
├── 📂 Factions/
│   ├── 📂 Kingdoms & States/
│   ├── 📂 Non-Human Groups/
│   ├── 📂 Criminal & Underground/
│   └── 📂 Mage Orders/
│
├── 📂 Items & Equipment/
│   ├── 📂 Witcher Gear/
│   ├── 📂 Magic Items/
│   └── 📂 Gwyhyr & Named Weapons/
│
├── 📂 Player Handouts/
│
└── 📂 _Templates/
    ├── NPC Template.md
    ├── Location Template.md
    ├── Session Notes Template.md
    ├── Witcher Contract Template.md
    ├── Bulletin Board Quest Template.md
    ├── Faction Template.md
    ├── Monster Template.md
    └── Magic Item Template.md
```

---

## Tag System

### Type Tags
`#npc` `#location` `#faction` `#quest` `#contract` `#session` `#monster` `#item` `#lore`

### Race/Species Tags
`#human` `#elf` `#dwarf` `#halfling` `#witcher` `#mage` `#dryad` `#gnome`

### Status Tags
`#active` `#dead` `#completed` `#available` `#wip` `#rumor`

### Region Tags
`#cintra` `#verden` `#brokilon` `#temeria` `#redania` `#aedirn` `#kaedwen` `#nilfgaard` `#mahakam`

### Tone/Content Tags
`#political` `#combat` `#mystery` `#monster-hunt` `#moral-dilemma` `#non-human-tension`

### Alignment/Allegiance Tags
`#pro-human` `#pro-nonhuman` `#neutral` `#nilfgaard-aligned` `#scoia-tael-sympathizer`

### Monster Category Tags
`#cursed-one` `#necrophage` `#vampire` `#draconid` `#hybrid` `#relict` `#elemental` `#ogroids`

---

## Linking Conventions

- `[[Double Brackets]]` for every named NPC, location, faction, or monster the first time it appears
- `[[Note Name|Display Text]]` when the linked name reads awkwardly in context
- Each Region folder has a `_Region Overview.md` as its hub — everything in that region links back to it
- Every Witcher Contract links to its `[[Monster]]` entry in the Bestiary
- Every Quest links to its relevant `[[Location]]` and `[[NPC]]` entries

---

## Recommended Plugins

| Plugin | Use |
|---|---|
| **Dataview** | Query active contracts, list NPCs by region, track completed quests |
| **Templater** | Auto-fill templates with filenames and dates |
| **Kanban** | Quest board — mirrors an in-world notice board |
| **Breadcrumbs** | Navigate region → location → NPC hierarchies |
| **Calendar** | Link session notes to real session dates |
