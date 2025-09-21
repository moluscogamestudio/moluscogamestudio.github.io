# Game Design Document

# High Level Concept
- Title: Wizard apprentice. (in progress)
- Concept statement: You are some guy with magic powers, shunned of your kingdom and put in a giant dungeon to die in. You must get free an confront your jailer traversing the dungeon using your randomly acquired magic powers and your creativity alone. 
- Genre: First person puzzle
- Target audience: Fans of ultima underworld and those crpg games.
- Unique selling point: The FUN happens when you cause chaos or find new ways to use your spells. A spiderweb spell can be used to slow down enemies, build a bridge, make a jump platform, or to make something burn longer.

# Product Design:
- Player Experience: the setting is "medieval goofy" as in (Dis)enchantment, the game is a mix of puzzle and party game where you don't take it seriously. The player is a wizard apprentice who's not completely in control of its powers.
- Style: (Dis)enchantment, comic, bold colors, goofy animations.
- Game World: TBD. Game comes first, lore comes later.
- Monetization: Nothing.
- Platform, technology and scope: PC so far. MKB support and maybe controller support.

# Game Design:
- This is the lengthiest section of the GDD: It should list all the locations, levels, enemies, items, player controls, menus, everything in-game. It's up to you how much detail you want to put into it. This section is "live" and should evolve as new concepts, ideas and mechanics are figured out.

## Mechanics

You have a melee weapon (club or dagger) and your spells. the dungeon is equal parts killzone and puzzle. you can defeat (kill) the enemies or disable them (stick them to the roof?) to advance, but you might also need to solve puzzles (how do i cross the chasm? how do I activate the lever on the other side of the rake?).
Further mechanics are explained in the Spells Section.

### Distances and ranges

Spells and effects are bound by three abstract units of distance called:

- Close: up to 2 meters away. "Cercano"
- Nearby: up to 6 meters away. "Proximo"
- Distant: up to 15 meters away. "Lejano"


### Damage, health, armor

- Damage is pure damage, there are no types. 
- Armor (Toughness) reduces damage. 
- Criticals ignores armor.
- DoT damage over time ticks once by second.


### Targets

Targets are game entities that can be affected by spells. 

- `wall`: Walls, floors and ceiling of the dungeon.
- `door`: Hinged doors, trapdoors, sewer covers, chests.
- `self`: the player
- `creature`: another creature that's not the player
- `object`: some kind of furniture, like a sconce or torch, debris, coins, etc.
- `area`: a circular area in range

Some entities share more than one target type. I.E.: Chests are both doors and objects. 

### Spells

There are several schools of spells. You start with a few spells and get random ones as you go on. The spells are of an agnostic nature and scale only with level. Their descriptions are purposefully vague and refer to `objectives`, `materials`, and `actions`

- Cast Time: how many seconds it takes to cast. I=0, S=1, M=2, L=3
- Duration: how many seconds the effect lasts. If the spell contains DoT it's the amount of ticks.
- Area: Area in the floor with a size of... S=Small, about the size of a chest. M=Medium, about the size of a Queen bed. L=Large, about the size of a bus.
- Range: C=Close, N=Nearby, F=Far
- Mana cost: S=Small, about 12% of the pool. M=Medium, about 20% of the pool. L=Large, about the 40% of the pool.



