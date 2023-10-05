---
title: Cannons
---
## Introduction

Cannons allows players to build multi-block cannons that fire different kinds of projectiles. Cannons are compatible with [[Movecraft]].

## Usage

This video covers the basics:

<iframe width="560" height="315" src="https://www.youtube.com/embed/g-boSAAQFB0?si=7Euh9ed1xpQk8zcC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

A more detailed guide: https://dev.bukkit.org/projects/cannons/pages/tutorial

## Configuration

### General
```yaml
general:
  #sets debug mode on or off. Turn off if you do not want to see as much info on in the server console or log files
  debugMode: false
  #relays the new BlockExplodeEvent to the old EntityExplodeEvent for protection plugins, which don't support this feature
  relayExplosionEvent: false
  #size of the box of the claim cannon command
  claimEdgeLength: 60

cannonLimits:
  #limits regarding how many cannons a player can build. set to false if you dont need it
  useLimits: false
  buildLimitA: 1
  buildLimitB: 100

keepProjectileAlive:
  #projectile will only be updated by minecraft if a player is close to it. Enable this to keep them alive forever
  enabled: true
  #teleports the projectile to the expected location when the difference is too big
  teleportProjectile: 5.0

tools:
  #the item a player needs to be holding to adjust the aim of a cannon. Default is air.
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  ajust: 'minecraft:air'
  #the item used to autoaim a cannon. Default is clock
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  autoaim: 'minecraft:clock'
  #range of the autoaim tool. Autoaiming will be cancelled if the player farther away than the given distance.
  autoaimRange: 4.0
  #the item used to fire a cannon. Default is flint and steel. Not every cannon needs a FiringItem.
  #a data value of -1 means that every durability is accepted for flint and steel
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  firing: 'minecraft:flint_and_steel'
  #required for cleaning a cannon after firing and pushing a projectile against the gunpowder
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  ramrod: 'minecraft:stick'
  #item used to rotate a cannon 90 degrees. Not implemented yet
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  rotatingItem: 'minecraft:rail'
  #item to measure the cannon temperature. Default is a gold nugget
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  thermometer: 'minecraft:gold_nugget'

#fake blocks/sound that are send to the player, to make effects visible at large distance
imitatedEffects:
  #is the player closer than this distance, there will be no fake block
  minimumBlockDistance: 80
  #if the player is above this distance, there will be no fake block
  maximumBlockDistance: 200
  #if the player is above this distance, there will be no sound
  maximumSoundDistance: 200
  #how loud the sound effects will be (possible values: 0.0-1.0)
  maximumSoundVolume: 0.8

  #mark the impact location with blocks from distance
  explosion:
    #are imitated blocks enabled
    enabled: false
    #size of the impact imitated explosion
    sphereSize: 3
    #material of the imitated explosion (default is a active minecraft:glowstone)
    material: 'minecraft:glowstone'
    #how long the effect will be displayed [s]
    time: 2

  #mark the impact location with particles from distance
  explosionParticles:
    #are imitated particles enabled
    enabled: true
    #particle type. Check https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for reference
    type: EXPLOSION_LARGE
    #number of particles for the explosion
    count: 5
    #diameter of the explosion from distance
    diameter: 3

  #firing effect if the player is far away and display the aiming angle of the cannon
  aiming:
    #set to true to show a line of blocks while aiming
    enabled: true
    #how long the aiming vector will be. Longer means it is easier to see where you are aiming
    length: 5
    #this block will used to display the angle
    block: 'minecraft:glass'
    #how long the effect will be displayed [s]
    time: 0.5

  firing:
    #will show fake blocks for players which are far away
    enabled: true
    #firing will show fire blocks if the player is far away
    fireBlock: 'minecraft:glowstone'
    #firing will show smoke blocks if the player is far away
    smokeBlock: 'minecraft:cobweb'
    #how long the effect will be displayed [s]
    time: 2

  predictor:
    #shows the impact of the projectile for a loaded cannon
    enabled: true
    #how many iterations until the projectile hits the surface
    maxIterations: 500
    #the predictor will work for this distance (muzzle to impact)
    maxDistance: 200.0
    #fake block which shows the impact location
    material: 'minecraft:glowstone'
    #how long the effect will be displayed [s]
    time: 0.5

#enter here the blocks which require the superbreaker ability to destroy.
#e.g. if you enter here the enchantment table it requires a projectile with superbreaker to be destroyed.
#else it can be destroyed by normal explosions
#https://www.digminecraft.com/lists/item_id_list_pc.php
superbreakerBlocks:
  #water
  - 'minecraft:water'
  #lava
  - 'minecraft:lava'
  #obsidian
  - 'minecraft:obsidian'
  #enchantmenttable
  - 'minecraft:enchanting_table'
  #enderchest
  - 'minecraft:ender_chest'
  #anvil
  - 'minecraft:anvil'
  #blocks which can't be destroyed by penetration of the projectile.
  #normal minecraft explosions are not affected by this option.

unbreakableBlocks:
  # bedrock
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  - 'minecraft:bedrock'

#some items will consumed when used as projectile (e.g. a egg will be thrown) and the event has to be canceled, else the item can't be used as projectile
#you can also enter here a lever to use it as right click trigger not as redstone trigger.
#https://www.digminecraft.com/lists/item_id_list_pc.php
cancelEventForLoadingItem:
  #EGG
  - 'minecraft:egg'
  #SNOW_BALL
  - 'minecraft:snowball'
  #SPAWN_EGG
  - 'minecraft:bat_spawn_egg'
  - 'minecraft:blaze_spawn_egg'
  - 'minecraft:cave_spider_spawn_egg'
  - 'minecraft:chicken_spawn_egg'
  - 'minecraft:cod_spawn_egg'
  - 'minecraft:cow_spawn_egg'
  - 'minecraft:creeper_spawn_egg'
  - 'minecraft:dolphin_spawn_egg'
  - 'minecraft:donkey_spawn_egg'
  - 'minecraft:drowned_spawn_egg'
  - 'minecraft:elder_guardian_spawn_egg'
  - 'minecraft:enderman_spawn_egg'
  - 'minecraft:endermite_spawn_egg'
  - 'minecraft:evoker_spawn_egg'
  - 'minecraft:ghast_spawn_egg'
  - 'minecraft:guardian_spawn_egg'
  - 'minecraft:horse_spawn_egg'
  - 'minecraft:husk_spawn_egg'
  - 'minecraft:llama_spawn_egg'
  - 'minecraft:magma_cube_spawn_egg'
  - 'minecraft:mooshroom_spawn_egg'
  - 'minecraft:mule_spawn_egg'
  - 'minecraft:ocelot_spawn_egg'
  - 'minecraft:parrot_spawn_egg'
  - 'minecraft:phantom_spawn_egg'
  - 'minecraft:pig_spawn_egg'
  - 'minecraft:polar_bear_spawn_egg'
  - 'minecraft:pufferfish_spawn_egg'
  - 'minecraft:rabbit_spawn_egg'
  - 'minecraft:salmon_mob_spawn_egg'
  - 'minecraft:sheep_spawn_egg'
  - 'minecraft:shulker_spawn_egg'
  - 'minecraft:silverfish_spawn_egg'
  - 'minecraft:skeleton_horse_spawn_egg'
  - 'minecraft:skeleton_spawn_egg'
  - 'minecraft:slime_spawn_egg'
  - 'minecraft:spider_spawn_egg'
  - 'minecraft:squid_spawn_egg'
  - 'minecraft:stray_spawn_egg'
  - 'minecraft:tropical_fish_spawn_egg'
  - 'minecraft:vex_spawn_egg'
  - 'minecraft:villager_spawn_egg'
  - 'minecraft:vindicator_spawn_egg'
  - 'minecraft:witch_spawn_egg'
  - 'minecraft:wither_skeleton_spawn_egg'
  - 'minecraft:wolf_spawn_egg'
  - 'minecraft:zombie_horse_spawn_egg'
  - 'minecraft:zombie_pigman_spawn_egg'
  - 'minecraft:zombie_spawn_egg'
  - 'minecraft:zombie_villager_spawn_egg'
  #ENDER_PEARL
  - 'minecraft:ender_pearl'
  #FIREWORK
  - 'minecraft:fireworks'
  #REDSTONE
  - 'minecraft:redstone'
```


### Designs

