---
title: Robbing
---
# Introduction
The robbing plugin allows players to pickpocket each other, handcuff each other, and make safes that can be cracked with lockpicks. The safes feature is not recommended, as they can be broken into without removing [[TWClaim]] protections.

# Pickpocketing
If you stand behind a player and sneak + right-click them, you will open up their inventory menu, allowing you to steal items. You cannot steal weapons  or armor. The pickpocketing menu will be closed if the pickpocketed player moves far enough away from you or punches you. There is a pickpocketing cooldown.

# Handcuffing
The handcuffs can be placed on players, which forces them to follow you. A handcuffed player can periodically attempt to escape the handcuffs.
![[9197492fecc7864fa4ec34733bbf9aac08a2b331 1.png]]
# Lockpick **CURRENTLY USELESS**
The lockpick is used for breaking into safes. If you fail to pick the lock too many times, your lockpick will break. Safes can only be made with commands, and there are currently no safes on the server, meaning this item **CURRENTLY HAS NO USE**.
![[814933d2980fb24bef24af83b22e116756d0236d.png]]
# Configuration
```yaml
# Robbing dev by FrahHS
# Check documentation on the official website: https://www.robbingrp.com/
# Spigot page: https://www.spigotmc.org/resources/robbing-%E2%AD%95-custom-items-%E2%AD%90-robbery-rp-experience.105443/
# If you need help or have any problem with the plugin join my discord: https://discord.gg/Hh9zMQnWvW
#
# Have fun with Robbing :D

general:
  # send on join message to operators if new version of the plugin will be available
  update_checker: true
  # actual supported languages: en, it
  # You can contribute to the translation of the texts here: https://www.robbingrp.com/
  language: en
  prefix: §3[§6Robbing§3] §f

robbing:
  enabled: true
  # enable alert to send to the robbed target, write {thief} to use thief Display Name
  alert: true
  # down here list of all items not stealable,
  # only names, no id
  denied_items:
  - WOODEN_SWORD
  - STONE_SWORD
  - IRON_SWORD
  - GOLD_SWORD
  - DIAMOND_SWORD
  - NETHERITE_SWORD
  - WOODEN_PICKAXE
  - STONE_PICKAXE
  - IRON_PICKAXE
  - GOLD_PICKAXE
  - DIAMOND_PICKAXE
  - NETHERITE_PICKAXE
  - WOODEN_SHOVEL
  - STONE_SHOVEL
  - IRON_SHOVEL
  - GOLD_SHOVEL
  - DIAMOND_SHOVEL
  - NETHERITE_SHOVEL
  - WOODEN_AXE
  - STONE_AXE
  - IRON_AXE
  - GOLD_AXE
  - DIAMOND_AXE
  - NETHERITE_AXE
  - WOODEN_HOE
  - STONE_HOE
  - IRON_HOE
  - GOLD_HOE
  - DIAMOND_HOE
  - NETHERITE_HOE
  - TRIDENT
  - SHIELD
  - LEATHER_HELMET
  - LEATHER_CHESTPLATE
  - LEATHER_LEGGINGS
  - LEATHER_BOOTS
  - CHAINMAIL_HELMET
  - CHAINMAIL_CHESTPLATE
  - CHAINMAIL_LEGGINGS
  - CHAINMAIL_BOOTS
  - IRON_HELMET
  - IRON_CHESTPLATE
  - IRON_LEGGINGS
  - IRON_BOOTS
  - GOLD_HELMET
  - GOLD_CHESTPLATE
  - GOLD_LEGGINGS
  - GOLD_BOOTS
  - DIAMOND_HELMET
  - DIAMOND_CHESTPLATE
  - DIAMOND_LEGGINGS
  - DIAMOND_BOOTS
  - NETHERITE_HELMET
  - NETHERITE_CHESTPLATE
  - NETHERITE_LEGGINGS
  - NETHERITE_BOOTS
  - TURTLE_HELMET
  - BOW
  - CROSSBOW
  whitelist_enabled: false
  whitelist_items:
  - GOLD_INGOT
  # max distance in block during robbing after that target inventory close
  max_distance: 5
  # cooldown setting (put timeout to 0 to disable)
  steal_cooldown: 120
  # sneaky right-click to steal if enabled, just right click if disabled
  sneak_to_steal: true
  # after a steal target will be blinded
  blindness_after_robbing: false
  # blindness duration in seconds (in enabled)
  blindness_duration: 5
  NPC_robbing: false
  # slowdown a thief shift left-clicking on him while he is robbing you,
  caught_robber:
    enabled: true
    slow_power: 5
    # how much time get slowed (in seconds)
    time: 20

handcuffing:
  enabled: true
  # enable right click handcuffed player to make he follow you
  following: true
  # put a cooldown to use handcuffs (in seconds)
  cooldown: 5
  enable_crafting: false
  # make possible escape from handcuffing
  try_escape:
    enabled: true
    # delay handcuffing after clicking (in seconds).
    delayed_handcuffing: 5
    # min distance to escape handcuffing
    distance: 3
  # permitted commands while handcuffed
  permitted_commands:
  - login
  - register
lockpick:
  enable_crafting: true

# Emergency call
# when a player use /911 every other players with robbing.emergency.alert will receive a notification
emergencycall:
  enabled: true
  message: '{player} called 911 from {coordinates}, for: {reason}.'
  # cooldown for /911 (in seconds), put 0 to disable
  cooldown: 10
```