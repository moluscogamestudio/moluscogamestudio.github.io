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

### Entities

- 
- 
- 
- 

### Targets

Targets are game entities that can be affected by spells. 

- Wall: Walls, floors and ceiling of the dungeon.
- Door: Hinged doors, trapdoors, chests.
- Self: the player
- Creature: another creature that's not the player
- Object: some kind of furniture, like a sconce or torch, debris, coins, etc.
- Area: a circular area in range

Some entities share more than one target type. I.E.: Chests are both doors and objects. 

### Spells

There are several schools of spells. You start with a few spells and get random ones as you go on. The spells are of an agnostic nature and scale only with level. Their descriptions are purposefully vague and refer to <objectives>, <materials>, and <actions>

- Acid: <creature> or <object> loses armor over time 1/S for 4 seconds. If armor reaches zero, does 1 damage per tick. 
- Anchor: <object> or <creature> can't move away from <object> or <creature>
- Attract: jolts <object> towards the player
- Barrier: Creates a see-thru but impassable wall in <area> for a certain time.
- Berzerk: <creature> does 2x damage and attacks the closest <creature> or <object>
- Burn: 1 damage. <creature> or <object> is temporarily set on fire, gets 1 damage / s for 4 seconds
- Charm: <creature> becomes friendly and fights by your side
- Climb: <self> can walk by <walls> (including ceiling).
- Confuse: <creature> walks randomly and is unable to attack
- Darkness: creates a wall of darkness in <area> that blocks visibility, but is passable
- Detect: detects <creatures> far and marks them
- Disguise: !!!!! MODIFY OR REMOVE !!!!  <self>, <door>, or <wall> changes aspect.
- Enlarge: <object/creature> increases size
- Entrophy: Armor turns to 0 for <creature> or <object>
- Fix: <object> or <door> heals 2 damage.
- Fog: creates fog in <area> at floor level.
- Follow: <object> becomes <creature> and levitates following you.
- Freeze: 1 damage. <object>, or <creature> becomes frozen
- Gravity: alters gravity in <area> where <objects> and <creatures> are heavily attracted to the floor.
- Haste: <creature> or <self> moves faster
- Illusion: Draws in <area> an  <object> or <creature> or <self> previously selected.
- Imprison: <creature> can't move an can't be damaged.
- Iron: <creature> or <self> raises armor to max, but halves movement.
- Levitate: <creature> or <object> levitates towards the ceiling and after the time runs out, slowly stops levitating.
- Light: creates a light emanating from a point in <wall> or <object>
- Luck: !!!!! MODIFY OR REMOVE !!!!! Next attack is critical. (how?)
- Magnet: <object 1> is magnetically attracted to <object 2> if close.
- Orbit: <object 1> starts orbiting <creature> or <self>, damaging other <objects> and <creatures> close.
- Pacify: <creature> stops aggro.
- Panacea: removes all altered status from <creature> or <self>
- Phase: <object> or <creature> dissapears and then reappears later in the same place.
- Poison: Creates a poisonous <area> at floor level that deals 1 damage/second to any creature on it 
- Portal: creates a magical door to a location you can see
- Reduce: <object/creature> decreases size
- Renew: <creature> or <self> heals 1 damage.
- Repel: <objects> and <creatures> close to <self> are pushed outwards explosively.
- Seal: !!!! MODIFY OR REMOVE !!!! locks door, chest or object. only you can open it.
- Shield: <self> gains 3 armor points
- Shock: 3 damage. <creature> stunned for some time
- Skeleton: !!!! MODIFY OR REMOVE !!!! the corpse of a nearby <creature> becomes a skeleton that aids you in combat
- Sling: <object> is hurled away from <self>
- Sound: !!!! MODIFY OR REMOVE !!!! emits sounds <area>, or mutes own sounds
- Splash: Creates a blob of water that flushes <objects> and <creatures> in <area> (and fills small ponds?)
- Switch: <object 1> and <object 2> change places
- Swoosh: <self> hurls forward several meters gaining momentum.
- Telekinesys: <object> levitates and can be transported
- Thorns: <area> is filled with thorns. any <creature> stepping on it receives 1 damage, and <self> heals 1 damage if nearby.
- Vision: you see through the eyes of target <object> or <creature>
- Ward: 1 damage when <creature> enteres the <area> and loud noise emmited.
- Web: Creates a sticky and jumpy web in <area> that can be set on fire.



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

Once the character levels up, it can choose one known spell to fortify. Fortified spells get better, up to 3 times. A fortified spell does more damage, or lasts longer, or gets a bigger area, depending on spell.
 
## Map Levels

## Enemies

## Story

So far: shunned from kingdom. put in dungeon. you must escape the dungeon and return to the castle, get to the throne room and confront the king's councellor. he's secretly also a wizard like you and after that you can choose to be the new councellor or escape as a rogue.