#### Classic
```yaml
general:
  #name of the cannon. This will show of on the cannon sign - therefore keep it short
  designName: "Classic"
  #This will be used for messages and will replace CANNON in all messages. (e.g. You created a classic cannon)
  messageName: "classic cannon"
  #a short description of the cannon
  description: "A small cheap cannon - nothing fancy. Will break very easily since it is made out of wool."
  #last user of cannon becomes to it's owner (cannon is public)
  lastUserBecomesOwner: false

signs:
  #this cannon needs a sign to operate. Important for moving cannons.
  isSignRequired: false

ammunition:
  #what the gunpowder is called
  gunpowderName: gunpowder
  #what item is used as gunpowder (minimum is id:data. Named items id:data;displayName;lore1;lore2;....)
  #'minecraft:gunpowder;$rGunpowder'
  gunpowderType: 'minecraft:gunpowder'
  #does this cannon need gunpowder. If false you can directly load the projectile
  needsGunpowder: true
  #gunpowder will be removed from inventories. If false you have to click the cannon until it is reloaded
  gunpowderConsumption: true
  #if false the cannons will not remove the projectile form the inventory but you still need a projectile
  projectileConsumption: true
  #if true, no item is removed from the players inventory
  ammoInfiniteForPlayer: false
  #if true, the cannons does not consume ammunition for autoreloading with redstone
  ammoInfiniteForRedstone: false
  #whether the cannon can reload from a chest
  autoreloadRedstone: true
  #after firing the projectile are usually gone, but you can set this to false to keep the cannon loaded. Just load the cannon once and it stays loaded until you break it.
  removeChargeAfterFiring: true
  #when set the gunpowder will taken from your inventory when a projectile is loaded, no loading of gunpowder required
  autoloadChargeWhenLoadingProjectile: false
  #after creating a cannon it will be preloaded with the maximum amount of gunpowder and the default projectile (first in the list)
  preloaded: false
  

barrelProperties:
  #maximum gunpowder that can be loaded in the cannon
  maxLoadableGunpowder: 3
  #how much faster the loaded projectile will fired for each gunpowder loaded
  multiplierVelocity: 1.0
  #the angle of which a fired projectile spreads when fired. Basically the lower this is, the more accurate the cannon is
  spreadOfCannon: 1.0

timings:
  #how long anyone near the cannon without a helmet will be confused when the cannon is fired
  blastConfusion: 5.0
  #the delay in seconds between when someone fires a cannon and when the actual projectiles fired from the cannon
  fuseBurnTime: 1.0
  #fuseBurnTime is multiplied with this with this factor. 0 means the burn time is always the same while 1 it can change vary from 1x to 2x the fuseBurnTime
  fuseBurnTimeRandomness: 0.5
  #the time in seconds before the cannon can be fired again. Outdated due to heat management
  barrelCooldownTime: 0.0
  #time to load gunpowder and projectile for autoreload
  loadTime: 3.0

angles:
  #used to adjust in what direction a projectile is fired from a cannon. adjust this if your cannon is firing sideways or at itself
  defaultHorizontalFacing: west
  #the default angle vertical angle which the cannon aims at when built. this is good for mortars and similar upwards firing weapons
  defaultVerticalAngle: 0.0
  #min and max horizontal angles determine how far to the left and right the cannon can be aim
  maxHorizontalAngle: 45.0
  minHorizontalAngle: -45.0
  #min and max vertical angles determine how far upwards or downwards the cannon can be aimed
  maxVerticalAngle: 45.0
  minVerticalAngle: -45.0
  #if the cannon is on a ship the angles might be smaller
  maxHorizontalAngleOnShip: 10.0
  minHorizontalAngleOnShip: -10.0
  maxVerticalAngleOnShip: 45.0
  minVerticalAngleOnShip: -45.0
  #each change of the angles will change angle by this amount
  angleStepSize: 0.5
  #rougher steps to change cannon direction more quickly
  largeStepSize: 2.0
  #how fast the cannons can be turned in seconds (fastest is 0.05s)
  angleUpdateSpeed: 0.1
  #a message with the new angles is displayed to the user while aiming
  angleUpdateMessage: false

#the impact predictor will show the impact location of a loaded cannon
impactPredictor:
  #enable the impact predictor
  enabled: true
  #the impact location will be shown after the last angle change of the cannon [s]
  delay: 0.5
  #update rate. How often the impact predictor will be calculated per second
  update: 0.2

#sentry mode allows the gun to search and destroy targets automatically.
sentry:
  #this gun is a sentry gun. It will operate on its own.
  isSentry: false
  #does this fire like a mortar (indirect - from above) or like a cannon
  indirectFire: false
  #at which distance the sentry will stop firing because it is too close
  minRange: 5
  #at which distance the sentry will detected enemies
  maxRange: 50
  #how acurate can the final angle be calculated. The smaller the better
  spread: 0.5
  #how long the cannon updating firing solutions. Higher delays result in worse tracking of a moving target. [s]
  update: 1.0
  #the cannon will switch to the next target after some time [s]
  swapTime: 10.0

#enables the linking of several cannons together. Default is limited to the same design
linkCannons:
  #enables the feature to link cannons
  enabled: false
  #cannons can be link if they are closer than the given range to the operated cannons in a box shape
  distance: 40

heatManagement:
  #if heat management is used or not
  enabled: true
  #if true the cannon will refuse to fire if the cannon temperature after firing would be higher than critical
  automaticTemperatureControl: true
  #touching a hot cannon will hurt (in full hearts)
  burnDamage: 0.0
  #touching a hot cannon will slow you (in seconds)
  burnSlowing: 10
  #how much firing one gunpowder will increase the temperature of the barrel
  heatIncreasePerGunpowder: 10.0
  #heat dissipation time coefficient. Smaller time coefficient means it cools down faster
  coolingTimeCoefficient: 10.0
  #how much cooling with the cooling item (config.yml e.g. water bucket) will cool the cannon
  coolingAmount: 50.0
  #searchs for cooling items in chests and cools the cannon if the cannon temperature above the warning temperature
  automaticCooling: true
  #the barrel is hot and you will notice this effect
  warningTemperature: 60.0
  #the barrel damage is critical and the cannon can explode
  criticalTemperature: 150.0
  #if the cannon exceeds this temperature it will explode
  maximumTemperature: 300.0
  #items to cool down a cannon (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItems:
    - 'minecraft:water_bucket'
    - 'minecraft:ice'
    - 'minecraft:snow_block'
  #items which are returned after cooling the cannon. The order is the same like above.
  #setting a item to minecraft:AIR means it will only remove one item instead of replacing the item minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItemsUsed:
    - 'minecraft:bucket'
    - 'minecraft:air'
    - 'minecraft:air'

#cannon can be loaded with more gunpowder, but might explode after firing
overloading:
  #cannon can explode if overloaded with gunpowder
  #chance = chanceInc * ((all loaded gunpowder - maximum loadable gunpowder without overloading) * ChanceOfExplosionPerGunpowder)^Exponent
  enabled: true
  #in real mode cannon can also explode when not overloaded
  #chance = chanceInc * (all loaded gunpowder * ChanceOfExplosionPerGunpowder)^Exponent
  realMode: false
  exponent: 2
  chanceInc: 1
  maxOverloadableGunpowder: 1
  chanceOfExplosionPerGunpowder: 0.1
  #the explosion chance will be multiplied by cannon's temperature / maximumTemperature
  dependsOfTemperature: true
  #loaded gunpowder = 3 normal + 1 overloaded
  #exploding change = 1 * ((3+1)*0.1)^2 = 16%

  #For example, if cannon have:
  #Mode = 1
  #Exponent = 2
  #ChanceInc = 1
  #MaxLoadableGunpowder = 3
  #MaxOverloadableGunpowder = 3
  #ChanceOfExplosionPerGunpowder = 0.1
  #Loaded gunpowder = 5 (3 normal + 2 overloaded)
  #Chance of explosion = 1*((5-3)*0.1)^2 = 0.04 = 4%
  #=================================
  #Another example:
  #Mode = 1
  #Exponent = 2
  #ChanceInc = 1
  #MaxLoadableGunpowder = 3
  #MaxOverloadableGunpowder = 3
  #ChanceOfExplosionPerGunpowder = 0.1
  #Loaded gunpowder = 6 (3 normal + 3 overloaded)
  #Chance of explosion = 1*((6-3)*0.1)^2 = 0.1 = 10%
  #=================================
  #Another example:
  #Mode = 1
  #Exponent = 1
  #ChanceInc = 0.1
  #MaxLoadableGunpowder = 3
  #MaxOverloadableGunpowder = 3
  #ChanceOfExplosionPerGunpowder = 0.1
  #Loaded gunpowder = 6 (3 normal + 3 overloaded)
  #Chance of explosion = 0.1*((6-3)*0.1)^1 = 0.03 = 3%
  #=================================
  #Another example:
  #Mode = 1
  #Exponent = 3
  #ChanceInc = 4
  #MaxLoadableGunpowder = 3
  #MaxOverloadableGunpowder = 3
  #ChanceOfExplosionPerGunpowder = 0.1
  #Loaded gunpowder = 6 (3 normal + 3 overloaded)
  #Chance of explosion = 0.4*((6-3)*0.1)^3 = 0.108 = 10.8%
  #=================================
  #Another example:
  #Mode = 2
  #Exponent = 3
  #ChanceInc = 1
  #MaxLoadableGunpowder = 3
  #MaxOverloadableGunpowder = 3
  #ChanceOfExplosionPerGunpowder = 0.1
  #Loaded gunpowder = 6 (3 normal + 3 overloaded)
  #Chance of explosion = 1*(6*0.1)^3 = 0.216 = 21.6%

economy:
  #the money the is withdrawn from your account when you build a cannon. If you have not enough - no cannon will be created
  buildingCosts: 0
  #how much money you receive if your cannon was deconstructed
  dismantlingRefund: 90.0
  #how much money you receive if your cannon was destroyed
  destructionRefund: 10.0

realisticBehaviour:
  #whether a player has to right click while holding the firing item (e.g flint and steel) for the cannon to be fired
  isFiringItemRequired: false
  #firing a cannon produced soot (dirt) which needs to be cleaned. Cleaning is necessary if soot>=1
  sootPerGunpowder: 0.1
  #created cannon will have this amount of soot (0 to disable this feature)
  startingSoot: 10
  #after loading a projectile it is necessary to push the projectile against the gunpowder
  projectilePushing: 2
  #the cannon move one block back after firing (not implemented yet)
  hasRecoil: false
  #whether you have to load the cannon from the same place the projectile is fired (aka muzzle loading) (not implemented yet)
  isFrontloader: false
  #whether the whole cannon can be rotated 90 degrees (not implemented yet)
  isRotatable: false
  #whether the cannon can be used with fire missions to bombarded a certain location (not implemented yet)
  supportsFireMission: false
  #the mass in kilogram of a cannon is important for moving objects e.g. ships
  massOfCannon: 100
  #cannon explodes if a loaded cannon is destroyed. Explosion power 4 (like tnt) and 0 to disable it. Will be scaled with the loaded gunpowder.
  explodingLoadedCannon: 2.0
  #fire after loading projectile with the time delay given by the fuse time. Sneaking will stop immediate firing.
  fireAfterLoading: false
  #dismantling takes some time (fits to the sound) [s]
  dismantlingDelay: 1.75

permissions:
  #all the permissions required for a player to use certain parts of the cannon
  #more information can be found here: http://dev.bukkit.org/bukkit-plugins/cannons/pages/installation-and-configuration/cannons-2-0-and-up/permissions/
  build: cannons.player.build
  #for deconstructing a cannon you need to be the owner and have this permission
  dismantle: cannons.player.dismantle
  #give the cannon a new name
  rename: cannons.player.rename
  #permission for loading gunpowder and projectiles
  load: cannons.player.load
  #permission for firing a cannon
  fire: cannons.player.fire
  #permission for aiming with a cannon
  adjust: cannons.player.adjust
  #permission to used the ramrod (stick) to clean and push the projectile
  ramrod: cannons.player.ramrod
  #the cannon will follow the looking direction of the player if the aiming item is used (default: clock)
  autoaim: cannons.player.autoaim
  #player can add himself as an observer of a cannon with the cmd: '/cannons observer'
  observer: cannons.player.observer
  #not implemented yet
  targetTracking: cannons.player.tracking
  #if a player has no permission for redstone, it is not possible to wire a cannon with redstone or uses torches.
  #firing a prewired cannon however is possible.
  redstone: cannons.player.redstone
  #this player can use a thermometer to measure the temperature of a cannon (default item for thermometer is a gold nugget)
  thermometer: cannons.player.thermometer
  #cannon will autoreload if the player is sneaking and fires the cannon.
  #The ammunition comes from the chest next to the cannon
  autoreload: cannons.player.autoreload
  #how much better the player can handle the cannon.
  #possible values are cannons.player.spreadmultiplier.1 - cannons.player.spreadmultiplier.10 for a multiplier of 0.1 - 1.0
  spreadMultiplier: cannons.player.spreadmultiplier

accessRestriction:
  #whether only the owner of the cannon can use it or not (not implemented yet)
  ownerOnly: false

allowedProjectiles:
  #these are the list of projectiles a cannon can fire. The projectiles are taken from the config files in the projectiles folder.
  #they do not have to be named after an in-game item and can be named anything.
  #make sure the name matches the name of the config file of the projectile you want this cannon to be able to fire. the .yml part does not need to be included
  - cobblestone
  - diamond
  - canistershot
  - enderpearl
  - tnt
  - firework1

sounds:
  #sound effects for this cannon.
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #creating a new cannon
  create: 'BLOCK_ANVIL_LAND:1:0.5'
  #paying the cannon fee of a new cannon
  selected: 'BLOCK_ANVIL_LAND:1:2'
  #destroying a cannon
  destroy: 'ENTITY_ZOMBIE_ATTACK_IRON_DOOR:1:0.5'
  #dismantling a cannon
  dismantle: 'BLOCK_ANVIL_USE:1:0.5'
  #changing the angle of a cannon
  adjust: 'ENTITY_IRON_GOLEM_STEP:1:0.5'
  #fuse igniting sound when firing
  ignite: 'ENTITY_TNT_PRIMED:5:1'
  #firing sound
  firing: 'ENTITY_GENERIC_EXPLODE:20:1.5'
  #loading gunpowder
  gunpowderLoading: 'BLOCK_SAND_HIT:1:1.5'
  #overloading gunpowder
  gunpowderOverloading: 'BLOCK_GRASS_HIT:1:1.5'
  #cooling a cannon
  cool: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #smoke effects for touching a hot barrel
  hot: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #cleaning with the ramrod
  ramrodCleaning: 'BLOCK_SNOW_HIT:0.5:0'
  #cleaning with ramrod done
  ramrodCleaningDone: 'BLOCK_SNOW_HIT:0.5:1'
  #pushing projectile into the barrel
  ramrodPushing: 'BLOCK_STONE_HIT:0.5:0'
  #pushing projectile done
  ramrodPushingDone: 'BLOCK_ANVIL_LAND:0.5:0'
  #measuring the cannon temperature with a thermometer
  thermometer: 'BLOCK_ANVIL_LAND:1:1'
  #enabling the aiming mode with a clock
  enableAimingMode: 'NONE:1:1'
  #disabling aiming mode
  disableAimingMode: 'NONE:1:1'

constructionBlocks:
  #blocks of the cannon schematic which are ignored and not required to build the cannon. Default is sand
  ignore: 'minecraft:sand'
  #the block which the projectile is fired from the cannon, direction can be adjusted using the defaultHorizontalFacing property. Default is block of snow
  muzzle: 'minecraft:snow_block'
  #the block used to indicate when a cannon has been fired. default is torch. Makes fancy smoke on this location
  firingIndicator: 'minecraft:torch'
  #the block used to indicate where the player can place chests or signs on the cannon. Default is a blank wall sign
  chestAndSign: 'minecraft:oak_wall_sign'
  #indicates where redstone torches can be placed for redstone autoload and firing to work. Default is redstone torch
  redstoneTorch: 'minecraft:redstone_torch'
  #the block used to indicate where redstone wiring needs to be placed for redstone autoloading and firing to work. Default is redstone repeater
  restoneWireAndRepeater: 'minecraft:repeater'
  #options for where a redstone signal needs to lead to in order to activate redstone autoloading and firing
  redstoneTrigger:
    #the block used by the schematic to indicate where the redstone signal needs to lead to. Default is a lever
    schematic: 'minecraft:lever[face=wall,facing=east]'
    #the block used in game where the redstone signal needs to lead to. Default is stone button
    ingame: 'minecraft:stone_button[face=wall,facing=east]'
  #the blocks which a player right clicks in order to fire a cannon
  rightClickTrigger:
    #the block used in the cannons schematic which is used to fire the cannon when right clicked by a player. Default is torch
    schematic: 'minecraft:torch'
    #the block used in game to fire the cannon when right clicked by a player. Default is torch
    ingame: 'minecraft:torch'
  #list of blocks in the schematic that will be protected from explosions (e.g. buttons, because they break easily)
  protectedBlocks:
  - 'minecraft:torch'
  - 'minecraft:lever'
  - 'minecraft:stone_button'
```
#### Iron Cannon
```yaml
general:
  #name of the cannon. This will show of on the cannon sign - therefore keep it short
  designName: "ironCannon"
  #This will be used for messages and will replace CANNON in all messages. (e.g. You created a classic cannon)
  messageName: "iron cannon"
  #a short description of the cannon
  description: "Compact iron cannon. Sturdier than the wool design."
  #last user of cannon becomes to it's owner (cannon is public)
  lastUserBecomesOwner: false

signs:
  #this cannon needs a sign to operate. Important for moving cannons.
  isSignRequired: false

ammunition:
  #what the gunpowder is called
  gunpowderName: gunpowder
  #what item is used as gunpowder (minimum is id:data. Named items id:data;displayName;lore1;lore2;....)
  #'minecraft:gunpowder;$rGunpowder'
  gunpowderType: 'minecraft:gunpowder'
  #does this cannon need gunpowder. If false you can directly load the projectile
  needsGunpowder: true
  #gunpowder will be removed from inventories. If false you have to click the cannon until it is reloaded
  gunpowderConsumption: true
  #if false the cannons will not remove the projectile form the inventory but you still need a projectile
  projectileConsumption: true
  #if true, no item is removed from the players inventory
  ammoInfiniteForPlayer: false
  #if true, the cannons does not consume ammunition for autoreloading with redstone
  ammoInfiniteForRedstone: false
  #whether the cannon can reload from a chest
  autoreloadRedstone: true
  #after firing the projectile are usually gone, but you can set this to false to keep the cannon loaded. Just load the cannon once and it stays loaded until you break it.
  removeChargeAfterFiring: true
  #when set the gunpowder will taken from your inventory when a projectile is loaded, no loading of gunpowder required
  autoloadChargeWhenLoadingProjectile: false
  #after creating a cannon it will be preloaded with the maximum amount of gunpowder and the default projectile (first in the list)
  preloaded: false

barrelProperties:
  #maximum gunpowder that can be loaded in the cannon
  maxLoadableGunpowder: 3
  #how much faster the loaded projectile will fired for each gunpowder loaded
  multiplierVelocity: 1.0
  #the angle of which a fired projectile spreads when fired. Basically the lower this is, the more accurate the cannon is
  spreadOfCannon: 1.0

timings:
  #how long anyone near the cannon without a helmet will be confused when the cannon is fired
  blastConfusion: 5.0
  #the delay in seconds between when someone fires a cannon and when the actual projectiles fired from the cannon
  fuseBurnTime: 0
  #fuseBurnTime is multiplied with this with this factor. 0 means the burn time is always the same while 1 it can change vary from 1x to 2x the fuseBurnTime
  fuseBurnTimeRandomness: 0.5
  #the time in seconds before the cannon can be fired again. Outdated due to heat management
  barrelCooldownTime: 0.0
  #time to load gunpowder and projectile for autoreload
  loadTime: 0.05

angles:
  #used to adjust in what direction a projectile is fired from a cannon. adjust this if your cannon is firing sideways or at itself
  defaultHorizontalFacing: north
  #the default angle vertical angle which the cannon aims at when built. this is good for mortars and similar upwards firing weapons
  defaultVerticalAngle: 0.0
  #min and max horizontal angles determine how far to the left and right the cannon can be aim
  maxHorizontalAngle: 45.0
  minHorizontalAngle: -45.0
  #min and max vertical angles determine how far upwards or downwards the cannon can be aimed
  maxVerticalAngle: 45.0
  minVerticalAngle: -45.0
  #if the cannon is on a ship the angles might be smaller
  maxHorizontalAngleOnShip: 10.0
  minHorizontalAngleOnShip: -10.0
  maxVerticalAngleOnShip: 45.0
  minVerticalAngleOnShip: -45.0
  #each change of the angles will change angle by this amount
  angleStepSize: 0.5
  #rougher steps to change cannon direction more quickly
  largeStepSize: 2.0
  #how fast the cannons can be turned in seconds (fastest is 0.05s)
  angleUpdateSpeed: 0.1
  #a message with the new angles is displayed to the user while aiming
  angleUpdateMessage: false

#the impact predictor will show the impact location of a loaded cannon
impactPredictor:
  #enable the impact predictor
  enabled: true
  #the impact location will be shown after the last angle change of the cannon [s]
  delay: 0.5
  #update rate. How often the impact predictor will be calculated per second
  update: 0.2

#sentry mode allows the gun to search and destroy targets automatically.
sentry:
  #this gun is a sentry gun. It will operate on its own.
  isSentry: false
  #does this fire like a mortar (indirect - from above) or like a cannon
  indirectFire: false
  #at which distance the sentry will stop firing because it is too close
  minRange: 5
  #at which distance the sentry will detected enemies
  maxRange: 50
  #how acurate can the final angle be calculated. The smaller the better
  spread: 0.5
  #how long the cannon updating firing solutions. Higher delays result in worse tracking of a moving target. [s]
  update: 1.0
  #the cannon will switch to the next target after some time [s]
  swapTime: 10.0

#enables the linking of several cannons together. Default is limited to the same design
linkCannons:
  #enables the feature to link cannons
  enabled: true
  #cannons can be link if they are closer than the given range to the operated cannons in a box shape
  distance: 20

heatManagement:
  #if heat management is used or not
  enabled: true
  #if true the cannon will refuse to fire if the cannon temperature after firing would be higher than critical
  automaticTemperatureControl: true
  #touching a hot cannon will hurt (in full hearts)
  burnDamage: 0.0
  #touching a hot cannon will slow you (in seconds)
  burnSlowing: 10
  #how much firing one gunpowder will increase the temperature of the barrel
  heatIncreasePerGunpowder: 5.0
  #heat dissipation time coefficient. Smaller time coefficient means it cools down faster
  coolingTimeCoefficient: 10.0
  #how much cooling with the cooling item (config.yml e.g. water bucket) will cool the cannon
  coolingAmount: 50.0
  #searchs for cooling items in chests and cools the cannon if the cannon temperature above the warning temperature
  automaticCooling: true
  #the barrel is hot and you will notice this effect
  warningTemperature: 60.0
  #the barrel damage is critical and the cannon can explode
  criticalTemperature: 150.0
  #if the cannon exceeds this temperature it will explode
  maximumTemperature: 300.0
  #items to cool down a cannon (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItems:
    - 'minecraft:water_bucket'
    - 'minecraft:ice'
    - 'minecraft:snow_block'
  #items which are returned after cooling the cannon. The order is the same like above.
  #setting a item to minecraft:AIR means it will only remove one item instead of replacing the item minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItemsUsed:
    - 'minecraft:bucket'
    - 'minecraft:air'
    - 'minecraft:air'

#cannon can be loaded with more gunpowder, but might explode after firing
overloading:
  #cannon can explode if overloaded with gunpowder
  #chance = chanceInc * ((all loaded gunpowder - maximum loadable gunpowder without overloading) * ChanceOfExplosionPerGunpowder)^Exponent
  enabled: true
  #in real mode cannon can also explode when not overloaded
  #chance = chanceInc * (all loaded gunpowder * ChanceOfExplosionPerGunpowder)^Exponent
  realMode: false
  exponent: 2
  chanceInc: 1
  maxOverloadableGunpowder: 1
  chanceOfExplosionPerGunpowder: 0.05
  #the explosion chance will be multiplied by cannon's temperature / maximumTemperature
  dependsOfTemperature: true
  #loaded gunpowder = 3 normal + 1 overloaded
  #exploding change = 1 * ((3+1)*0.05)^2 = 4%

economy:
  #the money the is withdrawn from your account when you build a cannon. If you have not enough - no cannon will be created
  buildingCosts: 0
  #how much money you receive if your cannon was deconstructed
  dismantlingRefund: 90.0
  #how much money you receive if your cannon was destroyed
  destructionRefund: 10.0

realisticBehaviour:
  #whether a player has to right click while holding the firing item (e.g flint and steel) for the cannon to be fired
  isFiringItemRequired: false
  #firing a cannon produced soot (dirt) which needs to be cleaned. Cleaning is necessary if soot>=1
  sootPerGunpowder: 0.01
  #created cannon will have this amount of soot (0 to disable this feature)
  startingSoot: 0
  #after loading a projectile it is necessary to push the projectile against the gunpowder
  projectilePushing: 2
  #the cannon move one block back after firing (not implemented yet)
  hasRecoil: false
  #whether you have to load the cannon from the same place the projectile is fired (aka muzzle loading) (not implemented yet)
  isFrontloader: false
  #whether the whole cannon can be rotated 90 degrees (not implemented yet)
  isRotatable: false
  #whether the cannon can be used with fire missions to bombarded a certain location (not implemented yet)
  supportsFireMission: false
  #the mass in kilogram of a cannon is important for moving objects e.g. ships
  massOfCannon: 500
  #cannon explodes if a loaded cannon is destroyed. Explosion power 4 (like tnt) and 0 to disable it. Will be scaled with the loaded gunpowder.
  explodingLoadedCannon: 2.0
  #fire after loading projectile with the time delay given by the fuse time. Sneaking will stop immediate firing.
  fireAfterLoading: false
  #dismantling takes some time (fits to the sound) [s]
  dismantlingDelay: 1.75

permissions:
  #all the permissions required for a player to use certain parts of the cannon
  #more information can be found here: http://dev.bukkit.org/bukkit-plugins/cannons/pages/installation-and-configuration/cannons-2-0-and-up/permissions/
  build: cannons.player.build
  #for deconstructing a cannon you need to be the owner and have this permission
  dismantle: cannons.player.dismantle
  #give the cannon a new name
  rename: cannons.player.rename
  #permission for loading gunpowder and projectiles
  load: cannons.player.load
  #permission for firing a cannon
  fire: cannons.player.fire
  #permission for aiming with a cannon
  adjust: cannons.player.adjust
  #permission to used the ramrod (stick) to clean and push the projectile
  ramrod: cannons.player.ramrod
  #the cannon will follow the looking direction of the player if the aiming item is used (default: clock)
  autoaim: cannons.player.autoaim
  #player can add himself as an observer of a cannon with the cmd: '/cannons observer'
  observer: cannons.player.observer
  #not implemented yet
  targetTracking: cannons.player.tracking
  #if a player has no permission for redstone, it is not possible to wire a cannon with redstone or uses torches.
  #firing a prewired cannon however is possible.
  redstone: cannons.player.redstone
  #this player can use a thermometer to measure the temperature of a cannon (default item for thermometer is a gold nugget)
  thermometer: cannons.player.thermometer
  #cannon will autoreload if the player is sneaking and fires the cannon.
  #The ammunition comes from the chest next to the cannon
  autoreload: cannons.player.autoreload
  #how much better the player can handle the cannon.
  #possible values are cannons.player.spreadmultiplier.1 - cannons.player.spreadmultiplier.10 for a multiplier of 0.1 - 1.0
  spreadMultiplier: cannons.player.spreadmultiplier

accessRestriction:
  #whether only the owner of the cannon can use it or not (not implemented yet)
  ownerOnly: false
allowedProjectiles:
  #these are the list of projectiles a cannon can fire. The projectiles are taken from the config files in the projectiles folder.
  #they do not have to be named after an in-game item and can be named anything.
  #make sure the name matches the name of the config file of the projectile you want this cannon to be able to fire. the .yml part does not need to be included
  - cobblestone
  - diamond
  - canistershot
  - enderpearl
  - tnt
  - firework1

sounds:
  #sound effects for this cannon.
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #creating a new cannon
  create: 'BLOCK_ANVIL_LAND:1:0.5'
  #paying the cannon fee of a new cannon
  selected: 'BLOCK_ANVIL_LAND:1:2'
  #destroying a cannon
  destroy: 'ENTITY_ZOMBIE_ATTACK_IRON_DOOR:1:0.5'
  #dismantling a cannon
  dismantle: 'BLOCK_ANVIL_USE:1:0.5'
  #changing the angle of a cannon
  adjust: 'ENTITY_IRON_GOLEM_STEP:1:0.5'
  #fuse igniting sound when firing
  ignite: 'ENTITY_TNT_PRIMED:5:1'
  #firing sound
  firing: 'ENTITY_GENERIC_EXPLODE:20:1.5'
  #loading gunpowder
  gunpowderLoading: 'BLOCK_SAND_HIT:1:1.5'
  #overloading gunpowder
  gunpowderOverloading: 'BLOCK_GRASS_HIT:1:1.5'
  #cooling a cannon
  cool: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #smoke effects for touching a hot barrel
  hot: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #cleaning with the ramrod
  ramrodCleaning: 'BLOCK_SNOW_HIT:0.5:0'
  #cleaning with ramrod done
  ramrodCleaningDone: 'BLOCK_SNOW_HIT:0.5:1'
  #pushing projectile into the barrel
  ramrodPushing: 'BLOCK_STONE_HIT:0.5:0'
  #pushing projectile done
  ramrodPushingDone: 'BLOCK_ANVIL_LAND:0.5:0'
  #measuring the cannon temperature with a thermometer
  thermometer: 'BLOCK_ANVIL_LAND:1:1'
  #enabling the aiming mode with a clock
  enableAimingMode: 'NONE:1:1'
  #disabling aiming mode
  disableAimingMode: 'NONE:1:1'

constructionBlocks:
  #blocks of the cannon schematic which are ignored and not required to build the cannon. Default is sand
  ignore: 'minecraft:sand'
  #the block which the projectile is fired from the cannon, direction can be adjusted using the defaultHorizontalFacing property. Default is block of snow
  muzzle: 'minecraft:snow_block'
  #the block used to indicate when a cannon has been fired. default is torch. Makes fancy smoke on this location
  firingIndicator: 'minecraft:torch'
  #the block used to indicate where the player can place chests or signs on the cannon. Default is a blank wall sign
  chestAndSign: 'minecraft:oak_wall_sign'
  #indicates where redstone torches can be placed for redstone autoload and firing to work. Default is redstone torch
  redstoneTorch: 'minecraft:redstone_torch'
  #the block used to indicate where redstone wiring needs to be placed for redstone autoloading and firing to work. Default is redstone repeater
  restoneWireAndRepeater: 'minecraft:repeater'
  #options for where a redstone signal needs to lead to in order to activate redstone autoloading and firing
  redstoneTrigger:
    #the block used by the schematic to indicate where the redstone signal needs to lead to. Default is a lever
    schematic: 'minecraft:lever[face=wall,facing=east]'
    #the block used in game where the redstone signal needs to lead to. Default is stone button
    ingame: 'minecraft:stone_button[face=wall,facing=east]'
  #the blocks which a player right clicks in order to fire a cannon
  rightClickTrigger:
    #the block used in the cannons schematic which is used to fire the cannon when right clicked by a player. Default is torch
    schematic: 'minecraft:torch'
    #the block used in game to fire the cannon when right clicked by a player. Default is torch
    ingame: 'minecraft:torch'
  #list of blocks in the schematic that will be protected from explosions (e.g. buttons, because they break easily)
  protectedBlocks:
  - 'minecraft:torch'
  - 'minecraft:lever'
  - 'minecraft:stone_button'
```
#### Mortar
```yaml
general:
  #name of the cannon. This will show of on the cannon sign - therefore keep it short
  designName: "mortar"
  #This will be used for messages and will replace CANNON in all messages. (e.g. You created a classic cannon)
  messageName: "mortar"
  #a short description of the cannon
  description: "Compact iron mortar. Allows you to fire over walls."
  #last user of cannon becomes to it's owner (cannon is public)
  lastUserBecomesOwner: false

signs:
  #this cannon needs a sign to operate. Important for moving cannons.
  isSignRequired: false

ammunition:
  #what the gunpowder is called
  gunpowderName: gunpowder
  #what item is used as gunpowder (minimum is id:data. Named items id:data;displayName;lore1;lore2;....)
  #'minecraft:gunpowder;$rGunpowder'
  gunpowderType: 'minecraft:gunpowder'
  #does this cannon need gunpowder. If false you can directly load the projectile
  needsGunpowder: true
  #gunpowder will be removed from inventories. If false you have to click the cannon until it is reloaded
  gunpowderConsumption: true
  #if false the cannons will not remove the projectile form the inventory but you still need a projectile
  projectileConsumption: true
  #if true, no item is removed from the players inventory
  ammoInfiniteForPlayer: false
  #if true, the cannons does not consume ammunition for autoreloading with redstone
  ammoInfiniteForRedstone: false
  #whether the cannon can reload from a chest
  autoreloadRedstone: true
  #after firing the projectile are usually gone, but you can set this to false to keep the cannon loaded. Just load the cannon once and it stays loaded until you break it.
  removeChargeAfterFiring: true
  #when set the gunpowder will taken from your inventory when a projectile is loaded, no loading of gunpowder required
  autoloadChargeWhenLoadingProjectile: false
  #after creating a cannon it will be preloaded with the maximum amount of gunpowder and the default projectile (first in the list)
  preloaded: false

barrelProperties:
  #maximum gunpowder that can be loaded in the cannon
  maxLoadableGunpowder: 2
  #how much faster the loaded projectile will fired for each gunpowder loaded
  multiplierVelocity: 1.0
  #the angle of which a fired projectile spreads when fired. Basically the lower this is, the more accurate the cannon is
  spreadOfCannon: 1.0

timings:
  #how long anyone near the cannon without a helmet will be confused when the cannon is fired
  blastConfusion: 5.0
  #the delay in seconds between when someone fires a cannon and when the actual projectiles fired from the cannon
  fuseBurnTime: 1.0
  #fuseBurnTime is multiplied with this with this factor. 0 means the burn time is always the same while 1 it can change vary from 1x to 2x the fuseBurnTime
  fuseBurnTimeRandomness: 0.5
  #the time in seconds before the cannon can be fired again. Outdated due to heat management
  barrelCooldownTime: 0.0
  #time to load gunpowder and projectile for autoreload
  loadTime: 3.0

angles:
  #used to adjust in what direction a projectile is fired from a cannon. adjust this if your cannon is firing sideways or at itself
  defaultHorizontalFacing: NORTH
  #the default angle vertical angle which the cannon aims at when built. this is good for mortars and similar upwards firing weapons
  defaultVerticalAngle: 70.0
  #min and max horizontal angles determine how far to the left and right the cannon can be aim
  maxHorizontalAngle: 45.0
  minHorizontalAngle: -45.0
  #min and max vertical angles determine how far upwards or downwards the cannon can be aimed
  maxVerticalAngle: 20.0
  minVerticalAngle: -20.0
  #if the cannon is on a ship the angles might be smaller
  maxHorizontalAngleOnShip: 10.0
  minHorizontalAngleOnShip: -10.0
  maxVerticalAngleOnShip: 45.0
  minVerticalAngleOnShip: -45.0
  #each change of the angles will change angle by this amount
  angleStepSize: 0.5
  #rougher steps to change cannon direction more quickly
  largeStepSize: 2.0
  #how fast the cannons can be turned in seconds (fastest is 0.05s)
  angleUpdateSpeed: 0.1
  #a message with the new angles is displayed to the user while aiming
  angleUpdateMessage: false

#the impact predictor will show the impact location of a loaded cannon
impactPredictor:
  #enable the impact predictor
  enabled: true
  #the impact location will be shown after the last angle change of the cannon [s]
  delay: 0.5
  #update rate. How often the impact predictor will be calculated per second
  update: 0.2

#sentry mode allows the gun to search and destroy targets automatically.
sentry:
  #this gun is a sentry gun. It will operate on its own.
  isSentry: false
  #does this fire like a mortar (indirect - from above) or like a cannon
  indirectFire: false
  #at which distance the sentry will stop firing because it is too close
  minRange: 5
  #at which distance the sentry will detected enemies
  maxRange: 50
  #how acurate can the final angle be calculated. The smaller the better
  spread: 0.5
  #how long the cannon updating firing solutions. Higher delays result in worse tracking of a moving target. [s]
  update: 1.0
  #the cannon will switch to the next target after some time [s]
  swapTime: 10.0

#enables the linking of several cannons together. Default is limited to the same design
linkCannons:
  #enables the feature to link cannons
  enabled: true
  #cannons can be link if they are closer than the given range to the operated cannons in a box shape
  distance: 20

heatManagement:
  #if heat management is used or not
  enabled: true
  #if true the cannon will refuse to fire if the cannon temperature after firing would be higher than critical
  automaticTemperatureControl: true
  #touching a hot cannon will hurt (in full hearts)
  burnDamage: 0.0
  #touching a hot cannon will slow you (in seconds)
  burnSlowing: 10
  #how much firing one gunpowder will increase the temperature of the barrel
  heatIncreasePerGunpowder: 5.0
  #heat dissipation time coefficient. Smaller time coefficient means it cools down faster
  coolingTimeCoefficient: 10.0
  #how much cooling with the cooling item (config.yml e.g. water bucket) will cool the cannon
  coolingAmount: 50.0
  #searchs for cooling items in chests and cools the cannon if the cannon temperature above the warning temperature
  automaticCooling: true
  #the barrel is hot and you will notice this effect
  warningTemperature: 60.0
  #the barrel damage is critical and the cannon can explode
  criticalTemperature: 150.0
  #if the cannon exceeds this temperature it will explode
  maximumTemperature: 300.0
  #items to cool down a cannon (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItems:
    - 'minecraft:water_bucket'
    - 'minecraft:ice'
    - 'minecraft:snow_block'
  #items which are returned after cooling the cannon. The order is the same like above.
  #setting a item to minecraft:AIR means it will only remove one item instead of replacing the item minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItemsUsed:
    - 'minecraft:bucket'
    - 'minecraft:air'
    - 'minecraft:air'

#cannon can be loaded with more gunpowder, but might explode after firing
overloading:
  #cannon can explode if overloaded with gunpowder
  #chance = chanceInc * ((all loaded gunpowder - maximum loadable gunpowder without overloading) * ChanceOfExplosionPerGunpowder)^Exponent
  enabled: true
  #in real mode cannon can also explode when not overloaded
  #chance = chanceInc * (all loaded gunpowder * ChanceOfExplosionPerGunpowder)^Exponent
  realMode: false
  exponent: 2
  chanceInc: 1
  maxOverloadableGunpowder: 1
  chanceOfExplosionPerGunpowder: 0.1
  #the explosion chance will be multiplied by cannon's temperature / maximumTemperature
  dependsOfTemperature: true
  #loaded gunpowder = 3 normal + 1 overloaded
  #exploding change = 1 * ((2+1)*0.1)^2 = 9%

economy:
  #the money the is withdrawn from your account when you build a cannon. If you have not enough - no cannon will be created
  buildingCosts: 0
  #how much money you receive if your cannon was deconstructed
  dismantlingRefund: 90.0
  #how much money you receive if your cannon was destroyed
  destructionRefund: 10.0

realisticBehaviour:
  #whether a player has to right click while holding the firing item (e.g flint and steel) for the cannon to be fired
  isFiringItemRequired: false
  #firing a cannon produced soot (dirt) which needs to be cleaned. Cleaning is necessary if soot>=1
  sootPerGunpowder: 0.1
  #created cannon will have this amount of soot (0 to disable this feature)
  startingSoot: 10
  #after loading a projectile it is necessary to push the projectile against the gunpowder
  projectilePushing: 2
  #the cannon move one block back after firing (not implemented yet)
  hasRecoil: false
  #whether you have to load the cannon from the same place the projectile is fired (aka muzzle loading) (not implemented yet)
  isFrontloader: false
  #whether the whole cannon can be rotated 90 degrees (not implemented yet)
  isRotatable: false
  #whether the cannon can be used with fire missions to bombarded a certain location (not implemented yet)
  supportsFireMission: false
  #the mass in kilogram of a cannon is important for moving objects e.g. ships
  massOfCannon: 300
  #cannon explodes if a loaded cannon is destroyed. Explosion power 4 (like tnt) and 0 to disable it. Will be scaled with the loaded gunpowder.
  explodingLoadedCannon: 2.0
  #fire after loading projectile with the time delay given by the fuse time. Sneaking will stop immediate firing.
  fireAfterLoading: false
  #dismantling takes some time (fits to the sound) [s]
  dismantlingDelay: 1.75

permissions:
  #all the permissions required for a player to use certain parts of the cannon
  #more information can be found here: http://dev.bukkit.org/bukkit-plugins/cannons/pages/installation-and-configuration/cannons-2-0-and-up/permissions/
  build: cannons.player.build
  #for deconstructing a cannon you need to be the owner and have this permission
  dismantle: cannons.player.dismantle
  #give the cannon a new name
  rename: cannons.player.rename
  #permission for loading gunpowder and projectiles
  load: cannons.player.load
  #permission for firing a cannon
  fire: cannons.player.fire
  #permission for aiming with a cannon
  adjust: cannons.player.adjust
  #permission to used the ramrod (stick) to clean and push the projectile
  ramrod: cannons.player.ramrod
  #the cannon will follow the looking direction of the player if the aiming item is used (default: clock)
  autoaim: cannons.player.autoaim
  #player can add himself as an observer of a cannon with the cmd: '/cannons observer'
  observer: cannons.player.observer
  #not implemented yet
  targetTracking: cannons.player.tracking
  #if a player has no permission for redstone, it is not possible to wire a cannon with redstone or uses torches.
  #firing a prewired cannon however is possible.
  redstone: cannons.player.redstone
  #this player can use a thermometer to measure the temperature of a cannon (default item for thermometer is a gold nugget)
  thermometer: cannons.player.thermometer
  #cannon will autoreload if the player is sneaking and fires the cannon.
  #The ammunition comes from the chest next to the cannon
  autoreload: cannons.player.autoreload
  #how much better the player can handle the cannon.
  #possible values are cannons.player.spreadmultiplier.1 - cannons.player.spreadmultiplier.10 for a multiplier of 0.1 - 1.0
  spreadMultiplier: cannons.player.spreadmultiplier

accessRestriction:
  #whether only the owner of the cannon can use it or not (not implemented yet)
  ownerOnly: false

allowedProjectiles:
  #these are the list of projectiles a cannon can fire. The projectiles are taken from the config files in the projectiles folder.
  #they do not have to be named after an in-game item and can be named anything.
  #make sure the name matches the name of the config file of the projectile you want this cannon to be able to fire. the .yml part does not need to be included
  - cobblestone
  - diamond
  - canistershot
  - enderpearl
  - tnt
  - firework1

sounds:
  #sound effects for this cannon.
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #creating a new cannon
  create: 'BLOCK_ANVIL_LAND:1:0.5'
  #paying the cannon fee of a new cannon
  selected: 'BLOCK_ANVIL_LAND:1:2'
  #destroying a cannon
  destroy: 'ENTITY_ZOMBIE_ATTACK_IRON_DOOR:1:0.5'
  #dismantling a cannon
  dismantle: 'BLOCK_ANVIL_USE:1:0.5'
  #changing the angle of a cannon
  adjust: 'ENTITY_IRON_GOLEM_STEP:1:0.5'
  #fuse igniting sound when firing
  ignite: 'ENTITY_TNT_PRIMED:5:1'
  #firing sound
  firing: 'ENTITY_GENERIC_EXPLODE:20:1.5'
  #loading gunpowder
  gunpowderLoading: 'BLOCK_SAND_HIT:1:1.5'
  #overloading gunpowder
  gunpowderOverloading: 'BLOCK_GRASS_HIT:1:1.5'
  #cooling a cannon
  cool: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #smoke effects for touching a hot barrel
  hot: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #cleaning with the ramrod
  ramrodCleaning: 'BLOCK_SNOW_HIT:0.5:0'
  #cleaning with ramrod done
  ramrodCleaningDone: 'BLOCK_SNOW_HIT:0.5:1'
  #pushing projectile into the barrel
  ramrodPushing: 'BLOCK_STONE_HIT:0.5:0'
  #pushing projectile done
  ramrodPushingDone: 'BLOCK_ANVIL_LAND:0.5:0'
  #measuring the cannon temperature with a thermometer
  thermometer: 'BLOCK_ANVIL_LAND:1:1'
  #enabling the aiming mode with a clock
  enableAimingMode: 'NONE:1:1'
  #disabling aiming mode
  disableAimingMode: 'NONE:1:1'

constructionBlocks:
  #blocks of the cannon schematic which are ignored and not required to build the cannon. Default is sand
  ignore: 'minecraft:sand'
  #the block which the projectile is fired from the cannon, direction can be adjusted using the defaultHorizontalFacing property. Default is block of snow
  muzzle: 'minecraft:snow_block'
  #the block used to indicate when a cannon has been fired. default is torch. Makes fancy smoke on this location
  firingIndicator: 'minecraft:wall_torch'
  #the block used to indicate where the player can place chests or signs on the cannon. Default is a blank wall sign
  chestAndSign: 'minecraft:oak_wall_sign'
  #indicates where redstone torches can be placed for redstone autoload and firing to work. Default is redstone torch
  redstoneTorch: 'minecraft:redstone_torch'
  #the block used to indicate where redstone wiring needs to be placed for redstone autoloading and firing to work. Default is redstone repeater
  restoneWireAndRepeater: 'minecraft:repeater'
  #options for where a redstone signal needs to lead to in order to activate redstone autoloading and firing
  redstoneTrigger:
    #the block used by the schematic to indicate where the redstone signal needs to lead to. Default is a lever
    schematic: 'minecraft:lever[face=wall,facing=east]'
    #the block used in game where the redstone signal needs to lead to. Default is stone button
    ingame: 'minecraft:stone_button[face=wall,facing=east]'
  #the blocks which a player right clicks in order to fire a cannon
  rightClickTrigger:
    #the block used in the cannons schematic which is used to fire the cannon when right clicked by a player. Default is torch
    schematic: 'minecraft:wall_torch'
    #the block used in game to fire the cannon when right clicked by a player. Default is torch
    ingame: 'minecraft:wall_torch'
  #list of blocks in the schematic that will be protected from explosions (e.g. buttons, because they break easily)
  protectedBlocks:
  - 'minecraft:wall_torch'
  - 'minecraft:lever'
  - 'minecraft:stone_button'

```
#### Sentry
```yaml
general:
  #name of the cannon. This will show of on the cannon sign - therefore keep it short
  designName: "sentry"
  #This will be used for messages and will replace CANNON in all messages. (e.g. You created a classic cannon)
  messageName: "sentry"
  #a short description of the cannon
  description: "Sentry cannon which targets mobs automatically"
  #last user of cannon becomes to it's owner (cannon is public)
  lastUserBecomesOwner: false

signs:
  #this cannon needs a sign to operate. Important for moving cannons.
  isSignRequired: false

ammunition:
  #what the gunpowder is called
  gunpowderName: gunpowder
  #what item is used as gunpowder (minimum is id:data. Named items id:data;displayName;lore1;lore2;....)
  #'minecraft:gunpowder;$rGunpowder'
  gunpowderType: 'minecraft:gunpowder'
  #does this cannon need gunpowder. If false you can directly load the projectile
  needsGunpowder: true
  #gunpowder will be removed from inventories. If false you have to click the cannon until it is reloaded
  gunpowderConsumption: true
  #if false the cannons will not remove the projectile form the inventory but you still need a projectile
  projectileConsumption: true
  #if true, no item is removed from the players inventory
  ammoInfiniteForPlayer: false
  #if true, the cannons does not consume ammunition for autoreloading with redstone
  ammoInfiniteForRedstone: false
  #whether the cannon can reload from a chest
  autoreloadRedstone: true
  #after firing the projectile are usually gone, but you can set this to false to keep the cannon loaded. Just load the cannon once and it stays loaded until you break it.
  removeChargeAfterFiring: true
  #when set the gunpowder will taken from your inventory when a projectile is loaded, no loading of gunpowder required
  autoloadChargeWhenLoadingProjectile: false
  #after creating a cannon it will be preloaded with the maximum amount of gunpowder and the default projectile (first in the list)
  preloaded: false

barrelProperties:
  #maximum gunpowder that can be loaded in the cannon
  maxLoadableGunpowder: 1
  #how much faster the loaded projectile will fired for each gunpowder loaded
  multiplierVelocity: 0.8
  #the angle of which a fired projectile spreads when fired. Basically the lower this is, the more accurate the cannon is
  spreadOfCannon: 1.0

timings:
  #how long anyone near the cannon without a helmet will be confused when the cannon is fired
  blastConfusion: 5.0
  #the delay in seconds between when someone fires a cannon and when the actual projectiles fired from the cannon
  fuseBurnTime: 1.0
  #fuseBurnTime is multiplied with this with this factor. 0 means the burn time is always the same while 1 it can change vary from 1x to 2x the fuseBurnTime
  fuseBurnTimeRandomness: 0.5
  #the time in seconds before the cannon can be fired again. Outdated due to heat management
  barrelCooldownTime: 0.0
  #time to load gunpowder and projectile for autoreload
  loadTime: 3.0

angles:
  #used to adjust in what direction a projectile is fired from a cannon. adjust this if your cannon is firing sideways or at itself
  defaultHorizontalFacing: north
  #the default angle vertical angle which the cannon aims at when built. this is good for mortars and similar upwards firing weapons
  defaultVerticalAngle: 0.0
  #min and max horizontal angles determine how far to the left and right the cannon can be aim
  maxHorizontalAngle: 45.0
  minHorizontalAngle: -45.0
  #min and max vertical angles determine how far upwards or downwards the cannon can be aimed
  maxVerticalAngle: 45.0
  minVerticalAngle: -45.0
  #if the cannon is on a ship the angles might be smaller
  maxHorizontalAngleOnShip: 10.0
  minHorizontalAngleOnShip: -10.0
  maxVerticalAngleOnShip: 45.0
  minVerticalAngleOnShip: -45.0
  #each change of the angles will change angle by this amount
  angleStepSize: 0.5
  #rougher steps to change cannon direction more quickly
  largeStepSize: 2.0
  #how fast the cannons can be turned in seconds (fastest is 0.05s)
  angleUpdateSpeed: 0.1
  #a message with the new angles is displayed to the user while aiming
  angleUpdateMessage: false

#the impact predictor will show the impact location of a loaded cannon
impactPredictor:
  #enable the impact predictor
  enabled: true
  #the impact location will be shown after the last angle change of the cannon [s]
  delay: 0.5
  #update rate. How often the impact predictor will be calculated per second
  update: 0.2

#sentry mode allows the gun to search and destroy targets automatically.
sentry:
  #this gun is a sentry gun. It will operate on its own.
  isSentry: true
  #does this fire like a mortar (indirect - from above) or like a cannon
  indirectFire: false
  #at which distance the sentry will stop firing because it is too close
  minRange: 5
  #at which distance the sentry will detected enemies
  maxRange: 50
  #how acurate can the final angle be calculated. The smaller the better
  spread: 0.5
  #how long the cannon updating firing solutions. Higher delays result in worse tracking of a moving target. [s]
  update: 1.0
  #the cannon will switch to the next target after some time [s]
  swapTime: 10.0

#enables the linking of several cannons together. Default is limited to the same design
linkCannons:
  #enables the feature to link cannons
  enabled: false
  #cannons can be link if they are closer than the given range to the operated cannons in a box shape
  distance: 40

heatManagement:
  #if heat management is used or not
  enabled: true
  #if true the cannon will refuse to fire if the cannon temperature after firing would be higher than critical
  automaticTemperatureControl: true
  #touching a hot cannon will hurt (in full hearts)
  burnDamage: 0.0
  #touching a hot cannon will slow you (in seconds)
  burnSlowing: 10
  #how much firing one gunpowder will increase the temperature of the barrel
  heatIncreasePerGunpowder: 5.0
  #heat dissipation time coefficient. Smaller time coefficient means it cools down faster
  coolingTimeCoefficient: 10.0
  #how much cooling with the cooling item (config.yml e.g. water bucket) will cool the cannon
  coolingAmount: 50.0
  #searchs for cooling items in chests and cools the cannon if the cannon temperature above the warning temperature
  automaticCooling: true
  #the barrel is hot and you will notice this effect
  warningTemperature: 60.0
  #the barrel damage is critical and the cannon can explode
  criticalTemperature: 150.0
  #if the cannon exceeds this temperature it will explode
  maximumTemperature: 300.0
  #items to cool down a cannon (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItems:
    - 'minecraft:water_bucket'
    - 'minecraft:ice'
    - 'minecraft:snow_block'
  #items which are returned after cooling the cannon. The order is the same like above.
  #setting a item to minecraft:AIR means it will only remove one item instead of replacing the item minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2;....)
  coolingItemsUsed:
    - 'minecraft:bucket'
    - 'minecraft:air'
    - 'minecraft:air'

#cannon can be loaded with more gunpowder, but might explode after firing
overloading:
  #cannon can explode if overloaded with gunpowder
  #chance = chanceInc * ((all loaded gunpowder - maximum loadable gunpowder without overloading) * ChanceOfExplosionPerGunpowder)^Exponent
  enabled: true
  #in real mode cannon can also explode when not overloaded
  #chance = chanceInc * (all loaded gunpowder * ChanceOfExplosionPerGunpowder)^Exponent
  realMode: false
  exponent: 2
  chanceInc: 1
  maxOverloadableGunpowder: 1
  chanceOfExplosionPerGunpowder: 0.05
  #the explosion chance will be multiplied by cannon's temperature / maximumTemperature
  dependsOfTemperature: true
  #loaded gunpowder = 3 normal + 1 overloaded
  #exploding change = 1 * ((3+1)*0.05)^2 = 4%

economy:
  #the money the is withdrawn from your account when you build a cannon. If you have not enough - no cannon will be created
  buildingCosts: 0
  #how much money you receive if your cannon was deconstructed
  dismantlingRefund: 90.0
  #how much money you receive if your cannon was destroyed
  destructionRefund: 10.0

realisticBehaviour:
  #whether a player has to right click while holding the firing item (e.g flint and steel) for the cannon to be fired
  isFiringItemRequired: false
  #firing a cannon produced soot (dirt) which needs to be cleaned. Cleaning is necessary if soot>=1
  sootPerGunpowder: 0.0
  #created cannon will have this amount of soot (0 to disable this feature)
  startingSoot: 10
  #after loading a projectile it is necessary to push the projectile against the gunpowder
  projectilePushing: 2
  #the cannon move one block back after firing (not implemented yet)
  hasRecoil: false
  #whether you have to load the cannon from the same place the projectile is fired (aka muzzle loading) (not implemented yet)
  isFrontloader: false
  #whether the whole cannon can be rotated 90 degrees (not implemented yet)
  isRotatable: false
  #whether the cannon can be used with fire missions to bombarded a certain location (not implemented yet)
  supportsFireMission: false
  #the mass in kilogram of a cannon is important for moving objects e.g. ships
  massOfCannon: 500
  #cannon explodes if a loaded cannon is destroyed. Explosion power 4 (like tnt) and 0 to disable it. Will be scaled with the loaded gunpowder.
  explodingLoadedCannon: 2.0
  #fire after loading projectile with the time delay given by the fuse time. Sneaking will stop immediate firing.
  fireAfterLoading: false
  #dismantling takes some time (fits to the sound) [s]
  dismantlingDelay: 1.75

permissions:
  #all the permissions required for a player to use certain parts of the cannon
  #more information can be found here: http://dev.bukkit.org/bukkit-plugins/cannons/pages/installation-and-configuration/cannons-2-0-and-up/permissions/
  build: cannons.player.build
  #for deconstructing a cannon you need to be the owner and have this permission
  dismantle: cannons.player.dismantle
  #give the cannon a new name
  rename: cannons.player.rename
  #permission for loading gunpowder and projectiles
  load: cannons.player.load
  #permission for firing a cannon
  fire: cannons.player.fire
  #permission for aiming with a cannon
  adjust: cannons.player.adjust
  #permission to used the ramrod (stick) to clean and push the projectile
  ramrod: cannons.player.ramrod
  #the cannon will follow the looking direction of the player if the aiming item is used (default: clock)
  autoaim: cannons.player.autoaim
  #player can add himself as an observer of a cannon with the cmd: '/cannons observer'
  observer: cannons.player.observer
  #not implemented yet
  targetTracking: cannons.player.tracking
  #if a player has no permission for redstone, it is not possible to wire a cannon with redstone or uses torches.
  #firing a prewired cannon however is possible.
  redstone: cannons.player.redstone
  #this player can use a thermometer to measure the temperature of a cannon (default item for thermometer is a gold nugget)
  thermometer: cannons.player.thermometer
  #cannon will autoreload if the player is sneaking and fires the cannon.
  #The ammunition comes from the chest next to the cannon
  autoreload: cannons.player.autoreload
  #how much better the player can handle the cannon.
  #possible values are cannons.player.spreadmultiplier.1 - cannons.player.spreadmultiplier.10 for a multiplier of 0.1 - 1.0
  spreadMultiplier: cannons.player.spreadmultiplier

accessRestriction:
  #whether only the owner of the cannon can use it or not (not implemented yet)
  ownerOnly: false
allowedProjectiles:
  #these are the list of projectiles a cannon can fire. The projectiles are taken from the config files in the projectiles folder.
  #they do not have to be named after an in-game item and can be named anything.
  #make sure the name matches the name of the config file of the projectile you want this cannon to be able to fire. the .yml part does not need to be included
  - cobblestone
  - diamond
  - canistershot
  - enderpearl
  - tnt
  - firework1

sounds:
  #sound effects for this cannon.
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #creating a new cannon
  create: 'BLOCK_ANVIL_LAND:1:0.5'
  #paying the cannon fee of a new cannon
  selected: 'BLOCK_ANVIL_LAND:1:2'
  #destroying a cannon
  destroy: 'ENTITY_ZOMBIE_ATTACK_IRON_DOOR:1:0.5'
  #dismantling a cannon
  dismantle: 'BLOCK_ANVIL_USE:1:0.5'
  #changing the angle of a cannon
  adjust: 'ENTITY_IRON_GOLEM_STEP:1:0.5'
  #fuse igniting sound when firing
  ignite: 'ENTITY_TNT_PRIMED:5:1'
  #firing sound
  firing: 'ENTITY_GENERIC_EXPLODE:20:1.5'
  #loading gunpowder
  gunpowderLoading: 'BLOCK_SAND_HIT:1:1.5'
  #overloading gunpowder
  gunpowderOverloading: 'BLOCK_GRASS_HIT:1:1.5'
  #cooling a cannon
  cool: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #smoke effects for touching a hot barrel
  hot: 'BLOCK_FIRE_EXTINGUISH:1:1'
  #cleaning with the ramrod
  ramrodCleaning: 'BLOCK_SNOW_HIT:0.5:0'
  #cleaning with ramrod done
  ramrodCleaningDone: 'BLOCK_SNOW_HIT:0.5:1'
  #pushing projectile into the barrel
  ramrodPushing: 'BLOCK_STONE_HIT:0.5:0'
  #pushing projectile done
  ramrodPushingDone: 'BLOCK_ANVIL_LAND:0.5:0'
  #measuring the cannon temperature with a thermometer
  thermometer: 'BLOCK_ANVIL_LAND:1:1'
  #enabling the aiming mode with a clock
  enableAimingMode: 'NONE:1:1'
  #disabling aiming mode
  disableAimingMode: 'NONE:1:1'

constructionBlocks:
  #blocks of the cannon schematic which are ignored and not required to build the cannon. Default is sand
  ignore: 'minecraft:sand'
  #the block which the projectile is fired from the cannon, direction can be adjusted using the defaultHorizontalFacing property. Default is block of snow
  muzzle: 'minecraft:snow_block'
  #the block used to indicate when a cannon has been fired. default is torch. Makes fancy smoke on this location
  firingIndicator: 'minecraft:torch'
  #the block used to indicate where the player can place chests or signs on the cannon. Default is a blank wall sign
  chestAndSign: 'minecraft:oak_wall_sign'
  #indicates where redstone torches can be placed for redstone autoload and firing to work. Default is redstone torch
  redstoneTorch: 'minecraft:redstone_torch'
  #the block used to indicate where redstone wiring needs to be placed for redstone autoloading and firing to work. Default is redstone repeater
  restoneWireAndRepeater: 'minecraft:repeater'
  #options for where a redstone signal needs to lead to in order to activate redstone autoloading and firing
  redstoneTrigger:
    #the block used by the schematic to indicate where the redstone signal needs to lead to. Default is a lever
    schematic: 'minecraft:lever[face=wall,facing=east]'
    #the block used in game where the redstone signal needs to lead to. Default is stone button
    ingame: 'minecraft:stone_button[face=wall,facing=east]'
  #the blocks which a player right clicks in order to fire a cannon
  rightClickTrigger:
    #the block used in the cannons schematic which is used to fire the cannon when right clicked by a player. Default is torch
    schematic: 'minecraft:torch'
    #the block used in game to fire the cannon when right clicked by a player. Default is torch
    ingame: 'minecraft:torch'
  #list of blocks in the schematic that will be protected from explosions (e.g. buttons, because they break easily)
  protectedBlocks:
  - 'minecraft:torch'
  - 'minecraft:lever'
  - 'minecraft:stone_button'
```
### Projectiles

