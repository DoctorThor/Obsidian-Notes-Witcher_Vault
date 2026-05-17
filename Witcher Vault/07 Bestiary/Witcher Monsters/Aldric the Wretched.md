---
statblock: inline

tags: monster
---

# `=this.file.name`

> [!infobox]+
> 
> # `=this.file.name`
> 
> ![[Placeholder Image.png|cover hsmall]]
> 
> ###### Classification
> 
> |Type|Stat|
> |---|---|
> |Category|Cursed One|
> |Habitat|[[Old Hall — Weddle]], cellar|
> |Activity|Constant — trapped, can't leave|
> |Sentience|Low (degraded — was High)|
> |Status|Unique|
> 
> ##### Combat Profile
> 
> |Type|Stat|
> |---|---|
> |CR|4|
> |AC|13|
> |HP|75|
> |Speed|35 ft., climb 20 ft.|
> |Size|Large|
> 
> ##### Weaknesses
> 
> |Type|Effective|
> |---|---|
> |Silver|Yes — suppresses regeneration, reduces speed|
> |Steel|No|
> |Igni|Partial|
> |Yrden|No|
> |Aard|Partial|
> |Fire|Partial|
> |Specific Oil|Beast Oil|

---

## Bestiary Description

What stands in the cellar of Old Hall is not a bear. The proportions are wrong — too tall, the shoulders set too far back, the neck too short. The remnants of a scholar's robes hang in tatters across a body that was redesigned by something that did not care about aesthetics. The amulet glows faintly at his throat, fused into the skin in a ring of scar tissue that never healed cleanly.

His eyes are the worst part. They are too intelligent for an animal and too animal for a man.

---

## Lore & Origin

Aldric was a hedge mage of middling skill and enormous ambition. He spent years chasing enchanter status — able to identify magic items, never quite able to create them. When he heard rumors of a Bear School witcher medallion hidden in the abandoned Vester holdings outside Weddle, he moved into Old Hall and began studying it obsessively.

He identified the base medallion correctly as genuine Bear School work. He identified a secondary enchantment layered on top — cruder, more recent, clearly not witcher-made. He attempted to absorb the secondary enchantment directly to study its construction.

The amulet infected him in seconds. The transformation took three days. He has been in the cellar ever since, trapped by a compulsion he cannot explain or overcome, waiting for someone to come and end it.

### What Common Folk Believe

The old lord's family haunts Old Hall. Whatever lives there now is part of that haunting — a monster called up by old noble wickedness.

### What Witchers Know

A werebear variant created by a corrupted witcher medallion — the infection is magical rather than biological, which makes it both more controllable and more unpredictable than a natural lycanthrope. The amulet is the source. Aldric is the consequence.

---

## Behavior

- **Hunting Pattern:** Does not hunt. Is trapped. Responds to intrusion with aggression that fights against his remaining will.
- **Territory:** The cellar of Old Hall — he cannot leave, though he does not fully understand why.
- **Pack / Solitary:** Solitary.
- **Signs of Presence:** Claw marks on every surface at varying heights. Overwhelming animal musk. Scratch patterns on the cellar floor where he has paced the same path hundreds of times.

---

## Stat Block

