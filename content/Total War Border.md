---
title: Total War Border
---

# Explanation
Total War Border (or TWB) is a custom plugin designed to keep players within the earth map. Players are restricted to the earth map boundaries, which can be estimated by looking at the [[Dynmap]] or by looking at the config below.

The border is currently set to block players from moving past the north and south borders by teleporting them backwards 10 blocks. The east and west borders will teleport you across the map, and they are compatible with whatever you are riding and [[Movecraft]]. The north and south border are also compatible with [[Movecraft]], which will just stop moving when they hit the border.

# Config
```yaml
# Welcome to the TWB config
# Mode
# teleport - teleports player to other side of map. Currently, only works east and west
# because this plugin is designed for an earth map
# block - blocks players from crossing border
mode: teleport

corner-one:
  x: 30700
  z: 16000
corner-two:
  x: -1000
  z: -1000
```