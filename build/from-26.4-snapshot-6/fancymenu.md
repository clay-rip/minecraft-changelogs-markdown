# Minecraft 26.4 Snapshot 6

It's getting chilly in here! This week's 26.4 Snapshot 6 brings snow bricks, a new set of building blocks for anyone who wants their builds to look even cooler ;) We're also adding a new archetype to the Sulfur Cube family: the Cold Sulfur Cube. It's a frosty little friend that knows a thing or two about ice.

Stay cool and happy building!

## New Features

-   Added Snow Bricks
-   Added new Cold Sulfur Cube archetype

### Snow Bricks

-   Snow Bricks can be crafted from 2x2 Snow Blocks
-   Snow Bricks have a Slab, Stair, and Wall variant
-   A Stonecutter cannot be used to craft Snow Brick Slabs, Stairs, and Walls
-   Snow Bricks belong to the Fast Sliding Sulfur Cube archetype
-   Snow Bricks only drop themselves if mined with a Shovel

### Cold Sulfur Cube Archetype

-   A new Sulfur Cube archetype that belongs to the special archetype category
-   It has the same properties as the Fast Sliding archetype, but floats and replaces water below it with a disk of Frosted Ice when it moves, similar to the Frost Walker enchantment
-   Air blocks above the water block are required for Frosted Ice placement
-   Will only place Frosted Ice if the Sulfur Cube starts its movement while it is on ground
-   Used when the Sulfur Cube absorbs a Blue Ice block

## Changes

-   Changed the default JVM options
-   Mobs falling through lava may take slightly less fall damage in some cases

### Minor Tweaks to Blocks, Items and Entities

-   All Packed Ice Brick variants will now require a pickaxe to be mined in order to drop themselves
-   Brittle Ice will no longer crack when a Stray is standing on top of it

### Sounds

-   Added ambient sounds to Ice Crystals
    -   An Ice crystal block has a chance of playing an ambient sound if it has a block of packed ice below

### Default JVM Options

-   The game now automatically sets its Java heap size based on your system's RAM, using up to 25% with a maximum of 4 GB

## Technical Changes

-   The Data Pack version is now 125.1
-   The Resource Pack version is now 101.0

## Data Pack Version 125.1

### Sulfur Cube Archetypes

-   Added new `location_based_effects` field - an optional list of location-based effects
    -   The format for each entry is exactly the same as a location-based enchantment effect
    -   Level-based values in this definition will always be evaluated with level `1`

### World Generation

**Density Functions**

**Changed `gradient`**

-   The `from_coordinate` and `to_coordinate` fields now additionally accept a Vertical Anchor, as long as `axis` is `y`

**Added `domain_warp`**

Samples an input function by applying an offset to each sampled coordinate.

Note: if the offsets change rapidly by large amount, performance may degrade significantly. This function should be used sparingly.

Format: object with fields:

-   `input` - Density Function, the input function to sample
-   `offset_x` - Density Function, the offset to apply to sampled X coordinates
    -   The result is implicitly truncated to an integer
    -   If not specified, defaults to: `0.0`
-   `offset_y` - Density Function, the offset to apply to sampled Y coordinates
    -   The result is implicitly truncated to an integer
    -   If not specified, defaults to: `0.0`
-   `offset_z` - Density Function, the offset to apply to sampled Z coordinates
    -   The result is implicitly truncated to an integer
    -   If not specified, defaults to: `0.0`

At least one of `offset_x`, `offset_y`, or `offset_z` must be specified.

**Structure Pool Elements**

**Added optional `corner_constraint` Field**

Limits the placement of a structure pool element this by sampling a Density Function at the corners of its bounding box.

Format: list of objects with fields:

-   `density_function` - the Density Function to sample at the bounding box' corner
-   `acceptable_density` - inclusive range of doubles, a corner's sampled density within this range counts as "inside"
-   `padding` - integer between `0` and `8`, the padding of the bounding box before sampling its corners
    -   If not present, defaults to `0`
-   `corners` - one of `all`, `top`, or `bottom`, which corners to check
    -   If not present, defaults to `all`
-   `required_corners` - range between `1` and `8`, the number of corners that must be inside `acceptable_density` for the check to pass

### Tags

**Fluid Tags**