| Name           | Target       | Description                                                    | Cast | Dura | Ar | Rng | Mn |
|----------------|--------------|----------------------------------------------------------------|:----:|:----:|:--:|:---:|:--:|
| Acid           | C / O        | DoT of 0 damage. Reduces armor. If armor = 0, does 1 damage.   |  I   |   5  | -  |  C  | S  |
| Anchor         | C / O        | can't move away from `object` or `creature`                    |  S   |  10  | M  |  N  | M  |
| Attract        | O            | jolts `small` target towzards `self`                           |  I   |   -  | -  |  F  | L  |
| Barrier        | A            | creates see-thru but impassable wall                           |  S   |  30  | M  |  N  | L  |
| Berzerk        | C            | attacks closest `creature` or `object`. Does twice damage      |  S   |  20  | -  |  F  | M  |
| Burn           | C / O        | 1 damage, followed by DoT                                      |  S   |   4  | -  |  F  | S  |
| Charm          | C            | becomes friendly and fights by your side                       |  M   |  20  | -  |  N  | M  |
| Climb          | S            | can walk by `walls` (including ceilings)                       |  L   |  60  | -  |  -  | L  |
| Confuse        | C            | walks randomly and is unable to attacks                        |  M   |  20  | -  |  N  | L  |
| Darkness       | A            | creates a passable wall of darkness that blocks visibility     |  S   |  30  | M  |  F  | L  |
| Detect         | S            | detects every `creature` in range and marks them               |  L   |  20  | L  |  -  | M  |
| Entrophy       | C / O / D    | armor turns to 0                                               |  M   |   -  | -  |  F  | L  |
| Fix            | O / D        | heals 2 damage                                                 |  S   |   -  | -  |  C  | S  |
| Fog            | A            | creates fog that blocks visibility at floor level              |  M   |  30  | M  |  L  | M  |
| Follow         | O            | becomes `creature` and starts following the player             |  S   | 120  | -  |  L  | L  |
| Freeze         | C / O / D    | 1 damage. becomes frozen (can't move / animate )               |  I   |  10  | -  |  N  | M  |
| Gravity        | A            | gravity in area becomes 50. speed / 2                          |  M   |  30  | M  |  N  | M  |
| Haste          | C / S        | movement * 2                                                   |  L   |  60  | -  |  C  | L  |
| Illusion       | A            | creates illusion of the player                                 |  I   |   5  | S  |  F  | M  |
| Invisibility   | S            | can't be seen by others                                        |  S   |   5  | -  |  -  | L  |
| Imprison       | C            | can't move, can't animate, can't be damaged                    |  I   |   3  | -  |  C  | M  |
| Iron           | C / S        | can't be damaged. speed / 4                                    |  M   |      |    |     |    |
|                |              |                                                                |      |      |    |     |    |
|                |              |                                                                |      |      |    |     |    |
|                |              |                                                                |      |      |    |     |    |
|                |              |                                                                |      |      |    |     |    |


- Haste: `creature` or `self` moves faster
- Illusion: Draws in `area` an  `object` or `creature` or `self` previously selected.
- Invisibility: `self` becomes ethereal and can't be seen by enemies.
- Imprison: `creature` can't move an can't be damaged.
- Iron: `creature` or `self` raises armor to max, but halves movement.
- Levitate: `creature` or `object` levitates towards the ceiling and after the time runs out, slowly stops levitating.
- Light: creates a light emanating from a point in `wall` or `object`
- Magnet: `object 1` is magnetically attracted to `object 2` if close.
- Merge: `self` is fused to a selected `wall`. Can't move or act, but can see. 
- Orbit: `object 1` starts orbiting `creature` or `self`, damaging other `objects` and `creatures` close.
- Pacify: `creature` stops aggro.
- Pit: creates a pit in a `wall` (floor and ceiling included) filled with spikes that do 3 damage.
- Panacea: removes all altered status and ailments from `creature` or `self`, stopping any DoT
- Phase: `object` or `creature` dissapears and then reappears later in the same place.
- Poison: Creates a poisonous `area` at floor level that deals 1 DoT to any creature on it.
- Portal: creates a magical door connecting `wall 1` to `wall 2`
- Reduce: `object` or `creature` decreases it's size.
- Renew: `creature` or `self` heals 2 damage.
- Repel: `objects` and `creatures` close to `self` are pushed outwards explosively.
- Shield: `self` gains 3 armor points
- Shock: 3 damage. `creature` stunned for some time
- Sling: `object` is hurled away from `self`
- Slow: creature's speed is halved
- Splash: Creates a blob of water that flushes `objects` and `creatures` in `area` (and fills small ponds?)
- Switch: `object 1` and `object 2` change places
- Swoosh: `self` hurls forward several meters gaining momentum.
- Telekinesys: `object` levitates and can be transported
- Thorns: `area` is filled with thorns. any `creature` stepping on it receives 1 damage, and `self` heals 1 damage if nearby.
- Trick: `door` or `object` becomes invisible to enemies.             
- Vision: you see through the eyes of target `object` or `creature`
- Ward: 1 damage when `creature` enteres the `area` and loud noise emmited.
- Wall: Creates a `wall` in the selected `area`
- Web: Creates a sticky and jumpy web in `area` that can be set on fire.



### Altered status

- Frozen: 
- On fire:
- Stunned 
- Orbiting:
- Confused: 
- Haste
- Charmed
- Berzerk
- Immutable: ignores all damage and altered statuses


### Leveling up

Once the character levels up, it can choose to buff: Health amount, Mana recovery time, Casting Time, Lasting time, or range.
If you pick up a spell you already know, it gets fortified (up to 3 times). A fortified spell does more damage, or lasts longer, or gets a bigger area, affect bigger objects or new kind of targets, depending on spell. A fortified spell always costs less. (25% less, 50% less, 75% less)

 
## Map Levels

## Enemies

## Story

So far: shunned from kingdom. put in dungeon. you must escape the dungeon and return to the castle, get to the throne room and confront the king's councellor. he's secretly also a wizard like you and after that you can choose to be the new councellor or escape as a rogue.