#### Canister Shot
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: canistershot
  #a short description of the projectile
  description: 'Turns your cannon in a giant shotgun'
  #the name of the item to load this projectile
  itemName: 'melon seed'
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:melon_seeds'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

cannonball:
  #the type of the projectile entity
  #ARROW, EGG, FIREBALL, SMALL_FIREBALL, SNOWBALL, THROWN_EXP_BOTTLE, SPLASH_POTION, WITHER_SKULL
  entityType: SNOWBALL
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 3.0
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 0
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: false
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 0.05
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired with a single shoot
  numberOfBullets: 20
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 2.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: false
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: false
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #spawns additional delayed explosions around the explosion
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 50
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 10
  #the range of the potion effects specified below
  potionRange: 2
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: true

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: false
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time. 
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    #- 'PRIMED_TNT 1-3'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: false
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: false

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```
#### Cobblestone
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: cannonball
  #a short description of the projectile
  description: "A cheap and simple cannonball."
  #the name of the item to load this projectile
  itemName: cobblestone
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:cobblestone'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:
    - 'minecraft:stone'

cannonball:
  #the type of the projectile entity
  #ARROW, EGG, FIREBALL, SMALL_FIREBALL, SNOWBALL, THROWN_EXP_BOTTLE, SPLASH_POTION, WITHER_SKULL
  entityType: SNOWBALL
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 3
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired with a single shoot
  numberOfBullets: 1
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: true
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 2.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: true
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 100
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 10
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: true

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: false
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    - 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    #- 'LINGERING_POTION 20-50 {Potion:long_poison}'
    #- 'ZOMBIE 1-4{HelmetArmorItem:Iron_Helmet, LeggingsArmorItem:IRON_LEGGINGS, ChestplateArmorItem:IRON_CHESTPLATE, BootsArmorItem:Iron_Boots, MainHandItem:IRON_AXE, OffHandItem:SHIELD}'
    #- 'AREA_EFFECT_CLOUD 1-3 {Color:16711680, Duration:100, Radius:3, Potion:poison}'
    #- 'TIPPED_ARROW 30-50 {Potion:poison}'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: false
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: true

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```
#### Diamond
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: hardened cannonball
  #a short description of the projectile
  description: "This cannonball contains a diamond and will even break obsidian."
  #the name of the item to load this projectile
  itemName: diamond
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:diamond'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