```statblock
layout: Basic 5e Layout
name: Aldric, the Wretched
size: Large
type: Monstrosity
subtype: Cursed
alignment: Chaotic Neutral
ac: 13
hp: 75
hit_dice: 10d10+20
speed: 35 ft., climb 20 ft.
stats:
- 18
- 10
- 14
- 6
- 10
- 5
saves: ""
skillsaves:
- Perception: +2
damage_vulnerabilities: ""
damage_resistances: Cold, Poison
damage_immunities: Bludgeoning, Piercing, and Slashing from nonmagical non-silver weapons
condition_immunities: Charmed, Frightened
senses: Darkvision 60 ft., passive Perception 12
languages: Understands Common but can barely speak
cr: 4
traits:
- name: Amulet Bond
  desc: The amulet cannot be removed from Aldric while he lives. Any attempt to forcibly remove it causes Aldric to immediately use his Rampage bonus action against the creature that tried, regardless of other triggers or conditions.
- name: Regeneration
  desc: Aldric regains 5 hit points at the start of his turn. If he takes damage from a silver weapon, this trait doesn't function at the start of his next turn. Aldric dies only if he starts his turn with 0 hit points and doesn't regenerate.
- name: Keen Smell
  desc: Aldric has advantage on Wisdom (Perception) checks that rely on smell. He always knows the location of every creature in the cellar, even in total darkness.
- name: Wounded and Slow
  desc: Aldric was gravely wounded by a silver sword three weeks ago and has never fully healed. Whenever he takes damage from a silver weapon, his speed is reduced by 10 ft. until the end of his next turn.
- name: Lucid Moment (1/Encounter)
  desc: When first reduced below 30 hit points, Aldric regains enough coherence to speak one clear sentence. He looks at the party — really looks — and says quietly, "...Don't give it to the soldier." Then the intelligence leaves his eyes and the animal returns.
- name: Schoolblind
  desc: Aldric will not use Infectious Swipe against a creature he recognises as a Bear School witcher. Something in his degraded mind still processes the medallion. He cannot explain this. He simply doesn't.
actions:
- name: Multiattack
  desc: Aldric makes two attacks, one Bite and one Claws.
- name: Bite
  desc: "Melee Weapon Attack: +6 to hit, reach 5 ft., one target. Hit: 11 (2d6+4) piercing damage. If the target is Medium or smaller, it must succeed on a DC 14 Strength saving throw or be grappled (escape DC 14)."
- name: Claws
  desc: "Melee Weapon Attack: +6 to hit, reach 5 ft., one target. Hit: 13 (2d8+4) slashing damage."
- name: Infectious Swipe (Recharge 5-6)
  desc: "Melee Weapon Attack: +6 to hit, reach 5 ft., one target. Hit: 13 (2d8+4) slashing damage. The target must succeed on a DC 13 Constitution saving throw or become Infected (see Infected Condition below). Aldric will not use this against a Bear School witcher he can identify."
bonus_actions:
- name: Rampage
  desc: When Aldric reduces a creature to 0 hit points with a melee attack, he moves up to 10 feet and makes one Bite attack against another creature within reach.
- name: Persuasion Response
  desc: When a creature successfully persuades Aldric (DC 14 Charisma check, advantage if a Bear School witcher speaks or if the party referenced his notes), his will overrides his instinct. He uses this bonus action to rake his own claws across his chest, dealing 9 (2d8) damage to himself. This can only occur twice before his intelligence degrades completely.
reactions:
- name: Cornered Beast
  desc: When Aldric is reduced to 25 hit points or fewer for the first time, he makes one Claws attack against the creature that dealt the triggering damage. This attack is made with disadvantage — his hand shakes. The man inside is briefly visible.
- name: Instinctive Recoil
  desc: When Aldric takes damage from a silver weapon, he recoils and cannot make opportunity attacks until the start of his next turn.
legendary_actions: ""
```

---

## The Infected Condition

A creature that fails the saving throw against Infectious Swipe begins a slow transformation. Symptoms surface after a long rest. Full transformation takes one week without magical intervention.

**Day 1–2:** Advantage on Strength checks and saving throws. Disadvantage on all Intelligence checks. Sleep is disturbed — vivid, violent dreams. No mechanical penalty yet, but the player should feel it.

**Day 3–4:** Uncontrolled aggression surfaces. When the infected character takes damage, they must succeed on a **DC 12 Wisdom saving throw** or use their reaction to make one melee attack against the nearest creature, friend or foe.

**Day 5–6:** Physical changes become visible — increased body hair, thickened fingers, altered posture. Size category increases by one. The character has disadvantage on Charisma (Persuasion) checks as their appearance unnerves people.

**Day 7:** On the night of the seventh day, the character makes a final **DC 15 Wisdom saving throw.** On a success, transformation halts — they are permanently changed but remain a PC with a complicated future. On a failure, full transformation completes and the character becomes an NPC werebear.

**Curing the Infection:** Aldric's notes contain a partial counter-formula requiring three ingredients: **blackthorn root** (common, any herbalist), **harpy feathers** (requires a small hunt or purchase), and **echo moss** (grows only near sites of old magical activity — a source exists near a ruined pre-Conjunction elven outpost two days from Weddle). A character proficient in Medicine or the herbalism kit can complete the formula from the notes with a DC 15 Intelligence check. Alternatively, _Remove Curse_ cast at 3rd level works but causes one level of exhaustion per day since infection.

---

## Loot & Remains

|Item|Use / Value|
|---|---|
|The Amulet of Old Hall|Central quest item — see [[The Amulet of Old Hall]]|
|Werebear claws (harvestable, 4)|Alchemical ingredient — 8 NC each to the right buyer|
|Werebear hide (partial, degraded)|20 NC to a tanner willing to ask no questions|
|Remnants of Aldric's robes|Worthless as clothing. His name is embroidered inside the collar.|

---

## DM Notes

_Play him small inside the monster. The intelligence in his eyes matters more than the claws. The Lucid Moment and the Cornered Beast reaction are the two places where the man surfaces — make sure the table feels both._

_His letter to his sister is upstairs in the study. If the party read it before coming down here, the fight hits differently._

_He wants to die. That is the only coherent want he has left. If the party finds a way to give him that cleanly, without cruelty, it should feel like mercy, not victory._