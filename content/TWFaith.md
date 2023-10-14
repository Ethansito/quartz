# Total War: Faith

## Introduction

Total War: Faith is a custom plugin that allows players to create religions. The player who creates the religion is the god, and he can recruit followers, who give him faith points by praying. Faith points can be spent to purchase blessings for followers, curses for heathens, or extra powers for the god.

## Usage
<iframe width="560" height="315" src="https://www.youtube.com/embed/CMLi7lwL1Ec?si=4fiY3R6BBilrH5OK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

# Powers
## Blessings
Blessings are powers the god unlocks that directly benefits the followers.
### Divine Intervention (Trigger) (AoE)
Launches all followers within 30 blocks of the god into the air and gives them the glide effect until they hit the ground.
### Hell's Fury (Toggle) (AoE)
All followers within 30 blocks gain immunity to fire damage, and they spread fire wherever they move for the duration the power is active. Followers that leave the 30 block radius will still spread fire until the power ends, but followers outside the radius must enter before gaining the blessing.
### Mana (Trigger) (AoE)
Gives players within 30 blocks 16 bread.
### Powerful Flock (Toggle) (AoE)
The god and every follower within 30 blocks of the god gains a half heart of health for every other follower within 30 blocks of the god, including the god. With just the god and one follower nearby, this means both the god and the follower gain a half heart of health. 
### Summon God (Toggle)
While the god has this power active, followers can use the command `/faith summon` to request the god to teleport to them. The god can accept with `/faith accept`. Teleportation has a cooldown of 20 minutes per follower, and the god cannot return to their original location by teleportation unless another follower is there to summon them.
### Terrain Bonus (Toggle) (Server-Wide)
The terrain bonus power gives all followers on the server a potion effect when they are in the god's chosen terrain. The power selection menu allows the god to match any of the available potion effects with any of the terrain groups, provided they have unlocked both in the upgrade menu. 

Example: Give strength to all followers in Cold biomes.
## God Powers
God powers only affect the god.
### Lion's Heart (Toggle)
The god gains strength 0-4 depending on how many pieces of armor they are wearing. Wearing no armor gives strength 4 while wearing a full set of armor results in no strength bonus. Tools, weapons, and shields do not affect this power.
### Savior (Toggle) (Trigger) (AoE)
While this power is active, if a follower within 30 blocks has his health reduced to less than 3 hearts, and the god has at least 5 hearts of health, the follower and the god will swap places.
### Taunt (Trigger)
All heathens in a 30 block radius of the god suffer the hunger effect, and the god gains the glowing status effect. The heathens suffer hunger until they hit the god or the power runs out.
### Insidious (Toggle)
The god gains the invisibility potion effect when shifting. Only drains power when the god is invisible.
### Explosive Landing (Toggle) (Trigger)
Converts fall damage into an explosion. The larger the fall damage, the larger the explosion, up to a max due to the server crashing. Max value can be found in config under "explosive-max-mag".
### Flood (Trigger) (AoE)
In a 30-block radius around the god, the highest block in the world gets a water block above it, flooding the area for 30 seconds before disappearing. Due to this power only spawning water above the highest blocks around the player, it is not effective underground or inside buildings.
## Curses
### Crumbling (Toggle) (AoE)
Heathens in a 30-block radius take 10x durability damage on their armor, weapons, and tools.
### Discombobulation (Trigger) (AoE)
Heathens in a 30-block radius have their inventories scrambled.
### Entangle (Trigger) (AoE)
Heathens in a 30-block radius are encased in trees. This power only works in biomes where trees naturally spawn, and the type of tree depends on the biome.
### Heavy Boots (Toggle) (AoE)
Heathens in a 30-block radius gain slowness while wearing boots.
### Intoxicate (Toggle) (AoE)
Heathens in a 30-block radius gain nausea.

## Configuration
```yaml
# TWFaith Config File
# Version : Snapshot 1

# Pray cool down
pray-cool-down: 10

# Base stamina regeneration per second
base-stamina-regen: 1

# Powers
# cost: The number of faith points to purchase the upgrade
# stamina: The stamina cost (either per second or per trigger) to use the power
# cooldown: How many seconds the god must wait before triggering the power again. Only for triggered powers.

# Divine Intervention
divine-cost: 5
divine-stamina: 20
divine-cooldown: 10

# Hell's Fury
hells-cost: 5
hells-stamina: 5

# Mana
mana-cost: 5
mana-stamina: 10
mana-cooldown: 10

# Powerful Flock
flock-cost: 5
flock-stamina: 5

# Summon God
summon-cost: 5
summon-stamina: 11
summon-cooldown: 1500

# Terrain Bonus
terrain-cost: 5
terrain-stamina: 5

# Lion's Heart
lions-heart-cost: 5
lions-heart-stamina: 5

# Savior
savior-cost: 5
savior-stamina: 20
savior-cooldown: 10

# Taunt
taunt-cost: 5
taunt-stamina: 20
taunt-cooldown: 10

# Insidious
insidious-cost: 5
insidious-stamina: 5

# Explosive Landing
explosive-cost: 5
explosive-stamina: 20
explosive-cooldown: 10
explosive-max-mag: 40

# Flood
flood-cost: 5
flood-stamina: 30
flood-cooldown: 10

# Crumbling
crumbling-cost: 5
crumbling-stamina: 5

# Discombobulation
discombobulate-cost: 5
discombobulate-stamina: 100
discombobulate-cooldown: 300

# Entangle
entangle-cost: 5
entangle-stamina: 50
entangle-cooldown: 60

# Heavy Boots
heavy-cost: 5
heavy-stamina: 5

# Intoxicate
intoxicate-cost: 5
intoxicate-stamina: 5
```
