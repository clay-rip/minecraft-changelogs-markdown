# 26.3-snapshot-10

We've safely made it to 26.3 Snapshot 10! This week, the Dappled Forest panorama has made its way to the main menu, bringing cozy fall vibes every time you launch the game. This snapshot also includes a variety of technical changes and improvements, so dig in!

Happy mining!

## New Features

### Realms

-   Added a new Realms introduction screen showcasing Realms key features
    -   Accessible from the "Add Realm" button
    -   Automatically shown when entering Realms if a trial is available

## Changes

-   The Main Menu now has an updated background panorama showing the new Dappled Forest biome with an Abandoned Camp
-   Changed the Adventure Mode icon in the Game Mode Switcher to the Buried Treasure Map
-   Improvements to performance when trying to locate structures
-   Reverted recent changes to Drowned behavior and animations from this release cycle

### Minor Tweaks to Blocks, Items and Entities

-   Enchantments now apply to items being damaged from protecting an Undead mob from the sun
-   Teleporting randomly after eating a Chorus Fruit now shows particles into the direction of the teleportation

### Explorer Maps

-   The following Explorer Maps have been renamed to have more consistent naming
    -   Ocean Monument Explore Map -> Ocean Monument Map
    -   Swamp Hut Explorer Map -> Swamp Hut Map
    -   Trial Chambers Explorer Map -> Buried Trial Chambers Map
    -   Woodland Mansion Explorer Map -> Woodland Mansion Map
    -   Jungle Pyramid Explorer Map -> Jungle Pyramid Map

### Accessibility

-   Subtitles now point to the most recent sound in range

## Technical Changes

-   The Data Pack version is now 118.0
-   The Resource Pack version is now 97.0
-   The `none` swing animation type has been readded
    -   This affects the `/swing` command as well as the `minecraft:attack_animation` and `minecraft:interact_animation` components

## Data Pack Version 118

### Commands

**Added `compute`**

-   Evaluates `minecraft:number_provider` in various contexts
-   In all contexts `origin` is set to current command context position, while `this` entity is set to `@s`

Syntax:

-   `/compute <target> <provider> [<scale>|integer]`, where:
    -   `<target>` - one of:
        -   `default` - runs provider in `minecraft:command_compute_default` context, where only common arguments (position and `this` entity) are available
        -   `block <pos>` - runs provider in `minecraft:command_compute_position` context, where block state and block position are set based on block at position `<pos>`
        -   `entity <entity selector>` - runs provider in `minecraft:command_compute_entity` context, where `target_entity` is set to selector result
    -   `<provider>` - either an element of `minecraft:number_provider` registry or inline value
    -   `<scale>` - optional scale value, defaults to `1.0`
        -   Final result will be multiplied by `<scale>` and rounded towards negative infinity
    -   `integer` - optional marker to use integer mode
        -   Due to truncation between intermediate steps this mode is not equivalent to float mode even if scale is `1.0`

**Changes to `data`**

-   Added new source to `/data modify ... append|insert|merge|prepend|set` called `compute`
-   New source will evaluate a `minecraft:number_provider` and then provide the result either as an integer or a float tag
-   Syntax: `compute <target> <provider> [integer]`, where the syntax of `target`, `provider` and `integer` is the same as in `/compute` function
-   Example: `/data modify storage foo bar set compute entity @n[type=minecraft:armor_stand] {type:score,target:{type:context,target:target_entity},score:baz}`

### Data Components

**Changed `minecraft:consumable`**

-   Added a new optional field to the `teleport_randomly` consume effect:
    -   `directional_particles` - boolean, whether to show a particle trail into the direction of the teleportation
        -   If not present, defaults to `true`

**Updated `minecraft:block_transformer`**

-   Contents have been moved to a separate registry
-   Component must now always refer to `minecraft:block_transformer` registry - existing inline components are removed

**Changed `minecraft:attack_animation` and `minecraft:interact_animation`**

-   The `duration` field is now a non-negative integer

### Loot Tables

**Loot Table Types**

**Added `minecraft:command_compute_default`**

-   Currently used for `/compute default` command
-   It takes the following parameters:
    -   `origin`, the position at which the command was executed
    -   `this` entity, the `@s` entity of the command being executed (optional)

**Added `minecraft:command_compute_position`**

-   Currently used for `/compute block` command
-   It takes the following parameters:
    -   Everything included in `minecraft:command_compute_default`
    -   `block_entity`, the block entity of the block at the position given in a command
    -   `block_state`, the current state of the block at the position given in a command

**Added `minecraft:command_compute_entity`**

-   Currently used for `/compute entity` command
-   It takes the following parameters:
    -   Everything included in `minecraft:command_compute_default`
    -   `target_entity`, entity selected by the selector given in a command

### Loot Functions

