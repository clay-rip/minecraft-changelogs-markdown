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

# Minecraft 26.3 Snapshot 6

It's yet another Tuesday, and it seems that we've officially run out of quippy snapshot intros until the next delivery. Anyway, here's Snapshot 6, bringing some tweaks and improvements to the Abandoned Camp, a new World Options UI, as well as changing up how terrain is rendered.

Happy camping!

## Changes

-   Added a new Abandoned Camp campsite variant for each biome
-   Minor tweaks to Abandoned Camp structures

### UI

-   Fixed an issue where Realm owners could not select automatic region preference as their Realm region
-   Added a "Quit Shortcuts" option in Controls settings, which controls whether keyboard shortcuts can close the game (Alt + F4 on Windows/Linux, Cmd + Q and Cmd + W on macOS)
    -   Off by default

**World Options**

-   The World Options button has been moved to where the Open to Lan button used to be, accessible from the pause menu
    -   The World Options screen is divided into two sections: "General" and "Multiplayer"
        -   The "General" section contains the same options as the previous World Options screen
        -   The "Multiplayer" section contains three options:
            -   LAN: changes the multiplayer scope of the world
            -   Command Access: Controls whether players that join your world can use commands or not
            -   Port: the port number to use when opening the world to LAN
-   The Online button used to access the Online Options screen will now always be shown in the Options menu

## Technical Changes

-   The Data Pack version is now 113.0
-   The Resource Pack version is now 94.0
-   Terrain blocks are now rendered with MultiDrawIndirect on supported devices

## Data Pack Version 113.0

### Commands

**Changes to `publish`**

-   The `gamemode` argument has been removed
    -   Instead, the default game mode of the world should be set using the `defaultgamemode` command or the Game Mode button in the World Options screen, while player-specific game modes should be set using the `gamemode` command

### Data Components

**Changed `minecraft:cooking_fuel`**

-   `burn_time` and `speed_multiplier` can now additionally be defined by an inline number

**Changed `minecraft:brewing_fuel`**

-   `uses` and `speed_multiplier` can now additionally be defined by an inline number

**Changed `minecraft:compostable`**

-   `layers` can now additionally be defined by an inline number

### Entity Data

-   Added `invulnerable_time` tag which makes a mob temporarily invulnerable for a specific number of ticks

### Loot Table Types

**Changed `minecraft:block_interact`**

-   `origin` is now available in context, as the center of the block being interacted with

### World Generation

**Noises**

The format of Noises (defined in the `worldgen/noise` registry, or inline in noise-based Block State Providers) has been updated.

Noises define a fractal Brownian motion (fBm) configuration with the following properties:

-   Produces output values (approximately) fitting a normal distribution
    
-   Unless otherwise specified, fits the output amplitude to `[-1; 1]`
    
    -   Due to the normal distribution, in practice this means that 99.7% of all samples will fit in that range - but values may still be encountered outside of this range
-   Parameterized by persistence=0.5, lacunarity=2.0
    
    -   i.e. between each octave, the amplitude is halved and the frequency doubled
-   Has stable seeding such that an octave can be boosted, muted, or added without affecting the rest of the octaves
    
-   Renamed `firstOctave` to `base_octave`
    
-   Added `base_amplitude` - non-negative float, a scale factor to apply to the noise output
    
    -   If not specified, defaults to `1.0`
-   Added `octave_count` - integer between 1 and 32, the number of octaves to sample
    
-   Added `normalize` - boolean, or `"legacy"`, controls how the output amplitude should be normalized
    
    -   If `true`, `base_amplitude` is the expected amplitude of the output (i.e. 99.7% of all samples in `[-base_amplitude; base_amplitude]`)
    -   If `false`, `base_amplitude` is the amplitude of the first octave
    -   If `"legacy"`, inherits the same normalization behavior as expressed by the previous format
        -   This would generally fit to a range smaller than expected
    -   If not specified, defaults to `true`
    -   Note: normalization is _not_ affected by the `amplitude_modifiers` field - as such, modifying the amplitude of a single octave will not affect the amplitude of others
-   Renamed `amplitudes` to `amplitude_modifiers` - list of floats, a scaling factor to apply to each octave
    
    -   The number of elements in this list must match `octave_count`
    -   As described above, this scaling factor bypasses normalization and will affect the output amplitude
    -   This field is no longer required - if not specified, defaults to all `1.0`

**Density Functions**

**Added `pow`**

Raises the given base value to an exponent.

Format: object with fields:

-   `base` - Density Function, the base value
-   `exponent` - Density Function, the exponent

**Added `sqrt`**

Computes the square root of the given input.

Format: object with fields:

-   `input` - Density Function, the value for which to compute the square root

**Added `log`**

Computes the natural logarithm of the given input.

Format: object with fields:

-   `input` - Density Function, the value for which to compute the natural logarithm

