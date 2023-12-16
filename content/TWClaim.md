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

## Protecting Buildings
This section covers how to protect your builds (or anything you don't want broken). There are three ways of going about this. Each method has the same resource cost and the same protection applied. The one you use is a matter of preference/convenience. To leave the protection mode, simply type the command again to toggle off. 

### Reinforcing
Reinforcing is for when you want to protect blocks that have already been placed. Do `/tribe reinforce [tribe name]` to enter reinforcing mode. You can also do `/tribe reinforce` to reinforce to your private group, which only you have access to. This personal claiming mode works with the other commands too.

Once you are in reinforcing mode, hold the [[TWClaim#Config:|reinforcement material]] in your hand and right click the block you want to reinforce. If you want to claim an area of blocks, you can hold down right click while looking at each block you want to reinforce. If you try to reinforce a block that is already protected, you will be notified in chat, and you will keep the reinforcement material.

### Fortifying
Fortifying lets you protect blocks as you place them, which can be useful if you do not want to worry about whether you have protected what you have built. Simply hold the [[TWClaim#Config:|reinforcement material]] in your inventory and do `/tribe fortify [tribe name]` to enter fortifying mode. Personal claiming: `/tribe fortify`

Once you are in fortifying mode, place the blocks you want, and the materials for protecting them will be taken out of your inventory automatically. If you run out of materials to protect your blocks, you will be unable to place more blocks and be notified in chat. 

### Claiming
Claiming allows you to claim a volume of blocks that has already been placed, including air blocks. This is the only claiming method which allows you to claim air blocks. Do `/tribe claim [tribe name]`. Personal: `/tribe claim`.

Once you are in claiming mode, you will need to select the corners of the volume of blocks you want to protect. Left click a block to mark it as the first corner, and right click the second block to mark it as the second corner. You will receive messages in chat telling you the coordinates of the blocks you picked for the corners. If you selected the wrong block, just left or right click again to reselect the corner.

Once you are ready to protect the blocks, do `/tribe claim confirm`. If you have enough [[TWClaim#Config:|reinforcement materials]] in your inventory to protect the whole volume, they will be removed from your inventory, and the whole volume will be protected immediately. If you do not have enough to claim the whole volume, the claim will fail, and you will receive a chat message explaining that you do not have enough materials.

#### Multiple Material Claiming
There may be a rare case where you do not have enough of one type of material to claim the whole volume, but you do have enough of several types to claim the volume. However, using materials of different strengths to reinforce a volume would lead to inconsistencies in the protection of the blocks. If this situation happens, you will be asked to confirm that you want to claim the volume with multiple materials. Click the green confirm text in the message to confirm.

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
