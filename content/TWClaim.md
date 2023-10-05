---
title: "TWClaim: How to Claim Land"
---
## Intro

TWClaim is the plugin that allows players to form groups and protect land against enemies. It is a simple, flexible system that works in a way you have probably never seen before.

## Quick Info

Tutorial Video: This video showcases all of the commands and how to use them to claim land and manage your tribe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/elI8LY0Fu6Y?si=wH7tNhI3Fihct0IK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

Config: This should answer most questions not answered by the video, such as "what are the reinforcement and fuel materials?".
```yaml
# Welcome to the TWClaim Config!
# List of materials that can be used for reinforcement and how many reinforcement points they give
reinforcements:
  - stone: 100
  - coal: 150
  - iron_ingot: 250
  - diamond: 500

# Reinforcement value subtracted when a block is blown up
explosion-damage: 10
fire-damage: 5

# Bastions consume fuel to work. Set the fuel types and values here.
bastion-fuel:
  - charcoal: 100
  - coal: 100
  - blaze_powder: 1000
  - nether_star: 10000

# The rate at which bastions consume fuel without any upgrades
base-consumption: 10
# The amount of time (minutes) between fuel consumptions
base-consumption-period: 20

# Range of Bastion
bastion-range: 30

# Costs for bastion upgrades
anti-flight:
  - diamond: 10
  - fuel consumption when active: 10

anti-teleport:
  - diamond: 10
  - fuel consumption when active: 10

range:
  level-1:
    - diamond: 10
    - fuel consumption: 10
  level-2:
    - diamond: 20
    - fuel consumption: 20
  level-3:
    - diamond: 30
    - fuel consumption: 30

surveillance:
  - diamond: 10
  - fuel consumption when active: 10
  - fuel per person spied on: 1

exp-storage:
  - diamond: 10
  - fuel consumption when active: 10
  - fuel per 100 points: 1

# The min reinforcement percentage that reinforcement mats can be recovered when someone with perms breaks the block
recover-min: 80

# The radius around the player that the claims map will be generated
map-radius: 4

# The limit of blocks someone can select at once with the claim command
claim-limit: 1000
```
