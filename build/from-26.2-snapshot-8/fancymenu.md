# Minecraft 26.2 Snapshot 8

Today we're shipping 26.2 Snapshot 8! OpenGL is now the default, while Vulkan moves into experimental territory. You'll also find updates to the sulfur cave and sulfur cube, along with beds that are now a bit bouncier than before!

Happy bouncing!

## New Features

### Sulfur Caves biome

-   If exposed to the surface, the biome will generate with all the features of the underground Sulfur Caves biome

### Sulfur Cube mob

-   Sulfur Cubes containing a block inside are now immune to damage from Magma Blocks, as well as from other Sulfur Cubes that contain a Magma Block

## Changes

-   The game will now use OpenGL graphics API by default
-   Beds are now slightly more bouncy to match Bedrock

### Changed "Graphics API" Video Setting

-   "Vulkan" is now marked as "Experimental"
    -   You can still use it if you want, it works well on most common systems, but may reduce performance or cause instability on some other systems
-   "Default" option will now use OpenGL behind the scenes
-   The setting will be reset to "Default" for all players

### UI Sprites

-   Added `friends/background_dark` — a darker variant of the `friends/background` panel sprite, used as the background for confirmation dialogs in the Friends UI

## Technical Changes

-   The Data Pack version is now 106.0

### Damage Types

-   Added a new `minecraft:sulfur_cube_hot` damage type

## Data Pack Version 106.0

### Commands

**Publish**

-   The `publish` command now takes an additional boolean as it's first argument to specify whether the server should be opened to online multiplayer or just local multiplayer
    -   Default: true (online multiplayer)

**Unpublish**

-   Added `unpublish` command that unpublishes your integrated server if there is one present

## Fixed bugs in 26.2 Snapshot 8

