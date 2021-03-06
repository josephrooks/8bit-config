# 8bit-config
This repository contains most of the configuration files for the 8bit Minecraft server. (Don't bother looking for the seed; I'm not that dumb.)

I try to avoid changing vanilla gameplay where possible, but some cases (like villager AI or huge quanities of mobs in a small space) are too detrimental to performance to leave them as-is.

Below, I'm working on summarizing most of the settings players will need to know about, especially the ones that significantly affect vanilla behavior. Right now it's broken up into two main sections:

- Server Configuration (Paper plus all of the settings it inherits from Spigot, Bukkit, and Vanilla)
- Plugin Configuration (just the plugin-related changes that seriously affect gameplay mechanics)

#### To Do
- Finish gameplay-changing plugin summaries
- Move all of this to the Wiki, probably
- Create separate Wiki pages for user & mod guides to /modreq

---

# Server Configuration

8bit runs on [Paper](http://papermc.io), a high-performance fork of Spigot, which is itself a fork of Bukkit, which is built by reverse-engineering Mojang's Vanilla server. Each layer includes some additional optimizations and configuration options.

---

## Vanilla
**tl;dr:** Nothing worth noting here. Located in ```server.properties``` and inherited by Paper.

---

## Bukkit
**tl;dr:** Some mob spawning changes. Located in ```bukkit.yml``` and inherited by Paper.

#### Spawn Limits
**tl;dr:** This plus ```per-player-mob-spawning``` in ```paper.yml``` spreads mobs evenly to each player.
```
spawn-limits:
  water-ambient: 5
  monsters: 25
  animals: 5
  water-animals: 5
  ambient: 3
```
The only ones that will matter to most people are ```monsters```, and maybe ```water-animals``` for people with squid farms. In Vanilla, the hostile mob cap raises by about 70 for every player online, but Mojang's method doesn't guarantee even distribution of them. If two players are online and one is flying high or in a well-lit area, the other might get all 140 mobs concentrated around them. While great for hostile mob farms, it's not great for other gameplay or for performance.

#### Ticks Per Spawn
**tl;dr:** How often the game tops off empty mob slots. Attempts slightly less frequently than in Vanilla.
```
ticks-per-spawn:
  monster-spawns: 2
```
In Vanilla, the game tries to fill empty slots in the hostile mobcap (70 monsters times the number of players in vanilla; 25 monsters per player on 8bit) every 1 gametick, or every 1/20th of a second. I've doubled that to every 2 gameticks instead, slightly spacing out attempts to fill up the mobcap for a moderate performance increase. Most visibly noticeable at the Ender Ender or gold farms.

---

## Spigot
**tl;dr:** Settings Spigot adds to the game, and where the actual optimizations begin. Located in ```spigot.yml``` and inherited by Paper.

TBD

---

## Paper
**tl;dr:** The settings Paper adds on top of Spigot. Located in ```paper.yml```.

TBD

---

# Plugin Configuration

This list is incomplete, but only plugins with settings that substantially change gameplay mechanics will be summarized.

---

## MobLimiter
**tl;dr:** Deals with entity overload, especially passive mob "parking lots." Located in ```/plugins/Moblimiter/config.yml```.

MobLimiter prevents animal breeding once you reach a certain number of animals within a 3-chunk radius. It also removes mobs (passive and hostile) above a certain number on chunk unload, and speeds up the breeding and growth process to make up for it to players who are actively farming animals. MobLimiter should leave 4 animals to start breeding with next time. Tamed animals, villagers, nametagged mobs, and some other special cases are never removed automatically, and each color of sheep is treated as a separate mob.

**Plugin Config To-Do**
- EntityControl
- EntityTrackerFixer
- InventoryRollback
- NerdSpawn
- Sleep-Most
- ViaVersion
- VillagerOptimiser
- WorldBorder
- WorldGuard
