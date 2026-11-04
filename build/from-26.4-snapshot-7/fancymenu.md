# Minecraft 26.4 Snapshot 7

Minecraft 26.4 Snapshot 7 is here with a brand new music disc and a flurry of new blocks! These are the final gameplay features for the upcoming game drop, so grab your tools, turn up the music, and let's get to mining and crafting!

Happy building!

## New Features

-   Added Calcite Blockset
-   Added a new Music Disc with the track "Flurry" by Hyper Potions
-   Added a new decorative block to the game... somewhere

### Calcite

-   Added the Calcite Block Set
    -   Calcite now has a Pillar, Slab, Stair, and Wall variant
    -   Calcite Pillars, Slabs, Stairs, and Walls can also be crafted using a Stonecutter
-   Added the Polished Calcite Block Set
    -   Polished Calcite can be crafted from 2x2 Calcite Blocks
    -   Polished Calcite, Slabs, Stairs, and Walls can also be crafted using a Stonecutter
-   Added the Polished Calcite Bricks Block set
    -   Polished Calcite Bricks can be crafted from 2x2 Polished Calcite Blocks
    -   Polished Calcite Brick Slabs, Stairs, and Walls can also be crafted using a Stonecutter
-   Calcite, Polished Calcite, and Polished Calcite Bricks belong to the Slow Bouncy Sulfur Cube archetype

### Music and Sound

-   Added a new music disc
    -   "Flurry" by Hyper Potions
    -   Has a chance of being found in Igloo basement Chests
    -   Has a comparator output of 7 when played in a Jukebox

## Changes

-   Updated the Main Menu background panorama

### Minor Tweaks to Blocks, Items and Entities

-   Being on fire now counters the Freezing Effect similar to wearing leather armor
-   Wearing any piece of leather armor will prevent Zombies and Skeletons from converting into Frostbites or Strays
-   Strays now spawn in the following biomes:
    -   Deep Frozen Ocean
    -   Frozen Ocean
    -   Frozen Peaks
    -   Frozen River
    -   Jagged Peaks
    -   Snowy Slopes

### "Graphics API" Video Setting

-   "Default" will now randomly pick either OpenGL or Vulkan on each startup

> **Developer's Note**: _As we've been defaulting to Vulkan for this snapshot series, we have had little testing on the OpenGL backend. After some recent big changes to our rendering code, we want to temporarily test both backends. This will be reverted in a future snapshot._

### Realms

-   The "Play" buttons in the Realms menus are now purple

### UI

-   Hovering entries in lists, such as friends or worlds, now outlines the entry in gray
-   Navigating to edit boxes now differs between keyboard and arrow key navigation
    -   When using the Tab key, the edit box will be focused and editable
    -   When using arrow keys, the edit box will be highlighted but not editable, similar to slider buttons
        -   Pressing Enter or Space will make the box editable
-   The mouse cursor is now hidden while navigating the UI with the keyboard, and reappears when the mouse is moved
-   Added a tooltip to the recipe book button

### Accessibility

-   Gameplay screens, such as the Crafting Table, now support keyboard navigation and narration