cannonball:
  #the type of the projectile entity
  #ARROW, EGG, FIREBALL, SMALL_FIREBALL, SNOWBALL, THROWN_EXP_BOTTLE, SPLASH_POTION, WITHER_SKULL
  entityType: SNOWBALL
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 3
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 2
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired with a single shoot
  numberOfBullets: 1
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 1
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this means the cannonball will break through obsidian, water, and lava
    - superbreaker
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: true
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 3.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: true
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 150
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 15
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: true

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: false
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
#     - 'LINGERING_POTION 20-50 {Potion:long_poison}'
#     - 'ZOMBIE 1-4{HelmetArmorItem:Iron_Helmet, LeggingsArmorItem:IRON_LEGGINGS, ChestplateArmorItem:IRON_CHESTPLATE, BootsArmorItem:Iron_Boots, MainHandItem:IRON_AXE, OffHandItem:SHIELD}'
#     - 'AREA_EFFECT_CLOUD 1-3 {Color:16711680, Duration:100, Radius:3, Potion:poison}'
#     - 'TIPPED_ARROW 30-50 {Potion:poison}'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: false
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: true

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'

#### Ender Pearl

general:
  #the name of the projectile displayed in game
  projectileName: Teleporter projectile
  #a short description of the projectile
  description: "This cannonball will teleport you to the impact location."
  #the name of the item to load this projectile
  itemName: ender pearl
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:ender_pearl'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

