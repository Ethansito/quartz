---
title: "TWClaim: How to Claim Land"
---
## Intro

TWClaim is the plugin that allows players to form groups and protect land against enemies. It is a simple, flexible system that works in a way you have probably never seen before.

## Quick Info

Tutorial Video: This video showcases all of the commands and how to use them to claim land and manage your tribe.

<iframe width="560" height="315" src="https://www.youtube.com/embed/elI8LY0Fu6Y?si=wH7tNhI3Fihct0IK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>
## Important Info Not In The Video

### Bastion
While reinforcing, fortifying, and claiming all protect blocks from being broken by other players, the bastion protects the land from being built on by other players. Additionally, upgrades can be purchased for the bastion that improve its defensive capabilities and utility. 

The bastion requires fuel (see config for fuel types and values) and provides no protection when unfueled. Active upgrades cause the bastion to burn through fuel quicker. Purchased upgrades can be toggled off to reduce fuel consumption.

Before a bastion can be used, it must be reinforced, fortified, or claimed to determine ownership.

![[Pasted image 20231204231812.png]]

### Range Extender
Replacing the range upgrade on the bastion, the range extender allows you to project a bastion's influence in a 30 block radius around the extender. There is no distance minimum or maximum, so the extender can be used to influence areas not directly adjacent to your bastion. 

Area of effect upgrades on the bastion, such as anti-flight, are transmitted through the extenders. Every range extender connected to a bastion consumes 10 extra fuel per fuel consumption period (check config). Upgrade costs do not increase per bastion.

Before a range extender can be used, it must be reinforced, fortified, or claimed to determine ownership.

To assign a bastion to a range extender, right click the range extender to open up a selection menu. You will be able to select any bastion that belongs to you or any bastion that belongs to a tribe that gives you bastion permissions.

![[Pasted image 20231204231848.png]]

## Config: 
This should answer most questions not answered by the video, such as "what are the reinforcement and fuel materials?".
```yaml
# Welcome to the TWClaim Config!
# List of materials that can be used for reinforcement and how many reinforcement points they give
reinforcements:
  - stone: 200
  - coal: 300
  - iron_ingot: 500
  - diamond: 1000

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