-   [MC-306673](https://bugs.mojang.com/browse/MC-306673) The color of sleeping baby snow foxes' eyes is inconsistent with their adult variant
-   [MC-306738](https://bugs.mojang.com/browse/MC-306738) Blocks sometimes remain visible after breaking
-   [MC-306750](https://bugs.mojang.com/browse/MC-306750) The texture of snifflets contains unused pixels
-   [MC-306962](https://bugs.mojang.com/browse/MC-306962) The "Take Screenshot" key bind doesn't work when set to a mouse button
-   [MC-307212](https://bugs.mojang.com/browse/MC-307212) The texture of the back of gurgles' right arm has a line of miscolored pixels
-   [MC-307363](https://bugs.mojang.com/browse/MC-307363) Baby hoglins' mane no longer appears on both sides of the body texture
-   [MC-307833](https://bugs.mojang.com/browse/MC-307833) The world freezes when villagers with specific trade sets level up
-   [MC-307911](https://bugs.mojang.com/browse/MC-307911) The death message for dying to a sulfur cube with an absorbed magma block is " discovered the floor was lava"
-   [MC-308035](https://bugs.mojang.com/browse/MC-308035) Standing signs next to blocks now have an extra dark looking face
-   [MC-308047](https://bugs.mojang.com/browse/MC-308047) Friends service forbidden (403) — user may lack an active profile
-   [MC-308048](https://bugs.mojang.com/browse/MC-308048) The "options.inGameNotification" string is improperly capitalized
-   [MC-308058](https://bugs.mojang.com/browse/MC-308058) Sulfur cubes touching cacti spam the hurting sound
-   [MC-308061](https://bugs.mojang.com/browse/MC-308061) Games published with /publish are shown as offline in the multiplayer options screen
-   [MC-308073](https://bugs.mojang.com/browse/MC-308073) Text in the friends list warning screen can extend outside the window when reducing the resolution
-   [MC-308102](https://bugs.mojang.com/browse/MC-308102) Non-friends can join a friends-only world if they are using the same network
-   [MC-308103](https://bugs.mojang.com/browse/MC-308103) The sign editing screen no longer distinguishes between standing signs and wall signs
-   [MC-308104](https://bugs.mojang.com/browse/MC-308104) The side faces of wall signs do not get culled against blocks
-   [MC-308114](https://bugs.mojang.com/browse/MC-308114) The name of the debug property that simulates friend-only chat repeats the word "DEBUG;;_;;"
-   [MC-308145](https://bugs.mojang.com/browse/MC-308145) Cannot see own chat messages when chat is restricted to friends only by Xbox options
-   [MC-308163](https://bugs.mojang.com/browse/MC-308163) Entities pushed upward by geysers take fall damage proportional to the time they have been hovering for when landing
-   [MC-308168](https://bugs.mojang.com/browse/MC-308168) The skin preview in the skin reporting screen can no longer be rotated vertically
-   [MC-308181](https://bugs.mojang.com/browse/MC-308181) When the Villager Trade Rebalance experiment is on, the "Bounce" music disc does not generate

---

# Minecraft 26.2 Snapshot 7

In today's snapshot we're introducing the new Friends List for Java Edition, making it easier than ever to stay connected and jump into play together. Curious how it works? You can read more about Friends List [here](https://www.minecraft.net/article/friends-list-for-java-edition).

But that's not all! We might be feature complete – but we have a final surprise for you! Listen to the official soundtrack for Chaos Cubed by fingerspit (Paula Ruiz) today – including the music disc Bounce!

Happy Mining!

## New Features

-   Added a new Music Disc with the track "Bounce" by fingerspit
-   Added 5 new music tracks by fingerspit
-   Added the Friends List
-   Added the ability to easily play with your friends through **peer-to-peer**, even when you're not on the same local network

### Music

-   Added a new music disc:
    -   "Bounce" by fingerspit
    -   Has a chance of being found in Mineshaft Chest Minecarts that are located in a Sulfur Cave biome
    -   Has a comparator output of 8 when played in a Jukebox
-   Added 5 new background music tracks by fingerspit:
    -   "Shores"
    -   "Memories"
    -   "Nightly"
    -   "Home"
    -   "Ebb"

### Friends List

-   Added a Friends List, accessible from a new Friends button on the Title Screen and the Pause Menu
-   The Friends list can be opened with a new key bind (default: "O")
-   The Friends button shows a notification badge with the number of incoming friend requests, up to 5 (a "more" indicator is shown beyond that)
-   The Friends List is presented as an overlay with two tabs:
    -   Friends: shows your current friends, lets you remove them, and lets you send a new friend request by Profile Name
    -   Pending: shows incoming friend requests (which can be accepted or declined) and outgoing friend requests (which can be canceled)
-   The presence of your friends is shown under their name in the Friends List as one of the following:
    -   "Offline"
    -   "Online"
    -   "In a world"
    -   "In a joinable world"
-   Sending, accepting, declining, cancelling, and removing actions are confirmed in the UI and show a clear error message when the service is unreachable, rate limited, or the requested Profile Name does not exist
-   Friend changes that happen while the game is running are shown through toast notifications:
    -   When a friend request is sent
    -   When a friend request is received
    -   When an outgoing friend request is accepted by the other player
-   Toasts show the other player's face when the skin is available
-   The Friends List checks for updates once per minute while the Friends List is open, or every 5 minutes otherwise
-   The first time the Friends button is shown on the Title Screen, a confirmation dialog is presented to opt in to the Friends List
-   The Friends List, friend request privacy, and the Microsoft account safety settings link are managed from the new "Friends List" section in Online Options
-   Players that have their chat settings set to "Friends Only" on their XBox profile will only see chat messages from other players if they are friends

**Known Issues**

> **Developer's Note**: _This is the first version of this system, released with a few known issues. It will be improved over the coming snapshots._

-   Cancelling a friend request before the receiver has accepted it can leave the receivers incoming list in a desynced state
    -   The receiver will still see it as incoming, but when they accept it, it'll turn into an outgoing friend request for them
-   Rejecting a friend request can leave the sender's outgoing list in a desynced state
    -   The sender also needs to cancel their friend request to get back to a properly synced state
-   If a player has the friend list turned on, but the "Allow Requests" setting turned off, other players can't accept outgoing friend requests from them
-   If your Xbox profile chat setting is set to "Friends Only", you cannot see your own chat messages

### Peer-to-Peer

-   Added the ability to open singleplayer worlds to online multiplayer from the new Multiplayer Options screen
-   There are two paths to play with your friends
    -   Invite to world: the host can invite friends to their world, and the invited players can accept or deny the invitation
    -   Request to join world: players can request to join a friend's world (if it's open to online multiplayer), and the friend can accept or deny the request
-   Added new `p2p_connection` opt-in telemetry event

## Changes

-   The Slow Bouncy Sulfur Cube archetype is no longer buoyant
-   The grass color is now less green in Sulfur Caves
-   Updated the Main Menu background panorama

### Potent Sulfur

-   Eruption and cooldown times of Geysers are now randomized based on the position of the block and do not change if the block is replaced
-   Potent sulfur can now erupt when a Lava block is placed underneath
-   With Lava underneath, the Geyser eruption is continuous, but with slightly muted sounds compared to the eruption from a Magma block
-   Noxious Gas from Potent Sulfur can now rise through non-collidable waterlogged blocks and spread through other non-collidable blocks
-   Erupting Potent Sulfur can now emit its plume and boost entities through non-collidable blocks
    -   This includes Scaffolding, which can be used as an alternative to Copper Grates to stand above erupting Potent Sulfur without being affected by Noxious Gas

### UI

-   Added a Friends button to the Title Screen and the Pause Menu
-   Replaced the Open to LAN screen with the new Multiplayer Options screen

**Multiplayer Options**

-   This screen allows you to configure the multiplayer settings of the world you're currently in
-   The multiplayer scope can be set to one of the following:
    -   Off: (default) Nobody can join your world
    -   Local: only players in your local network can join your world, as the Open to LAN screen used to work
    -   Online: you can invite your friends to join your world from anywhere
-   The game mode and allow cheats options are also available in this screen

### Settings

-   Added a setting to control the availability of the Friends List and its features in Online Options
-   Added an "In-game Notification" toggle in Online Options to control whether Friends List toasts appear while in a world
-   Added an "Allow Requests" toggle in Online Options to control whether other players can send you friend requests
-   Added an "Xbox Settings..." button in Online Options that opens the Microsoft account privacy and online safety settings
-   Added a Presence option in Online Options screen to control how much activity is shared with friends (default: "All")
    -   "All": shares activity, and allows friends to request to join your world if opened up to online multiplayer
    -   "Limited": activity sharing limited to "Online" & "Offline"
    -   "None": no activity shared. Appearing as "Offline" to friends

## Technical Changes

-   The Data Pack version is now 105.1
-   The Resource Pack version is now 87.0

## Data Pack version 105.1

### Block Tags

-   Added `#causes_periodic_geyser_eruptions` - all blocks that cause periodic eruptions of Potent Sulfur blocks
-   Added `#causes_continuous_geyser_eruptions` - all blocks that cause continuous eruptions of Potent Sulfur blocks

## Resource Pack Version 87.0

-   Signs and Hanging Signs now use block models instead of built-in entity models
    -   The text on Signs and Hanging Signs cannot be configured yet
-   The `minecraft:signs` atlas has been removed

### Block Sprites

-   Signs and Hanging Signs now use block models and textures, replacing `<wood_type>` with the sign's wood type (e.g. `mangrove`)
    -   `block/<wood_type>_sign.png`
    -   `block/<wood_type>_hanging_sign.png`
-   The process of upgrading your pack's Bed, Sign, and Hanging Sign textures can be assisted by using this automated [Slicer](https://github.com/Mojang/slicer/releases) tool

### Item Sprites

Added new Item sprites:

-   `item/music_disc_bounce.png`

### UI Sprites

-   Added new textures for the Sign edit screen background, replacing `<wood_type>` with the sign's wood type (e.g. `mangrove`):
    -   `gui/sign/<wood_type>.png`
-   Added new UI sprites:
    -   `gui/sprites/friends/multiplayer/invite.png`
    -   `gui/sprites/friends/multiplayer/join_request.png`
    -   `gui/sprites/friends/accept.png`
    -   `gui/sprites/friends/accept_highlighted.png`
    -   `gui/sprites/friends/cancel.png`
    -   `gui/sprites/friends/friends.png`
    -   `gui/sprites/friends/illustrations_00.png`
    -   `gui/sprites/friends/list_separator_top.png`
    -   `gui/sprites/friends/loading.png`
    -   `gui/sprites/friends/reject.png`
    -   `gui/sprites/friends/reject_highlighted.png`
    -   `gui/sprites/friends/remove.png`
    -   `gui/sprites/friends/background.png`
    -   `gui/sprites/friends/button.png`
    -   `gui/sprites/friends/button_disabled.png`
    -   `gui/sprites/friends/button_highlighted.png`
    -   `gui/sprites/friends/toast_background.png`
    -   `gui/sprites/pause_menu/player_reporting.png`
    -   `gui/sprites/pause_menu/bug.png`
    -   `gui/sprites/pause_menu/social_interactions.png`

### Sounds

-   Added sounds for Geyser eruptions:
    -   `block.potent_sulfur.geyser_continuous_eruption`
    -   `block.potent_sulfur.geyser_continuous_eruption_active`
-   Added biome music for Sulfur Caves:
    -   `music.overworld.sulfur_caves`

### Item Models

-   The following special model types have been removed:
    -   `minecraft:standing_sign`
    -   `minecraft:hanging_sign`

## Telemetry

### New opt-in events

-   `p2p_connection`
    -   This event is sent after a peer-to-peer connection attempt
    -   Added new property: `p2p_connection_successful`
        -   Whether the peer-to-peer connection was established successfully
    -   Added new property: `p2p_connection_failure_stage`
        -   The stage where an unsuccessful connection attempt failed, such as `SIGNALING`, `ICE_CONNECT`, or `TIMEOUT`
    -   Added new property: `p2p_connection_ice_path`
        -   The type of network path used for the connection, such as `LOCAL`, `DIRECT`, `RELAY`, or `UNKNOWN`
    -   Added new properties: `p2p_connection_local_candidate_type` and `p2p_connection_remote_candidate_type`
        -   The ICE candidate types used by each side of the connection, such as `HOST`, `SRFLX`, `PRFLX`, or `RELAY`
    -   Added new properties: `p2p_connection_total_time_ms`, `p2p_connection_signaling_time_ms`, and `p2p_connection_ice_connect_time_ms`
        -   Timing information for each stage of the peer-to-peer connection flow

## Fixed bugs in 26.2 Snapshot 7

-   [MC-297491](https://bugs.mojang.com/browse/MC-297491) Glyphs from TTF files are no longer rendered correctly on glow signs
-   [MC-306401](https://bugs.mojang.com/browse/MC-306401) Shulkers' name tags display inside them when they're open
-   [MC-306972](https://bugs.mojang.com/browse/MC-306972) Wardens repeatedly roar in place when detecting ghasts
-   [MC-307144](https://bugs.mojang.com/browse/MC-307144) The game reads world generation data from data packs or world;;_;;gen;;_;;settings.dat inconsistently, preventing updating large biome sources
-   [MC-307221](https://bugs.mojang.com/browse/MC-307221) The missing texture is no longer used for blocks with no model or an invalid model
-   [MC-307272](https://bugs.mojang.com/browse/MC-307272) Servers can no longer detect left clicks from players in Spectator mode
-   [MC-307336](https://bugs.mojang.com/browse/MC-307336) Colors are less saturated with the Vulkan rendering backend on some Mac systems
-   [MC-307339](https://bugs.mojang.com/browse/MC-307339) The player's vertical motion is reset when moving on the ground
-   [MC-307387](https://bugs.mojang.com/browse/MC-307387) When using Vulkan, the `Globals` uniform is not available in multiple core shaders unless explicitly defined
-   [MC-307418](https://bugs.mojang.com/browse/MC-307418) The game crashes when trying to upgrade a legacy world
-   [MC-307421](https://bugs.mojang.com/browse/MC-307421) Vulkan does not trigger an error when a resource pack that cannot be loaded is loaded
-   [MC-307442](https://bugs.mojang.com/browse/MC-307442) The game crashes upon startup on Mac systems with Intel graphics of Gen8 architecture
-   [MC-307455](https://bugs.mojang.com/browse/MC-307455) The game crashes when minimized on some Intel graphics
-   [MC-307498](https://bugs.mojang.com/browse/MC-307498) The `standing_sign` special model renderer uses a field misspelled as "attachement"
-   [MC-307499](https://bugs.mojang.com/browse/MC-307499) The game crashes upon detecting invalid shader files during loading
-   [MC-307585](https://bugs.mojang.com/browse/MC-307585) The `fall_after_explosion` advancement trigger does not work with TNT anymore
-   [MC-307605](https://bugs.mojang.com/browse/MC-307605) The "Exclusive Fullscreen" and "Graphics API" options prompt the user to restart the game differently
-   [MC-307817](https://bugs.mojang.com/browse/MC-307817) Target selectors no longer allow specifying `type` multiple times when using tags
-   [MC-307877](https://bugs.mojang.com/browse/MC-307877) Bone meal cannot be used on dry grass with a block directly above it
-   [MC-307905](https://bugs.mojang.com/browse/MC-307905) Crash report generation can crash when StackTraceElement.getFileName() is null
-   [MC-307912](https://bugs.mojang.com/browse/MC-307912) Sulfur spikes in sulfur springs are not waterlogged
-   [MC-307919](https://bugs.mojang.com/browse/MC-307919) Geysers' force goes through some transparent blocks
-   [MC-307920](https://bugs.mojang.com/browse/MC-307920) Bucketed sulfur cubes can despawn
-   [MC-307929](https://bugs.mojang.com/browse/MC-307929) Dispensers can equip armor on sulfur cubes
-   [MC-307952](https://bugs.mojang.com/browse/MC-307952) The enchantment glint does not render on top of banner patterns applied on a shield

---

# Minecraft 26.2 Snapshot 6

Test the final features from Chaos Cubed in 26.2 snapshot 6! Feed magma to sulfur cubes and watch them heat up – but don't touch them unless it's for science! A new potential effect makes sulfur cubes slow, heavy and bouncy, but what block causes it? It's up to you to find out! Finally, check out the new look of sulfur springs.

Happy Mining!

## New Features

-   New Sulfur Cube archetypes: Slow Bouncy and Hot
-   Added Gallo language support to the game
-   Added Uzbek language support to the game
-   Added Võro language support to the game

### Sulfur Cube mob

-   Added new Slow Bouncy and Hot archetypes to the Sulfur Cube

**Sulfur Cube archetypes**

-   There is a new archetype:
    -   Slow Bouncy: slow speed, high bounciness, medium friction and medium air drag
        -   It is buoyant
        -   Used when absorbing stone blocks
-   There is also a new special archetype:
    -   Hot: same properties as Regular, but damages entities on contact like Magma Blocks do
        -   Used when absorbing Magma Blocks

### Advancements

-   Added new "Uh Oh" Husbandry advancement for having a Sulfur Cube absorb a TNT block

## Changes

### Sulfur Caves biome

-   Redesigned all surface Sulfur Springs features
-   The Sulfur Caves biome is less likely to generate underneath Oceans, Hills or Mountains
-   Sulfur Caves no longer generate with bands of Tuff and Granite

> **Developer's Note:** _Thanks to player feedback we've decided to revert tuff and granite blocks generating in sulfur caves, in favor of generating more sulfur to increase the chances of pools spawning. Sulfur spikes remain unaffected._

### Potent Sulfur

-   Geyser eruptions emit game events at the beginning and at the end of the eruption that can be detected by Sculk Sensors

### Sounds

-   Updated eruption sounds for Sulfur Spring

## Technical Changes

## Data Pack Version 105.0

-   Added `minecraft:sulfur_cube_archetype` registry entries:
    -   `hot`
    -   `slow_bouncy`
-   Entry format for `minecraft:sulfur_cube_archetype` registry has been updated:
    -   `explosion_fuse` has been replaced by `explosion`: an optional field, if present, the Sulfur Cube of this archetype will explode:
        -   `fuse`: positive integer, the fuse time when ignited
        -   `power`: non-negative integer, the explosion power
        -   `causes_fire`: boolean, whether the explosion causes fire
    -   Added `contact_damage`: an optional field, if present, the Sulfur Cube of this archetype will deal damage to entities when they come in contact with it
        -   `amount`: non-negative float, amount of damage dealt
        -   `damage_type`: damage type
        -   `attribute_to_source`: boolean indicating if the damage is attributed to the Sulfur Cube
    -   Added `knockback_modifiers`: a field that contains various modifier fileds for the Sulfur Cubes knockback magnitude and direction
        -   `horizontal_power`: float that represenst the horizontal power of the knockback
        -   `vertical_power`: float that represenst the vertical power of the knockback
-   Removed the `HurtByTimestamp` tag from Living Entities, `ticks_since_last_hurt_by_mob` should be used instead

### World Generation

**Surface Rules**

**Changed `noise_threshold` Surface Rule Condition**

-   Added new `is_3d` field - boolean, true if the noise should be evaluated in 3D
    -   If not specified, defaults to `false`

**Removed `noise_gradient` Surface Rule**

-   Can be replaced with `noise_threshold`

**Configured Features**

**Added `minecraft:weighted_random_selector` Feature Type**

Randomly selects one of the given features to generate based on their weights.

Format: object with fields:

-   `features` - list of Placed Features and their weights

**Changes to `minecraft:large_dripstone`**

-   The maximum allowed value for `column_radius` has been reduced from 19 to 16 to prevent features from reaching beyond neighboring chunks
-   Wind offset is now clamped to ensure the full dripstone (radius + wind) stays within neighboring chunk bounds

**Changes to `minecraft:root_system`**

-   New field `level_test_distance` indicating how far away from the origin the root system will check the existing terrain
-   New field `max_level_deviation` indicating how far the ground level can deviate from the original ground level at these test positions

**Structure Processors**

**Changed `minecraft:block_rot` Structure Processor**

-   Now evaluates the block state produced by previous block processors in the chain, instead of always using the original block defined in the structure
    -   The first processor in the chain still always evaluates against the original structure-defined block

### Tags

**Item Tags**

-   Added the following tags for items that can be placed inside a Sulfur Cube to determine its archetype:
    -   `#sulfur_cube_archetype/hot`
    -   `#sulfur_cube_archetype/slow_bouncy`

## Fixed bugs in 26.2 Snapshot 6

-   [MC-248758](https://bugs.mojang.com/browse/MC-248758) Logged Error: Detected setBlock in a far chunk
-   [MC-302554](https://bugs.mojang.com/browse/MC-302554) Glowing falling blocks no longer show the glowing outline
-   [MC-305239](https://bugs.mojang.com/browse/MC-305239) Growing world borders reset to their starting size upon reopening the world
-   [MC-306778](https://bugs.mojang.com/browse/MC-306778) The fog color no longer transitions smoothly when the weather changes at night while under the Night Vision effect
-   [MC-307043](https://bugs.mojang.com/browse/MC-307043) Applying a freeze effect while damaging a mob causes an incorrect value for `ticks_since_last_hurt_by_mob`
-   [MC-307281](https://bugs.mojang.com/browse/MC-307281) `/item replace` cannot place items in sulfur cubes' body slot
-   [MC-307297](https://bugs.mojang.com/browse/MC-307297) Sulfur cubes shake from freezing when inside powder snow despite not being able to freeze
-   [MC-307310](https://bugs.mojang.com/browse/MC-307310) Potent sulfur can generate outside of water
-   [MC-307323](https://bugs.mojang.com/browse/MC-307323) Sulfur caves can generate on the surface
-   [MC-307351](https://bugs.mojang.com/browse/MC-307351) Dispenser arrows cannot push sulfur cubes
-   [MC-307397](https://bugs.mojang.com/browse/MC-307397) Mace effects do not apply when hitting sulfur cubes
-   [MC-307407](https://bugs.mojang.com/browse/MC-307407) Vertical velocity after bouncing does not take drag into consideration
-   [MC-307424](https://bugs.mojang.com/browse/MC-307424) Chiseled cinnabar and sulfur are listed incorrectly in the Creative mode inventory
-   [MC-307482](https://bugs.mojang.com/browse/MC-307482) Sulfur cubes with an absorbed block don't inherit any status effects from tipped arrows
-   [MC-307517](https://bugs.mojang.com/browse/MC-307517) Beacon beams render in front of nether fog
-   [MC-307544](https://bugs.mojang.com/browse/MC-307544) Sulfur spikes have an inaccurate map color
-   [MC-307560](https://bugs.mojang.com/browse/MC-307560) Wandering traders are unable to sell sulfur spikes
-   [MC-307584](https://bugs.mojang.com/browse/MC-307584) The border around the selected pack in the resource/data pack menu disappears when pressing Enter
-   [MC-307667](https://bugs.mojang.com/browse/MC-307667) Dispensers can equip small sulfur cubes
-   [MC-307673](https://bugs.mojang.com/browse/MC-307673) Sulfur caves appear much smaller due to their tuff border
-   [MC-307674](https://bugs.mojang.com/browse/MC-307674) Knockback does nothing to sulfur cubes if they have a block inside
-   [MC-307684](https://bugs.mojang.com/browse/MC-307684) Named sulfur cubes can despawn after being picked up with a bucket and replaced
-   [MC-307774](https://bugs.mojang.com/browse/MC-307774) The `bool(arg)` SNBT operation returns false for some non-zero number values
-   [MC-307777](https://bugs.mojang.com/browse/MC-307777) The patterns on banners are now invisible under some circumstances
-   [MC-307778](https://bugs.mojang.com/browse/MC-307778) Priming sulfur cubes with absorbed TNT does not play the hand use animation
-   [MC-307779](https://bugs.mojang.com/browse/MC-307779) Potent sulfur no longer causes noxious gas to appear upon world generation
-   [MC-307780](https://bugs.mojang.com/browse/MC-307780) The server crashes when the management server is enabled
-   [MC-307782](https://bugs.mojang.com/browse/MC-307782) Sulfur spring geysers can push players in Creative mode who are flying
-   [MC-307783](https://bugs.mojang.com/browse/MC-307783) Lines are drawn between leashed entities in view
-   [MC-307784](https://bugs.mojang.com/browse/MC-307784) Structure block rotation buttons aren't disabled correctly
-   [MC-307785](https://bugs.mojang.com/browse/MC-307785) Geysers do not emit a game event when erupting
-   [MC-307797](https://bugs.mojang.com/browse/MC-307797) Dying to a sulfur cube doesn't increase the player's `killed_by:sulfur_cube` statistic
-   [MC-307802](https://bugs.mojang.com/browse/MC-307802) The player's arm swings when attempting to interact with a sulfur cube with ignited TNT inside
-   [MC-307803](https://bugs.mojang.com/browse/MC-307803) The game crashes when a sulfur cube with an archetype that has `explosion_fuse` set to a value lower than 4 is primed by an explosion
-   [MC-307821](https://bugs.mojang.com/browse/MC-307821) The glowing effect is now always white on the frame part of bell block displays
-   [MC-307824](https://bugs.mojang.com/browse/MC-307824) Attempting to light a sulfur cube with TNT inside while TNT explosions are disabled does not display a message
-   [MC-307825](https://bugs.mojang.com/browse/MC-307825) Disabling TNT explosions does not prevent already primed TNT sulfur cubes from exploding
-   [MC-307829](https://bugs.mojang.com/browse/MC-307829) Sulfur cubes with TNT absorbed still explode with the game rule `mob_griefing` set to false
-   [MC-307837](https://bugs.mojang.com/browse/MC-307837) Igniters deplete when used on TNT sulfur cubes while TNT explosions are disabled
-   [MC-307854](https://bugs.mojang.com/browse/MC-307854) Weapons enchanted with Fire Aspect don't ignite TNT sulfur cubes
-   [MC-307864](https://bugs.mojang.com/browse/MC-307864) Small sulfur cubes become large client-side when fed a slimeball after restarting their aging

---

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