cannonball:
  #the type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 6
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 0
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: false
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 1
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #the player is tied to the projectile and will follow its path to the target
    - teleport

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: true
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: false
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 100
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 1
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 1
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 0
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: true

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: false
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
#    - 'LINGERING_POTION 20-50 {Potion:long_poison}'
#    - 'ZOMBIE 1-4{HelmetArmorItem:Iron_Helmet, LeggingsArmorItem:IRON_LEGGINGS, ChestplateArmorItem:IRON_CHESTPLATE, BootsArmorItem:Iron_Boots, MainHandItem:IRON_AXE, OffHandItem:SHIELD}'
#    - 'AREA_EFFECT_CLOUD 1-3 {Color:16711680, Duration:100, Radius:3, Potion:poison}'
#    - 'TIPPED_ARROW 30-50 {Potion:poison}'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: false
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
    #red
    - 'FF0000'
    #white
    - 'FFFFFF'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: true

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```
#### Firework 1
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: fireworks
  #a short description of the projectile
  description: "Cluster fireworks. It will split 4 times and spawn now firworks."
  #the name of the item to load this projectile
  itemName: firework rocket
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:firework_rocket'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: true
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

cannonball:
  #the type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 3
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 1.0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 1
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 10
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 5
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: false

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: true
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    #- 'PRIMED_TNT 1-3'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:
    - firework2

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: true
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: STAR
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
      #red
      - 'FF0000'
      #white
      - 'FFFFFF'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: false

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'

```
#### Firework 2
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: fireworks
  #a short description of the projectile
  description: "Second stage of the fireworks."
  #the name of the item to load this projectile
  itemName: firework rocket
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:air'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:
    - 'STONE:0'

