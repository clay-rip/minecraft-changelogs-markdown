# Minecraft 26.2 Snapshot 5

Boom!! 26.2 Snapshot 5 just exploded into the scene! This snapshot introduces erupting Geysers and a new explosive archetype for the Sulfur Cube!

Happy mining!

## New Features

-   New Sulfur Cube archetype: Explosive
-   Potent Sulfur can now form Geysers

### Sulfur Cube mob

-   With a block inside, it is now immune to explosions

**Sulfur Cube archetypes**

-   There is now a third special archetype:
    -   Explosive: similar properties to a Regular with a slightly higher air drag,
        -   Used when absorbing a TNT block
        -   Absorbed TNT can be primed by Redstone, fire sources (including a Dispenser with a Flint and Steel) or nearby explosions
        -   When primed by fire or Redstone, absorbed TNT uses a fuse time of 6 seconds
        -   When primed by an explosion, absorbed TNT uses a randomized fuse time between 0.75 and 3 seconds
        -   Sulfur Cubes with an absorbed, primed TNT block cannot be picked up with a Bucket
        -   Sulfur Cubes with an absorbed, primed TNT block cannot be damaged
        -   Absorbed, primed TNT blocks cannot be sheared out
        -   On explosion, no Small Sulfur Cubes are spawned

### Potent Sulfur

-   When placed above a Magma block and under 1-4 Water source blocks, it creates a Geyser
-   The Geyser will erupt at random intervals, shooting a plume of water particles upwards and applying an upward impulse to entities above it

## Changes

-   Tweaked various mobs hitbox, eye height, and rider positions

### Mob Spawning

-   Hoglins are now considered hostile and do not spawn on Peaceful difficutly

### Sounds

-   Added sounds for Geyser eruptions
-   Sulfur Spikes now have unique sound events

### Settings

-   Removed Touchscreen Mode

> **Developer's Note**: _Touch screen mode has been poorly implemented and not properly supported for a long time. We plan to deprecate this feature in this release. To provide your feedback on this topic, head over to [the feedback site](https://aka.ms/mctouchscreenjavafeedback)._

## Technical Changes

-   The Data Pack version is now 104.0
-   The Resource Pack version is now 86.2
-   A player's score will no longer be displayed in the player tab overlay if the player doesn't have the objective

### Minecraft Server Management Protocol 3.0.0

-   The management server now starts before the Minecraft server starts
    -   Most notably, this means the heartbeat will be sent while the world is loading and potentially upgrading
-   The `rpc.discover` and `notification/server/status` methods are now accessible before the dedicated server spins up
    -   The server will return an error when other methods are called during this time

## Data Pack Version 104.0

-   Entries in the `minecraft:sulfur_cube_archetype` registry have a new field:
    -   `explosion_fuse`: optional integer, if present, the Sulfur Cube of this archetype will explode with this fuse time when ignited
-   Added `geyser`, `geyser_poof`, `geyser_base`, and `geyser_plume` particles

### Commands

-   Team color arguments (used in `team modify [name] color` and `waypoint modify [name] color`) now accept only lowercase names with underscores
    -   I.e. only `dark_purple` is accepted and not `darkpurple` or `DarkPurple`
    -   Values now match color names in text components

**Changed `minecraft:nameplate_distance`**

-   Renamed to `minecraft:name_tag_distance`

### World Generation

-   Added `matching_biomes` world generation-type block predicate type which checks if the block position matches one of the specified biomes
    -   Format: object with fields:
        -   `biomes` - biome ID, list of biome IDs, or hash-prefixed biome tag: the biomes to match
-   `tree` feature configuration's `below_trunk_provider` block state provider no longer has a default value

**Configured Features**

**Changes to `minecraft:multiface_growth`**

-   Field `block` is now mandatory (defaulted to `minecraft:grow_lichen`)

**Density Functions**

**Added `minecraft:interval_select`**

Selects between a number of Density Functions based on an input Density Function and a set of threshold values. Format: object with fields:

-   `input` - Density Function, the value to be compared with any given `thresholds`
-   `thresholds` - non-empty list of floats, the threshold values to compare `input` with
    -   If `input < thresholds[i]`, the result of `functions[i]` will be selected
    -   If the input is greater than the last threshold value, the last function will be selected
    -   Must be one fewer `thresholds` than `functions`
-   `functions` - list of at least 2 Density Functions, the resulting functions to be selected from
    -   Must be one more element in `functions` than in `thresholds`

**Removed `minecraft:weird_scaled_sampler`**

-   This Density Function has been removed, with its functionality replaced by `interval_select`
-   When `rarity_value_mapper` was `type_1`, equivalent to:
    -   `interval_select` with thresholds `-0.75, -0.5, 0.5, 0.75`
    -   Selected functions follow: `abs(rarity * noise(x/rarity, y/rarity, z/rarity))`
        -   Corresponding rarity values: `0.5, 0.75, 1.0, 2.0, 3.0`
-   When `rarity_value_mapper` was `type_2`, equivalent to:
    -   `interval_select` with thresholds `-0.5, 0.0, 0.5`
    -   Selected functions follow: `abs(rarity * noise(x/rarity, y/rarity, z/rarity))`
        -   Corresponding rarity values: `0.75, 1.0, 1.5, 2.0`

### Tags

**Block Tags**

-   Added the following tags for blocks which some mobs are immune to. These have effect on dismounting, and valid surroundings of spawn placements for some mobs. They do not have an effect on pathfinding.
    -   `#fox_immune_to`
    -   `#polar_bear_immune_to`
    -   `#snow_golem_immune_to`
    -   `#stray_immune_to`
    -   `#wither_immune_to`
    -   `#wither_skeleton_immune_to`
    -   `#default_immune_to` - this tag is intentionally left empty

### Particles

**Added `minecraft:geyser_base`**

-   Spawns as a cloud on the base of an erupting Potent Sulfur block
-   Format: object with fields:
    -   `water_blocks` - positive integer, scales the particle size and its burst impulse
    -   `burst_impulse_base` - float, scales the initial burst impulse

**Added `minecraft:geyser_poof`**

-   Spawns as a cloud on the base of an erupting Potent Sulfur block
-   Format: object with fields:
    -   `water_blocks` - positive integer, scales the particle size and its burst impulse
    -   `burst_impulse_base` - float, scales the initial burst impulse

**Added `minecraft:geyser_plume`**

-   Spawns as an upwards stream above an erupting Potent Sulfur block
-   Format: object with fields:
    -   `water_blocks` - positive integer, scales the particle size and its burst impulse

**Added `minecraft:geyser`**

-   An emitter particle that spawns the `geyser_base`, `geyser_poof`, and `geyser_plume` particles above an erupting Potent Sulfur block
-   Format: object with fields:
    -   `water_blocks` - positive integer, scales the particle size and its burst impulse

### Game Test Environments

**Added `minecraft:difficulty`**

Sets the difficulty of the game test environment. Fields:

-   `difficulty`: The difficulty ID to set
    -   One of: `peaceful`, `easy`, `normal`, `hard`

## Resource Pack Version 86.2

### Sounds

-   Added sounds for Geyser eruptions:
    -   `block.potent_sulfur.geyser_eruption`
    -   `block.potent_sulfur.geyser_eruption_active`

### Particles

-   Added new Particle textures:
    -   `particle/noxious_gas_01.png`
    -   `particle/noxious_gas_02.png`
    -   `particle/noxious_gas_03.png`
    -   `particle/noxious_gas_04.png`
    -   `particle/noxious_gas_05.png`
    -   `particle/noxious_gas_06.png`
    -   `particle/noxious_gas_07.png`
    -   `particle/noxious_gas_08.png`
    -   `particle/geyser_base_01.png`
    -   `particle/geyser_base_02.png`
    -   `particle/geyser_base_03.png`
    -   `particle/geyser_base_04.png`
    -   `particle/geyser_base_05.png`
    -   `particle/geyser_base_06.png`
    -   `particle/geyser_base_07.png`
    -   `particle/geyser_base_08.png`
    -   `particle/geyser_plume_01.png`
    -   `particle/geyser_plume_02.png`
    -   `particle/geyser_plume_03.png`
    -   `particle/geyser_plume_04.png`
    -   `particle/geyser_plume_05.png`
    -   `particle/geyser_plume_06.png`
    -   `particle/geyser_plume_07.png`
    -   `particle/geyser_plume_08.png`
    -   `particle/geyser_poof_01.png`
    -   `particle/geyser_poof_02.png`
    -   `particle/geyser_poof_03.png`
    -   `particle/geyser_poof_04.png`
    -   `particle/geyser_poof_05.png`
    -   `particle/geyser_poof_06.png`
    -   `particle/geyser_poof_07.png`
    -   `particle/geyser_poof_08.png`