-   Added `#swimmable` for fluids that players can swim in

**Item Tags**

-   Added `#sulfur_cube_archetype/cold` - items that can be placed inside the Sulfur Cube that turns it into a Cold Sulfur Cube archetype

**Entity Type Tags**

-   Added `#swimming` - entity types that are considered swimming in water
-   Added `#flying` - entity types that are considered flying

## Resource Pack Version 101.0

### Block Sprites

-   Added new Block textures:
    -   `block/snow_bricks.png`

### Sounds

-   Added new sound events:
    -   `block.ice_crystal.ambient`

### Block Models

-   Removed Block Models:
    -   `block/cube_top`

## Fixed bugs in 26.4 Snapshot 6

-   [MC-127491](https://bugs.mojang.com/browse/MC-127491) - Drowned, zombie villagers and zombified piglins have the `DrownedConversionTime` and `InWaterTime` tags
-   [MC-269319](https://bugs.mojang.com/browse/MC-269319) - Bringing the camera close to the player in third-person view underwater disables the water overlay and zoom effect
-   [MC-308361](https://bugs.mojang.com/browse/MC-308361) - Small sulfur cubes that split from bucketed sulfur cubes can despawn
-   [MC-311992](https://bugs.mojang.com/browse/MC-311992) - The code used to join a Realm is inconsistently referred to as both an "Invite Code" and a "Join Code"
-   [MC-311994](https://bugs.mojang.com/browse/MC-311994) - Delayed block breaking completes early or stalls
-   [MC-312016](https://bugs.mojang.com/browse/MC-312016) - The water overlay does not render when the player's head is against a block above them
-   [MC-312270](https://bugs.mojang.com/browse/MC-312270) - The game crashes when trying to open the inventory while spectating a mob
-   [MC-312384](https://bugs.mojang.com/browse/MC-312384) - Standing in fire or lava while under the effect of Freezing spams the fire extinguishing sound
-   [MC-312450](https://bugs.mojang.com/browse/MC-312450) - Jumping right before breaking a block makes the block reappear for a short amount of time
-   [MC-312489](https://bugs.mojang.com/browse/MC-312489) - The "How Did We Get Here?" advancement doesn't require the Freezing effect
-   [MC-312490](https://bugs.mojang.com/browse/MC-312490) - The "A Furious Cocktail" advancement doesn't require the Freezing effect
-   [MC-312501](https://bugs.mojang.com/browse/MC-312501) - The `multiplayer.other_players.not_available` string is missing a verb and is improperly capitalized
-   [MC-312529](https://bugs.mojang.com/browse/MC-312529) - The `gui.player_options.unfriend.confirm` string refers to the friends list as "your Friends", unlike similar strings
-   [MC-312530](https://bugs.mojang.com/browse/MC-312530) - The `options.hideMatchedNames.tooltip` string refers to muted players as "hidden players", unlike similar strings
-   [MC-312531](https://bugs.mojang.com/browse/MC-312531) - The `gui.abuseReport.discard.draft.overwrite` string uses the words "report draft" instead of "draft report", unlike similar strings
-   [MC-312532](https://bugs.mojang.com/browse/MC-312532) - Zombie villagers spawn as their plains variant in ice caves instead of the snowy one
-   [MC-312533](https://bugs.mojang.com/browse/MC-312533) - The `gui.abuseReport.draft.restart` string uses the verb "Start" instead of "Create", unlike similar strings
-   [MC-312574](https://bugs.mojang.com/browse/MC-312574) - Entities can crack and destroy brittle ice when the `mob_griefing` game rule is set to false
-   [MC-312576](https://bugs.mojang.com/browse/MC-312576) - Brittle ice can be cracked and destroyed by players inside spawn protection
-   [MC-312579](https://bugs.mojang.com/browse/MC-312579) - The game crashes when opening the inventory while a `below_name` scoreboard objective is active
-   [MC-312584](https://bugs.mojang.com/browse/MC-312584) - The chat messages report button claims chat is disabled or blocked when reporting friends from the title screen
-   [MC-312589](https://bugs.mojang.com/browse/MC-312589) - Frostbites, zombie villagers and zombified piglins have the `FrostbiteConversionTime` tag
-   [MC-312592](https://bugs.mojang.com/browse/MC-312592) - Gravel blobs generate in a different order than before, causing feature order cycles in data packs
-   [MC-312606](https://bugs.mojang.com/browse/MC-312606) - Sculk sensors are activated upon jukeboxes automatically switching discs in playlists
-   [MC-312610](https://bugs.mojang.com/browse/MC-312610) - Shulkers do not crack brittle ice when standing on it
-   [MC-312624](https://bugs.mojang.com/browse/MC-312624) - Lily pads cannot be placed on brittle ice
-   [MC-312625](https://bugs.mojang.com/browse/MC-312625) - Iron golems summoned by villagers can spawn on brittle ice
-   [MC-312629](https://bugs.mojang.com/browse/MC-312629) - Ice caves generate gravel, diorite, and andesite blobs twice
-   [MC-312632](https://bugs.mojang.com/browse/MC-312632) - Icicles and sulfur spikes are not part of the `#dangerous_for_teleportation` block tag, unlike pointed dripstone
-   [MC-312638](https://bugs.mojang.com/browse/MC-312638) - Music discs ejected from jukeboxes with chests above them spawn inside the chests
-   [MC-312639](https://bugs.mojang.com/browse/MC-312639) - Opening a screen while in a world automatically focuses a button if the tab or any of the arrow keys was used previously
-   [MC-312651](https://bugs.mojang.com/browse/MC-312651) - The bottom face of a jukebox uses its new texture when the "Programmer Art" resource pack is enabled
-   [MC-312665](https://bugs.mojang.com/browse/MC-312665) - The game crashes in the pause menu when the music toast is on and a music track cannot be played
-   [MC-312678](https://bugs.mojang.com/browse/MC-312678) - Spruce wall hanging signs use the oak map color on maps
-   [MC-312682](https://bugs.mojang.com/browse/MC-312682) - Lava can start fires next to crimson and warped shelves
-   [MC-312775](https://bugs.mojang.com/browse/MC-312775) - UI elements from screens behind popups can be hovered over with the mouse cursor
-   [MC-312778](https://bugs.mojang.com/browse/MC-312778) - Red and brown mushrooms can visually float on top of walls that have the `up` block state property set to false
-   [MC-312780](https://bugs.mojang.com/browse/MC-312780) - Oak, birch, spruce, and jungle trees no longer convert the block below their trunks into dirt
-   [MC-312783](https://bugs.mojang.com/browse/MC-312783) - Consumable and equippable items lose their default sounds after upgrading worlds
-   [MC-312801](https://bugs.mojang.com/browse/MC-312801) - Magma cubes stop being visible at a shorter distance than slimes and sulfur cubes of the same size
-   [MC-312804](https://bugs.mojang.com/browse/MC-312804) - Some villager trades still unexpectedly differ from 1.21.11

---

# Minecraft 26.4 Snapshot 5

This week's snapshot comes packed with a bunch of new things for you to try out! In 26.4 Snapshot 5, we're introducing Packed Ice Bricks, including a bunch of variants, and YES, they work in the Stonecutter! We've also got a frosty new advancement for anyone who decides to fight ice with ice and take out a Frostbite with an Ice Ball.

Happy Mining!

## New Features

-   Added Packed Ice Bricks

### Packed Ice Bricks

-   Packed Ice Bricks can be crafted from 2x2 Packed Ice
-   Packed Ice Bricks have a Slab, Stair, Wall, and Chiseled variant
-   Packed Ice Brick Slabs, Stairs, Walls, as well as Chiseled Packed Ice can also be crafted using a Stonecutter
-   Packed Ice Bricks and Chiseled Packed Ice belong to the Fast Sliding Sulfur Cube archetype

### Advancements

-   Added new "What Goes Around Comes Around" Adventure advancement for killing a Frostbite with an Ice Ball

## Changes

-   Mobs can now break Decorated Pots, Chorus Flowers and Speleothem blocks with projectiles in an adventure mode world, unless the `mob_griefing` gamerule is set to false

### Sounds

-   Added ambient sounds to regular Ice block
    -   When an Ice block is surrounded by at least 8 Ice blocks in all horizontal directions (east, west, north, and south), with one Air block above and one Water block below, it has a chance to emit a sound

### Video Settings

**"Prefer DXGI Present" Video Setting**

-   This is a new option to attempt to use DirectX to present the game
-   This only exists on Windows, and not all hardware supports it
-   The default is off, and we consider this option "experimental" - it may not work for everyone
-   With DXGI enabled, you _may_ see improvements with IME support, Variable Refresh Rate support, and faster alt-tabbing whilst in fullscreen mode

## Technical Changes

-   The Data Pack version is now 125.0
-   The Resource Pack version is now 100.2

### Network Protocol

**Modified Login Protocol**

-   Encryption and compression must now be explicitly applied by the server by sending one of two packets that carry connection options
    -   The client must acknowledge the change with a matching packet
    -   Every packet sent and received by the client after the acknowledgement will use the new settings
    -   Previously changes were applied immediately on both sides, which might've lead to malformed packets
-   Packets that can carry options:
    -   `minecraft:login_finished` (clientbound) and `minecraft:login_acknowledged` (serverbound)
    -   `minecraft:apply_options` (clientbound) and `minecraft:options_applied` (serverbound)

## Data Pack Version 125.0

### Data Components

**`minecraft:consumable`**

-   The `sound` field is now fully optional (defaulted to `minecraft:entity.generic.eat` before)

**`minecraft:equippable`**

-   The `equip_sound` field is now fully optional (defaulted to `minecraft:item.armor.equip_generic`)
-   The `shearing_sound` field is now fully optional (defaulted to `minecraft:item.shears.snip`)

### World Generation

**Features**

**Changed `ore` and `scattered_ore`**

-   Blocks discarded due to air exposure will no longer fall through to the next replacement rule

**Density Functions**

**Changed `upscale` (renamed from `interpolated`)**

Samples the input function at a reduced resolution, and upscales on each axis with the specified modes. Modes that require more samples will generally perform worse. Upscaling is performed by axis in order: Z, X, then Y.

Format: object with fields:

-   `input` - Density Function, the input function to sample
-   `x`, `y`, `z` - object with fields, the configuration for this axis
    -   `mode` - one of: `nearest_neighbor`, `interpolate_linear`, `interpolate_cosine`, `interpolate_cubic`, `b_spline_cubic`, the mode to use
        -   `nearest_neighbor`
            -   1 sample per axis
            -   Value is discontinuous across cell boundaries, gradient is always `0`
            -   Values at cell vertices always equal the cell value
        -   `interpolate_linear`
            -   2 samples per axis
            -   Value is continuous, gradient is constant within a cell but discontinuous across cell boundaries
            -   Values at cell vertices always equal the cell value
        -   `interpolate_cosine`
            -   2 samples per axis
            -   Value and gradient are continuous
            -   Gradient is `0` at cell boundaries
            -   Values at cell vertices always equal the cell value
        -   `interpolate_cubic`
            -   4 samples per axis
            -   Value and gradient are continuous
            -   Values at cell vertices always equal the cell value
        -   `b_spline_cubic`
            -   4 samples per axis
            -   Value and gradient are continuous
            -   Values at cell vertices do not necessarily equal the cell value
    -   `cell_size` - integer between 1 and 64, the size of each upscaling cell

### Tags

**Biome Tags**

-   Added `#spawns_ice_variants_underground` to describe all biomes which allow the spawning of cold variants without requiring sky access
-   Renamed `spawns_strays_without_powder_snow` to `spawns_cold_variants_underground`

**Entity Type Tags**

-   Replaced the `#ignores_poison_and_regen` tag with separate `#immune_to_poison` and `#immune_to_regeneration` tags
-   Renamed the `#freeze_immune_entity_types` tag to `#immune_to_freezing`
-   Added `#immune_to_wither` for mobs that are immune to the wither effect
-   Added `#immune_to_weakness` for mobs that are immune to the weakness effect

## Resource Pack Version 100.2

### Block Sprites

-   Added new Block textures:
    -   `block/chiseled_packed_ice.png`
    -   `block/packed_ice_bricks.png`

## Fixed bugs in 26.4 Snapshot 5

-   [MC-25976](https://bugs.mojang.com/browse/MC-25976) - Blocks broken by flowing fluids do not produce particles or make breaking sounds
-   [MC-170550](https://bugs.mojang.com/browse/MC-170550) - The `snowy_shepherds_house_1` village structure never generates
-   [MC-270793](https://bugs.mojang.com/browse/MC-270793) - Mobs with multiple entity type tags corresponding to effect immunity only respect one
-   [MC-308621](https://bugs.mojang.com/browse/MC-308621) - Race condition in the dedicated server's compression setup
-   [MC-312316](https://bugs.mojang.com/browse/MC-312316) - Creakings still try to attack players after they switch to Creative mode
-   [MC-312360](https://bugs.mojang.com/browse/MC-312360) - Paintings break outside the world border
-   [MC-312377](https://bugs.mojang.com/browse/MC-312377) - The bottom face of icicles on the floor is rotated 180 degrees
-   [MC-312386](https://bugs.mojang.com/browse/MC-312386) - The `#spawns_strays_without_powder_snow` biome tag's name makes no sense
-   [MC-312404](https://bugs.mojang.com/browse/MC-312404) - Frostbites can naturally spawn in normal caves under cold biomes, unlike strays
-   [MC-312431](https://bugs.mojang.com/browse/MC-312431) - Red and brown mushrooms now spread incorrectly
-   [MC-312496](https://bugs.mojang.com/browse/MC-312496) - Icicle models use the deprecated `shade` field
-   [MC-312497](https://bugs.mojang.com/browse/MC-312497) - Template models for icicles are not prefixed with `template_`
-   [MC-312563](https://bugs.mojang.com/browse/MC-312563) - The icicle in the Creative mode inventory is placed in the wrong spot
-   [MC-312587](https://bugs.mojang.com/browse/MC-312587) - The game crashes when trying to render the hidden tooltips of music discs in jukebox playlists
-   [MC-312612](https://bugs.mojang.com/browse/MC-312612) - Jukeboxes can pull from double chests if a single chest was turned into a double chest after being placed
-   [MC-312613](https://bugs.mojang.com/browse/MC-312613) - Jukeboxes don't pull discs from single chests that are created by breaking a double chest
-   [MC-312621](https://bugs.mojang.com/browse/MC-312621) - Zombies, husks, drowned, strays, and frostbites are now affected by Poison and Regeneration
-   [MC-312630](https://bugs.mojang.com/browse/MC-312630) - Ruined portals don't generate in ice caves
-   [MC-312631](https://bugs.mojang.com/browse/MC-312631) - Ice caves are not part of the `#stronghold_biased_to` biome tag
-   [MC-312640](https://bugs.mojang.com/browse/MC-312640) - Any mouse button can be used to select entries in the statistics menu
-   [MC-312641](https://bugs.mojang.com/browse/MC-312641) - Any mouse button can be used to open links on the death screen
-   [MC-312642](https://bugs.mojang.com/browse/MC-312642) - Pointed dripstone below flowing lava drips water instead of lava
-   [MC-312644](https://bugs.mojang.com/browse/MC-312644) - Dispensers filling glass bottles don't play the bottle filling sound
-   [MC-312645](https://bugs.mojang.com/browse/MC-312645) - Dispensers equipping chests on donkeys, mules or llamas don't play the chest equipping sound
-   [MC-312652](https://bugs.mojang.com/browse/MC-312652) - Flint and steel and fire charges don't make a sound when igniting sulfur cubes holding TNT
-   [MC-312654](https://bugs.mojang.com/browse/MC-312654) - Dispensers consume the durability of flint and steel and play their clicking sound despite there being nothing to ignite
-   [MC-312669](https://bugs.mojang.com/browse/MC-312669) - Any mouse button can be used to close the friends and other players menus when clicking outside of them
-   [MC-312693](https://bugs.mojang.com/browse/MC-312693) - Projectiles shot by mobs can no longer break decorated pots, chorus flowers, pointed dripstone, sulfur spikes, or icicles
-   [MC-312715](https://bugs.mojang.com/browse/MC-312715) - The game crashes when a jukebox in a playlist has a negative `playlist_position` value
-   [MC-312717](https://bugs.mojang.com/browse/MC-312717) - Mobs can spawn on honey blocks

---

# Minecraft 26.4 Snapshot 4

With 26.4 Snapshot 4, we're breaking out a cool new block, introducing Brittle Ice! And Jukeboxes can now keep the music going with playlists by putting your music discs in a chest above them, making dance parties much easier. Just be careful not to dance on the Brittle Ice, as it'll start cracking under your feet...

Happy Dance Break!

## New Features

-   Added Jukebox Playlists
-   Added Brittle Ice

### Jukebox Playlists

-   Place a single Chest, Trapped Chest, or any Copper Chest variant directly above a Jukebox to use its Music Discs as a playlist
-   Discs play in slot order, skipping empty slots and other non-music-disc items and looping back to the start
-   When a disc finishes, the Jukebox swaps it with the next disc in the chest
-   If the chest has no Music Discs, the disc in the Jukebox plays again
-   Ejecting the current disc skips to the next available disc

### Brittle Ice

-   Brittle Ice is a new block that can be found in Ice Caves
-   Once a player or mob steps on it, it will start to crack and eventually break
-   The Frostbite mob can walk on Brittle Ice without breaking it
-   Brittle Ice only generates naturally in Ice Caves as part of the crevasse feature
-   It is obtainable with Silk Touch
-   It can also be created by water flowing onto a Blue Ice block
    -   Any water block that borders the Blue Ice block horizontally will turn into Brittle Ice

## Changes

### Minor Tweaks to Blocks, Items and Entities

-   Frosted Ice now emits a vibration event when changing state
-   Ice, Frosted Ice, and Brittle Ice will no longer show their inside block faces when placed next to each other
-   Zombies, Drowned, and Husks are now immune to freezing and will not take damage from the Freezing effect
-   Drowned now turn into a Zombie before converting into a Frostbite when they are in Powder Snow

### Sounds

-   Added custom sounds for Ice, Packed Ice, Blue Ice and Frosted Ice blocks
-   Renamed `minecraft:amethyst` block sound set to `minecraft:amethyst_block` to better match sound event names

## Technical Changes

-   The Data Pack version is now 124.0
-   The Resource Pack version is now 100.1

### Network Protocol

-   The server now more consistently disconnects clients when a packet they sent causes an error

## Data Pack Version 124.0

### Sound events

-   Removed sound events:
    -   `minecraft:intentionally_empty`

### Sulfur Cube Archetypes

-   Fields `hit_sound` and `push_sound` in `sound_settings` structure are now optional

### Chicken Sound Variants

-   Fields `ambient_sound`, `hurt_sound`, `death_sound`, `step_sound` in `adult_sounds` and `baby_sounds` structures are now optional

### Cow Sound Variants

-   Fields `ambient_sound`, `hurt_sound`, `death_sound`, `step_sound` are now optional

### Cat Sound Variants

-   Fields `ambient_sound`, `stray_ambient_sound`, `hiss_sound`, `hurt_sound`, `death_sound`, `eat_sound`, `beg_for_food_sound`, `purr_sound`, `purreow_sound` in `adult_sounds` and `baby_sounds` structures are now optional

### Pig Sound Variants

-   Fields `ambient_sound`, `hurt_sound`, `death_sound`, `step_sound`, `eat_sound` in `adult_sounds` and `baby_sounds` structures are now optional

### Wolf Sound Variants

-   Fields `ambient_sound`, `hurt_sound`, `death_sound`, `step_sound`, `growl_sound`, `pant_sound`, `whine_sound` in `adult_sounds` and `baby_sounds` structures are now optional

### Fluid States

-   Removed `flowing_water` and `flowing_lava` fluid types
-   Fluid types now have the following properties
    -   `level`: Integer; same as before, the level of fluid from 1 to 8
    -   `source`: Boolean; true for source blocks, false otherwise

### Predicates

**Block Predicates**

**Updated `matching_fluids`**

Added a `state` field to match state properties

Format:

-   `state`: A map of name-value properties to be matched against the fluid state properties
    -   Value can be integer, boolean or string or object with optional `min` and `max` properties

### Enchantments

**Changed `minecraft:explode` Enchantment Effect**

-   Fields `small_particle`, `large_particle` and `sound` are now optional

### World Generation

**Features**

**Added `crevasse` Feature Type**

Carves a winding, tapered crevasse into exposed terrain. The crevasse follows the terrain surface, extends in opposite directions from its placement position and requires a minimum connected footprint before carving.

-   Format: object with fields:
    -   `max_width` - integer (between 2 and 8), maximum cross-section width in blocks
    -   `max_length` - integer (between 4 and 16), maximum end-to-end length in blocks
    -   `min_footprint` - integer (between 1 and 32), minimum connected horizontal footprint required before carving
    -   `cursor_surface_search_range` - positive integer, maximum amount of blocks the cursor will scan downwards to find its next position
    -   `column_surface_search_range` - positive integer, maximum amount of blocks each carving will scan downwards to find a carvable surface
    -   `twistiness` - float (between 0.0 and 16.0), amount of horizontal curvature
    -   `tapering` - float (between 0.0 and 1.0), amount of tapering applied on each step of growing the crevasse
    -   `turn_factor` - float (between 0.0 and 1.0), intensity of rotation applied on each step of growing the crevasse
    -   `carve_depth` - int provider, carve depth below the origin terrain surface
    -   `fill_depth` - int provider, fill depth below the origin terrain surface
    -   `surface_block` - Block state provider, block placed over the crevasse opening
    -   `fill_block` - Block state provider, block placed at or below the selected fill depth
    -   `carvable_blocks` - Block predicate, which blocks the crevasse is allowed to remove
    -   `acceptable_barrier` - Block predicate, which pre-existing blocks to accept as part of a barrier

### Tags

**Block Tags**

-   Added block tag `#jukebox_containers` to describe all blocks usable by a Jukebox as a source for music disc playlists
-   Added block tag `#face_occluding_ice_blocks` to describe all ice blocks that should enable face culling when placed next to each other

**Entity Type Tags**

-   Added the entity type tag `#does_not_break_brittle_ice` for mobs that do not break Brittle Ice blocks when stepping on them

## Resource Pack Version 100.1

### Block Sprites

-   Updated the following Block textures:
    
    -   `block/jukebox_side.png`
    -   `block/jukebox_top.png`
-   Added new Block textures:
    
    -   `block/brittle_ice_0.png`
    -   `block/brittle_ice_1.png`
    -   `block/brittle_ice_2.png`
    -   `block/brittle_ice_3.png`
    -   `block/jukebox_bottom.png`

### Sounds

-   Added new sound events:
    -   `block.blue_ice.break`
    -   `block.blue_ice.fall`
    -   `block.blue_ice.hit`
    -   `block.blue_ice.place`
    -   `block.blue_ice.step`
    -   `block.brittle_ice.break`
    -   `block.brittle_ice.fall`
    -   `block.brittle_ice.hit`
    -   `block.brittle_ice.place`
    -   `block.brittle_ice.step`
    -   `block.brittle_ice.crack`
    -   `block.frosted_ice.break`
    -   `block.frosted_ice.fall`
    -   `block.frosted_ice.hit`
    -   `block.frosted_ice.place`
    -   `block.frosted_ice.step`
    -   `block.ice.ambient`
    -   `block.packed_ice.break`
    -   `block.packed_ice.fall`
    -   `block.packed_ice.hit`
    -   `block.packed_ice.place`
    -   `block.packed_ice.step`
    -   `entity.drowned.converted_to_zombie`

## Fixed bugs in 26.4 Snapshot 4

-   [MC-80827](https://bugs.mojang.com/browse/MC-80827) - Mob statistics are missing space between the mob's name and the description
-   [MC-148455](https://bugs.mojang.com/browse/MC-148455) - Dispensing an item with special behavior only plays the item's usage sound for certain cases
-   [MC-149032](https://bugs.mojang.com/browse/MC-149032) - Clicking non-button areas of the stonecutter block selection GUI plays a clicking sound
-   [MC-163196](https://bugs.mojang.com/browse/MC-163196) - Several blocks which can be placed on the sides of slime blocks cannot be placed on the sides of honey blocks
-   [MC-166792](https://bugs.mojang.com/browse/MC-166792) - Attempting to navigate beyond the 100 page limit in a book and quill plays the page rustling sound
-   [MC-195474](https://bugs.mojang.com/browse/MC-195474) - Can't move focus away from the "Done" button after pressing Tab to focus on it in the sign editing screen
-   [MC-207916](https://bugs.mojang.com/browse/MC-207916) - Flint and steel and fire charges do not make a sound when igniting TNT
-   [MC-251040](https://bugs.mojang.com/browse/MC-251040) - Several blocks which can be placed on top of slime blocks cannot be placed on top of honey blocks
-   [MC-251041](https://bugs.mojang.com/browse/MC-251041) - Several blocks which can be placed on the bottom of slime blocks cannot be placed on the bottom of honey blocks
-   [MC-275975](https://bugs.mojang.com/browse/MC-275975) - The "Unknown element name" codec error is missing a space
-   [MC-280455](https://bugs.mojang.com/browse/MC-280455) - Items equippable on the saddle slot that have a custom equipping sound do not play the specified sound when saddling entities
-   [MC-280480](https://bugs.mojang.com/browse/MC-280480) - The flint and steel clicking sound is not played when attempting to ignite TNT with a flint and steel when the `tnt_explodes` game rule is set to false
-   [MC-304895](https://bugs.mojang.com/browse/MC-304895) - The overworld sky is no longer black in End biomes
-   [MC-305544](https://bugs.mojang.com/browse/MC-305544) - Using the middle mouse button in Survival/Creative/Adventure mode and switching to Spectator mode opens the Spectator mode hotbar
-   [MC-307672](https://bugs.mojang.com/browse/MC-307672) - The `name_tag_distance` attribute overrides the `below_name_distance` attribute
-   [MC-309335](https://bugs.mojang.com/browse/MC-309335) - Any mouse button can be used to interact with entries in the world, server, and language selection screens
-   [MC-309336](https://bugs.mojang.com/browse/MC-309336) - Any mouse button can be used to select and apply command autocomplete suggestions
-   [MC-310088](https://bugs.mojang.com/browse/MC-310088) - The taskbar icon displays the Java logo instead of the game's logo
-   [MC-311312](https://bugs.mojang.com/browse/MC-311312) - Endermen and entities eating chorus fruit can still pass through the world border
-   [MC-312200](https://bugs.mojang.com/browse/MC-312200) - "Vegetation" is misspelled as "Vegitation" on the debug overlay
-   [MC-312201](https://bugs.mojang.com/browse/MC-312201) - "Continents" is misspelled as "Contintents" on the debug overlay
-   [MC-312242](https://bugs.mojang.com/browse/MC-312242) - Mushrooms cannot be placed on thin blocks that provide central support, unlike in Bedrock Edition
-   [MC-312256](https://bugs.mojang.com/browse/MC-312256) - Breaking an armor stand in one hit does not trigger sculk shriekers
-   [MC-312273](https://bugs.mojang.com/browse/MC-312273) - The placement sound is not played when a dispenser places an armor stand
-   [MC-312362](https://bugs.mojang.com/browse/MC-312362) - Frostbites throwing ice balls shows and plays the "Drowned throws Trident" sound in closed captions
-   [MC-312367](https://bugs.mojang.com/browse/MC-312367) - The closed caption for hurting a frostbite says "hurts" instead of "is hurt"
-   [MC-312378](https://bugs.mojang.com/browse/MC-312378) - Ice caves are not part of the `#is_cave` biome tag
-   [MC-312379](https://bugs.mojang.com/browse/MC-312379) - Gravel blobs no longer generate in biomes they previously did
-   [MC-312382](https://bugs.mojang.com/browse/MC-312382) - Husks and zombies take damage from powder snow before converting, unlike skeletons
-   [MC-312383](https://bugs.mojang.com/browse/MC-312383) - Frostbites convert to themselves while in powder snow
-   [MC-312385](https://bugs.mojang.com/browse/MC-312385) - Drowned die in powder snow instead of converting to frostbites
-   [MC-312398](https://bugs.mojang.com/browse/MC-312398) - Clicking on villagers with shears while they are holding out certain items causes the items to drop
-   [MC-312415](https://bugs.mojang.com/browse/MC-312415) - The closed caption for husks converting to zombies in powder snow is incorrect
-   [MC-312456](https://bugs.mojang.com/browse/MC-312456) - Mobs immune to freezing in powder snow can get the Freezing effect applied to them, unlike frostbites

---