cannonball:
  #the type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 1
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.5
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 5
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: false
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 10
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 5
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: false

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: true
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    #- 'PRIMED_TNT 1-3'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:
    - firework3

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: true
  #if the firework flickers or not
  flicker: true
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
      #white
      - 'FFFFFF'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: false

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```
#### Firework 3
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: fireworks
  #a short description of the projectile
  description: "Third stage of the fireworks."
  #the name of the item to load this projectile
  itemName: firework rocket
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:air'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

cannonball:
  #the type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 1
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.5
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 2
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: false
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 10
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 5
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: false

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #true it on or off
  enabled: false
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: true
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    #- 'PRIMED_TNT 1-3'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:
    - firework4

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: true
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: false
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BURST
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
      #white
      - 'FF0000'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: false

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'

#### Firework 4

general:
  #the name of the projectile displayed in game
  projectileName: fireworks
  #a short description of the projectile
  description: "Fourth stage of the fireworks."
  #the name of the item to load this projectile
  itemName: firework rocket
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:air'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....
  alternativeId:

cannonball:
  #the type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 1
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0.5
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 1.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 2
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  ##possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: false
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 0.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 10
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 5
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: false

#spawns additional delayed explosions around the explosion
clusterExplosion:
 #true it on or off
 enabled: false
 #explosion can also be in blocks and not only in air
 explosionInBlocks: false
 #how many explosions will be spawned
 amount: 10
 #after which time the explosion will be triggered [s]
 minDelay: 0.5
 #how long the explosion will last [s]
 maxDelay: 5.0
 #in which sphere radius this explosion will occur
 radius: 5.0
 #explosion power
 power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: false
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    - 'PRIMED_TNT 1-3'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: true
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: false
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BURST
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
      #white
      - 'FFFFFF'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FF0000'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: false

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```
#### TNT
```yaml
general:
  #the name of the projectile displayed in game
  projectileName: clusterbomb
  #a short description of the projectile
  description: "Spawn primed TNT on impact."
  #the name of the item to load this projectile
  itemName: TNT
  #the item which is associated with the projectile.
  #items can be assigned to many different projectiles which are used with different cannons
  #example: one cannon can be loaded with stone but will fire an armor piercing round, while a different cannon
  #can be loaded with stone and it will fire an explosive projectile (minimum is minecraft:material. Named items minecraft:material;displayName;lore1;lore2:....)
  #https://www.digminecraft.com/lists/item_id_list_pc.php
  loadingItem: 'minecraft:netherite_ingot'
  #some item create a block when placed e.g. redstone dust makes a wire if placed on ground. 
  #if you load the dust, type in the wire id and data, else there is a wire on the cannon.
  #minimum is id:data. Named items id:data:displayName:lore1:lore2:....
  alternativeId:

cannonball:
  #type of the projectile entity
  #Arrow, Egg, EnderPearl, Fireball, Fish, LargeFireball, SmallFireball, Snowball, ThrownExpBottle, ThrownPotion, WitherSkull
  entityType: snowball
  #set to true if you want to have a burning projectile
  isOnFire: false
  #the velocity of the projectile.
  velocity: 3
  #how many blocks the projectile will penetrate before it explodes. If it hits something impenetrable (e.g. obsidian) it will explode instantly.
  penetration: 1
  #whether the .projectile destroys blocks it penetrates. If false it will explode if it hits something impenetrable.
  doesPenetrationDamage: true
  #how many seconds after firing the projectile will detonate if it does not hit anything
  timefuse: 0
  #the delay in seconds between two fired cannonball in the automatic firing mode. Highest firing frequency is 20 shots per second - 0.05s
  automaticFiringDelay: 5.0
  #a cannon can fire several times with a single projectile - like a magazine in a automatic firearm
  automaticFiringMagazineSize: 1
  #how many projectiles are fired
  numberOfBullets: 1
  #the higher this is, the more inaccurate the projectile. This multiplies the "spreadOfCannon" property of the cannon it is fired from
  spreadMultiplier: 1.0
  #ignored the set number of blocks for sentries and will target entities behind walls
  sentryIgnoredBlocks: 0
  #different properties of the projectile. If you don't want any of these properties then just leave this all blank.
  #possible properties are: superbreaker, incendiary, human_cannonball, teleport, observer
  properties:
    #this property sets the impact area on fire. range is determined by the explosion power property
    - incendiary

smokeTrail:
  #the projectile has a smoke trail which makes it easier to spot
  enabled: true
  #distance between two smoke clouds
  distance: 10
  #material the smoke is made of
  material: 'minecraft:cobweb'
  #how long the smoke will stay in seconds
  duration: 5.0
  particles:
    # whether to use particles for the smoke trail instead of a block
    enabled: false
    # name of the particle to use - see https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Particle.html for a list
    type: SMOKE_NORMAL
    # how many particles to spawn
    count: 1
    # the x, y and z offset of the particles
    x_offset: 0
    y_offset: 0
    z_offset: 0
    # how fast the particle travels to its offset position
    speed: 1

explosion:
  #the explosion power of the cannonball when it hits; this number determines the explosions range in blocks.
  #for comparison, the explosion power of a creeper is 3. anything above 50 will cause lag on smaller servers
  explosionPower: 2.0
  #explosion power depends on velocity (see kinetic energy)
  explosionPowerDependsOnVelocity: false
  #whether the explosion will destroy blocks
  doesExplosionDamage: true
  #the explosion power is set to zero if the explosion is underwater (superbreaker will still do damage)
  doesUnderwaterExplosion: false
  #if the projectile hits the player additional damage is done. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  directHitDamage: 100
  #if the player is next to an explosion he will receive additional damage
  playerDamageRange: 5
  #the damage which the player receives when he is near an explosion. Damage is in half hearts and the player has 20 half hearts in vanilla minecraft.
  playerDamage: 5
  #the range of the potion effects specified below
  potionRange: 5
  #how long the effects will last. If the potion duration is <= 0 it will be disabled
  potionDuration: 7
  #how powerful the effect is, the higher this is the more powerful the effect. If set to 1 it has potion effect type II, if 0 potion effect type I
  potionAmplifier: 1
  #which potion effects are used. a list of effects supported by bukkit can be found here-
  #http://jd.bukkit.org/rb/apidocs/org/bukkit/potion/PotionEffectType.html
  potionEffects:
   - harm
   - slow
  #marks the impact with blocks (default: glowstone)
  impactIndicator: true

#spawns additional delayed explosions around the explosion
clusterExplosion:
  #turn it on or off
  enabled: true
  #explosion can also be in blocks and not only in air
  explosionInBlocks: false
  #how many explosions will be spawned
  amount: 10
  #after which time the explosion will be triggered [s]
  minDelay: 0.5
  #how long the explosion will last [s]
  maxDelay: 5.0
  #in which sphere radius this explosion will occur
  radius: 5.0
  #explosion power
  power: 4.0

#spawn blocks, entities or/and new projectiles on impact
spawnOnExplosion:
  #enable this feature
  enabled: true
  #the radius where blocks will be placed. If the radius is too small there might be no air gap to spawn a block.
  blockRadius: 2.0
  #the radius where entities will be placed. If the radius is too small there might be no air gap to spawn a block.
  entityRadius: 2.0
  #the velocity of blocks/entities are slinged away from the impact
  velocity: 0.5
  #the blocks which will be placed. does not seem to support more tha one block type at a time.
  #spawn an block with (minecraft:material minAmount-maxAmount)
  block:
    #this is a cobweb to slow the enemy
    #- 'minecraft:cobweb 1-3'
  #spawn entity with the name. (Formatting 'NAME min-max')
  #https://hub.spigotmc.org/javadocs/bukkit/org/bukkit/entity/EntityType.html
  entity:
    - 'PRIMED_TNT 1-3 {FUSE:100}'
  #spawns a new projectiles after the explosion of this projectile with the given name (file name)
  #spawning the same projectile more than once results in a endless loop
  #the number of spawned projectile depends on 'numberOfBullets' of the spawned projectile
  projectiles:

spawnFireworks:
  #if true fireworks will be spawned on projectile explosion
  enabled: false
  #if the firework flickers or not
  flicker: false
  #if the firework has a trail
  trail: true
  #effect type of the fireworks: BALL, BALL_LARGE, BURST, CREEPER, STAR,
  type: BALL
  #main colors (RGB in hex notation)
  #if there are no color, than there will be no fireworks
  colors:
    #red
    - 'FF0000'
    #white
    - 'FFFFFF'
  #fade colors in RGB hex notation
  fadeColors:
    #white
    - 'FFFFFF'

messages:
  #if this projectile can send a message of the impact location.
  hasImpactMessage: true

sounds:
  #You can enter new sounds in the following way 'NAME:VOLUME:PITCH'. Like 'IRON_GOLEM_WALK:1:0.5'
  #NAME: You can use minecraft sounds (block.anvil.hit), custom resource sound packs, or bukkit sound names (https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Sound.html)
  #VOLUME: How far you will hear this sound
  #PITCH: How fast it is played. (0.5-2)
  #USE 'none:1:1' to disable this sound

  #loading sound of projectile
  loading: 'ENTITY_IRON_GOLEM_ATTACK:5:0.5'
  #impact sound
  impact: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact sound if the area is protected by an plugin (ProjectileImpactEvent was cancelled)
  impactProtected: 'ENTITY_GENERIC_EXPLODE:10:0.5'
  #impact on water surface
  impactWater: 'ENTITY_GENERIC_SPLASH:10:0.3'
```