**Changed `minecraft:set_loot_table`**

-   Removed unused field `type`
-   The `tag` field, previously known as `name`, has been renamed to `loot_table_id`

### Block Transformers

-   Added `minecraft:block_transformer` registry containing rules for transforming a block into another block
-   Format: list of objects with fields:
    -   `block_state_provider` - Block State Provider, used to provide the state for the transformed block
        -   If the Block State Provider returns no result (as by `rule_based_state_provider`, for example), the next rule in the list will be attempted
        -   The set of Block State Providers are the same as the Block State Providers used in World Generation
    -   `sound` - optional field, Sound Event to play on interaction, e.g. `minecraft:item.axe.strip`
        -   If not present, defaults to play no Sound Event
    -   `particle` - optional field, particles to play on interaction
        -   If not present, defaults to `none`
            -   `none`
            -   `scrape`
            -   `wax_on`
            -   `wax_off`
    -   `disallowed_faces` - optional field, list of Directions specifying which faces on the clicked Block that cannot be interacted with
        -   If a disallowed face is interacted with, the next rule in the list will be attempted
        -   If not present, defaults to an empty list
        -   Values:
            -   `up`
            -   `down`
            -   `north`
            -   `south`
            -   `east`
            -   `west`
    -   `loot` - optional Loot Table, the Loot Table to use for dropping items on a successful transformation, e.g. `minecraft:till/rooted_dirt`
        -   If not present, defaults to using no Loot Table
    -   `drop_strategy` - optional field, configures from where in the Block any loot should drop
        -   If not present, defaults to `from_middle`
        -   Values:
            -   `from_middle` - from the middle of the Block
            -   `clicked_face` - from the face interacted with
    -   `update_from_neighbors` - optional Boolean, if the transformed block should update based on neighboring blocks. This allows e.g. fences to connect
        -   If not present, defaults to true
    -   `transform_type` - optional field, configures how nearby blocks should be affected by the transformation
        -   If not present, defaults to `single_block`
        -   Values:
            -   `single_block` - only affects the Block interacted with
            -   `copper_chest` - if input and output blocks are both copper chests of any weathering state, waxed or unwaxed, this transformation will affect both sides of a double chest
    -   `consume_on_use` - optional Boolean, determines if the item should be consumed or not
        -   Only applies to stackable items
        -   If not present, defaults to `true`
    -   `item_damage_per_use` - optional Integer, determines how much damage the item takes with each use
        -   Only applies to non-stackable items
        -   If not present, defaults to `0`
-   Default values in vanilla:
    -   `minecraft:shovel` - default value for shovels
    -   `minecraft:axe` - default value for axes
    -   `minecraft:hoe` - default value for hoes

### World Generation

**Noise Settings**

-   Renamed `preliminary_surface_level` to `chunk_surface_level`
    -   This Density Function is no longer implicitly interpolated across the entire chunk
-   The `ore_veins_enabled` field has been removed, and replaced by the `minecraft:ore_vein` Material Rule
-   Removed `noise.size_horizontal` and `noise.size_vertical` fields, these are now specified in the `interpolated` density function
-   Added optional `debug_functions` field - list of objects with fields, Density Function values to show in the `chunk_generation_stats` debug entry
    -   Fields:
        -   `label` - string, label to identify this Density Function
        -   `function` - Density Function, the Density Function to compute and show at the player position
    -   If not specified, no density function values will be shown

**Material Rules**

**Added `minecraft:ore_vein`**

-   Format: object with fields:
    -   `ore_block` - Block State, the ore block to place
    -   `raw_ore_block` - Block State, the raw ore block to place
    -   `filler_block` - Block State, the filler block to place
    -   `raw_ore_chance` - float between 0 and 1, the probability for a `raw_ore_block` to be placed instead of an `ore_block`
    -   `density` - Density Function, the probability between 0 and 1 for the ore vein to replace a block
        -   If `0` or lower, no block will be replaced
    -   `richness` - Density Function, the probability between 0 and 1 for `ore_block` or `raw_ore_block` to be placed (as opposed to `filler_block`)
        -   If `0` or lower, all blocks will be `filler_block`
        -   If `1` or greater, no blocks will be `filler_block`
    -   `filler_gap` - Density Function, acts as an override to `richness`: if positive, `filler_block` will always be placed

**Changed `minecraft:noise`**

The following fields have been introduced:

-   `shift_x` - optional Density Function, a domain warp to apply on x
    -   If not specified, no warping will be applied (equivalent to `0`)
-   `shift_y` - optional Density Function, a domain warp to apply on y
    -   If not specified, no warping will be applied (equivalent to `0`)
-   `shift_z` - optional Density Function, a domain warp to apply on z
    -   If not specified, no warping will be applied (equivalent to `0`)

**Removed `minecraft:shifted_noise`**