> **Developer's Note**: _This is the first step towards making gameplay screens more accessible. As always, we'd love to hear your feedback, so please head on over to [the feedback site](https://aka.ms/MCKeyboardNavigationNarrationGameplayScreensJava)._

**Gameplay Screen Keyboard Navigation**

-   Gameplay screens can now be focused and used with the keyboard
-   Tab moves between groups of slots, and the arrow keys move between slots within a group
    -   The Stonecutter recipes, Loom patterns, Enchanting Table options, and Villager and Wandering Trader trades are also navigated as a group
-   The following interactions can be used on slots:
    -   Enter/Space behaves as a left-click
    -   Holding Control while pressing Enter/Space behaves like a right-click
    -   Holding Shift while pressing Enter/Space behaves like Shift-clicking
    -   Double-pressing Enter/Space collects matching items, like double-clicking
    -   Moving with the arrow keys while holding Enter/Space spreads the carried stack across slots, like holding left-click and dragging with the mouse
    -   The hotbar keys and the Drop item key act on the focused slot
-   The Creative Inventory and the Recipe Book are not yet supported

**Gameplay Screen Narration**

-   The narrator now reads out slots in gameplay screens
    -   Slots are narrated with their contents, item tooltip, and name for special slots such as armor, fuel, and potion slots
    -   The slot's position is narrated (e.g. "3 out of 9") in a group or as a column and row in a grid
-   Stonecutter recipes and Loom patterns are narrated with their column and row, and trades and Enchanting Table options with their position in the list
-   When a group is focused, the narrator mentions which arrow keys move within it

## Technical Changes

-   The Data Pack version is now 126.0
-   The Resource Pack version is now 102.0

## Data Pack Version 126.0

### Commands

-   The `effect` command now accepts mob effect tags
-   Time arguments now fail if the provided value in ticks is greater than 2147483647

### Debug Worlds

-   Can now be modified as normal with block placement, breaking, and commands
-   The blocks will no longer update automatically, you must create a new debug world to see new blocks
-   Now include one of each entity type
    -   Entity types that can be babies will have a baby version included above the adult version
-   Will now be tick-frozen on load
-   Will now be created in "Normal" difficulty
-   Will now have the following game rules set to `false`:
    -   `advance_time`
    -   `advance_weather` (this was already the case, listing here for completeness)
    -   `spawn_wandering_traders`
    -   `tnt_explodes`

### Tags

-   Removed unused `#swimming` and `#flying` Entity Type Tags

### Block Sound Sets

-   Removed unused `minecraft:twisting_vines` block sound set

## Resource Pack Version 102.0

### Block Sprites

-   Renamed Block Textures:
    -   Renamed `block/icicle_down_base.png` to `block/icicle_base.png`
    -   Renamed `block/icicle_down_frustum.png` to `block/icicle_frustum.png`
    -   Renamed `block/icicle_down_middle.png` to `block/icicle_middle.png`
    -   Renamed `block/icicle_down_tip.png` to `block/icicle_tip.png`
    -   Renamed `block/icicle_down_tip_merge.png` to `block/icicle_tip_merge.png`
-   Added new Block textures:
    -   `block/calcite_pillar_side.png`
    -   `block/calcite_pillar_top.png`
    -   `block/polished_calcite.png`
    -   `block/polished_calcite_bricks.png`
    -   `block/polished_calcite_slab_side.png`

### Item Sprites

-   Added new Item texture:
    -   `item/music_disc_flurry.png`

### Sounds

-   Added new sound event:
    -   `entity.parrot.imitate.frostbite`

## Fixed bugs in 26.4 Snapshot 7

-   [MC-80859](https://bugs.mojang.com/browse/MC-80859) - Starting to drag item stacks over other compatible stacks makes the latter invisible until their stack size increases
-   [MC-148140](https://bugs.mojang.com/browse/MC-148140) - The scroll bar in the stonecutter UI appears 2 pixels too low when at the bottom of its rail
-   [MC-165610](https://bugs.mojang.com/browse/MC-165610) - The scroll bar in the trading UI reaches the bottom too early
-   [MC-185630](https://bugs.mojang.com/browse/MC-185630) - The bounding boxes of options in the enchanting table UI for clicking and hovering are inaccurate
-   [MC-235363](https://bugs.mojang.com/browse/MC-235363) - Stonecutter recipe hitboxes are misaligned in height
-   [MC-264554](https://bugs.mojang.com/browse/MC-264554) - The button highlights of focused trades in the trading UI move to other trades when scrolling
-   [MC-270272](https://bugs.mojang.com/browse/MC-270272) - Any mouse button can be used to select options in the enchanting table UI
-   [MC-270555](https://bugs.mojang.com/browse/MC-270555) - The outline of certain slots is obscured before the item is placed within the slot
-   [MC-280006](https://bugs.mojang.com/browse/MC-280006) - Experience orbs floating around a player no longer fall to the ground when that player leaves the server
-   [MC-297502](https://bugs.mojang.com/browse/MC-297502) - Any mouse button can be used to select options in the enchanting table, loom and stonecutter UIs
-   [MC-297624](https://bugs.mojang.com/browse/MC-297624) - The stonecutter UI buttons are not keyboard-navigable, preventing the player from refilling the input by pressing Space
-   [MC-298546](https://bugs.mojang.com/browse/MC-298546) - The loom UI buttons are not keyboard-navigable, preventing the player from refilling the inputs by pressing Space
-   [MC-298547](https://bugs.mojang.com/browse/MC-298547) - The enchanting table UI buttons are not keyboard-navigable
-   [MC-302022](https://bugs.mojang.com/browse/MC-302022) - Experience orbs desync after bouncing on lava
-   [MC-306817](https://bugs.mojang.com/browse/MC-306817) - The scroll position in the trading UI is not synced to the visual scroll bar when there's a large amount of trades
-   [MC-306853](https://bugs.mojang.com/browse/MC-306853) - `/time` does not throw errors when the values are too high
-   [MC-307422](https://bugs.mojang.com/browse/MC-307422) - Changing the window size causes warnings in the game log
-   [MC-307991](https://bugs.mojang.com/browse/MC-307991) - The game prefers to use the software GPU (llvmpipe) with the Vulkan rendering backend rather than the actual GPU with the OpenGL one when the GPU in use does not support Vulkan
-   [MC-309586](https://bugs.mojang.com/browse/MC-309586) - The scroll position in the stonecutter UI resets when taking an item out of the result slot
-   [MC-311029](https://bugs.mojang.com/browse/MC-311029) - The `equipment` entity predicate doesn't support the saddle slot
-   [MC-311520](https://bugs.mojang.com/browse/MC-311520) - `writeToTexture` and `copyBufferToTexture` never check for GL errors, unlike the neighboring methods
-   [MC-311522](https://bugs.mojang.com/browse/MC-311522) - The source buffer overrun check in `FrontendCommandEncoder#writeToTexture` uses integer arithmetic
-   [MC-311856](https://bugs.mojang.com/browse/MC-311856) - Error when writing textures to the buffer with the OpenGL rendering backend
-   [MC-311883](https://bugs.mojang.com/browse/MC-311883) - Mobs jitter and slide in crowds when they cannot reach the targeted player
-   [MC-311954](https://bugs.mojang.com/browse/MC-311954) - The OpenGL rendering backend can't be used when running under XWayland
-   [MC-311974](https://bugs.mojang.com/browse/MC-311974) - The new entity interpolation method introduced in 26.3 causes observable stutters compared to prior versions
-   [MC-312394](https://bugs.mojang.com/browse/MC-312394) - Drowned with tridents have a significantly reduced attack range
-   [MC-312405](https://bugs.mojang.com/browse/MC-312405) - The texture of frostbites contains unused pixels on the top left
-   [MC-312430](https://bugs.mojang.com/browse/MC-312430) - Falling pointed blocks deal more damage than before
-   [MC-312491](https://bugs.mojang.com/browse/MC-312491) - Parrots don't imitate frostbites
-   [MC-312637](https://bugs.mojang.com/browse/MC-312637) - Sculk sensors aren't activated upon ice melting in the Nether
-   [MC-312653](https://bugs.mojang.com/browse/MC-312653) - The `below_name` score is displayed above entities whose name tag is hidden
-   [MC-312658](https://bugs.mojang.com/browse/MC-312658) - Ores inside tuff blobs at heights 0-3 no longer generate as their deepslate variant
-   [MC-312667](https://bugs.mojang.com/browse/MC-312667) - The tooltips of the items in the statistics menu don't appear when they are focused with the keyboard
-   [MC-312672](https://bugs.mojang.com/browse/MC-312672) - The narrator reads villager trade offers as "button" without providing any context
-   [MC-312733](https://bugs.mojang.com/browse/MC-312733) - Snow golem attack range is significantly reduced
-   [MC-312768](https://bugs.mojang.com/browse/MC-312768) - Any mouse button can be used to drag the scroll bars of the stonecutter, loom, and villager trading menus
-   [MC-312779](https://bugs.mojang.com/browse/MC-312779) - Heads and blocks worn by small armor stands are stretched
-   [MC-312781](https://bugs.mojang.com/browse/MC-312781) - Witches, withers, and llamas no longer attack targets outside of their attack radius
-   [MC-312785](https://bugs.mojang.com/browse/MC-312785) - Any mouse button can be used to select entries in the "Experimental Feature Requirements" screen
-   [MC-312803](https://bugs.mojang.com/browse/MC-312803) - Lightning removes the wax from a waxed copper golem, unlike waxed copper blocks
-   [MC-312823](https://bugs.mojang.com/browse/MC-312823) - Any mouse button can be used to select entries in the "Add Realm" screen
-   [MC-312824](https://bugs.mojang.com/browse/MC-312824) - Any mouse button can be used to select entries in the "Changes From Last Backup" screen
-   [MC-312837](https://bugs.mojang.com/browse/MC-312837) - The `twisting_vines` block sound set is unused
-   [MC-312845](https://bugs.mojang.com/browse/MC-312845) - Item frames and glow item frames can be placed outside of the world border by placing them against blocks within the world border, unlike paintings
-   [MC-312864](https://bugs.mojang.com/browse/MC-312864) - Semi-transparent text renders darker when the "Improved Transparency" option is enabled
-   [MC-312866](https://bugs.mojang.com/browse/MC-312866) - Any mouse button can be used to open the "Terms of Service" link on the "Realms Terms of Service" screen
-   [MC-312893](https://bugs.mojang.com/browse/MC-312893) - Horses' `gallopSoundCounter` is not reset properly
-   [MC-312909](https://bugs.mojang.com/browse/MC-312909) - The `campsite_pale_garden_2` abandoned camp structure never generates
-   [MC-312912](https://bugs.mojang.com/browse/MC-312912) - The giant trees in the `campsite_old_growth_pine_taiga_1`, `campsite_old_growth_spruce_taiga_4`, and `campsite_snowy_taiga_3` abandoned camp structures never generate
-   [MC-312913](https://bugs.mojang.com/browse/MC-312913) - The trees in several abandoned camp tents don't generate
-   [MC-312942](https://bugs.mojang.com/browse/MC-312942) - The sound previews of volume sliders cannot be heard when the "UI" volume slider is turned off
-   [MC-312962](https://bugs.mojang.com/browse/MC-312962) - The Vulkan rendering backend leaks native memory on every render pass

---

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