**Added `sign`**

Computes the sign of the input:

-   If the input is positive, returns `1`
-   If the input is `0`, returns `0`
-   If input is negative, returns `-1`

Format: object with fields:

-   `input` - Density Function, the value of which to compute the sign

**Added `distance_to_point`**

Computes the distance to a fixed point using the specified distance function.

Format: object with fields:

-   `point` - array of 3 integers in form `[x, y, z]`, the point to compute distance to
-   `metric` - one of:
    -   `euclidean` - i.e. `sqrt(dx^2 + dy^2 + dz^2)`
    -   `euclidean_squared` - i.e. `dx^2 + dy^2 + dz^2`
    -   `manhattan` - i.e. `abs(dx) + abs(dy) + abs(dz)`
    -   `chebyshev` - i.e. `max(abs(dx), abs(dy), abs(dz))`

**Updated `gradient` (renamed from `y_clamped_gradient`)**

Format: object with fields:

-   `axis` - `x`, `y`, or `z`, the axis over which to define this gradient
-   `tiling` - one of:
    -   `clamp_to_edge` - outside the gradient boundaries, the value at the nearest boundary will be used
    -   `repeat` - the gradient will be repeated outside its boundaries
    -   `mirrored_repeat` - the gradient will be repeated such that odd repetitions are mirrored, ensuring continuity between repetitions
-   `from_coordinate` - int, the coordinate at which the gradient starts
-   `to_coordinate` - int, the coordinate at which the gradient ends
    -   Must not be equal to `from_coordinate`
-   `from_value` - float, the value at which the gradient starts
-   `to_value` - float, the value at which the gradient ends

**Added `slice`**

Removes a dimension from the input domain by taking a "slice" along an axis with a specific coordinate. For example, with `axis=y` and `coordinate=0`, a slice will be taken along the XZ plane, with all values sampled at `y=0`.

Format: object with fields:

-   `axis` - `x`, `y`, or `z`, the axis to remove
-   `coordinate` - int, the fixed coordinate to be passed to the input function
-   `input` - Density Function, the input function

**Changed `end_outer_islands`**

Renamed from `end_islands`. No longer computes the density of the main island.

**Structure Pool Elements**

**Changed `minecraft:feature_pool_element`**

-   Can now connect to Jigsaw blocks with any target name, instead of just `minecraft:bottom`

## Resource Pack Version 94.0

### Shaders & Post-process Effects

-   `terrain.vsh` and `terrain.fsh` shaders are refactored to support multi-draw
-   Some of the members in `Globals` and `DynamicTransforms` are shuffled to use less memory for those uniform blocks
-   Introduced new define: `RENDERPEARL_EXPLICIT_DEPTH_INVARIANCE` - If present, indicates that an OIT shader should explicitly output a depth value because a device it is running on can produce a slightly different implicit value

### Equipment Assets

The `trim_palette_replacements` field has been replaced with `trim_overrides`. This can be used to swap out the texture or palette used with specific trim materials or patterns for a given equipment asset, not just swap specific palettes.

-   Format: list of override entries with fields:
    -   `when` - object with fields, the material and/or pattern to match
        -   `material` - optional Trim Material ID, the material to match (if specified)
        -   `pattern` - optional Trim Pattern ID, the pattern to match (if specified)
            -   Note: this is _not_ the palette ID, as `trim_palette_replacements` used to be!
        -   At least one of `material` or `pattern` must be specified
        -   If both are specified, both must match for the entry to be used
    -   `texture` - optional trim pattern asset ID, a replacement texture to use if this entry matches
        -   Textures are specified in the same format as `asset_id`
        -   If not specified, the default texture for the pattern will be used
    -   `palette` - optional palette ID, a replacement palette to use if this entry matches
        -   If not specified, no palette remapping will be applied to the texture
    -   The first matching entry will always be selected
    -   At least one of `texture` or `palette` must be defined

## Fixed bugs in 26.3 Snapshot 6