-   Replaced by `minecraft:noise`

**Updated `minecraft:interpolated`**

Added fields:

-   `cell_size_xz` - positive int, size in blocks of the interpolation grid cells on the XZ axes
-   `cell_size_y` - positive int, size in blocks of the interpolation grid cells on the Y axis

**Updated `minecraft:cache` (renamed from `minecraft:cache_once`)**

-   No format change

**Removed `minecraft:cache_2d`, `minecraft:cache_all_in_cell`, and `minecraft:flat_cache`**

-   May be replaced with `minecraft:cache`
-   `minecraft:slice` may be used to always pick Y=0, as formerly handled by `minecraft:flat_cache`

### Tags

**Block Tags**

-   Added `#nether_portal_frame` - blocks that can be used to create a Nether Portal
-   Added `#conduit_effect_block` - blocks that can be used to build a Conduit

**Structure Tags**

-   Renamed `#on_woodland_explorer_maps` to `#on_woodland_mansion_maps`
-   Renamed `#on_ocean_explorer_maps` to `#on_ocean_monument_maps`
-   Renamed `#on_jungle_explorer_maps` to `#on_jungle_pyramid_maps`
-   Renamed `#on_swamp_explorer_maps` to `#on_swamp_hut_maps`
-   Renamed `#on_trial_explorer_map` to `#on_buried_trial_chambers_map`

**Fluid Tags**

-   Added `#axolotl_try_find_liquid` for all liquids Axolotls are trying to find
-   Added `#dolphin_try_find_liquid` for all liquids Dolphins are trying to find
-   Added `#frog_try_find_land_near_liquid` for all liquids Frogs are trying to find land near to
-   Added `#entity_floatable` for all fluids that make entities float

## Resource Pack Version 97

### Item Sprites

-   Renamed `item/trial_chamber_map.png` to `item/buried_trial_chambers_map.png`
-   Renamed `item/jungle_temple_map.png` to `item/jungle_pyramid_map.png`

### UI Sprites

-   Added new UI textures:
    -   `gui/realms/friends.png`
    -   `gui/realms/minigames.png`
    -   `gui/realms/private_server.png`
    -   `gui/sprites/widget/realms_button.png`
    -   `gui/sprites/widget/realms_button_disabled.png`
    -   `gui/sprites/widget/realms_button_highlighted.png`

---

# Minecraft 26.3 Snapshot 9

Looks like this Snapshot couldn't wait until Tuesday! Arriving a day early, it brings new customization options for Realms. Owners can now increase render distance up to 25 chunks and separately configure render and simulation distance to find the balance that works best for their world.

Aside from these changes, we've also included plenty of technical improvements and bug fixes.

Happy mining!

## New Features

### Realms

-   Added render distance and simulation distance sliders to Realm configuration settings

### Minor Tweaks to Blocks, Items and Entities

-   Endermen will now take damage from projectiles if they're riding something
-   Endermen and Shulkers no longer teleport onto Bedrock

### UI

-   On macOS, added a "Right Click Emulation" option in Controls settings, which treats Control + left-click as a right-click
    -   Off by default

## Technical Changes

-   The Data Pack version is now 117.0

## Data Pack Version 117.0

### Advancements

**Validation**

-   Visible root advancements (i.e. ones that have `display` field, but no `parent` field) must always declare `background` field in `display` structure
-   Only root advancements can have `background` field in `display` structure

### Slot Sources

**Changed `minecraft:group`**

-   Can only use an inline definition in a top-level file

### Loot Functions

**Changed `minecraft:sequence`**

-   Can only use an inline definition in a top-level file

### Number Providers

**Changed `minecraft:sum`**

-   The `summands` field was renamed to `operands` and now accepts an inline value, a single namespaced ID, a list of namespaced IDs, a list of inline values, or a hash-prefixed tag ID of a `minecraft:number_provider` type
-   Now requires at least one operand
-   When used in integer mode, integer mode is used for intermediate steps as well

**Added `minecraft:product`**

-   Fields:
    -   `operands` - A list of numbers as an inline value, a single namespaced ID, a list of namespaced IDs, a list of inline values, or a hash-prefixed tag ID of a `minecraft:number_provider` type
-   Returns the product of the operands, multiplying them all together
-   Requires at least one operand

**Added `minecraft:minimum`**

-   Fields:
    -   `operands` - A list of numbers as an inline value, a single namespaced ID, a list of namespaced IDs, a list of inline values, or a hash-prefixed tag ID of a `minecraft:number_provider` type
-   Returns the minmimum value of the operands
-   Requires at least one operand

**Added `minecraft:maximum`**

-   Fields:
    -   `operands` - A list of numbers as an inline value, a single namespaced ID, a list of namespaced IDs, a list of inline values, or a hash-prefixed tag ID of a `minecraft:number_provider` type
