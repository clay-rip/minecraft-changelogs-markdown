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

# Minecraft 26.3 Pre-Release 3

The road to release continues with pre-release 3! Today we're tackling another batch of bug fixes as we prepare for a full release of 26.3.

Happy Mining!

## Technical Changes

-   The Data Pack version is now 121.0

### Number Providers

**Changed `minecraft:mod` Float Provider Type**

-   Now uses standard modulus instead of floor modulus, matching the int variant

**Changed `minecraft:pow` Float Provider Type**

-   Raising 0 to the power of 0 will now cause an error and halt computation, matching the int variant

## Fixed bugs in 26.3 Pre-Release 3

-   [MC-309262](https://bugs.mojang.com/browse/MC-309262) - Falling blocks disappear for a split second when landing
-   [MC-310189](https://bugs.mojang.com/browse/MC-310189) - The `post_effect` debug overlay entry does not upgrade to `post_effects`
-   [MC-311113](https://bugs.mojang.com/browse/MC-311113) - The game does not hand off focus when clicking links on Wayland
-   [MC-311419](https://bugs.mojang.com/browse/MC-311419) - Breaking a falling block with another one on top causes the top block to briefly become invisible when landing, revealing unlit block particles
-   [MC-311579](https://bugs.mojang.com/browse/MC-311579) - The player can see through blocks when the camera is inside snow layers
-   [MC-311631](https://bugs.mojang.com/browse/MC-311631) - Changing the "Exclusive Fullscreen Mode" option does not update the game's actual resolution on macOS
-   [MC-311634](https://bugs.mojang.com/browse/MC-311634) - Setting the "Exclusive Fullscreen Mode" option to "Current" keeps the previously selected resolution
-   [MC-311650](https://bugs.mojang.com/browse/MC-311650) - Integer and float number providers return inconsistent results for 0^0
-   [MC-311651](https://bugs.mojang.com/browse/MC-311651) - Integer and float number providers return inconsistent results for (4 % -3)
-   [MC-311664](https://bugs.mojang.com/browse/MC-311664) - Normal fullscreen does not take effect after disabling the "Exclusive Fullscreen" option on Windows
-   [MC-311673](https://bugs.mojang.com/browse/MC-311673) - Shovels no longer lose durability when extinguishing campfires
-   [MC-311676](https://bugs.mojang.com/browse/MC-311676) - Block breaking particles and sounds are not cancelled and continue appearing when pausing the game in multiplayer or using a portal
-   [MC-311678](https://bugs.mojang.com/browse/MC-311678) - Damaging a villager so that it has zero reputation toward the player while trading allows for trades to be completed without payment
-   [MC-311679](https://bugs.mojang.com/browse/MC-311679) - Players can complete trades without payment if the villager restocks while the trading screen is open
-   [MC-311683](https://bugs.mojang.com/browse/MC-311683) - Borderless fullscreen doesn't take up the whole screen
-   [MC-311714](https://bugs.mojang.com/browse/MC-311714) - Players no longer immediately benefit from the "Reduce fps when" option being set to "Minimized" when playing with the "Exclusive Fullscreen" option enabled and then switching focus
-   [MC-311721](https://bugs.mojang.com/browse/MC-311721) - The rightmost column of pixels does not render correctly in windowed mode
-   [MC-311722](https://bugs.mojang.com/browse/MC-311722) - Pressing Windows+↓ in fullscreen mode incorrectly restores the game window to a borderless windowed state
-   [MC-311738](https://bugs.mojang.com/browse/MC-311738) - The block hitting sound is not played when breaking blocks that are destroyed quickly

---

# Minecraft 26.3 Pre-Release 2

Two pre-releases in one week!? That's right! Now that we're in the pre-release phase, we're no longer following our regular snapshot schedule. This also means we're spending more time hunting bugs as we get things ready for release, and this pre-release is no exception. Hope you brought your bug spray!

Happy Mining!

## Changes

### UI

-   Removed the custom rendering of IME candidates

## Technical Changes

-   The Data Pack version is now 120.0

## Data Pack Version 120.0

### Tags

**Structure Tags**

-   Renamed `on_abandoned_camp_windswept` to `on_abandoned_camp_windswept_forest`

## Fixed bugs in 26.3 Pre-Release 2

-   [MC-210117](https://bugs.mojang.com/browse/MC-210117) - Sculk sensors don't detect ice/snow melting
-   [MC-211708](https://bugs.mojang.com/browse/MC-211708) - Client spawns crit particles when attacking another player that cannot be harmed
-   [MC-228273](https://bugs.mojang.com/browse/MC-228273) - Goats do not move correctly after they are tempted during a long jump
-   [MC-237053](https://bugs.mojang.com/browse/MC-237053) - Block breaking particles cannot be seen by other players
-   [MC-237165](https://bugs.mojang.com/browse/MC-237165) - Block breaking sounds cannot be heard by other players
-   [MC-247034](https://bugs.mojang.com/browse/MC-247034) - Particles produced from entities growing cannot be seen by other players
-   [MC-248600](https://bugs.mojang.com/browse/MC-248600) - Particles produced from moving in powder snow cannot be seen by other players
-   [MC-263100](https://bugs.mojang.com/browse/MC-263100) - Cave biomes interfere with relief on exploration maps
-   [MC-299460](https://bugs.mojang.com/browse/MC-299460) - Saddled pigs in boats carried by happy ghasts can cause a desync when unequipping a carrot on a stick
-   [MC-304719](https://bugs.mojang.com/browse/MC-304719) - `InhabitedTime` for some chunks can be set to impossibly high values when a world is opened
-   [MC-307449](https://bugs.mojang.com/browse/MC-307449) - Spawners with their light limits set no longer spawn mobs underground at night time
-   [MC-310088](https://bugs.mojang.com/browse/MC-310088) - The taskbar icon displays the Java logo instead of the game's logo
-   [MC-310169](https://bugs.mojang.com/browse/MC-310169) - The IME candidate box sometimes twitches while typing
-   [MC-310300](https://bugs.mojang.com/browse/MC-310300) - Other windows cannot be displayed on top of the game window even with the "Exclusive Fullscreen" option disabled
-   [MC-310592](https://bugs.mojang.com/browse/MC-310592) - Severe rendering errors occur on Windows devices with a Snapdragon 8cx Gen 2 CPU
-   [MC-310756](https://bugs.mojang.com/browse/MC-310756) - The mouse cursor is invisible in fullscreen mode with the OpenGL rendering backend
-   [MC-310939](https://bugs.mojang.com/browse/MC-310939) - Interacting with camels with two passengers is preferred over using items
-   [MC-311186](https://bugs.mojang.com/browse/MC-311186) - The water overlay and fog does not render when the player's head is inside a block underwater
-   [MC-311219](https://bugs.mojang.com/browse/MC-311219) - Pressing a mouse button after unmaximizing the game window while in a world can cause odd behavior
-   [MC-311245](https://bugs.mojang.com/browse/MC-311245) - Ruined portals can generate replacing end portal frames
-   [MC-311271](https://bugs.mojang.com/browse/MC-311271) - Some loot context parameters are missing from "generic" loot context
-   [MC-311272](https://bugs.mojang.com/browse/MC-311272) - Some LootContextUser can crash when referenced parameter is not provided
-   [MC-311285](https://bugs.mojang.com/browse/MC-311285) - Unnamed key binds from previous versions cause several options to be reset
-   [MC-311345](https://bugs.mojang.com/browse/MC-311345) - Reloading resource packs with the OpenGL rendering backend when in a world causes visual glitches and crashes
-   [MC-311430](https://bugs.mojang.com/browse/MC-311430) - The name of the `#on_abandoned_camp_windswept` structure tag does not contain the full name of the biome it generates in
-   [MC-311445](https://bugs.mojang.com/browse/MC-311445) - In the 26.3 snapshots, game input freezes after triggering emoji panel with Win + .
-   [MC-311453](https://bugs.mojang.com/browse/MC-311453) - Particles from feeding flowers to brown mooshrooms cannot be seen by other players
-   [MC-311454](https://bugs.mojang.com/browse/MC-311454) - Particles from water evaporating in the Nether are not properly displayed
-   [MC-311482](https://bugs.mojang.com/browse/MC-311482) - Kelp and seagrass can generate floating on submerged beached shipwrecks
-   [MC-311485](https://bugs.mojang.com/browse/MC-311485) - The fog color when the weather is rain or thunder is much bluer compared to previous versions
-   [MC-311488](https://bugs.mojang.com/browse/MC-311488) - Some IME software still cannot be used in fullscreen even with borderless mode.
-   [MC-311583](https://bugs.mojang.com/browse/MC-311583) - Riding saddled pigs with carrot on a stick in boats carried by happy ghasts causes severe desync
-   [MC-311592](https://bugs.mojang.com/browse/MC-311592) - Cursor containment does not update
-   [MC-311593](https://bugs.mojang.com/browse/MC-311593) - Spear animation jitters when swapping into spear slot and charging it in the same tick
-   [MC-311594](https://bugs.mojang.com/browse/MC-311594) - Some number providers produce an unexpected error when used in /compute
-   [MC-311610](https://bugs.mojang.com/browse/MC-311610) - Clicking on an unopened double loot chest in Spectator mode plays the locked chest sound
-   [MC-311652](https://bugs.mojang.com/browse/MC-311652) - Player-caused damage while trading allows villager trades to be completed without payment

---

