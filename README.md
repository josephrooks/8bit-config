# 8bit-config
This repository contains most of the configuration files for the 8bit Minecraft server.

I try to avoid changing vanilla gameplay where possible, but some cases (like villager AI or huge quanities of mobs in a small space) are too detrimental to performance to leave them as-is.

Below, I'm working on summarizing most of the settings players will need to know about, especially the ones that significantly affect vanilla behavior. Right now it's broken up into two main sections:

- Server Configuration (Paper plus all of the settings it inherits from Spigot, Bukkit, and Vanilla)
- Plugin Configuration (just the plugin-related changes that seriously affect gameplay mechanics)

# Server Configuration

## Vanilla settings
Inherited by Paper. Located in ```server.properties```.

Nothing particularly worth noting here.

## Bukkit settings
Inherited by Paper. Located in ```bukkit.yml```.

#### Spawn Limits
tl;dr: This plus ```per-player-mob-spawning``` (in ```paper.yml```) guarantees each player gets their fair share of mobs without getting an overwhelming number of them.
```
spawn-limits:
  water-ambient: 5
  monsters: 25
  animals: 5
  water-animals: 5
  ambient: 3
```
The only ones that will matter to most people are ```monsters```, and ```water animals``` for people with squid farms. In Vanilla, the hostile mob cap raises by about 70 for every player online, but Mojang's method doesn't guarantee even distribution of them. If two players are online and one is flying high or in a well-lit area, the other might get all 140 mobs concentrated around them. While great for hostile mob farms, it's not great for other gameplay or for performance.

#### Spawn Frequency
tl;dr: How often mobs spawn. Slightly more spaced out. Minimal effect on gameplay.
```
ticks-per-spawn:
  monster-spawns: 2
```
In Vanilla, the game tries to fill empty slots in the hostile mobcap (70 monsters times the number of players in vanilla; 25 monsters per player on 8bit) every 1 gametick, or every 1/20th of a second. I've doubled that to every 2 gameticks instead, slightly spacing out attempts to fill up the mobcap for a moderate performance increase. Most noticeable at the Ender Ender or gold farms.

## Spigot settings
Settings native to Spigot. Inherited by Paper. Located in ```spigot.yml```.

TBD

## Paper
Settings native to Paper, which is a fork that builds on top of Spigot. Located in ```paper.yml```.

TBD

---

#Plugin Configuration

## MobLimiter
Used to deal with entity "parking lots." Located in ```/plugins/Moblimiter/config.yml```.

TBD