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

# Minecraft 26.2 Snapshot 1

We are back in the shipping room once more with a jam-packed snapshot Tuesday!

Test the first features from our next drop, Chaos Cubed! Scour the Overworld for sulfur springs and then dig down to discover what lies below. Meet the sulfur cube – a curious new mob with a transformative appetite for blocks. Experiment by feeding it different blocks and test how the sulfur cube reacts, explore its home in the sulfur caves, mine for new cinnabar and sulfur blocks, and more.

And that's not all! With today's release we are also bringing Vulkan support into snapshot testing. This is a major step towards bringing Vibrant Visuals to Java Edition, as previously mentioned in this article: [Another step towards Vibrant Visuals](https://www.minecraft.net/en-us/article/another-step-towards-vibrant-visuals-for-java-edition). Players will be able to toggle between OpenGL and Vulkan during the testing period, and we will stay in the testing period until we're confident that the Vulkan implementation is stable, performant and ready.

The default option for this snapshot will be to use Vulkan if supported, but this may change in the future as we receive more feedback.

Happy mining!

## New Features

-   Added support for rendering the game through Vulkan
-   Added new option "Graphics API" in Video Settings

### Sulfur Cube mob

-   Added the Sulfur Cube mob
-   Spawns in the new Sulfur caves biome
-   When a Player interacts with it while holding a block, the Sulfur Cube will absorb the block and disable its AI
-   With a block inside, a Player can also interact with the Sulfur Cube while holding Shears to shear the block. This enables its AI
-   The Sulfur Cube will follow a Player holding a block it can absorb
-   The Sulfur Cube can also look for block items nearby and move towards them to absorb them
-   When killed, the Sulfur Cube splits into two smaller Sulfur Cubes
-   The small Sulfur Cubes can be tempted and fed with Slime Balls to grow them into large Sulfur Cubes
-   With a block inside, the Sulfur Cube will not take any fall or Player damage and will become a physical object that players can interact with by punching and pushing
-   With a block inside, it will assume one of the archetypes (listed below) and change its physical properties to match the block it absorbs
-   A large Sulfur Cube can be picked up using an empty bucket
-   Dispensers can now equip and swap blocks inside a Sulfur Cube, as well as shear it with Shears to remove the block it is holding
-   Dispensers can spawn a Sulfur Cube from a Bucket of Sulfur Cube.

**Sulfur Cube archetypes**

-   Each archetype is characterized by the speed of the ball when hit, how bouncy it is when colliding with blocks and collidable entities, as well as its ground friction, air drag and if it floats in liquids
-   There are the following archetypes:
    -   Regular: medium speed, medium bounciness, medium ground friction and low air drag
        -   It is buoyant
        -   Used when absorbing stone and mineral blocks
    -   Bouncy: fast speed, high bounciness, medium ground friction and low air drag
        -   It is buoyant
        -   Used when absorbing wooden blocks
    -   Slow Flat: slow speed, low bounciness, medium ground friction and medium air drag
        -   Used when absorbing metal blocks
    -   Fast Flat: fast speed, low bounciness, medium ground friction and low air drag
        -   Used when absorbing organic blocks
    -   Light: slow speed, high bounciness, medium ground friction and high air drag
        -   It is buoyant
        -   Used when absorbing all wool blocks
    -   Fast Sliding: fast speed, no bounciness, low ground friction and low air drag
        -   Used when absorbing icy blocks
    -   Slow Sliding: slow speed, no bounciness, low ground friction and low air drag
        -   Used when absorbing shroom blocks
-   There are also two special archetypes:
    -   High Resistance: very slow, low drag with low bounce with high friction
        -   Used when absorbing Soul Sand and Soul Soil
    -   Sticky: same properties as a golf ball, but sticks with extremely high ground friction and no bounce to simulate stickiness
        -   Used when absorbing Honeycomb Block

### Cinnabar and Sulfur block sets

-   Added Cinnabar and Sulfur stone block sets
-   Each of them has the Polished and the Bricks variants
-   Each variant has its Slabs, Stairs and Walls blocks
-   Added Chiseled Cinnabar and Chiseled Sulfur blocks

### Sulfur caves biome

-   Added sulfur caves underground biome
-   Now generate naturally underground and inside hills or mountains
-   The sulfur caves biome has bands of sulfur and cinnabar
-   Spawns the new Sulfur Cube mob as well as Cave Spiders
-   Generates with Sulfur Pools which contain Potent Sulfur

### Potent Sulfur

-   Is a new block that generates naturally in water pools inside the sulfur caves biome
-   Produces bubbles which rise up to 4 water source blocks above it
-   When placed underneath up to 4 water source blocks, it generates a cloud of nausea-causing gas on the water surface
    -   This cloud spreads across adjacent water with a maximum radius of 3 blocks
-   Can be crafted from 9 Sulfur blocks
-   The Potent Sulfur Block can be crafted into 4 Sulfur Blocks

### Sulfur Spring

-   Is a new feature which generates naturally above the sulfur cave biome
-   Consists of Sulfur, Potent Sulfur and Magma Blocks
-   Sulfur Springs come in 4 different size variants:
    -   Small
    -   Medium
    -   Large
    -   Extra Large

### Vulkan Support

-   As [previously announced](https://www.minecraft.net/article/another-step-towards-vibrant-visuals-for-java-edition), we intend to switch the game from OpenGL to Vulkan
-   Vulkan is not supported by older hardware or drivers - OpenGL will be used as a fallback on those cases
    -   The current requirement is Vulkan 1.2 with dynamic rendering and push descriptors, but this requirement may increase or decrease over time
-   This is currently an experimental rendering backend, and may not be as performant or stable. Please report any bugs you find with it to [our bug tracker](https://bugs.mojang.com)!
-   Under Vulkan, we will prefer your **dedicated graphics card** over any integrated graphics, which is a change from OpenGL
-   You can see which backend is being used in your F3 debug overlay (in the `system_specs` section)
-   On MacOS, we use MoltenVK to translate Vulkan to Metal

### "Graphics API" Video Setting

-   This is a new option available in the "Video Settings"
-   There are three values: **Default**, **Prefer Vulkan** and **Prefer OpenGL**
-   "Default" may be changed at our discretion, and we recommend this for all users unless you experience issues and need to change
    -   Currently, it is the same as "Prefer Vulkan"
-   "Prefer Vulkan" will attempt to render using Vulkan, but fall back to OpenGL if it doesn't work
-   "Prefer OpenGL" will attempt to render using OpenGL, but fall back to Vulkan if it doesn't work

## Changes

-   Fixed baby Hoglin's and Zoglin's left ear texture so it's properly mirrored

### Minor Tweaks to Blocks, Items and Entities

-   When an entity bounces off of a block or other collidable entity, it emits a vibration of frequency 2

> **Developer's Note**: _We have tweaked how Beds and Slime Blocks restitute entity velocity after collisions. For instance, when air drag is removed via the entity attribute, Slime Blocks will now correctly bounce Mobs indefinitely. This may affect player perception of the bounciness of Beds and Slime Blocks._

### Sounds

Added block sounds for Sulfur, Potent Sulfur and Cinnabar Added mob sounds for Sulfur Cube and Small Sulfur Cube

## Technical Changes

-   The Data Pack version is now 101.2
-   The Resource Pack version is now 85
-   Profiling the game with Tracy (launching with `--tracy`) now includes GPU timings
-   Rendering now uses a reversed depth buffer, which helps with Z-fighting on most hardware

## Data Pack Version 101.2

-   Added `minecraft:sulfur_cube_archetype` registry with the following values:
    -   `regular`
    -   `bouncy`
    -   `slow_flat`
    -   `fast_flat`
    -   `light`
    -   `fast_sliding`
    -   `slow_sliding`
    -   `high_resistance`
    -   `sticky`
-   Entry format: Object with fields:
    -   `items`: item tag that contains all items that can be fed to Sulfur Cubes of this archetype
    -   `buoyant`: boolean indicating if the Sulfur Cube of this archetype floats in liquids
    -   `attribute_modifiers`: a list of objects with fields:
        -   `attribute`: attribute to modify
        -   `id`: unique identifier for the modifier
        -   `amount`: amount to modify the attribute by
        -   `operation`: how to modify the attribute, one of `add_value`, `add_multiplied_base` and `add_multiplied_total`

### Commands

-   When granting or revoking several advancements, the command output will now report how many advancements changed state across all players
-   When granting or revoking advancements or a criterion on several players, the command output will now report the number of players that any change applied to

### Attributes

**Added `minecraft:bounciness`**

    - Determines what portion of the velocity is restituted after the entity collides with blocks and collidable entities
    - When landing on bouncy blocks, like Beds and Slime Blocks, the higher bounciness (of the block or the entity) is applied
    - Accepts values between `0.0` and `1.0`
    - Default value: `0.0` - no velocity is restituted
    - Maximum value: `1.0` - full velocity is restituted, collisions with blocks and collidable entities will have no effect on lowering the velocity
    

**Added `minecraft:friction_modifier`**

    - Determines how much ground friction is applied to the entity with regards to the block it is on
    - Accepts values between `0.0` and `2048.0`
    - Default value: `1.0` - friction of blocks is not modified
    - Minimum value: `0.0` - friction of blocks is reduced to zero
    - Values higher than `1.0` increase the friction applied to the entity from the blocks it is on
    

**Added `minecraft:air_drag_modifier`**

    - Determines how much drag is applied to an entity while in the air
    - Accepts values between `0.0` and `2048.0`
    - Default value: `1.0` - the entity uses existing drag when moving in the air
    - Minimum value: `0.0` - no drag is applied to the entity
    - Values higher than `1.0` increase the drag applied to the entity when moving through the air
    

**Updated the minimum value of `minecraft:knockback_resistance`**

    - The minimum value was changed from `0.0` to `-2.0`
    

### Data Components

**Added `minecraft:sulfur_cube_content`**

-   Represents the item that is absorbed by the Sulfur Cube
-   Format: item that is absorbed by the Sulfur Cube
    -   e.g. `minecraft:sulfur_cube_content=green_wool`

### World Generation

**Dripstone Features**

-   Renamed Feature Type `pointed_dripstone` to `speleothem`
    -   Added field `base_block` - Block State, describes the block forming the base of the Speleothem
    -   Added field `pointed_block` - Block State, describes the block creating the columns of the Speleothem
    -   Added field `replaceable_blocks` - Block ID, list of Block IDs, or hash-prefixed Block Tag describing which blocks this feature can generate on
    -   Renamed field `chance_of_taller_dripstone` to `chance_of_taller_generation`
-   Renamed Feature Type `dripstone_cluster` to `speleothem_cluster`
    -   Added field `base_block` - Block State, describes the block forming the base of the Speleothem
    -   Added field `pointed_block` - Block State, describes the block creating the columns of the Speleothem
    -   Added field `replaceable_blocks` - Block ID, list of Block IDs, or hash-prefixed Block Tag describing which blocks this feature can generate on
    -   Renamed field `dripstone_block_layer_thickness` to `speleothem_block_layer_thickness`
    -   Renamed field `chance_of_dripstone_column_at_max_distance_from_center` to `chance_of_speleothem_at_max_distance_from_center`
    -   Renamed field `max_distance_from_edge_affecting_chance_of_dripstone_column` to `max_distance_from_edge_affecting_chance_of_speleothem`
-   Adjusted Feature Type `large_dripstone`
    -   Added field `replaceable_blocks` - Block ID, list of Block IDs, or hash-prefixed Block Tag describing which blocks this feature can generate on

**Added `noise_gradient` Surface Rule**

Replaces blocks based on the specified noise and gradient list.

Format: object with fields:

-   `noise` - noise id, the noise to sample
-   `gradient` - non-empty list of objects with fields, the list to sample based on the noise value:
    -   `state` (optional) - the block state to select at this index
        -   If this field is not defined, the surface rule will not replace any block when sampling this entry

**Added `sequence` Feature Type**

Generates a list of Placed Features in order. If any feature in the list is not placed, the following features will also be skipped.

Format: object with fields:

-   `features` - list of Placed Features or hash-prefixed Placed Feature tag, the features to generate

**Added `template` Feature Type**

Places one template randomly chosen from the given Weighted List of Identifiers. By default, the template will be spawned randomly rotated, centered around the origin.

Format: object with fields:

-   `templates` - Weighted List of structure template entries. Each structure template entry is composed of an Identifier and a list of rotations to randomly choose from
    -   `id` - The template Identifier
    -   `rotations` - Optional list of rotations to choose from and apply to this template if it is picked
        -   Allowed values: `none`, `clockwise_90`, `180`, `counterclockwise_90`
        -   If not specified, defaults to all allowed values

**Dimension Types**

-   The field `infiniburn` now also accepts an ID and a list of IDs in addition to a tag

**Configured Features**

**`minecraft:geode`**

-   The fields `cannot_replace` and `invalid_blocks` in `blocks` section of feature configuration now also accept an ID and a list of IDs in addition to a tag

**`minecraft:root_system`**

The field `root_replaceable` in the feature configuration now also accepts an ID or a list of IDs in addition to a tag

**`minecraft:vegetation_patch`**

-   The field `replaceable` in the feature configuration now also accepts an ID and or a list of IDs in addition to a tag

**`minecraft:waterlogged_vegetation_patch`**

-   The field `replaceable` in the feature configuration now also accepts an ID and or a list of IDs in addition to a tag

**Structure Processors**

**`minecraft:protected_blocks`**

-   The field `value` now also accepts an ID or a list of IDs in addition to a tag

### Tags

**Block Tags**

-   Added `#suppresses_bounce` - all blocks that suppress the bounciness of entities when colliding with them
-   Added `#glazed_terracotta`, `#concrete` blocks collection tags
-   `#concrete_powder` collection tag has been renamed to `#concrete_powders`
-   Added `#shears_extreme_breaking_speed` for blocks that can be broken with shears with speed 15
-   Added `#shears_major_breaking_speed` for blocks that can be broken with shears with speed 5
-   Added `#shears_minor_breaking_speed` for blocks that can be broken with shears with speed 2

**Item Tags**

-   Added `#glazed_terracotta`, `#concrete`, and `#concrete_powders` items collection tags
-   Added `#sulfur_cube_food` - all items that can be fed to small Sulfur Cube
-   Added `#sulfur_cube_swallowable` - all items that can be placed inside a large Sulfur Cube
-   Added the following tags for items that can be placed inside a Sulfur Cube to determine its archetype:
    -   `#sulfur_cube_archetype/regular`
    -   `#sulfur_cube_archetype/bouncy`
    -   `#sulfur_cube_archetype/slow_flat`
    -   `#sulfur_cube_archetype/fast_flat`
    -   `#sulfur_cube_archetype/light`
    -   `#sulfur_cube_archetype/fast_sliding`
    -   `#sulfur_cube_archetype/slow_sliding`
    -   `#sulfur_cube_archetype/high_resistance`
    -   `#sulfur_cube_archetype/sticky`

**Entity Tags**

-   `minecraft:sulfur_cube` is added to `non_controlling_rider`
-   Added `minecraft:sulfur_cube_with_block_immune_to` for all damage types that Sulfur Cubes are immune to when having a block absorbed
-   Updated `not_scary_for_pufferfish` to include the Sulfur Cube

### Game Events

**Added `minecraft:bounce`**

-   Emitted when an entity collides with a block or a collidable entity with non-zero bounciness
-   Has a vibration frequency of `2`

### Particles

-   Added `sulfur_cube_goo` - particles showing on a Sulfur Cube mob when hopping around

## Resource Pack Version 85

### Block Sprites

-   Added new Block textures:
    -   `block/chiseled_cinnabar.png`
    -   `block/chiseled_sulfur.png`
    -   `block/cinnabar.png`
    -   `block/cinnabar_bricks.png`
    -   `block/polished_cinnabar.png`
    -   `block/polished_sulfur.png`
    -   `block/potent_sulfur.png`
    -   `block/sulfur.png`
    -   `block/sulfur_bricks.png`

### Item Sprites

-   Added new Item sprites:
    -   `item/sulfur_cube_bucket.png`

### Entity Textures

-   Added new Entity textures:
    -   `entity/sulfur_cube/sulfur_cube_outer.png`
    -   `entity/sulfur_cube/sulfur_cube_inner.png`

### Sounds

-   Added sounds for Sulfur Block:
    -   `block.sulfur.break`
    -   `block.sulfur.hit`
    -   `block.sulfur.place`
    -   `block.sulfur.step`
    -   `block.sulfur.fall`
-   Added sounds for Potent Sulfur Block:
    -   `block.potent_sulfur.break`
    -   `block.potent_sulfur.hit`
    -   `block.potent_sulfur.place`
    -   `block.potent_sulfur.step`
    -   `block.potent_sulfur.fall`
    -   `block.potent_sulfur.noxious_gas`
-   Added sounds for Cinnabar Block:
    -   `block.cinnabar.break`
    -   `block.cinnabar.hit`
    -   `block.cinnabar.place`
    -   `block.cinnabar.step`
    -   `block.cinnabar.fall`
-   Added sounds for Sulfur Cube:
    -   `entity.sulfur_cube.jump`
    -   `entity.sulfur_cube.squish`
    -   `entity.sulfur_cube.hurt`
    -   `entity.sulfur_cube.death`
    -   `entity.sulfur_cube.absorb`
    -   `entity.sulfur_cube.eject`
    -   `entity.sulfur_cube.bounce`
    -   `entity.sulfur_cube.hit`
    -   `entity.sulfur_cube.push`
-   Added sounds for Small Sulfur Cube:
    -   `entity.small_sulfur_cube.jump`
    -   `entity.small_sulfur_cube.squish`
    -   `entity.small_sulfur_cube.hurt`
    -   `entity.small_sulfur_cube.death`

### Shaders & Post-process Effects

-   The `core/rendertype_text`, `core/rendertype_text_see_through`, `core/rendertype_text_intensity`, `core/rendertype_text_intensity_see_through`, `core/rendertype_text_background`, and `core/rendertype_text_background_see_through` shaders have been replaced by `core/text` and `core/text_background`
    -   Variants are now controlled by shader defines: `IS_GUI`, `IS_SEE_THROUGH`, and `IS_GRAYSCALE`

## Fixed bugs in 26.2 Snapshot 1

-   [MC-236770](https://bugs.mojang.com/browse/MC-236770) The "Ambient" and "Axolotl" mob caps both display as "A" in the debug overlay
-   [MC-252814](https://bugs.mojang.com/browse/MC-252814) The `clamp` density function takes a direct input and doesn't allow a reference
-   [MC-269520](https://bugs.mojang.com/browse/MC-269520) The game freezes when using /locate in a world without structures enabled
-   [MC-269786](https://bugs.mojang.com/browse/MC-269786) "ID" is not capitalized in some strings
-   [MC-277395](https://bugs.mojang.com/browse/MC-277395) The "options.screenEffectScale.tooltip" string displayed when holding your mouse cursor over the "Distortion Effects" slider is improperly capitalized
-   [MC-277396](https://bugs.mojang.com/browse/MC-277396) Strings referencing nether portals are inconsistently capitalized
-   [MC-279122](https://bugs.mojang.com/browse/MC-279122) Some strings that contain the abbreviation "id" are improperly capitalized
-   [MC-279125](https://bugs.mojang.com/browse/MC-279125) Some "/locate" strings are missing articles before the word "reasonable"
-   [MC-279126](https://bugs.mojang.com/browse/MC-279126) The "mco.configure.world.restore.download.question.line1" string incorrectly spells the word "singleplayer" as "single player"
-   [MC-279137](https://bugs.mojang.com/browse/MC-279137) The "options.directionalAudio.on.tooltip" string is missing a hyphen between the words "HRTF" and "compatible"
-   [MC-279138](https://bugs.mojang.com/browse/MC-279138) The "command.failed" string is missing a conjunction
-   [MC-279154](https://bugs.mojang.com/browse/MC-279154) The "advancements.story.enter;;_;;the;;_;;nether.description" string is missing a serial comma
-   [MC-279156](https://bugs.mojang.com/browse/MC-279156) The titles within some player reporting and punishment menus are improperly capitalized
-   [MC-279158](https://bugs.mojang.com/browse/MC-279158) The "I know what I'm doing!" button is improperly capitalized
-   [MC-279182](https://bugs.mojang.com/browse/MC-279182) Strings used to describe water and lava conversion game rules are missing commas
-   [MC-279183](https://bugs.mojang.com/browse/MC-279183) The "options.allowServerListing.tooltip" string is missing a comma
-   [MC-279184](https://bugs.mojang.com/browse/MC-279184) The "datapackFailure.title" string is missing an article and always pluralizes the word "pack"
-   [MC-279186](https://bugs.mojang.com/browse/MC-279186) The "build.tooHigh" string is missing an article before the word "Height"
-   [MC-279189](https://bugs.mojang.com/browse/MC-279189) The "mco.configure.world.leave.question.line1" string is missing a comma
-   [MC-302488](https://bugs.mojang.com/browse/MC-302488) Strings that contain the term "Safe Mode" are inconsistently capitalized
-   [MC-302628](https://bugs.mojang.com/browse/MC-302628) Dolphins don't dismount minecarts when passing over activator rails
-   [MC-304113](https://bugs.mojang.com/browse/MC-304113) Underwater fog is not applied correctly at low render distances
-   [MC-304873](https://bugs.mojang.com/browse/MC-304873) The "options.textureFiltering.rgss.tooltip" string is missing a hyphen between the words "shader" and "based"
-   [MC-304874](https://bugs.mojang.com/browse/MC-304874) The "options.textureFiltering.anisotropic.tooltip" string is missing a hyphen between the words "hardware" and "based"
-   [MC-305467](https://bugs.mojang.com/browse/MC-305467) The ender dragon's death animation effects render in front of worn armor
-   [MC-306064](https://bugs.mojang.com/browse/MC-306064) Mobs can be forced to look like they're dying while they aren't by using commands
-   [MC-306399](https://bugs.mojang.com/browse/MC-306399) The Spectator mode 'Teleport to Player' action only updates the list of valid targets after the Spectator menu is hidden
-   [MC-306890](https://bugs.mojang.com/browse/MC-306890) Campfires cause bees to work much more slowly
-   [MC-306903](https://bugs.mojang.com/browse/MC-306903) Cubic Bézier easing functions sometimes produce wrong values
-   [MC-306946](https://bugs.mojang.com/browse/MC-306946) The block light transition from level 1 to 0 under the night sky is not smooth when Smooth Lighting is enabled

---

# Minecraft 26.1.1 Release Candidate 1

We are releasing 26.1.1 Release Candidate 1, addressing an issue with player reporting that we missed in the previous version. If no further issues are encountered, we will release 26.1.1 tomorrow with no additional changes.

Happy mining!

## Fixed bugs in 26.1.1 Release Candidate 1

-   [MC-307140](https://bugs.mojang.com/browse/MC-307140) Chat messages can no longer be reported if the chat is enabled

---

# Minecraft 26.1 Release Candidate 3

Today we are shipping Release Candidate 3 for 26.1, addressing a bug in the Ender Dragon fight and fixing a crash.

Happy mining!

## Fixed bugs in 26.1 Release Candidate 3

-   [MC-306989](https://bugs.mojang.com/browse/MC-306989) The ender dragon initiates its death animation as soon as it dies, no matter how close to the exit portal it is

---

# 26.1 Release Candidate 2

Friday Surprise! Today we are shipping the second release candidate for 26.1 and the Tiny Takeover game drop to address an important internationalization issue. If no other critical issues are found, this will be the version that we ship for the eventual full release.

Happy mining!

## Fixed bugs in 26.1 Release Candidate 2

-   [MC-306928](https://bugs.mojang.com/browse/MC-306928) Switching to another window still forcibly sets the input method to English when no input field is focused

---

# Minecraft 26.1 Release Candidate 1

Today we are shipping the first release candidate for 26.1 and the Tiny Takeover game drop! If no critical issues are found, this will be the version that we ship for the eventual full release.

Happy mining!

---

# Minecraft 26.1 Pre-Release 3

Today we are shipping the third pre-release with minor tech changes and bug fixes.

Happy mining!

## Technical Changes

-   The Data Pack version is now 101.1

## Data Pack Version 101.1

### World Generation

**Placement Modifiers**

**`count` Placement Modifier**

-   The `count` field is now limited to a range of `0` to `4096` instead of the previous `256`

## Fixed bugs in 26.1 Pre-Release 3

-   [MC-305118](https://bugs.mojang.com/browse/MC-305118) Resource packs previously labeled as "Broken or incompatible" don't show up at all
-   [MC-306240](https://bugs.mojang.com/browse/MC-306240) /fill does not obey the max;;_;;block;;_;;modifications game rule if too many blocks are in the specified area
-   [MC-306620](https://bugs.mojang.com/browse/MC-306620) Feeding a snifflet with a golden dandelion resets its age to the wrong amount of ticks
-   [MC-306805](https://bugs.mojang.com/browse/MC-306805) Baby zombie villagers' arms are positioned and move incorrectly when holding an item
-   [MC-306840](https://bugs.mojang.com/browse/MC-306840) Dolphins still drown themselves when no players are nearby
-   [MC-306850](https://bugs.mojang.com/browse/MC-306850) The `caves` and `floating_islands` noise settings no longer generate as intended
-   [MC-306854](https://bugs.mojang.com/browse/MC-306854) Unmentioned differences of villager trades between 1.21.11 and 26.1 snapshots
-   [MC-306859](https://bugs.mojang.com/browse/MC-306859) The arms of baby zombies, baby husks, gurgles, and baby zombie villagers clip through their worn chestplates when holding items
-   [MC-306860](https://bugs.mojang.com/browse/MC-306860) Player object text components in server status messages (MotD) are no longer replaced by fallback text
-   [MC-306898](https://bugs.mojang.com/browse/MC-306898) Placed / Configured Features are now limited to only 256 tries, previously higher numbers where possible
-   [MC-306899](https://bugs.mojang.com/browse/MC-306899) The blocklists of the `fire_patch` and `soul_fire_patch` features are inverted, causing generation issues

---

