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

# Minecraft 26.4 Snapshot 2

Hi there! It is time for the second snapshot for 26.4, featuring improved render distance fog, a new celestial occluder, and a fresh redesign of the F3 screen.

Happy mining!

## Changes

-   When "Improved Transparency" is on, sky background and clouds that are behind the terrain are now blended into the terrain render distance fog making the boundary between the sky and the terrain invisible
-   In the Overworld, the bottom half of the skybox is now occluding the celestial objects such as the sun, the moon and the stars

### UI

-   The debug overlay (F3 by default) has been redesigned to be easier to read and understand

## Technical Changes

-   The Data Pack version is now 122.1
-   The Resource Pack version is now 99.0

## Data Pack Version 122.1

### New Environment Attributes

**`minecraft:visual/has_sky_occluder`**

Determines whether the sky occluder is enabled for the environment. The sky occluder will occlude the sky box up until a certain angle with fog color with a smooth occlusion border.

-   Value type: boolean
-   Default value: `true` for the Overworld, `false` for the Nether and the End
-   Interpolated: no

### Predicates

**Added `below_heightmap`:**

Checks if the height of the position is below a given heightmap value.

Format:

-   `heightmap`: Heightmap type to compare origin against

## Resource Pack Version 99.0

### Shaders & Post-process Effects

-   `screenquad.vsh` was renamed to `screentriangle.vsh` since it was actually representing a single triangle for a while now

**Changes for the "Improved Fog" feature that is controlled by the "Improved Transparency" video setting**

-   Removed OIT (Order-Independent Transparency, controlled by "Improved Transparency" video setting) support from the `clouds.fsh`, since it is now used to render clouds when OIT is off and to render clouds to an offscreen target when OIT is on
-   Added `blit_clouds.fsh` shader with OIT support that renders clouds from an offscreen target to OIT targets

**New Shaders for the Sky Occlusion**

-   Added `sky_occluder.vsh` and `sky_occluder.fsh` shaders which are used to occlude the sky box up until the certain angle with fog color with a smooth occlusion border

## Fixed bugs in 26.4 Snapshot 2

