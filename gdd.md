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


### Controls

So far, this is the default KB+M layout.

- **WASD** = Movement
- **Space** = Jump
- **Shift** = Sprint mod
- **E** = Opoerate
- **F** = Target Self
- **Q** = Spellbook
- **1-4** = Use item
- **LMB** = Left Hand Spell
- **RMB** = Right Hand Spell
- **ESC** = Menu

### Spells

There are 50 different spells. You start with a few spells and get random ones as you go. You can power up the spells via potions and leveling up.
Every spell has a target, a cast time, and a mana cost. Optionally it can have a duration, an area and a range.

- **Target:** *Required* C=Creature, O=Object, D=Door, W=Wall, A=Area, S=Self
- **Cast Time:** *Required* how many seconds it takes to cast. I=0, S=1, M=2, L=3
- **Mana cost:** *Required* S=Small, about 12% of the pool. M=Medium, about 20% of the pool. L=Large, about the 40% of the pool.
- **Duration:** *optional* how many seconds the effect lasts. If the spell contains DoT it's the amount of ticks.
- **Area:** *optional* Area in the floor with a size of... S=Small, about the size of a chest. M=Medium, about the size of a Queen bed. L=Large, about the size of a bus.
- **Range:** *optional* C=Close, N=Nearby, F=Far




