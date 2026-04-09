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

-   Added sulfur caves undeground biome
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

# Minecraft 26.1 Pre-Release 2

Today we're shipping another pre-release for 26.1 that includes tech changes and fixes to features included in the Tiny Takeover game drop.

Happy Friday mining!

## Changes

-   Updated the dismount speed thresholds for Spears to match Bedrock
-   Fixed issue with Baby Axolotl's right hind leg not moving correctly when swimming
-   Baby Cat is now scaled up to be the same size as baby Ocelot
-   Baby Horse model is no longer scaled up slightly

### UI

-   Added a new display option called "Exclusive Fullscreen" which controls if fullscreen mode should take full control of a monitor
    -   Defaults to `false` (i.e. non-exclusive mode)
    -   Any change will be applied only after the game restarts
    -   Warning: exclusive fullscreen mode might prevent use of input methods (IME)

### Trades

-   The Master Librarian will now have three available trades to ensure that an enchanted book trade is always offered when using the Rebalance experiment

## Technical Changes

### Text components

-   Components in server status messages (MotD) nested more than 16 times will now be discarded and replaced with an ellipsis

## Fixed bugs in 26.1 Pre-Release 2

-   [MC-153831](https://bugs.mojang.com/browse/MC-153831) Trader llamas spawned from breeding can despawn
-   [MC-181169](https://bugs.mojang.com/browse/MC-181169) Skeleton trapped horses with PersistenceRequired still despawn
-   [MC-248092](https://bugs.mojang.com/browse/MC-248092) Untamed cats on lead despawn when attached to fence post
-   [MC-274238](https://bugs.mojang.com/browse/MC-274238) Persistent trader llamas will still despawn when leashed to wandering traders
-   [MC-303684](https://bugs.mojang.com/browse/MC-303684) Hoglins despawn when attached to a lead
-   [MC-303685](https://bugs.mojang.com/browse/MC-303685) Zoglins despawn when attached to leads
-   [MC-303749](https://bugs.mojang.com/browse/MC-303749) Dolphins can despawn when attached to leads
-   [MC-303750](https://bugs.mojang.com/browse/MC-303750) Squids & glow squids can despawn when attached to leads
-   [MC-304446](https://bugs.mojang.com/browse/MC-304446) Activating a stasis chamber with a sponge deletes the ender pearl
-   [MC-305123](https://bugs.mojang.com/browse/MC-305123) Curse of Vanishing doesn't work when the item is equipped on an armor stand
-   [MC-305196](https://bugs.mojang.com/browse/MC-305196) Witches always miss their shots when close to their target
-   [MC-306064](https://bugs.mojang.com/browse/MC-306064) Mobs can be forced to look like they're dying while they aren't by using commands
-   [MC-306327](https://bugs.mojang.com/browse/MC-306327) The chat restriction warning ignores the Chat Width option
-   [MC-306328](https://bugs.mojang.com/browse/MC-306328) Using golden dandelions to unlock aging forcibly removes persistence of baby animals
-   [MC-306351](https://bugs.mojang.com/browse/MC-306351) Line spacing between the chat restriction warning and messages does not have a background
-   [MC-306502](https://bugs.mojang.com/browse/MC-306502) Uploading a world to a snapshot Realm wipes it
-   [MC-306516](https://bugs.mojang.com/browse/MC-306516) G-Sync cannot be enabled in the new borderless window mode
-   [MC-306564](https://bugs.mojang.com/browse/MC-306564) Item entities' health does not decrease uniformly when on cacti
-   [MC-306601](https://bugs.mojang.com/browse/MC-306601) The IME pre-edit window appears in the unfocused text box of the anvil UI when no items are placed in the anvil slots
-   [MC-306626](https://bugs.mojang.com/browse/MC-306626) Adult horses' old black dots markings aren't included in the "Programmer Art" resource pack
-   [MC-306632](https://bugs.mojang.com/browse/MC-306632) Baby undead horses age again
-   [MC-306657](https://bugs.mojang.com/browse/MC-306657) The models for baby horses and baby cats have a different scale compared to Bedrock Edition
-   [MC-306658](https://bugs.mojang.com/browse/MC-306658) Dolphins will let themselves drown even with ample access to air
-   [MC-306709](https://bugs.mojang.com/browse/MC-306709) Librarians' master level book trade is no longer guaranteed when Villager Trade Rebalance is enabled
-   [MC-306741](https://bugs.mojang.com/browse/MC-306741) Opening the chat forces a CJK input method when one is enabled in the system
-   [MC-306798](https://bugs.mojang.com/browse/MC-306798) Ender dragons with a `DragonDeathTime` of 200 or greater never disappear
-   [MC-306812](https://bugs.mojang.com/browse/MC-306812) Inventories with no text fields cause key binds to conflict with IME input methods
-   [MC-306814](https://bugs.mojang.com/browse/MC-306814) `environment_attribute` value providers give incorrect results on subsequent accesses within a tick
-   [MC-306830](https://bugs.mojang.com/browse/MC-306830) The mouse cursor now changes to the "not allowed" shape when hovering over part of the Creative mode inventory's Survival Inventory tab

---

# Minecraft 26.1 Pre-Release 1

Today we are shipping the first pre-release for Java version 26.1, the Tiny Takeover game drop! From now on, you should mostly see bugs being fixed. In addition to that, pre-releases don't follow the regular snapshot cadence of releasing on Tuesdays, so keep your eyes peeled for the next pre-release.

## Changes

-   Updated the Main Menu background panorama

## Technical Changes

-   The Data Pack version is now 101
-   The Resource Pack version is now 84
-   Changes to the `minecraft:nbt` text component format
-   Changes to the `minecraft:selector`, `minecraft:nbt` and `minecraft:object` text component formats

## Data Pack Version 101

-   The "Default Components" report generator no longer outputs files for entries without any components

### Commands

**Changes to `time`**

Syntax:

-   `time [of <clock>] rate <rate>` - sets the rate multiplier at which the clock should advance
    -   Note: this only changes the rate at which the World Clock and any Timelines dependent on it advance their internal timers
        -   For example, in the case of the `minecraft:overworld` clock, the day/night cycle will pass quicker with a larger value, but actual game simulation will not speed up (as would happen with `/tick rate`)
    -   A `rate` of `1` corresponds to normal speed
    -   `rate` is a float between `0` (exclusive) and `1000` (inclusive)

### Data Components

**Modified `minecraft:provides_banner_patterns`**

-   The component now also accepts an ID or a list of IDs in addition to a tag

**Modified `minecraft:blocks_attacks`**

-   The field `bypassed_by` now also accepts an ID or a list of IDs in addition to a tag

**Modified `minecraft:damage_resistant`**

-   The field `types` now also accepts an ID or a list of IDs in addition to a tag

### Loot Functions

**Changed `minecraft:set_instrument`**

-   The `options` field now also accepts an ID and a list of IDs in addition to a tag

### Predicates

**Added `minecraft:environment_attribute_check` Loot Predicate**

Exactly matches the value of an Environment Attribute at a given position. Note: this predicate requires a context with an `origin` position set as long as the Environment Attribute can vary positionally.

Format: object with fields:

-   `attribute` - Environment Attribute ID to test
-   `value` - Exact value of the Environment Attribute to match
-   e.g. `{condition: 'environment_attribute_check', attribute: 'gameplay/piglins_zombify', value: true}`

### Number Providers

**Added `minecraft:environment_attribute`**

Fetches and provides the value of an Environment Attribute (that can be represented as a number). Note: this provider requires a context with an `origin` position set as long as the Environment Attribute can vary positionally.

Format: object with fields:

-   `attribute` - Environment Attribute ID to fetch
-   e.g. `{type: 'environment_attribute', attribute: 'gameplay/sky_light_level'}`

### World Generation

**Flower Features**

-   Features spawned from Bone Meal are no longer restricted to the `flower` feature type, and instead controlled by the `#can_spawn_from_bone_meal` Configured Feature Tag
-   The `flower`, `flower_no_bonemeal`, and `random_patch` feature types have been removed
    -   Instead, patches can be expressed as a sequence of `count` and `random_offset` placement modifiers

**Int Providers**

**Added `trapezoid` Int Provider**

Select a random value with a trapezoid distribution, similar to the `trapezoid` Float Provider.

Format: object with fields:

-   `min`: integer, the minimum value to generate
-   `max`: integer, the maximum value to generate
-   `plateau`: integer, the width of the "plateau" of the distribution in which all values are equally likely to occur
    -   A value of `0` is equivalent to a triangle distribution
    -   A value of `max-min` is equivalent to a uniform distribution

### Tags

**Configured Feature Tags**

-   Added `#can_spawn_from_bone_meal` - features that, when added in a biome, can be spawned when using Bone Meal in that biome

### Text components

**;;`;;minecraft:object**

-   Added a new optional field named `fallback` that contains a text component to be used when object component itself can't be displayed (for example when printing messages in server logs or during narration)
-   Objects of type `player` (player heads) no longer can be used in server status messages (MotD)
    -   All components of that type will be replaced by a fallback text

## Resource Pack Version 84

-   Updated textures for Pup to fix issues with overlapping textures

### Item Models

**`minecraft:end_cube` Special Model Type**

-   New special model type that renders a cube with the same texture effects as the End Portal and the End Gateway blocks
-   Fields:
    -   `effect` - texture effect to apply, one of: `portal`, `gateway`

### Block State Rendering

-   End Gateway and End Portal should now look the same when rendered on a Block Display as they look when placed in world

### Shaders & Post-process Effects

-   The `core/rendertype_translucent_moving_block` shaders have been removed in favor of `core/block`

## Fixed bugs in 26.1 Pre-Release 1

-   [MC-195237](https://bugs.mojang.com/browse/MC-195237) End portals and end gateways held by endermen or as block display entities are not rendered, but nether portals are
-   [MC-230746](https://bugs.mojang.com/browse/MC-230746) Pointed dripstone does not grow with a waterlogged block 2 blocks above it but does fill cauldrons
-   [MC-305518](https://bugs.mojang.com/browse/MC-305518) Baby wolves' tail uses an incorrect UV map
-   [MC-305702](https://bugs.mojang.com/browse/MC-305702) Zombies and their variants have lost their special animation when holding spears
-   [MC-305914](https://bugs.mojang.com/browse/MC-305914) /swing does not swing players' arms on their perspective
-   [MC-306056](https://bugs.mojang.com/browse/MC-306056) The selected difficulty does not visually update when going into and out of the game rules menu
-   [MC-306232](https://bugs.mojang.com/browse/MC-306232) The block breaking animation on banners is now amplified
-   [MC-306315](https://bugs.mojang.com/browse/MC-306315) The left side of wolf pups' heads is misaligned, causing a gap and texture error
-   [MC-306338](https://bugs.mojang.com/browse/MC-306338) Baby zombified piglins' snout texture was made for a 4×3×1 cube model, even though the snout model is actually a 3×3×1 cube
-   [MC-306341](https://bugs.mojang.com/browse/MC-306341) Helmets on baby humanoids shift off-center when their heads rotate
-   [MC-306427](https://bugs.mojang.com/browse/MC-306427) Certain mobs holding items with empty "kinetic;;_;;weapon" components crash the game whenever target acquisition succeeds
-   [MC-306532](https://bugs.mojang.com/browse/MC-306532) The error that occurred when a resource pack used textures that were too large is now incomprehensible
-   [MC-306571](https://bugs.mojang.com/browse/MC-306571) CommandEncoder#copyTextureToBuffer has incorrect parameter validation statements
-   [MC-306612](https://bugs.mojang.com/browse/MC-306612) Baby zombies, baby husks, and gurgles now hold items like players do
-   [MC-306624](https://bugs.mojang.com/browse/MC-306624) Various translucent geometry is now invisible behind name plates
-   [MC-306631](https://bugs.mojang.com/browse/MC-306631) Baby zombies, husks, drowned, and zombified piglins spawned by using spawn eggs on normal ones can't pick up items
-   [MC-306633](https://bugs.mojang.com/browse/MC-306633) The "Toggle GUI" key bind doesn't work when set to a mouse button
-   [MC-306653](https://bugs.mojang.com/browse/MC-306653) Name plates are no longer visible through opaque blocks
-   [MC-306705](https://bugs.mojang.com/browse/MC-306705) Copper golem statues with a pose now appear upside down as items
-   [MC-306706](https://bugs.mojang.com/browse/MC-306706) The game hangs/freezes upon losing focus
-   [MC-306708](https://bugs.mojang.com/browse/MC-306708) Block state rendering of chests for the left and right block states uses the single chest texture
-   [MC-306713](https://bugs.mojang.com/browse/MC-306713) The most transparent pixels of the gradient banner patterns are no longer visible
-   [MC-306742](https://bugs.mojang.com/browse/MC-306742) Rendering an empty item model with oversized;;_;;in;;_;;gui causes a crash
-   [MC-306748](https://bugs.mojang.com/browse/MC-306748) Profiler tick ended before path was fully popped (remainder: 'root'). Mismatched push/pop?
-   [MC-306796](https://bugs.mojang.com/browse/MC-306796) Text displays with `see_through` set to 1 now z-fight with themselves

---