-   Returns the minmimum value of the operands
-   Requires at least one operand

**Added `minecraft:average`**

-   Fields:
    -   `operands` - A list of numbers as an inline value, a single namespaced ID, a list of namespaced IDs, a list of inline values, or a hash-prefixed tag ID of a `minecraft:number_provider` type
-   Returns the average value of the operands
-   Requires at least one operand

### Tags

**Block Tags**

-   Added `#uncarvable` - blocks that Carvers can never carve
-   Added `#dangerous_for_teleportation` - collection tag defining blocks that are dangerous to teleport on
-   Added `#cat_does_not_teleport_to` - blocks that Cats do not teleport to
-   Added `#enderman_does_not_teleport_to` - blocks that Endermen do not teleport to
-   Added `#shulker_does_not_teleport_to` for blocks that Shulkers do not teleport to
-   Added `#consumable_does_not_teleport_to` - blocks that entities do not teleport to when they consume food that teleports randomly when eaten
    -   Empty by default

**Item Tags**

-   Added `#brewing_potion_inputs` - Items that can be placed in a Brewing Stand potion slot, regardless of whether they are brewing recipe inputs

**Potion Tags**

-   Added `#douses_fire` - Potions that douse Fire blocks when they hit something
-   Added `#hurts_water_sensitive_entities` - Potions that will hurt entities which are sensitive to water (e.g. Endermen)
-   Added `#extinguishes_entities` - Potions that can extinguish entities
-   Added `#rehydrates_axolotls` - Potions that will cause Axolotls to rehydrate

---

# Minecraft 26.3 Snapshot 8

This Wednesday, a hot new Snapshot enters the Realm! That's right, in 26.3 Snapshot 8, Realm owners can now create and manage Invite Codes, making it easier than ever to join the fun.

Alongside these additions, we've made further improvements to the World Options screen and included several gameplay fixes and technical updates.

Happy mining!

## New Features

### Explorer Maps

-   Renamed the following maps:
    -   Buried Ancient City Map
    -   Buried Mineshaft Map
    -   Abandoned Camp Map

### Realms

-   Realm owners can now create and manage Invite Codes
    -   Each Realm can have up to five Invite Codes
    -   Invite Codes can be configured to be active / inactive and deleted
    -   The expiration of an Invite Code can also be configured
-   Players can now easily join a Realm by entering an Invite Code in a new "Join Realm" screen

## Changes

-   Cushions are now only destroyed when fully covered by blocks that cause suffocation
-   New Villager trades, unlocked from a Villager leveling up their profession, will now update even if the player is in the process of trading with them

### UI

**World Options**

-   Some further improvements have been made to the World Options screen, which is now accessible from the pause menu
    -   The "Game Mode" button has been renamed to "Default Game Mode"
    -   The "General" section has a new addition:
        -   Personal Game Mode: your active game mode in the current world (equivalent to the `/gamemode` command, or F3+F4)
    -   The "Multiplayer" section has a new addition:
        -   Force Game Mode: controls whether other players game mode is forced to match the default game mode of the world or not

## Technical Changes

-   The Data Pack version is now 116.0
-   The Resource Pack version is now 96.0

## Data Pack Version 116.0

### World Generation

**Features**

-   Removed feature types:
    -   `minecraft:desert_well`

**Changed `minecraft:template`**

-   Added field `processors`: Namespaced ID or inline definition of a structure processor list to apply to the template

**Placement Modifiers**

**Added `minecraft:randomly_selected`**

Randoly selects a Placement Modifier from a list and delegates placement to it.

Format:

-   `placements`: Non-empty list of Placement Modifiers to pick from

**Block Predicates**

**Added `minecraft:volume_match`**

Checks that every block in a volume matches a given Block Predicate.

Format:

-   `min`: List of 3 integers in range `-16` to `16` specifying the lower corner of the volume as an offset from the test position
-   `max`: List of 3 integers in range `-16` to `16` specifying the upper corner of the volume as an offset from the test position
-   `match`: Block Predicate to test on each position

## Resource Pack Version 96

### Shaders & Post-process Effects

**Removed Core Shaders**

-   `core/text_background.fsh` and `core/text_background.vsh` were removed and text background in Text Display Entities is now rendered using the text shaders

**Order-independent Transparency (OIT)-related Shader Changes**

-   `OIT_FORCE_ZERO_DEPTH` shader define was removed since the see-through text it was used for is now rendered in a separate pass outside OIT

## Fixed bugs in 26.3 Snapshot 8