| Name         | Target    | Description                                                          | Cast | Dura | Ar | Rng | Mn |
| ------------ | --------- | -------------------------------------------------------------------- | ---- | ---- | -- | --- | -- |
| Acid         | C / O / D | DoT of 0 damage. Reduces armor. If armor = 0, does 1 damage.         | I    | 5    | -  | C   | S  |
| Anchor       | C / O / D | needs to cast twice. selecteds can't be moved away                   | S    | 10   | M  | N   | M  |
| Attract      | O         | jolts target object towards you at high speeds doing ?? damage       | I    | -    | -  | F   | L  |
| Barrier      | A         | creates see-thru but impassable wall                                 | S    | 30   | M  | N   | L  |
| Berzerk      | C         | attacks closest `creature` or `object`. Does twice damage            | M    | 20   | -  | F   | M  |
| Burn         | C / O / D | 1 damage, followed by DoT                                            | S    | 4    | -  | F   | S  |
| Charm        | C         | becomes friendly and fights by your side                             | M    | 20   | -  | N   | M  |
| Climb        | S         | can walk by `walls` (including ceilings)                             | L    | 60   | -  | -   | L  |
| Confuse      | C         | walks randomly and is unable to attacks                              | M    | 20   | -  | N   | L  |
| Darkness     | A         | creates a passable wall of darkness that blocks visibility           | S    | 30   | M  | F   | L  |
| Detect       | S         | detects every `creature` in range and marks them                     | L    | 20   | L  | -   | M  |
| Entrophy     | C / O / D | armor turns to 0                                                     | M    | -    | -  | F   | L  |
| Fix          | O / D     | heals 2 damage                                                       | S    | -    | -  | C   | S  |
| Fog          | A         | creates fog that blocks visibility at floor level                    | M    | 30   | M  | L   | M  |
| Follow       | O         | becomes `creature` and levitates, following the player               | S    | 120  | -  | L   | L  |
| Freeze       | C / O / D | 1 damage. becomes frozen (can't move / animate )                     | I    | 10   | -  | N   | M  |
| Gravity      | A         | gravity in area becomes 50. speed / 2                                | M    | 30   | M  | N   | M  |
| Haste        | C / S     | movement * 2                                                         | L    | 60   | -  | C   | L  |
| Host         | C         | you control an enemy, can move and attack                            | L    | 7    | -  | M   | M  |
| Illusion     | A         | creates illusion of the player                                       | I    | 5    | S  | F   | M  |
| Imprison     | C         | can't move, can't animate, can't be damaged                          | I    | 3    | -  | C   | M  |
| Invisibility | S         | can't be seen by others                                              | S    | 5    | -  | -   | L  |
| Iron         | C / S     | can't be damaged. (max armor?) speed / 4                             | M    | 20   | -  | -   | L  |
| Levitate     | C / O     | levitates upwards and after time runs out, slowly descents           | M    | 7    | -  | F   | M  |
| Light        | W / O     | creates light emanating from target                                  | S    | 120  | -  | N   | S  |
| Merge        | W         | fuses with selected wall. Can't move or act, but can see.            | S    | 10   | -  | C   | M  |
| Orbit        | S         | 1 damage for every creature and object in M area around self         | S    | -    | M  | -   | L  |
| Pacify       | C         | stops aggro                                                          | L    | 20   | -  | N   | S  |
| Phase        | C / O     | Dissapears and reappears later                                       | M    | 5    | -  | F   | M  |
| Pit          | W         | (ceiling and floor included) creates pit with spikes for 7 damage    | L    | 30   | M  | N   | L  |
| Poison       | A         | creates poison fog at floor level. DoT of 1 to everyone on it        | S    | 10   | M  | N   | M  |
| Portal       | W         | needs to cast twice. Creates connected portals that spew you off     | I    | 7    | -  | F   | M  |
| Renew        | C / S     | Heals 2 damage                                                       | S    | -    | -  | C   | S  |
| Repel        | S         | every `object` or `creature` is pushed outwards explosively          | I    | -    | M  | C   | M  |
| Sanctuary    | A         | creatures can't enter the area                                       | S    | 30   | M  | N   | L  |
| Shield       | S         | Gains 3 armor points                                                 | L    | 120  | -  | -   | M  |
| Shock        | C         | 3 damage, stunned                                                    | M    | 3    | -  | N   | L  |
| Shrink       | C / S     | decreases it’s size                                                  | S    | 20   | -  | N   | S  |
| Sling        | O         | hurled away from player                                              | L    | -    | -  | C   | S  |
| Slow         | C         | Movement / 2                                                         | M    | 60   | -  | N   | M  |
| Splash       | A         | creates blob of water that pushes `objects` and `creatures` away     | M    | -    | M  | N   | M  |
| Switch       | C         | needs to cast twice. Switches 2 creatures positions                  | I    | 7    | -  | F   | M  |
| Swoosh       | S         | hurls forward several meters gaining momentum.                       | I    | -    | -  | -   | L  |
| Telekinesys  | O         | levitates and can be transported                                     | S    | -    | -  | C   | L  |
| Thorns       | A         | fills with thorns. 1 damage to everyone on it. vampire heal          | M    | 7    | M  | N   | M  |
| Trick        | O / D     | becomes invisible to others                                          | S    | 20   | -  | F   | S  |
| Vision       | C / O     | you see through the eyes of target                                   | L    | 5    | -  | F   | L  |
| Wall         | A         | creates a `wall`                                                     | M    | 30   | M  | N   | L  |
| Ward         | A         | 1 damage to first to enter area. Loud noise emitted                  | S    | 120  | S  | C   | S  |
| Web          | A         | Creates a sticky and jumpy web that can be set on fire               | S    | 30   | M  | F   | L  |






### Leveling up

Once the character levels up, it can choose to buff: Health amount, Mana recovery time, Casting Time, Lasting time, or range.
If you pick up a spell you already know, it gets fortified (up to 3 times). A fortified spell does more damage, or lasts longer, or gets a bigger area, affect bigger objects or new kind of targets, depending on spell. A fortified spell always costs less. (25% less, 50% less, 75% less)

 
## Map Levels

## Enemies

## Development

### Entities

- wall: affected by climb, merge, light, pit, portal, wall. Properties: *indestructible* can be modified temporarily with pit.
- door: affected by acid, anchor, burn, entrophy, fix, freeze, trick. Properties: *can be destroyed*, *can be operated*. HP, ARMOR, LOCKED




## Story

So far: shunned from kingdom. put in dungeon. you must escape the dungeon and return to the castle, get to the throne room and confront the king's councellor. he's secretly also a wizard like you and after that you can choose to be the new councellor or escape as a rogue.


