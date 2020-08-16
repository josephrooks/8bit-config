# 8bit-config
This repository contains most of the configuration files for the 8bit Minecraft server.

I try to avoid changing vanilla gameplay where possible, but some cases (like villager AI or huge quanities of mobs in a small space) are too detrimental to performance to leave them as-is.

Below, I'm working on summarizing most of the settings players will need to know about, especially the ones that significantly affect vanilla behavior. Right now it's broken up into two main sections:

- Server Configuration (Paper plus all of the settings it inherits from Spigot, Bukkit, and Vanilla)
- Plugin Configuration (just the plugin-related changes that seriously affect gameplay mechanics)

# Server Configuration

## Vanilla settings
```server.properties```

Nothing particularly worth noting here.

## Bukkit settings
```bukkit.yml```

#### Spawn Limits
```
spawn-limits:
  water-ambient: 5
  monsters: 25
  animals: 5
  water-animals: 5
  ambient: 3
```
How many mobs of each type can spawn around each player. The only ones that will matter to most people are ```monsters```, and ```water animals``` for people with squid farms.

In Vanilla, the hostile mob cap raises by about 70 for every player online, but Mojang's method doesn't guarantee even distribution of them. If two players are online and one is flying high or in a well-lit area, the other might get all 140 mobs concentrated around them.

Great for farms, not great for other gameplay or for performance. To address both, the numbers in this setting are turned down, and then ```per-player-mob-spawning``` is turned on in ```paper.yml```. This guarantees that each player can have up to 25 mobs spawned around them.

#### Spawn Frequency

```
ticks-per-spawn:
  monster-spawns: 2
```
In Vanilla, the game tries to fill the hostile mobcap to the maximum (```70 monsters * number of players``` in vanilla, ```25 monsters per player``` on 8bit) every 1 gametick, or every 1/20th of a second. I've doubled that to every 2 gameticks instead. This doesn't slow farms down, so much as space the spawns out a little bit more. Most noticeable at a farm like the Ender Ender.

## spigot.yml

TBD

## Paper
```paper.yml```

TBD

---

#Plugin Configuration

## MobLimiter
```/plugins/Moblimiter/config.yml```

TBD