-   [MC-44654](https://bugs.mojang.com/browse/MC-44654) - Some entities' positions are not updated on the client when teleported
-   [MC-122731](https://bugs.mojang.com/browse/MC-122731) - Camera movement stutters when turning in a boat
-   [MC-206540](https://bugs.mojang.com/browse/MC-206540) - Increased input delay when riding an entity
-   [MC-236497](https://bugs.mojang.com/browse/MC-236497) - The head rotations of passengers in boats are not correctly displayed for other players
-   [MC-237679](https://bugs.mojang.com/browse/MC-237679) - The head rotations of passengers in boats are constantly forced to turn in certain directions if the rider were to dismount the boat while moving left or right
-   [MC-249200](https://bugs.mojang.com/browse/MC-249200) - Several entities constantly deviate visually from their actual positions on the client when teleported
-   [MC-253023](https://bugs.mojang.com/browse/MC-253023) - Breaking paintings, item frames, glow item frames cannot trigger sculk shriekers
-   [MC-258579](https://bugs.mojang.com/browse/MC-258579) - The player's head does not rotate smoothly (with delay) in third person view while riding a vehicle
-   [MC-259512](https://bugs.mojang.com/browse/MC-259512) - Horizontal camera rotation lags when riding
-   [MC-260780](https://bugs.mojang.com/browse/MC-260780) - Shulker bullets always push fireballs south
-   [MC-280250](https://bugs.mojang.com/browse/MC-280250) - Projectiles sometimes desync when thrown/shot while moving
-   [MC-300000](https://bugs.mojang.com/browse/MC-300000) - Players desync when teleporting all users riding a happy ghast
-   [MC-305214](https://bugs.mojang.com/browse/MC-305214) - Arrows deflecting off of entities get offset
-   [MC-308961](https://bugs.mojang.com/browse/MC-308961) - When changing the game mode using debug hotkeys while in the World Options screen, the "Game Mode" button does not update
-   [MC-309284](https://bugs.mojang.com/browse/MC-309284) - Poplar leaves don't use the `dark_cutout` mipmap strategy
-   [MC-309668](https://bugs.mojang.com/browse/MC-309668) - Straw beds are not broken faster when using hoes
-   [MC-309670](https://bugs.mojang.com/browse/MC-309670) - Cushions z-fight with the tops of dragon heads
-   [MC-309716](https://bugs.mojang.com/browse/MC-309716) - Cushions can be broken in Adventure mode
-   [MC-310066](https://bugs.mojang.com/browse/MC-310066) - Tridents thrown by drowned still visually bounce off entities
-   [MC-310097](https://bugs.mojang.com/browse/MC-310097) - Experience orbs desync and appear to phase through blocks
-   [MC-310103](https://bugs.mojang.com/browse/MC-310103) - The "Text Background Opacity" setting makes the text darker when the "Text Background" setting is set to Everywhere
-   [MC-310166](https://bugs.mojang.com/browse/MC-310166) - The straw bed is not placed immediately after regular beds in the Creative mode inventory
-   [MC-310175](https://bugs.mojang.com/browse/MC-310175) - Missing resource warning when loading up the game
-   [MC-310200](https://bugs.mojang.com/browse/MC-310200) - The player's model flickers while falling into the void when viewed from certain angles
-   [MC-310393](https://bugs.mojang.com/browse/MC-310393) - Certain projectiles thrown at the world border rubberband repeatedly
-   [MC-310476](https://bugs.mojang.com/browse/MC-310476) - Projectiles only collide outright with the world border when underwater
-   [MC-310530](https://bugs.mojang.com/browse/MC-310530) - Changing the game mode in the World Options screen no longer changes the player's game mode
-   [MC-310540](https://bugs.mojang.com/browse/MC-310540) - A noise definition with `base_amplitude` set to 0.0 crashes the game during world load
-   [MC-310543](https://bugs.mojang.com/browse/MC-310543) - The JVM crashes with `EXCEPTION_ACCESS_VIOLATION` in `atio6axx.dll` on Boot Camp (AMD Radeon Pro 555X)
-   [MC-310549](https://bugs.mojang.com/browse/MC-310549) - `invulnerable_time` never decreases for some entities
-   [MC-310632](https://bugs.mojang.com/browse/MC-310632) - Farmer villagers no longer throw excess wheat to other villagers
-   [MC-310642](https://bugs.mojang.com/browse/MC-310642) - Landing on farmland deals no fall damage when the block is prevented from being trampled
-   [MC-310687](https://bugs.mojang.com/browse/MC-310687) - Languages other than "English (US)" fail to load
-   [MC-310691](https://bugs.mojang.com/browse/MC-310691) - Stonecutter recipes for concrete stairs and slabs are missing
-   [MC-310692](https://bugs.mojang.com/browse/MC-310692) - The error message when the game is unable to load translations can extend outside the screen
-   [MC-310705](https://bugs.mojang.com/browse/MC-310705) - The difficulty lock warning screen shows the wrong difficulty after changing the difficulty
-   [MC-310718](https://bugs.mojang.com/browse/MC-310718) - Unused color attachments are unusable with the OpenGL rendering backend
-   [MC-310726](https://bugs.mojang.com/browse/MC-310726) - The mansion icon in the texture of woodland explorer maps doesn't match the respective icon on the map
-   [MC-310728](https://bugs.mojang.com/browse/MC-310728) - Cushions can still be used to see through blocks in third person mode
-   [MC-310729](https://bugs.mojang.com/browse/MC-310729) - Explorer maps from previous versions prevent saved hotbars from loading
-   [MC-310743](https://bugs.mojang.com/browse/MC-310743) - The category headers in the Debug Options screen are still different than the other options screens
-   [MC-310757](https://bugs.mojang.com/browse/MC-310757) - In OIT shaders, `coefficients[0]` is accumulated using `depth` but subtracted using `originalDepth`
-   [MC-310771](https://bugs.mojang.com/browse/MC-310771) - The common abandoned camp map is named "Abandoned Campsite Map" instead of "Abandoned Camp Map"
-   [MC-310783](https://bugs.mojang.com/browse/MC-310783) - Resource packs with custom namespaces cause the "English (US)" language to fail to load
-   [MC-310787](https://bugs.mojang.com/browse/MC-310787) - Villagers do not level up until the trading window is closed for several seconds
-   [MC-310789](https://bugs.mojang.com/browse/MC-310789) - Chunks sometimes don't fade in correctly
-   [MC-310812](https://bugs.mojang.com/browse/MC-310812) - Placing and breaking cushions does not trigger sculk shriekers
-   [MC-310917](https://bugs.mojang.com/browse/MC-310917) - Chunk generation can corrupt on worlds upgraded from previous versions

---

# Minecraft 26.3 Snapshot 7

Step up your building and exploring with the final features entering testing! You can now find different maps in some abandoned camps and craft Concrete Stairs & Slabs in 16 colors. Out now in 26.3 Snapshot 7!

Happy exploring!

## New Features

-   Added Concrete Stairs and Concrete Slabs for all Concrete blocks
-   New Explorer Maps have been added to the Abandoned Camps

### Abandoned Camp Explorer Maps

-   Added maps showing the location of other Abandoned Camps in the following biomes:
    -   Bamboo Jungle
    -   Cherry Grove
    -   Birch Forest
    -   Dappled Forest
    -   Flower Forest
    -   Pale Garden
    -   Swamp
    -   Windswept Forest
-   Added maps for the following structures:
    -   Ancient City
    -   Trial Chambers
    -   Mineshaft
    -   Desert Pyramid
    -   Jungle Pyramid
    -   Warm Ocean Ruins
    -   Woodland Mansion

## Changes

-   Cushions no longer prevent vibrations when placed, broken or interacted with
-   Updated loot table for the Abandoned Camp Barrel
-   Replaced Firework Rocket with Gunpowder in Abandoned Camp Chest loot table
-   The player icon on maps have been updated to always show the direction the player is facing
-   Added support for Realms to use additional server regions in Canada, Mexico, South Africa, and Arizona, USA if they become available in the future

### Explorer Maps

-   Explorer Maps are now their own items instead of renamed Filled Maps, and each has its own icon:
    -   Ocean Explorer Map
    -   Woodland Explorer Map
    -   Trial Explorer Map
    -   Jungle Explorer Map
    -   Swamp Explorer Map
    -   Desert Village Map
    -   Plains Village Map
    -   Savanna Village Map
    -   Snowy Village Map
    -   Taiga Village Map
    -   Buried Treasure Map
    -   Ancient City Map
    -   Mineshaft Map
    -   Desert Pyramid Map
    -   Abandoned Campsite Map
    -   Warm Ocean Ruins Map
-   Map and Empty Map have new icons
-   These items cannot be obtained from the Creative inventory
-   Existing Explorer Maps in old worlds are converted to the matching new item on load
-   Explorer Maps can still be cloned in a Crafting Table, and the copies keep their own item type
-   Explorer Maps and Buried Treasure Maps can no longer be zoomed out, neither in a Crafting Table nor at a Cartography Table
    -   Buried Treasure Maps could previously be zoomed out at both
    -   Explorer Maps could previously be zoomed out at a Cartography Table
    -   Only maps in the `#minecraft:extendable_maps` tag can be zoomed out

## Technical Changes

-   The Data Pack version is now 115.0
-   The Resource Pack version is now 95.0
-   `level.dat` now contains a `version_history` list with prior data versions of the file

## Data Pack Version 115.0

-   The following Block State fields has been renamed
    -   `Name` is now `id`
    -   `Properties` is now `properties`
-   The default Block State of a Block can now be referred to in a compact form directly by the Block id
-   `minecraft:exploration_map` no longer changes the type of the item it is applied to

### Commands

**Changes to `swing`**

-   When used on a player, the player's attack strength will no longer be reset
-   Added a new optional argument to set the swing animation to play
    -   Allowed values: `whack`, `stab`
    -   If omitted, defaults to `whack`
-   Added a new argument to set the duration of the swing animation, if provided
    -   Format: positive time value (by default in ticks)
    -   If omitted, defaults to `6t`

### Data Components

**Added `minecraft:attack_animation`**

-   The animation to play when the item is being used to attack something
-   Format: object with fields:
    -   `type` - swing animation type, one of `whack` or `stab`
    -   `duration` - positive integer, the length of the animation in ticks

**Added `minecraft:interact_animation`**

-   The animation to play when the item is being used to interact with something
-   Format: Same as `minecraft:attack_animation`

**Removed `minecraft:swing_animation`**

-   This has been replaced by `minecraft:attack_animation` and `minecraft:interact_animation`
    -   The `none` swing animation type has been removed
    -   Existing items in the world will be migrated to using the default `whack`
    -   Setting both of these new components to the same value will be functionally identical to the old component, except for:
        -   The `/swing` command - animation type now specified by the command
        -   Items being dropped by entities

**Removed `minecraft:map_color`**

-   Maps are no longer drawn as a tinted overlay, so there is nothing left for the color to apply to
-   Existing maps have the component stripped on load
-   See the Resource Pack section for the matching removal of the `minecraft:map_color` tint source

### Loot Functions

**Changed `minecraft:exploration_map`**

-   The `map_color` field has now been removed
-   The function no longer changes the type of the item it is applied to - it now only adds map data to the existing item
    -   Previously it required a `minecraft:map` and produced a `minecraft:filled_map`
    -   The item to produce is now chosen by the loot entry or villager trade itself, so a data pack that produced exploration maps has to change its item from `minecraft:map` to `minecraft:filled_map` (or one of the explorer map items)
    -   If no matching structure is found, the item is left without a `minecraft:map_id` - use `minecraft:filtered` with `minecraft:discard_item` to drop those, as the vanilla loot tables and villager trades now do

### Density Functions

-   Density Functions and noises are no longer evaluated with double-precision floating point values, but instead with single-precision
    -   This affects all intermediate steps, not just the final result

> **Developer's Note**: ;;_;;We are aware that the details of floating point rounding have been used in some Data Packs, and this change may affect specific configurations. We have introduced alternatives for the use-cases that we are aware of, but please do share with us on [feedback.minecraft.net](https://feedback.minecraft.net) or in the [feedback Discord](https://discord.com/invite/minecraftfeedback) if you encounter use-cases that are no longer possible to support.

### Tags

**Block Tags**

-   Added `#concrete_stairs` - All Concrete Stairs blocks
-   Added `#concrete_slabs` - All Concrete Slabs blocks

**Item Tags**

-   Added `#concrete_stairs` - All Concrete Stairs items
-   Added `#concrete_slabs` - All Concrete Slabs items
-   Added `#cloneable_maps` - Filled Map plus all Explorer Map items and Buried Treasure Maps, used as the input to the `map_cloning` recipe
-   Added `#extendable_maps` - maps that can be zoomed out with paper, either in a Crafting Table or at a Cartography Table

## Resource Pack Version 95.0

### Item Sprites

-   Removed `item/filled_map_markings.png`

### Map Sprites

-   Added new Map textures:
    -   `abandoned_camp.png`
    -   `ancient_city.png`
    -   `desert_pyramid.png`
    -   `mineshaft.png`
    -   `warm_ocean_ruins.png`
-   The following Icons have been updated in order to show player rotation on the map:
    -   `/player.png`
    -   `/player_off_limits.png`
    -   `/player_off_map.png`

### Item Models

**Tint Sources**

-   Removed `minecraft:map_color`
    -   The `minecraft:map_color` component it read no longer exists

**Order-independent Transparency (OIT)-related Shader Changes**

Renamed defines:

-   `OIT_WAVELET_RANK` - was previously `WAVELET_RANK`
-   `OIT_COEFF_COUNT` - was previously `COEFF_COUNT`
-   `OIT_COEFF_ATTACHMENT_COUNT` - was previously `COEFF_ATTACHMENT_COUNT`

## Fixed bugs in 26.3 Snapshot 7

-   [MC-121375](https://bugs.mojang.com/browse/MC-121375) - The Command (⌘) key on macOS is displayed as "Win" in the key binds screen
-   [MC-189953](https://bugs.mojang.com/browse/MC-189953) - The Super key on macOS is displayed as "Win" in the key binds screen
-   [MC-218156](https://bugs.mojang.com/browse/MC-218156) - Shipwrecks and ocean ruins can generate with empty buried treasure maps
-   [MC-276079](https://bugs.mojang.com/browse/MC-276079) - Sending a swing packet to the client causes it to send one back to the server
-   [MC-302271](https://bugs.mojang.com/browse/MC-302271) - Sniffers stop sniffing after relog
-   [MC-302661](https://bugs.mojang.com/browse/MC-302661) - Interacting with something while holding spears plays the spear jab animation
-   [MC-302687](https://bugs.mojang.com/browse/MC-302687) - Throwing items out of your inventory while holding spears plays the spear jab animation
-   [MC-302705](https://bugs.mojang.com/browse/MC-302705) - Having a spear in the main hand affects the hand animation speed for items held in the off hand
-   [MC-304213](https://bugs.mojang.com/browse/MC-304213) - Zombies, husks and drowned hold out the incorrect arm when holding spears
-   [MC-304920](https://bugs.mojang.com/browse/MC-304920) - Spears in third person look wrong when the left hand is the main hand
-   [MC-309644](https://bugs.mojang.com/browse/MC-309644) - Some textures of geyser plume particles still use inconsistent colors
-   [MC-309671](https://bugs.mojang.com/browse/MC-309671) - Shelf mushrooms still use the wrong sounds
-   [MC-309679](https://bugs.mojang.com/browse/MC-309679) - Cushions can be used to see through blocks
-   [MC-309732](https://bugs.mojang.com/browse/MC-309732) - The `straw_bed_head` block model is stored in two directories
-   [MC-309797](https://bugs.mojang.com/browse/MC-309797) - Cushions can be placed inside full blocks when the player's head intersects them
-   [MC-309875](https://bugs.mojang.com/browse/MC-309875) - New translations for the tooltip of the "Improved Transparency" option are wrongly backported
-   [MC-309931](https://bugs.mojang.com/browse/MC-309931) - Placed cushions face inconsistent directions
-   [MC-310057](https://bugs.mojang.com/browse/MC-310057) - Pressing the "Advancements" key bind while its menu was opened from the pause menu closes both menus
-   [MC-310062](https://bugs.mojang.com/browse/MC-310062) - Armadillos do not follow players holding spider eyes
-   [MC-310094](https://bugs.mojang.com/browse/MC-310094) - The decimal point keypad key is displayed as "key.keyboard.99" in the key binds menu
-   [MC-310105](https://bugs.mojang.com/browse/MC-310105) - The Menu key is displayed as "key.keyboard.101" in the key binds menu
-   [MC-310109](https://bugs.mojang.com/browse/MC-310109) - The keypad plus-or-minus key is still not prefixed with "Keypad"
-   [MC-310110](https://bugs.mojang.com/browse/MC-310110) - The keypad left and right parentheses keys are still not prefixed with "Keypad"
-   [MC-310112](https://bugs.mojang.com/browse/MC-310112) - Using a Nether portal in Spectator mode while spectating an entity teleports the player to the incorrect location
-   [MC-310118](https://bugs.mojang.com/browse/MC-310118) - Pressing Windows+D to minimize all windows makes the game no longer visually update with the Vulkan rendering backend
-   [MC-310337](https://bugs.mojang.com/browse/MC-310337) - The game log outputs the incorrect minimum format version requiring the `pack_format` field in `pack.mcmeta`
-   [MC-310358](https://bugs.mojang.com/browse/MC-310358) - The conditions for `depthBiasEnable` differ between OpenGL and Vulkan
-   [MC-310529](https://bugs.mojang.com/browse/MC-310529) - The World Options menu UI breaks when resizing the game window
-   [MC-310532](https://bugs.mojang.com/browse/MC-310532) - Trying to lock the difficulty of the world resets the difficulty
-   [MC-310536](https://bugs.mojang.com/browse/MC-310536) - The category headers in the World Options screen are formatted inconsistently with other settings screens
-   [MC-310550](https://bugs.mojang.com/browse/MC-310550) - Command+W on macOS now closes the window
-   [MC-310553](https://bugs.mojang.com/browse/MC-310553) - The `campsite_wooded_badlands_4` and `campsite_swamp_2` abandoned camp structures contain overlapping cushions
-   [MC-310556](https://bugs.mojang.com/browse/MC-310556) - Pressing Alt+F4 closes the game window on kwin;;_;;wayland even when the "Quit Shortcuts" option is disabled
-   [MC-310590](https://bugs.mojang.com/browse/MC-310590) - Adding the `entity_outline` post effect to the player, restarting the game, and entering the same world causes the game to crash
-   [MC-310595](https://bugs.mojang.com/browse/MC-310595) - The Option key on macOS is displayed as "Alt" in the key binds screen
-   [MC-310610](https://bugs.mojang.com/browse/MC-310610) - Several abandoned camp structures contain underwater oxidized copper chests that are not waterlogged

---

