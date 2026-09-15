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

