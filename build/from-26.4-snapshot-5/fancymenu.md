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

# Minecraft 26.4 Snapshot 3

Brr! Does it feel colder all of a sudden? Minecraft LIVE revealed the first look at our next game drop – and it's frosty. Explore ice caves filled with glittering icicles and ice crystals, plus meet a not-so-chill new hostile mob! This frozen zombie variant is well adapted to colder conditions and can freeze players with its attacks. We're super excited to hear what you think about the new features. Make sure to visit our feedback site at [https://aka.ms/mc-gamedrop;;_;;winter26](https://aka.ms/mc-gamedrop_winter26) and leave your thoughts!

Beyond the frozen depths, we've also made a number of improvements to Friends! The Friends list has received a refreshed design, along with new search and sorting options to make it easier to find, organize, and manage your friends. So grab your friends and explore!

Happy ice-caving!

## New Features

-   Added the new Ice Caves Biome
-   Added Ice Crystals
-   Added Icicles
-   Added the Frostbite mob
-   Added the Freezing mob effect
-   Added the Ice Ball

### Ice Caves

-   The Ice Cave is a new cave biome that can generate under the colder biomes in the Overworld
-   It consists mainly of Packed Ice and Calcite
-   Icicles generate hanging from the ceiling
-   Large Icicles made of Packed Ice generate on the ground and hanging from the ceiling
-   Patches of Snow occasionally generate on the ground
-   Ores generate embedded in pockets of Stone and Deepslate
-   Glow Lichen does not generate in this biome
-   In addition to the mobs that normally spawn in caves, Strays and Frostbites can also spawn here
-   Ice Crystals occasionally generate on the ground

### Ice Crystal

-   A new crystal-like block similar to Amethyst Clusters
-   Breaks if the support block is removed
-   It emits light and can be placed in any direction

### Icicle

-   A new speleothem-like block similar to Dripstone and Sulfur Spikes
-   Icicles can be found all over the ceiling of ice caves
-   Can naturally grow up to 5 blocks long when pointing downward
-   Only grows in areas without nearby light sources and outside the Nether
-   It can be placed in any direction and has a base, middle and tip variant
-   Damages entities when it falls and deals extra damage to entities that land on it
-   Pointed blocks break when exposed to nearby light sources or when placed in the Nether

### Frostbite

-   The Frostbite is a zombie variant that can throw Ice Balls
-   Spawns in cold/icy biomes
-   Switches between melee and ranged combat based on target distance and whether they have Ice Balls
-   Melee attacks apply Freezing, while ranged attacks throw Ice Balls
-   Transforms into a Zombie when underwater for long enough
-   Drops Rotten Flesh and Ice Balls
-   It can stand on top of Powder Snow
-   It is immune to freezing and does not get slowed by the Freezing effect or Powder Snow
-   Zombies and Husks transform into Frostbites when inside Powder Snow

### Freezing Mob Effect

-   The Freezing effect will cause players to shake and eventually deal damage
-   Causes those affected to slowly become frozen as if in Powdered Snow for its duration
-   Leather Armor protects from freezing, just like with Powder Snow, but will not keep the effect from being applied and will not remove the effect
-   Mobs will take additional damage from Freezing while they are affected by this effect
    -   Mobs that are vulnerable to Freezing have a five times multiplier to the damage taken
-   Lingering Potion, Splash Potion, and Potion of Freezing can be brewed using Ice Balls
-   Arrows of Freezing can be crafted by placing a Lingering Potion of Freezing in the middle of the crafting table surrounded by eight Arrows

### Ice Ball

-   Ice Balls are new projectile used by the Frostbite
-   They deal a small amount of damage and have knockback
-   Deals 4 damage to entities it hits, scaling down with velocity
-   Breaks on impact with blocks or entities, creating a particle effect and sound

## Changes

### Minor Tweaks to Blocks, Items and Entities

-   Snow can now be placed on Packed Ice
-   Snowballs now apply knockback to players

### UI

-   Lightmap visualization is now configurable as `lightmap_texture` in debug options and appears in the Light group
    -   Its visibility setting is saved with the debug profile
    -   It can now be displayed alongside the FPS and network charts
-   The Social Interactions screen has been replaced with the new Other Players screen
-   The "Social Interactions" keybind has been renamed to "Other Players"
-   The Friends button has received a new icon
-   The "Visibility" option has been moved from Online Options into the Friends list
-   The icon buttons in the pause menu have been reordered to match the main menu

**Friends**

-   Updated the design of the Friends list
-   Added searching
    -   In the Friends tab, the profile name text box used for sending requests also functions as a search box
    -   In the requests tab, a search box appears at the top if you have 15 or more requests
-   Added sorting
    -   Sort modes can be cycled through by pressing the new sort button
    -   The current sort modes are:
        -   Sort by who's online - friends who are listed as online appear at the top of the list
        -   Sort by alphabetical order - friends are sorted according to the alphabetical order of their names
-   Clicking on a player's icon in the Friends list now opens their Player Options
-   Removed "Remove Friend" button
    -   This functionality is now accessible through Player Options instead

**Player Options**

Player Options is a new screen accessible through both the Friends list and Other Players.

-   It contains per-player social actions previously spread across the Friends list and Social Interactions
-   These actions are:
    -   Sending or canceling a friend request
    -   Accepting or declining a friend request
    -   Muting a player
    -   Reporting a player
-   Muting a player hides their chat messages until the next time you start the game
-   Blocking players is managed through Other Players

**Other Players**

Other Players is a new menu which has been added to replace Social Interactions.

-   Other Players is only available when playing on a world open to multiplayer
    -   This includes:
        -   Playing in singleplayer worlds open to LAN
        -   Playing on dedicated servers
        -   Playing on Realms
    -   It can be opened by pressing the "Other Players" icon button in the pause menu
    -   It can also be opened from in-game using the "Other Players" key ('P' by default)
-   It lists the players currently online in the world you are in
-   It lists players who are not online anymore, but may still be of interest:
    -   Players who were just online but left
    -   Players who recently sent messages in the chat
-   Clicking on a player's icon in the list opens their Player Options

**Player Reporting**

-   Redesigned the save/discard draft confirmation screen
-   Player reports saved as drafts no longer prompt you to discard them upon exiting a world if they can be continued later
    -   Chat reports can never be continued
    -   Name reports can be continued if the reported player is in your Friends list
    -   Skin reports can be continued if the reported player is in your Friends list
-   Pressing "Quit Game" in the main menu will now give a warning if you have an unsent draft report that would be lost

**Debug Overlay**

-   A new `chunk_section_status` shows the rendering status of chunks around you. This will impact performance at high view distances.
-   The chunk load overlay has been split off from `visualize_chunks_on_server` and into a new `chunk_load_status`

## Technical Changes

-   The Data Pack version is now 123.0
-   The Resource Pack version is now 100.0

## Data Pack Versions 122.0 through 123.0

### World Generation

**Features**

**Changed `minecraft:speleothem_cluster`**

-   Added `placement_options` - a field that contains various settings for the placement of the Speleothem cluster:
    -   `placement_mode` - represented by an enum that is one of `floor_and_ceiling`, `floor_only`, `ceiling_only`
    -   `base_block_transformer` - sets a state on the base block of the Speleothem block
        -   `none` - the regular base block state used in Sulfur Spikes and Dripstone Spikes
        -   `set_attached` - the state of the base block of the Icicle when it is attached to a surface
    -   `allow_water_placement` - boolean indicating whether the Speleothem can be placed in water or not

**Changed `minecraft:large_dripstone` (renamed from `minecraft:large_speleothem`)**

-   Added field `base_block` - Block State Provider, the block to build the large dripstone out of

**Noise Settings**

-   Added new Noises:
    -   `ice_cave_gradient`

**Feature Placements**

-   Added the following Ore Placements:
    -   `ice_cave_ore_coal_upper`
    -   `ice_cave_ore_coal_lower`
    -   `ice_cave_ore_copper`
    -   `ice_cave_ore_diamond`
    -   `ice_cave_ore_diamond_medium`
    -   `ice_cave_ore_diamond_large`
    -   `ice_cave_ore_diamond_buried`
    -   `ice_cave_ore_iron_upper`
    -   `ice_cave_ore_iron_middle`
    -   `ice_cave_ore_iron_small`
    -   `ice_cave_ore_gold`
    -   `ice_cave_ore_gold_lower`
    -   `ice_cave_ore_lapis`
    -   `ice_cave_ore_lapis_buried`
    -   `ice_cave_ore_redstone`
    -   `ice_cave_ore_redstone_lower`
    -   `ice_cave_ore_andesite_upper`
    -   `ice_cave_ore_andesite_lower`
    -   `ice_cave_ore_diorite_upper`
    -   `ice_cave_ore_diorite_lower`
    -   `ice_cave_ore_gravel`
-   These are all identical to their non-ice-cave counterparts, only that they place a patch of stone or deepslate (depending on y-level) before placing the ore itself
    -   They can replace Ice and Calcite as well

### Block Sound Sets

Added `minecraft:block_sound_set` registry containing definitions for sounds produced by different categories of blocks.

Format: object with fields:

-   `volume` - a float between `0.00001` and `10.0`, the relative volume at which all sounds will be played
    -   If not present, defaults to `1.0`
-   `pitch` - a float between `0.00001` and `2.0`, the relative pitch at which all sounds will be played
    -   If not present, defaults to `1.0`
-   `break_sound` - Sound Event, the sound that will be played when the block gets broken
-   `step_sound` - Sound Event, the sound that will be played when an entity walks on top of the block
-   `place_sound` - Sound Event, the sound that will be played when the block gets placed
-   `hit_sound` - Sound Event, the sound that will be played while the block is being destroyed
-   `fall_sound` - Sound Event, the sound that will be played when an entity falls onto the block
-   All sound fields are optional

### Tags

**Block Tags**

-   Added block tag `ice_cave_ore_replaceables` to describe all blocks which are allowed to be replaced by ores within Ice Caves (in addition to `stone_ore_replaceables`, `height_specific_ore_replaceables` and `deepslate_ore_replaceables`)
-   Added block tag `melts_icicle_above` to describe all blocks causing Icicles directly above to melt
-   Added block tag `large_icicle_replaceable` to describe all blocks which are allowed to be replaced by Large Icicles within the Ice Caves biome
-   Added several block tags to affect how mobs pathfind:
    -   `#pathfinding/avoid_in_air` - blocks to be avoided while flying, either due to danger our potential to get stuck
    -   `#pathfinding/damage_cautious` - blocks that will damage entities that walk through them, but are not considered dangerous enough to avoid entirely
    -   `#pathfinding/damaging` - blocks that will damage entities that walk through them
    -   `#pathfinding/drop_down` - blocks that can be dropped down through
    -   `#pathfinding/leaves` - blocks that are considered leaves
    -   `#pathfinding/open` - blocks that are considered completely open to walk through
    -   `#pathfinding/powder_snow` - blocks that are considered powder snow
    -   `#pathfinding/rails` - blocks that are considered rails
    -   `#pathfinding/sticky` - blocks that are considered sticky, causing slowed movement and inability to jump

**Item Tags**

-   Added `#frostbite_preferred_weapons` for items picked up and used by the Frostbite
-   Added `#knocks_back_players_even_with_zero_damage` for items which shall apply knockback even if they do 0 damage
-   Added `#sheep_wool_dyes` - items that can be used to dye a Sheep's wool
    -   The color will be taken from the `minecraft:dye` component of the used item stack

**Biome Tags**

-   Added `#spawns_strays_without_powder_snow` to describe all biomes which allow the spawning of strays without requiring powder snow on the surface above them

**Block Sound Set Tags**

-   Added `#sounds_wooden` - block sound sets which when stepped on cause Horses to produce a galloping sound

### Particles

-   Removed particle type `minecraft:item_snowball`

**Added `minecraft:freezing`**

-   Emitted by Entities which are affected by the Freezing mob effect
-   Has no fields

## Resource Pack Versions 98.0 through 100.0

### Block Sprites

-   Added new Block texture:
    -   `block/ice_crystal.png`
-   Added new Block textures:
    -   `block/ice_crystal.png`
    -   `block/icicle_down_base.png`
    -   `block/icicle_down_frustum.png`
    -   `block/icicle_down_middle.png`
    -   `block/icicle_down_tip.png`
    -   `block/icicle_down_tip_merge.png`
    -   `block/icicle_side.png`
    -   `block/icicle_top.png`

### Item Sprites

-   Added new Item texture:
    -   `item/ice_crystal.png`
-   Added new Item texture:
    -   `item/frostbite_spawn_egg.png`
    -   `item/ice_ball.png`
    -   `item/ice_crystal.png`
    -   `item/icicle.png`

### UI Sprites

-   Added new UI textures:
    -   `mob_effect/freezing.png`
    -   `friends/background_light.png`
    -   `friends/presence_all.png`
    -   `friends/presence_limited.png`
    -   `friends/presence_none.png`
    -   `friends/profile.png`
    -   `friends/profile_highlighted.png`
    -   `friends/sort_alphabetical.png`
    -   `friends/sort_presence.png`
    -   `friends/tab_selected.png`
    -   `pause_menu/other_players.png`
-   The following textures have been renamed:
    -   `friends/button.png` -> `friends/tab.png`
    -   `friends/button_highlighted.png` -> `friends/tab_highlighted.png`
    -   `friends/loading.png` -> `widget/loading.png`
    -   `pause_menu/social_interactions.png` -> `pause_menu/feedback.png`
-   The following textures have been removed:
    -   `friends/button_disabled.png`
    -   `friends/remove.png`
    -   `pause_menu/player_reporting.png`
    -   `toast/social_interactions.png`

### Entity Textures

-   Added new Entity textures:
    -   `entity/zombie/frostbite.png`
    -   `entity/zombie/frostbite_baby.png`
    -   `entity/zombie/frostbite_outer_layer.png`

### Sounds

-   Added new sound events:
    -   `entity.frostbite.ambient`
    -   `entity.frostbite.death`
    -   `entity.frostbite.hurt`
    -   `entity.frostbite.step`
    -   `block.ice.break`
    -   `block.ice.fall`
    -   `block.ice.hit`
    -   `block.ice.place`
    -   `block.ice.step`
    -   `block.ice_crystal.break`
    -   `block.ice_crystal.fall`
    -   `block.ice_crystal.hit`
    -   `block.ice_crystal.place`
    -   `block.ice_crystal.step`
    -   `block.icicle.break`
    -   `block.icicle.fall`
    -   `block.icicle.hit`
    -   `block.icicle.place`
    -   `block.icicle.step`
    -   `block.icicle.land`
    -   `entity.ice_ball.break`
    -   `entity.ice_ball.throw`

### Particles

-   Added new Particle textures:
    -   `particle/freezing_0.png`
    -   `particle/freezing_1.png`
    -   `particle/freezing_2.png`
    -   `particle/freezing_3.png`
    -   `particle/freezing_4.png`
    -   `particle/freezing_5.png`

### Item Models

-   Added new Item Models:
    -   `item/icicle`

### Block Models

-   Added new Block Models:
    -   `block/icicle`
    -   `block/icicle_base`

## Fixed bugs in 26.4 Snapshot 3

-   [MC-212616](https://bugs.mojang.com/browse/MC-212616) - The dye staining sound does not play when dyes are used on tamed wolves or cats
-   [MC-303468](https://bugs.mojang.com/browse/MC-303468) - Pets can be teleported to the incorrect coordinates when going through a nether portal
-   [MC-306017](https://bugs.mojang.com/browse/MC-306017) - The main arm doesn't swing when making a tamed wolf sit or stand while holding a dye matching its collar color
-   [MC-307830](https://bugs.mojang.com/browse/MC-307830) - The game's framerate is limited to 20 fps with the Vulkan rendering backend on some systems
-   [MC-308037](https://bugs.mojang.com/browse/MC-308037) - Unselected tabs in the friends menu show white text instead of gray
-   [MC-308051](https://bugs.mojang.com/browse/MC-308051) - The icons on several buttons do not adhere to the UI pixel grid
-   [MC-308747](https://bugs.mojang.com/browse/MC-308747) - The social interactions button in the game menu is grayed out in LAN worlds with no players
-   [MC-308994](https://bugs.mojang.com/browse/MC-308994) - The Chat Restrictions screen does not display Xbox communication settings that affect the chat
-   [MC-309896](https://bugs.mojang.com/browse/MC-309896) - The `options.allowFriendRequests.tooltip` and `options.inGameNotification.tooltip` strings lack a period, unlike similar strings
-   [MC-309906](https://bugs.mojang.com/browse/MC-309906) - The term "Friends List" is inconsistently capitalized across strings
-   [MC-310124](https://bugs.mojang.com/browse/MC-310124) - Leaving a menu that was opened using the keyboard doesn't select its button from the previous screen
-   [MC-310237](https://bugs.mojang.com/browse/MC-310237) - The `gui.friends.error.generic` string uses an em dash, unlike similar strings
-   [MC-310854](https://bugs.mojang.com/browse/MC-310854) - The buttons in the friends screen have inconsistent outlines
-   [MC-311932](https://bugs.mojang.com/browse/MC-311932) - The Caps Lock key can no longer activate sprinting, sneaking, etc. when the control in question is set to "Hold"
-   [MC-311963](https://bugs.mojang.com/browse/MC-311963) - The `subtitles.block.poplar_leaves.ambient` string uses a present participle instead of the present tense, unlike similar strings
-   [MC-312120](https://bugs.mojang.com/browse/MC-312120) - Enabling the "Exclusive Fullscreen" option while the game is windowed and then entering non-exclusive fullscreen does not update the "Exclusive Fullscreen" option's button to "OFF"
-   [MC-312198](https://bugs.mojang.com/browse/MC-312198) - Almost no small mushrooms generate on mushroom islands anymore
-   [MC-312213](https://bugs.mojang.com/browse/MC-312213) - The game crashes when using custom Superflat presets containing air

---