-   [MC-299582](https://bugs.mojang.com/browse/MC-299582) - Special crafting recipes behave differently than other recipe types with /recipe and the `limited_crafting` game rule
-   [MC-304195](https://bugs.mojang.com/browse/MC-304195) - The arm overlay textures of parched have unused pixels not used by the model
-   [MC-307206](https://bugs.mojang.com/browse/MC-307206) - `Std140Builder` incorrectly pads `vec3s` and `ivec3s`
-   [MC-307996](https://bugs.mojang.com/browse/MC-307996) - The game cannot use hardware acceleration on devices lacking the `fillModeNonSolid` Vulkan feature
-   [MC-308694](https://bugs.mojang.com/browse/MC-308694) - Using /defaultgamemode changes everyone's game mode to the one set in "Settings for Other Players" in LAN worlds
-   [MC-308699](https://bugs.mojang.com/browse/MC-308699) - Switching the host's game mode causes new LAN players to ignore the forced game mode
-   [MC-308749](https://bugs.mojang.com/browse/MC-308749) - Exiting and rejoining the same LAN session resets your game mode
-   [MC-309720](https://bugs.mojang.com/browse/MC-309720) - The texture of straw beds has missing and extra pixels
-   [MC-309958](https://bugs.mojang.com/browse/MC-309958) - Off-by-one error in `SynchedEntityData.Builder#define`
-   [MC-310088](https://bugs.mojang.com/browse/MC-310088) - The taskbar icon displays the Java logo instead of the game's logo
-   [MC-310099](https://bugs.mojang.com/browse/MC-310099) - The game freezes if the head part of straw beds has a different facing than the foot part
-   [MC-310101](https://bugs.mojang.com/browse/MC-310101) - Command+W now closes the game on macOS
-   [MC-310122](https://bugs.mojang.com/browse/MC-310122) - Traversing the pie chart with keys does not work correctly
-   [MC-310132](https://bugs.mojang.com/browse/MC-310132) - Armor trim textures can no longer be overridden
-   [MC-310134](https://bugs.mojang.com/browse/MC-310134) - The "Exclusive Fullscreen" button and "Exclusive Fullscreen Mode" slider are still present and enabled on macOS
-   [MC-310136](https://bugs.mojang.com/browse/MC-310136) - Player skin rendering is messed up when the "Improved Transparency" setting is enabled
-   [MC-310143](https://bugs.mojang.com/browse/MC-310143) - IME candidates are invisible in fullscreen mode even when the "Exclusive Fullscreen" option is disabled
-   [MC-310155](https://bugs.mojang.com/browse/MC-310155) - After entering macOS fullscreen by clicking the "Fullscreen" button in the Video Settings menu, you cannot reveal the menu bar or dock by navigating to the edge of the screen
-   [MC-310168](https://bugs.mojang.com/browse/MC-310168) - When editing a glowing sign, the glow on the placed sign temporarily disappears
-   [MC-310195](https://bugs.mojang.com/browse/MC-310195) - Control+Left click no longer counts as a right click on macOS
-   [MC-310213](https://bugs.mojang.com/browse/MC-310213) - On-screen keyboard handling is inconsistent
-   [MC-310228](https://bugs.mojang.com/browse/MC-310228) - The game freezes when a player destroys a bed at the exact same moment a villager sleeps in it
-   [MC-310235](https://bugs.mojang.com/browse/MC-310235) - The game crashes when a piston pushes a water cauldron with the "Improved Transparency" option enabled
-   [MC-310241](https://bugs.mojang.com/browse/MC-310241) - Brewing recipes show up in the command suggestions for /recipe, but cannot be granted or revoked
-   [MC-310281](https://bugs.mojang.com/browse/MC-310281) - Using keyboard shortcuts to navigate tabs within UIs doesn't work correctly
-   [MC-310311](https://bugs.mojang.com/browse/MC-310311) - Item modifiers that reference themselves crash the game when invoked
-   [MC-310313](https://bugs.mojang.com/browse/MC-310313) - Predicates that reference themselves crash the game when invoked
-   [MC-310314](https://bugs.mojang.com/browse/MC-310314) - Number providers that reference themselves crash the game when invoked
-   [MC-310315](https://bugs.mojang.com/browse/MC-310315) - Slot sources that reference themselves crash the game when invoked
-   [MC-310319](https://bugs.mojang.com/browse/MC-310319) - The game crashes when the `spider` post effect is applied
-   [MC-310321](https://bugs.mojang.com/browse/MC-310321) - The `creeper` post effect is ineffective
-   [MC-310357](https://bugs.mojang.com/browse/MC-310357) - The OpenGL rendering backend passes 3 to `GL_UNPACK_ALIGNMENT`, which is invalid
-   [MC-310359](https://bugs.mojang.com/browse/MC-310359) - `mipLevel` is not respected when `copyTextureToTexture` is used
-   [MC-310360](https://bugs.mojang.com/browse/MC-310360) - `clearColorTexture` and `clearDepthTexture` clear all mipmaps with the Vulkan rendering backend, unlike with the OpenGL one
-   [MC-310382](https://bugs.mojang.com/browse/MC-310382) - The game crashes when applying a resource pack with a shader that uses `#include` with uppercase characters in the path
-   [MC-310383](https://bugs.mojang.com/browse/MC-310383) - The per-target blend state diverges between the OpenGL and Vulkan rendering backends
-   [MC-310388](https://bugs.mojang.com/browse/MC-310388) - The `caves` and `floating_islands` noise settings no longer generate as intended
-   [MC-310455](https://bugs.mojang.com/browse/MC-310455) - `copyTextureToBuffer` produces padded rows with the OpenGL rendering backend but tightly-packed rows with the Vulkan one

---