## Fixed bugs in 26.2 Snapshot 5

-   [MC-304862](https://bugs.mojang.com/browse/MC-304862) Activating a dispenser with a hostile mob spawn egg in Peaceful difficulty consumes the egg and plays a sound
-   [MC-306622](https://bugs.mojang.com/browse/MC-306622) The height of chicken jockeys is slightly off
-   [MC-306685](https://bugs.mojang.com/browse/MC-306685) The riding position on baby hoglins is too low
-   [MC-307012](https://bugs.mojang.com/browse/MC-307012) When a scoreboard objective is set to the `below_name` display mode, all named entities with no score display it with a score of 0
-   [MC-307125](https://bugs.mojang.com/browse/MC-307125) Target selectors with duplicate `team` arguments are parsed inconsistently depending on argument order
-   [MC-307194](https://bugs.mojang.com/browse/MC-307194) The discount given by fletchers for tipped arrow trades decreases the arrow cost instead of the emerald cost
-   [MC-307266](https://bugs.mojang.com/browse/MC-307266) Zombie villagers change biome type after being cured
-   [MC-307283](https://bugs.mojang.com/browse/MC-307283) Placing sulfur springs using /place does not update the affected blocks
-   [MC-307513](https://bugs.mojang.com/browse/MC-307513) Using /deop on multiple players shows the same player in all success messages
-   [MC-307623](https://bugs.mojang.com/browse/MC-307623) Chunk sections are sometimes invisible until they are updated
-   [MC-307689](https://bugs.mojang.com/browse/MC-307689) The player's arm swings when failing to use a spawn egg in Peaceful difficulty
-   [MC-307690](https://bugs.mojang.com/browse/MC-307690) The error message produced by /difficulty doesn't use the difficulty's translated name
-   [MC-307702](https://bugs.mojang.com/browse/MC-307702) Skeletons' AI breaks when picking up any item
-   [MC-307706](https://bugs.mojang.com/browse/MC-307706) The game inconsistently refers to name tags and name plates
-   [MC-307710](https://bugs.mojang.com/browse/MC-307710) Deoxidizing waxed copper blocks now takes priority over scraping off the wax
-   [MC-307754](https://bugs.mojang.com/browse/MC-307754) Monsters now spawn regardless of the "Spawn Monsters" game rule

---

# Minecraft 26.2 Snapshot 4

Today we thought we'd bring you a fourth snapshot for 26.2! With this release we have added in language support for two new languages and made some changes to the sulfur cube and the sulfur cave biome. Also in this release, our peaceful players can now spawn Hoglins, Piglins and Sulfur cubes!

Happy Mining!

## New Features

-   Added Swiss French language support to the game
-   Added Chuvash language support to the game

### Sulfur Cube mob

-   Naturally-spawned small Sulfur Cubes now have the correct size
-   The outer texture of the Sulfur Cube has been updated

### Sulfur Caves biome

-   Granite and Tuff blocks are now dispersed between Sulfur and Cinnabar blocks
-   The Sulfur Spike Clusters have been made slightly shorter, on average

## Changes

### Mob Spawning

-   Hoglins, Piglins and Sulfur Cubes now spawn on Peaceful difficulty

### Sounds

-   Added sounds for when using a bucket on a Sulfur Cube

## Technical Changes

-   The Data Pack version is now 103.0
-   The Resource Pack version is now 86.1

## Data Pack Version 103.0

### Attributes

**Added `minecraft:nameplate_distance`**

-   Controls how far away in blocks the nameplate of an entity is visible
-   The nameplate cannot be visible if the entity is not visible
-   Accepts values between `0.0` and `512.0`
-   Default value: `64.0`

**Added `minecraft:below_name_distance`**

-   Controls how far away in blocks the `below_name` scoreboard display is visible
-   The nameplate cannot be visible if the entity is not visible
-   Accepts values between `0.0` and `512.0`
-   Default value: `10.0`

### Predicates

**Entity Predicates**

-   Slime sub-predicate has been renamed from `minecraft:type_specific/slime` to `minecraft:type_specific/cube_mob`

## Resource Pack Version 86.1

-   The `minecraft:beds` atlas has been removed

### Telemetry

**New required events**

-   `graphics_capabilities`
    -   This is a new event that posts on startup, and informs us of the capabilities of the graphics device used to play the game
    -   Added new property: `backend_name`
        -   This will be `Vulkan` or `OpenGL`, and will help us understand which graphics api players are using
    -   Added new property: `backend_failure_reason`
        -   This will be a list of short error codes, for example `vulkan_device_version_too_low`, which will help us identify any issues with our targeted Vulkan requirements
    -   Added new property: `backend_failure_message`
        -   This will be a short and vague messages, such as `Failed to find the GLFW platform surface extensions`, which will help us narrow down issues if players are experiencing issues running with Vulkan
    -   Added new property: `backend_failure_missing_capabilities`
        -   This will be a list of missing capabilities from Vulkan, for example `VULKAN_CORE_1_2, VK_KHR_dynamic_rendering`, which will help us know which capabilities players would need in order to use Vulkan

## Fixed bugs in 26.2 Snapshot 4

-   [MC-186131](https://bugs.mojang.com/browse/MC-186131) Piglins and hoglins cannot spawn naturally on Peaceful difficulty
-   [MC-296343](https://bugs.mojang.com/browse/MC-296343) Using the mouse wheel to switch between cast fishing rods briefly displays the uncast texture in first-person
-   [MC-307002](https://bugs.mojang.com/browse/MC-307002) Using the `kill` command on one of the end crystals used to respawn the ender dragon no longer aborts the respawn sequence
-   [MC-307327](https://bugs.mojang.com/browse/MC-307327) VSync limits the framerate inconsistently in fullscreen with the Vulkan rendering backend on some Mac systems
-   [MC-307378](https://bugs.mojang.com/browse/MC-307378) The glowing effect is not visible with the Vulkan rendering backend on some graphics
-   [MC-307434](https://bugs.mojang.com/browse/MC-307434) Sulfur cubes cannot spawn naturally on Peaceful difficulty
-   [MC-307532](https://bugs.mojang.com/browse/MC-307532) Lava buckets now remain filled server-side when emptied into flowing water
-   [MC-307539](https://bugs.mojang.com/browse/MC-307539) The game crashes upon startup on some Mac systems
-   [MC-307545](https://bugs.mojang.com/browse/MC-307545) The "High Contrast" resource pack is listed as incompatible
-   [MC-307549](https://bugs.mojang.com/browse/MC-307549) `beds.png-atlas` still exists
-   [MC-307587](https://bugs.mojang.com/browse/MC-307587) Wet sponges are no longer removed from the inventory server-side when placed in the Nether
-   [MC-307624](https://bugs.mojang.com/browse/MC-307624) The cube mob entity sub-predicate is called `type_specific/slime` rather than `cube_mob`
-   [MC-307626](https://bugs.mojang.com/browse/MC-307626) The selection lists in the pack selection screen can extend outside the bounds of the game window, violating the Vulkan specification
-   [MC-307647](https://bugs.mojang.com/browse/MC-307647) Crash on startup with the Vulkan validation layer enabled — the `NORMAL` vertex attribute uses a format without guaranteed `VERTEX_BUFFER_BIT` support

---

# Minecraft 26.2 Snapshot 3

We are back again with a third snapshot for 26.2, today we are bringing you sulfur spikes to test out! These sharp blocks grow in sulfur caves, adding a colorful, pointy touch to your builds! But watch out - falling sulfur spikes sure pack a puncture!

Happy Mining!

## New Features

### Sulfur Spike

-   Is a new block that generates naturally on Sulfur blocks inside the sulfur caves biome
-   Forms a stalactite if placed on the ceiling or a stalagmite if placed on the floor
-   Can be combined to form longer stalactites & stalagmites
-   Stalactites and stalagmites merge if the tips are next to each other, unless you press shift while placing
-   Stalagmites will break if they're not attached to something below
-   Stalactites fall down if not attached to something above
-   Being hit by a falling stalactite hurts, and they are sharp!
-   Thrown Tridents break Sulfur Spike

## Changes

-   The Potent Sulfur block no longer crafts back into Sulfur blocks
-   Updated the textures for the following blocks:
    -   `Chiseled Cinnabar`
    -   `Chiseled Sulfur`
    -   `Cinnabar`
    -   `Cinnabar Bricks`
    -   `Polished Cinnabar`
    -   `Polished Sulfur`
    -   `Sulfur Bricks`

### Sulfur Cube mob

-   Can no longer be picked up by Boats

### Sounds

-   Updated sounds for Nautilus jets and Nautilus recovers

## Technical Changes

-   The Data Pack version is now 102.0
-   The Resource Pack version is now 86.0

## Data Pack Version 102.0

### Block Entity Data

-   The `minecraft:bed` block entity has been removed

### Predicates

**Entity Predicates**

Entity predicate format has changed from a structure with multiple optional fields to one similar to data component maps.

For example, previously `effects` was an optional field:

    {
        "effects": {...}
    }
    

In this version it has become a component-like sub-predicate entry:

    {
        "minecraft:effects": {...}
    }
    

The main functional changes are:

-   All keys in entity predicates are now identifiers
    -   Since identifiers can be written without namespace (default to `minecraft` namespace), existing field names are still valid
    -   Exception: field `type` has been renamed to `minecraft:entity_type`
-   Unrecognized sub-predicate components are now rejected (previously unknown fields were ignored)

Existing type-specific sub-predicates have been renamed and moved to top-level.

-   `minecraft:lightning` to `minecraft:type_specific/lightning`
-   `minecraft:fishing_hook` to `minecraft:type_specific/fishing_hook`
-   `minecraft:player` to `minecraft:type_specific/player`
-   `minecraft:raider` to `minecraft:type_specific/raider`
-   `minecraft:sheep` to `minecraft:type_specific/sheep`
-   `minecraft:slime` to `minecraft:cube_mob` as it now includes Sulfur Cubes in addition to Slimes and Magma Cubes

For example:

    {
      "type_specific": {
        "type": "minecraft:player",
        "looking_at": {
          "type": "minecraft:ender_dragon"
        }
      }
    }
    

becomes

    {
      "minecraft:type_specific/player": {
        "looking_at": {
          "minecraft:type": "minecraft:ender_dragon"
        }
      }
    }
    

**Added `minecraft:entity_tags` entity sub-predicate**

This predicate matches entity tags (i.e. ones set with the `/tag` command).

Fields:

-   `any_of` - optional list of strings, if present the matched entity must have at least one of the listed tags
-   `all_of` - optional list of strings, if present the matched entity must have all the listed tags
-   `none_of` - optional list of strings, if present the matched entity must have none of the listed tags

### World Generation

**Overworld Features**

-   Adjusted Feature Type `lake`
    -   Added field `can_place_feature` - Block Predicate, describes which blocks this feature can be placed on
    -   Added field `can_replace_with_air_or_fluid` - Block Predicate, describes which blocks this feature can replace with air or the provided `fluid` block
    -   Added field `can_replace_with_barrier` - Block Predicate, describes which blocks this feature can replace with the provided `barrier` block

### Tags

**Block Tags**

-   Added `#speleothems` for blocks which are speleothems like Pointed Dripstone and Sulfur Spike

## Resource Pack Version 86.0

### Block Sprites

-   Added new Block textures:
    -   `block/sulfur_spike_down_base.png`
    -   `block/sulfur_spike_down_frustum.png`
    -   `block/sulfur_spike_down_middle.png`
    -   `block/sulfur_spike_down_tip.png`
    -   `block/sulfur_spike_down_tip_merge.png`
    -   `block/sulfur_spike_up_base.png`
    -   `block/sulfur_spike_up_frustum.png`
    -   `block/sulfur_spike_up_middle.png`
    -   `block/sulfur_spike_up_tip.png`
    -   `block/sulfur_spike_up_tip_merge.png`
-   Beds now use block models and textures, replacing `<color>` with the respective bed's color's name
    -   `block/bed_down.png`
    -   `block/bed_head_north.png`
    -   `block/<color>_bed_foot_east.png`
    -   `block/<color>_bed_foot_south.png`
    -   `block/<color>_bed_foot_up.png`
    -   `block/<color>_bed_foot_west.png`
    -   `block/<color>_bed_head_east.png`
    -   `block/<color>_bed_head_up.png`
    -   `block/<color>_bed_head_west.png`

### Item Sprites

-   Added new Item sprites:
    -   `item/sulfur_spike.png`

### Item Models

-   The `minecraft:bed` special model type has been removed

## Fixed bugs in 26.2 Snapshot 3

-   [MC-229057](https://bugs.mojang.com/browse/MC-229057) Picking up an axolotl with a lead attached destroys the lead
-   [MC-277744](https://bugs.mojang.com/browse/MC-277744) Blocks with emissive textures don't emit much light when held by endermen
-   [MC-302496](https://bugs.mojang.com/browse/MC-302496) Glowing dragon fireballs no longer show the glowing outline
-   [MC-307177](https://bugs.mojang.com/browse/MC-307177) Enabling JFR profiling causes the client to crash on startup
-   [MC-307227](https://bugs.mojang.com/browse/MC-307227) Using an empty `Offers` NBT tag to disable trades doesn't work after a relog/data merge
-   [MC-307289](https://bugs.mojang.com/browse/MC-307289) Polished sulfur is named "Polished Sulfur Block", which is inconsistent with all other polished stone blocks
-   [MC-307291](https://bugs.mojang.com/browse/MC-307291) The game crashes when an entity with the `friction_modifier` attribute set to 2.5 moves
-   [MC-307298](https://bugs.mojang.com/browse/MC-307298) Sulfur cubes with blocks inside them produce footstep sounds when moving across the ground
-   [MC-307300](https://bugs.mojang.com/browse/MC-307300) Magma blocks held by sulfur cubes are not emissive
-   [MC-307315](https://bugs.mojang.com/browse/MC-307315) Frogs try to eat large magma cubes now
-   [MC-307316](https://bugs.mojang.com/browse/MC-307316) Magma cubes no longer drop magma cream
-   [MC-307340](https://bugs.mojang.com/browse/MC-307340) The bottom face of slimes' outer layer z-fights with the ground
-   [MC-307347](https://bugs.mojang.com/browse/MC-307347) Releasing a sulfur cube from a bucket and killing it does not cause it to drop its held block
-   [MC-307357](https://bugs.mojang.com/browse/MC-307357) Sulfur cubes don't emit light when holding a glowing block
-   [MC-307371](https://bugs.mojang.com/browse/MC-307371) The `#sulfur_cube_archetype/fast_flat` item tag contains `pumpkin` twice
-   [MC-307405](https://bugs.mojang.com/browse/MC-307405) When picking up a leashed sulfur cube with a bucket, the lead disappears
-   [MC-307420](https://bugs.mojang.com/browse/MC-307420) The game now renders fluid faces that should not be rendered
-   [MC-307473](https://bugs.mojang.com/browse/MC-307473) The block breaking texture on bamboo stalks is now always displayed centered
-   [MC-307483](https://bugs.mojang.com/browse/MC-307483) Emptying a sulfur cube bucket underwater doesn't place the sulfur cube at the targeted block

---

# Minecraft 26.1.2 Release Candidate 1

Today we are shipping the first release candidate for 26.1.2, fixing a couple of critical issues found in the release. If no further issues are encountered, 26.1.2 will be released tomorrow with no additional changes.

Happy mining!

---