-   [MC-152504](https://bugs.mojang.com/browse/MC-152504) - The sky overlaps fog underwater, notably at sunrise and sunset
-   [MC-184161](https://bugs.mojang.com/browse/MC-184161) - The "Oh Shiny" advancement title is missing a comma
-   [MC-195836](https://bugs.mojang.com/browse/MC-195836) - Some closed captions aren't in the correct tense or are formatted incorrectly
-   [MC-212623](https://bugs.mojang.com/browse/MC-212623) - Some closed captions use the word "angers" as a verb, therefore making them grammatically incorrect
-   [MC-236052](https://bugs.mojang.com/browse/MC-236052) - Z-fighting can be seen around the necks of small armor stands
-   [MC-264274](https://bugs.mojang.com/browse/MC-264274) - Placing lily pads and frogspawn does not increment their `used:[block]` statistics
-   [MC-300250](https://bugs.mojang.com/browse/MC-300250) - Clouds render behind foggy terrain
-   [MC-300894](https://bugs.mojang.com/browse/MC-300894) - The harness layer is not scaled correctly on baby happy ghasts
-   [MC-310503](https://bugs.mojang.com/browse/MC-310503) - `LivingEntity`'s constructor randomizes the yaw in radians instead of degrees
-   [MC-311424](https://bugs.mojang.com/browse/MC-311424) - The Right Shift key is recognized as `key.keyboard.unknown` ("Not Bound") with certain input methods
-   [MC-311451](https://bugs.mojang.com/browse/MC-311451) - Mouse input is not recognized on monitors that are in negative positions on Wayland
-   [MC-311458](https://bugs.mojang.com/browse/MC-311458) - The "Adventure" advancement's icon is inconsistent with the Adventure game mode's icon in the game mode switcher
-   [MC-311758](https://bugs.mojang.com/browse/MC-311758) - Block breaking particles and sounds are not canceled and continue appearing when opening the game mode switcher
-   [MC-311777](https://bugs.mojang.com/browse/MC-311777) - Block breaking particles and sounds are not canceled and continue appearing when instantly mining a block and swapping the item into the off hand simultaneously
-   [MC-311780](https://bugs.mojang.com/browse/MC-311780) - Trigonometric functions don't wrap angles before being applied and aren't fully periodic
-   [MC-311781](https://bugs.mojang.com/browse/MC-311781) - The game is not minimized when losing focus in fullscreen mode
-   [MC-311826](https://bugs.mojang.com/browse/MC-311826) - On some systems, tabbing in and out of the game in fullscreen mode while the "Toggle Cinematic Camera" key bind is unbound will toggle it
-   [MC-311924](https://bugs.mojang.com/browse/MC-311924) - Breaking an armor stand or block-attached entity near a sculk catalyst consumes the player's experience
-   [MC-311933](https://bugs.mojang.com/browse/MC-311933) - The horizontal scroll direction is inverted in the Advancements screen
-   [MC-311949](https://bugs.mojang.com/browse/MC-311949) - The "Not Bound" scancode can activate key binds
-   [MC-311965](https://bugs.mojang.com/browse/MC-311965) - The `commands.posteffect.list.success` string always pluralizes the word "effects"
-   [MC-311969](https://bugs.mojang.com/browse/MC-311969) - Some strings that mention specified slots are missing articles
-   [MC-311970](https://bugs.mojang.com/browse/MC-311970) - The `options.debugGuiScale.tooltip` string lacks a period, unlike similar strings
-   [MC-311971](https://bugs.mojang.com/browse/MC-311971) - Some strings refer to the "LAN" setting as the "multiplayer scope" and write its value as "Off" instead of "OFF"
-   [MC-311973](https://bugs.mojang.com/browse/MC-311973) - The `options.worldOptions.guest.command_access.tooltip` string redundantly includes "or not"
-   [MC-311977](https://bugs.mojang.com/browse/MC-311977) - The closed caption for riding zombie nautiluses is "Nautilus bubbles"
-   [MC-311978](https://bugs.mojang.com/browse/MC-311978) - Some argument error strings introduce the invalid value with a colon instead of surrounding it with single quotes, unlike similar strings
-   [MC-311997](https://bugs.mojang.com/browse/MC-311997) - The `options.macFullscreenMenuVisibility.tooltip` string is improperly capitalized
-   [MC-311999](https://bugs.mojang.com/browse/MC-311999) - The `options.ctrlClickEmulatesRightClick` string is missing a hyphen between the words "Right" and "Click"
-   [MC-312035](https://bugs.mojang.com/browse/MC-312035) - Attacking an entity in Creative mode, then switching to Survival mode adds 5 ticks of block break delay
-   [MC-312046](https://bugs.mojang.com/browse/MC-312046) - Mushrooms now generate in excessive quantities in swamps
-   [MC-312064](https://bugs.mojang.com/browse/MC-312064) - The game can randomly crash during chunk generation
-   [MC-312065](https://bugs.mojang.com/browse/MC-312065) - Some test coordinate strings are displayed with two sets of square brackets, unlike similar strings
-   [MC-312066](https://bugs.mojang.com/browse/MC-312066) - Donkeys, horses and mules in water can no longer be ridden onto land without the aid of a partial block
-   [MC-312068](https://bugs.mojang.com/browse/MC-312068) - Some strings are missing articles before the word "invalid"
-   [MC-312075](https://bugs.mojang.com/browse/MC-312075) - The `options.directionalAudio.off.tooltip` string is improperly capitalized, unlike similar strings
-   [MC-312078](https://bugs.mojang.com/browse/MC-312078) - The `options.hideMatchedNames.tooltip` string is improperly capitalized, unlike similar strings
-   [MC-312079](https://bugs.mojang.com/browse/MC-312079) - The `options.fullscreen.unavailable` string is improperly capitalized, unlike similar strings
-   [MC-312080](https://bugs.mojang.com/browse/MC-312080) - The `telemetry.event.world_loaded.description` string is improperly capitalized, unlike similar strings
-   [MC-312082](https://bugs.mojang.com/browse/MC-312082) - The `advancements.husbandry.uh_oh.title` string is missing a hyphen between the words "Uh" and "Oh"
-   [MC-312084](https://bugs.mojang.com/browse/MC-312084) - The `options.fullscreen.entry` string is missing a hyphen before the word "bit"
-   [MC-312087](https://bugs.mojang.com/browse/MC-312087) - The word "towards" within the `options.vignette.tooltip` string isn't spelled in American English
-   [MC-312088](https://bugs.mojang.com/browse/MC-312088) - Some application control key name strings are displayed without the "AC" prefix, unlike similar strings
-   [MC-312089](https://bugs.mojang.com/browse/MC-312089) - Some strings that name screens are improperly capitalized, unlike similar strings
-   [MC-312091](https://bugs.mojang.com/browse/MC-312091) - The `chat.copy.click` string is improperly capitalized, unlike similar strings
-   [MC-312092](https://bugs.mojang.com/browse/MC-312092) - The `multiplayer.socialInteractions.not_available` string is improperly capitalized, unlike similar strings
-   [MC-312102](https://bugs.mojang.com/browse/MC-312102) - The `disconnect.loginFailedInfo.invalidSession` string is improperly capitalized, unlike similar strings
-   [MC-312103](https://bugs.mojang.com/browse/MC-312103) - The entity name "Experience Orbs" isn't capitalized within some game rule description strings, unlike similar strings
-   [MC-312107](https://bugs.mojang.com/browse/MC-312107) - The `selectWorld.backupQuestion.experimental` string is improperly capitalized, unlike similar strings
-   [MC-312108](https://bugs.mojang.com/browse/MC-312108) - The `jigsaw_block.final_state` string is improperly capitalized, unlike similar strings
-   [MC-312111](https://bugs.mojang.com/browse/MC-312111) - Some Realms snapshot popup strings are improperly capitalized, unlike similar strings
-   [MC-312112](https://bugs.mojang.com/browse/MC-312112) - The `mco.configure.world.invite_codes.subtitle` string uses the verb "add" instead of "create", unlike similar strings
-   [MC-312126](https://bugs.mojang.com/browse/MC-312126) - The `options.inGameNotification.tooltip` string is improperly capitalized, unlike similar strings

---

# Minecraft 26.4 Snapshot 1

Welcome to the first snapshot of 26.4! We're kicking things off with a range of technical updates and improvements, including Vulkan becoming the default graphics API.

## Changes

### World Generation

-   Upgrading worlds from before Caves and Cliffs will now also generate sulfur caves below old chunks

### Minor Tweaks to Blocks, Items and Entities

-   Red and Brown Mushrooms can now be placed on any block with a solid top face regardless of lighting conditions
    -   They can still not spread unless the brightness is less than 13, or their support block overrides light requirements

### "Graphics API" Video Setting

-   "Default" now behaves the same as "Prefer Vulkan"
-   The game will no longer change the graphics API setting automatically if a startup crash is detected.

## Technical Changes

-   The Data Pack version is now 122.0
-   The Resource Pack version is now 98.0

### Network Protocol

**Added `minecraft:mod_list` Custom Packet Payload**

-   This packet is intended to inform servers about client mods to simplify debugging
-   Vanilla client sends an empty packet at the start of configuration phase, as it does not know about any mods - that is still a responsibility of 3rd-party modding platforms

**Modified `minecraft:intention` Packet**

-   The `host` field in the serverbound intention packet can now hold additional parameters (previously it stored only the domain name used for connecting to a server)
    -   The new format is similar to URI query strings - the domain can now optionally be followed by a `?` character and then followed by `key=value` pairs separated by a `&` character
    -   Empty values can be omitted (including `=` sign)
    -   Keys and values are escaped according to the standard URI rules ("percent-encoded component")
    -   Keys starting with `_` are reserved for vanilla use
    -   Example: `example.com?key1=value2&key2`
    -   Users can now input properties in any "Server Address" field in the server list
        -   Additionally, any address in form of `<id>@<host>` will be parsed as `<host>?_id=<id>`
    -   If a server uses SRV DNS records, the `host` field will contain both original and resolved domains
        -   If the resolved domain is different from the original domain, the resolved one will be used as the "primary" one, while the original one will be added as `_o` ("origin") property
        -   Example host string: `<redirected domain>?_o=<original domain>:<original port>`, while the `port` field in the intention packet will be set to the resolved port value
    -   The field size has been extended to 1024 characters
    -   Note: since the `minecraft:intent` packet is unencrypted, properties should not be used for any security-sensitive purpose

**Modified `minecraft:transfer` Packet**

-   Added `properties` field - a string to string map of properties that will be added to the host field in the `minecraft:intent` packet sent to the target server

### Dedicated Server Properties

-   Added `allowed-connection-ids`
    -   A list of comma-separted ids
    -   If non-empty, the server will match the values against `_id` property in `minecraft:intent` packet
        -   If there is no match, the server will reject the connection
    -   This works both for both status and login connections, so any user connecting without the correct `_id` in the server address will not see the status and will not be able to join the server
-   Added `status-contact-details` field
    -   If non-empty, the value of this field will be sent in the `minecraft:status_response` packet JSON payload under the `contact` property
    -   This value is meant to be used to signal a way to contact the server owners about the server, even if there is no website or other information about it
    -   This field is meant to be human-readable, but there are no other restrictions on field format
-   Added `enable-legacy-status` field
    -   This option allows disabling existing legacy (pre-1.7) server status and ping protocol handling
    -   To preserve existing functionality, value defaults to `true`
    -   Note: `enable-status` needs to be set for any status information (modern or legacy) to be set

## Data Pack Version 122.0

-   Entries for different biomes in multi-noise biome sources can no longer overlap across all noise parameters with the same offset

### Commands

-   The `fillbiome` command will now fill biomes with block accuracy
-   NBT conversion from floating point types to integer types now always converts to the closest possible valid number after rounding down

### World Generation

**Features**

**Changed `straight_trunk_placer`**

-   Added `trunk_width` field
    -   optional int provider, the width of the trunk centered around the origin
    -   defaults to 1.0

**Placed Features**

-   The possible domain in the XZ plane of Placed Features included in biomes is now validated
    -   Feature placement can only occur within a 3x3 chunk region: as such, it is not valid for a Placed Feature to select a position outside of that range
    -   Note: the size of the feature itself is not currently taken into consideration, which may still overflow the chunk

**Placement Modifiers**

**Changed `cuboid`**

-   `xz_size` and `y_size` have been adjusted to represent the actual size of the cuboid, instead of implicitly being 1 block larger
    -   As such, an `xz_size` of `2` will actually produce a 2x2 cuboid instead of 3x3

**Changed `fixed_placement`**

-   `positions` now requires at least one element

**Noise Settings**

-   The `default_block` field has been removed
    -   This is now always `air` - any other block should be defined by the Material Rule

**Material Conditions**

**Updated `minecraft:steep`**

-   No longer considers height modifications from Eroded Badlands "surface extensions" in an order-dependent way

### Tags

**Biome Tags**

-   Added `#generated_in_below_zero_retrogen` - biomes to generate below worlds that predate Caves and Cliffs
-   Added `#is_cave` collection tag

## Resource Pack Version 98.0

### Shaders & Post-process Effects

**Order-Independent Transparency shaders**

-   The OIT algorithm was simplified by replacing the wavelet-based mathematics with depth bin-based accumulation
    -   Slightly improved performance at least on some devices
    -   Reduced floating point precision issues on average
    -   `OIT_WAVELET_RANK` shader define was removed
    -   `OIT_COEFF_COUNT` shader define was replaced by `OIT_NUMBER_OF_DEPTH_BINS`
    -   `OIT_COEFF_ATTACHMENT_COUNT` shader define was renamed to `OIT_TRANSMITTANCE_TARGET_COUNT`

## Fixed bugs in 26.4 Snapshot 1

-   [MC-8959](https://bugs.mojang.com/browse/MC-8959) - The player automatically jumps when pressing against a block while in water
-   [MC-44560](https://bugs.mojang.com/browse/MC-44560) - When pushed to the edge of water or lava, entities jump by themselves
-   [MC-50749](https://bugs.mojang.com/browse/MC-50749) - Jumping into water against a wall causes the player to bounce
-   [MC-123848](https://bugs.mojang.com/browse/MC-123848) - Item frames (and items within) drop atop the block they're attached to instead of under it when removed from a ceiling
-   [MC-135211](https://bugs.mojang.com/browse/MC-135211) - Entities automatically jump when falling into 1-block-deep water from certain heights
-   [MC-135212](https://bugs.mojang.com/browse/MC-135212) - Entities automatically jump when falling into water of any depth from certain heights
-   [MC-262252](https://bugs.mojang.com/browse/MC-262252) - The generation of lush caves and dripstone caves is poorly defined
-   [MC-276879](https://bugs.mojang.com/browse/MC-276879) - `/data` truncates floats when casting to longs, but rounds down in all other cases
-   [MC-278651](https://bugs.mojang.com/browse/MC-278651) - The host name in handshake packets for SRV records is inconsistent
-   [MC-296053](https://bugs.mojang.com/browse/MC-296053) - Item frames don't update properly when modifying their `Facing` NBT tag
-   [MC-299060](https://bugs.mojang.com/browse/MC-299060) - Setting item frames' direction with commands can cause desyncs
-   [MC-303702](https://bugs.mojang.com/browse/MC-303702) - Small gaps still appear in item models
-   [MC-307065](https://bugs.mojang.com/browse/MC-307065) - Missing optimization for the side faces of the `builtin/generated` item model
-   [MC-310051](https://bugs.mojang.com/browse/MC-310051) - Floating point cancellation artifacts from `bits.fsh`
-   [MC-310131](https://bugs.mojang.com/browse/MC-310131) - Placeable entities momentarily appear at the wrong location when placed
-   [MC-310767](https://bugs.mojang.com/browse/MC-310767) - Pipelines always declare a `D32_FLOAT` depth attachment format with the Vulkan rendering backend
-   [MC-311195](https://bugs.mojang.com/browse/MC-311195) - Placed armor stands are rotated incorrectly for one tick
-   [MC-311265](https://bugs.mojang.com/browse/MC-311265) - The world border renders incorrectly from outside
-   [MC-311473](https://bugs.mojang.com/browse/MC-311473) - Duplicating items with the scroll wheel in Creative mode can produce ghost items
-   [MC-311582](https://bugs.mojang.com/browse/MC-311582) - The texture of desert pyramid maps has one inconsistent pixel compared to the others
-   [MC-311726](https://bugs.mojang.com/browse/MC-311726) - The water inside waterlogged copper grates has the `falling` fluid state property set to true
-   [MC-311727](https://bugs.mojang.com/browse/MC-311727) - The check for whether a player is standing on air doesn't use the player's updated position
-   [MC-311773](https://bugs.mojang.com/browse/MC-311773) - Red and brown mushrooms cannot be placed at any light level, unlike in Bedrock Edition
-   [MC-311786](https://bugs.mojang.com/browse/MC-311786) - Running `/test run` with a `rotationSteps` value that is out of range causes an error
-   [MC-311788](https://bugs.mojang.com/browse/MC-311788) - Teleporting item frames moves them further than it should visually
-   [MC-311818](https://bugs.mojang.com/browse/MC-311818) - Traveling to the End in Spectator mode regenerates the obsidian platform
-   [MC-311836](https://bugs.mojang.com/browse/MC-311836) - Minecart sounds are now distorted
-   [MC-311859](https://bugs.mojang.com/browse/MC-311859) - Damaged dyed wolf armor no longer shows cracks in the colored parts
-   [MC-311966](https://bugs.mojang.com/browse/MC-311966) - The tooltip of the "Quit Shortcuts" option calls the Command key "Cmd"

---

# Minecraft 26.3 Release Candidate 3

They say that third time's the charm! Release Candidate 3 for 26.3 is here with yet another handful of fixes as we put the final touches on the Wilderness Bound game drop.

Happy mining!

## Fixed bugs in 26.3 Release Candidate 3

-   [MC-311456](https://bugs.mojang.com/browse/MC-311456) - VSync can be disabled even when the option isn't
-   [MC-311477](https://bugs.mojang.com/browse/MC-311477) - Changes to the "Server Resource Packs" option when editing a server's options are not saved
-   [MC-311586](https://bugs.mojang.com/browse/MC-311586) - VSync can be enabled even when the option isn't
-   [MC-311799](https://bugs.mojang.com/browse/MC-311799) - Sprint-attacking another player no longer slows down the attacker

---

# Minecraft 26.3 Release Candidate 2

Today we are shipping a second release candidate for 26.3, the Wilderness Bound game drop coming on September 15th! If no critical issues are found, this will be the version that we ship for the eventual full release. Happy mining!

## Fixed bugs in 26.3 Release Candidate 2

-   [MC-311782](https://bugs.mojang.com/browse/MC-311782) - Clicking a button that opens a folder now freezes the game until the folder is opened

---

# Minecraft 26.3 Release Candidate 1

Today we are shipping the first release candidate for 26.3, the Wilderness Bound game drop! If no critical issues are found, this will be the version that we ship for the eventual full release.

Happy mining!

## Fixed bugs in 26.3 Release Candidate 1

-   [MC-311607](https://bugs.mojang.com/browse/MC-311607) - Items with the `weapon` component with `disable_blocking_for_seconds` set no longer disable items with the `blocks_attacks` component
-   [MC-311705](https://bugs.mojang.com/browse/MC-311705) - Axes can no longer disable shields
-   [MC-311725](https://bugs.mojang.com/browse/MC-311725) - The `match_block` loot predicate always requires a block entity
-   [MC-311776](https://bugs.mojang.com/browse/MC-311776) - Throwing ender pearls at blocks at a specific angle allows the player to briefly see through blocks

---

