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

# Minecraft 26.1 Snapshot 11

Tuesday rolls around once more! We're back in the shipping room for another 26.1 snapshot and like a wise man once said, this one goes to 11. This week spells polish and finishing touches on our upcoming game drop features, technical changes, as well as bug fixes.

Happy mining!

## Known Issue

-   If you minimize the game while in Fullscreen mode (by pressing Alt + Tab, for example) you can not maximize it again

## Changes

-   Fixed adult and baby Rabbit textures to be consistent with the other new textures
-   Pig sound variants now has sound for eating
-   Baby Goats now rotate their head when ramming
-   Baby Hoglin's mane now appears on both sides of the body texture
-   Fixed texture on the back of the baby Panda's head

### Trades

-   The Master Librarian no longer offers Name Tags
-   The Master Librarian will now offer Red Candles and Yellow Candles for the price of three Emeralds
-   The Wandering Trader will now offer Name Tags for the price of one Emerald

### Sounds

-   Updated the trumpet note block sound assets

## Technical Changes

-   The Data Pack version is now 100
-   The Resource Pack version is now 83

## Data Pack Version 100

### Pig Sound Variants

Eating sound customization is now supported through the new field `eat_sound` big variant sound sets

### Game Test Environments

**Added `timeline_attributes` definitions to set any number of timelines**

-   `timelines`: A list of timelines to set

### Block States

-   `rotation` property in default block state of Banners and Signs has been changed from `0` to `8`

> **Developer's Note**: Default block state is used in very few contexts, most notably `/setblock` without any properties. This change was done to align default orientation of those blocks with other ones (like Skulls or Dispensers)

### Loot Tables

-   Removed Name Tag from Ancient Cities and Woodland Mansions

### World Generation

-   Block state providers now have a new type called `rule_based_state_provider`
    -   This was previously a separately parsed type but is now instead a sub-type of block state providers
    -   They can now be used in any other feature configurations as a block state provider and are no longer unique to the `disk` feature
    -   Format:
        -   `fallback` - An optional block state provider
        -   `rules` - A list of rules
            -   `if_true` - A block predicate that checks the block position before providing the block
            -   `then` - A block state provider

### Tags

**Block Tags**

-   Added `#prevents_nearby_leaf_decay` which defines what block types prevent leaf blocks from decaying within a taxicab distance of 6 blocks

## Resource Pack Version 83

-   Item model format now supports transformation for individual sub-models

### Sounds

-   Added new sound events for the Pig:
    -   `entity.baby_pig.eat`
    -   `entity.pig_mini.eat`
    -   `entity.pig_big.eat`
    -   `entity.pig.eat`

### Item Models

-   The `minecraft:model`, `minecraft:special`, `minecraft:range_dispatch`, `minecraft:composite`, `minecraft:select`, `minecraft:condition` item model types now have `transformation` fields
    -   Those fields have the same format as the `transformation` field on the `minecraft:display` entity, i.e. either an array of 16 numbers representing a matrix or structure with decomposed translation, scale and rotation info
    -   For types with children (`minecraft:range_dispatch`, `minecraft:composite`, `minecraft:select`, `minecraft:condition`), the transformation will be composed with the transformation of the children, except for `minecraft:bundle/selected_item`
    -   Model transformations will be applied AFTER item display transformations (i.e. `display` section in model files)
-   The transformations for some special item models (types referenced by the `minecraft:special` item model) have been extracted to item models itself
    -   Affected special model types:
        -   `minecraft:bed`
        -   `minecraft:banner`
        -   `minecraft:conduit`
        -   `minecraft:copper_colem_statue`
        -   `minecraft:head`
        -   `minecraft:player_head`
        -   `minecraft:shulker_box`
        -   `minecraft:shield`
        -   `minecraft:trident`
        -   `minecraft:standing_sign`
        -   `minecraft:hanging_sign`

**`minecraft:bell` Special Model Type**

-   New special model type that renders the animated part of a Bell block
-   No fields

**`minecraft:book` Special Model Type**

-   New special model type that renders a book that normally is a part of Enchanting Table and Lectern
-   Fields:
    -   `open_angle` - angle (in degrees) between book cover and book centerline (`0` means closed, `90` means open flat)
    -   `page1`, `page2` - the positions of two pages inside the book
        -   `0.0` means the page is in the leftmost position, `1.0` means the page in the rightmost position

**`minecraft:bed` Special Model Type**

-   The model now renders only one half of the Bed
-   To render both halves, use a `minecraft:composite` model
-   New fields:
    -   `part` - one of: `head`, `foot`

**`minecraft:banner` Special Model Type**

-   New field:
    -   `attachment` - selects a model to be used, one of `wall`, `ground`, default: `ground`

**`minecraft:chest` Special Model Type**

-   New field:
    -   `chest_type` - selects a model to be used, one of `single`, `left`, `right`, default: `single`

**`minecraft:hanging_sign` Special Model Type**

-   New field:
    -   `attachment` - selects a model to be used, one of `wall`, `ceiling`, `ceiling_middle`, default: `ceiling_middle`

**`minecraft:standing_sign` Special Model Type**

-   New field:
    -   `attachment` - selects a model to be used, one of `wall`, `ground`, default: `ground`

**`minecraft:shulker_box` Special Model Type**

;;=;; Removed the `orientation` field

### Block State Rendering

-   Some changes have been made to the way blocks states render in places like Enderman-held blocks, Block Display entities, etc. (but not falling blocks or Pistons)
    -   Enchanting Table will now show a closed book on the top of the block
    -   Blocks that use special renderers (like Chests, Banners, Skulls) should now respect block state properties:
        -   Rendering now respects the `rotation` and `facing` properties (where applicable)
        -   Beds now only render one half of the model, depending on the `part` property
        -   Copper Golem Statues will now respect the `copper_golem_pose` property
        -   Wall and freestanding Signs, Hanging Sign, Banners and Skulls/Heads will now have separate models
        -   Chests now respect `part` properties (where applicable)
    -   Note: in general, all block states should look the same when rendered on a Block Display as they look when placed in world, except:
        -   Fluids
        -   End Gateway
        -   End Portal

## Fixed bugs in 26.1 Snapshot 11

-   [MC-199975](https://bugs.mojang.com/browse/MC-199975) Endermen holding bells or bell block display entities only render the bell frame
-   [MC-231663](https://bugs.mojang.com/browse/MC-231663) Dragon eggs do not check whether there is a block under their destination when teleporting
-   [MC-275014](https://bugs.mojang.com/browse/MC-275014) Weathered and oxidized copper bulbs cast stronger shadows on themselves when lit with smooth lighting enabled
-   [MC-301003](https://bugs.mojang.com/browse/MC-301003) The bell part of bells worn on copper golems' "saddle" is not visible
-   [MC-303344](https://bugs.mojang.com/browse/MC-303344) Tooltips for selected items in dialogs are displayed even when the item isn't being hovered over
-   [MC-304683](https://bugs.mojang.com/browse/MC-304683) Wandering traders don't spawn in single biome snowy plains worlds
-   [MC-304796](https://bugs.mojang.com/browse/MC-304796) Hovering over a disabled slider shows the pointing hand cursor instead of the forbidden cursor
-   [MC-305797](https://bugs.mojang.com/browse/MC-305797) The texture of the warm piglet contains unused pixels
-   [MC-305857](https://bugs.mojang.com/browse/MC-305857) Entity hitboxes now move jaggedly when the game is frozen
-   [MC-306082](https://bugs.mojang.com/browse/MC-306082) The back texture of one of baby woods wolves' legs is inconsistent with the other three legs
-   [MC-306110](https://bugs.mojang.com/browse/MC-306110) The side textures of black, white splotched, killer, and Toast rabbits' heads extend to the bottom of their heads
-   [MC-306180](https://bugs.mojang.com/browse/MC-306180) Hitting a rolled up baby armadillo causes its legs to stick out and z-fight with the shell
-   [MC-306190](https://bugs.mojang.com/browse/MC-306190) The game closes when upgrading a world fails
-   [MC-306303](https://bugs.mojang.com/browse/MC-306303) Plains zombie villagers use the texture of their baby variant
-   [MC-306309](https://bugs.mojang.com/browse/MC-306309) Some new animal sound variants are missing
-   [MC-306312](https://bugs.mojang.com/browse/MC-306312) Some strings introduced in 26.1 Snapshot 7 are grammatically incorrect
-   [MC-306466](https://bugs.mojang.com/browse/MC-306466) The back texture of baby pandas' heads has a black stripe on one of its edges
-   [MC-306472](https://bugs.mojang.com/browse/MC-306472) The texture of chainmail helmets on baby humanoid mobs has no transparent pixels on its top, unlike on adult mobs
-   [MC-306483](https://bugs.mojang.com/browse/MC-306483) Golden dandelions do not prevent baby trader llamas from despawning
-   [MC-306520](https://bugs.mojang.com/browse/MC-306520) Baby donkeys and baby mules are offset from their hitbox, and their tail is offset from their body
-   [MC-306607](https://bugs.mojang.com/browse/MC-306607) Endermen now display the block-holding pose even when empty-handed
-   [MC-306608](https://bugs.mojang.com/browse/MC-306608) Glow item frames now resemble item frames
-   [MC-306625](https://bugs.mojang.com/browse/MC-306625) The "Programmer Art" and "High Contrast" resource packs are listed as incompatible
-   [MC-306639](https://bugs.mojang.com/browse/MC-306639) The worried baby panda's model is broken when hiding its face during a thunderstorm
-   [MC-306676](https://bugs.mojang.com/browse/MC-306676) The bottom texture of snifflets is made up of solid colors

---

# Minecraft 26.1 Snapshot 10

Another Tuesday, another snapshot! This week's release brings you some helpful new particles designed to better tell if your golden dandelion is keeping your mobs young or if you're about to reintroduce the concept of aging into their blocky lives. We've also shrunk baby zombie mob heads and fixed a collection of bugs, as we always do.

Happy mining!

## Changes

-   Fix pixel gap in Snifflet texture
-   Fix Strider baby not having its bristles animated
-   Striders now correctly inherit the warmth of the Strider they are standing on, matching Bedrock
-   Reduced the head size of the following baby mob models:
    -   Zombie
    -   Husk
    -   Drowned
-   Golden Dandelion now has different particles depending on if it is used to start or stop aging
    -   When aging is stopped green particles moving downwards will be shown
    -   When aging is started again green particles moving upwards will be shown
-   Small Armor Stand now displays correctly by using the adult armor and scaling it down

### UI

-   If there are no screens open, IME input will be canceled
-   IME will be opened when a text input gains focus and closed when a text input loses focus
-   `sound_cache` debug entry has been added

## Technical Changes

-   The Data Pack version is now 99.3
-   The Resource Pack version is now 82

## Data Pack Version 99.3

### Particles

-   Added `pause_mob_growth` - particles showing on a baby mob which has had its aging stopped using a Golden Dandelion
-   Added `reset_mob_growth` - particles showing on a baby mob which has had its aging reset and started using a Golden Dandelion

## Resource Pack Version 82

-   Updated textures for baby Zombie, baby Husk and Gurgle with smaller heads

## Fixed bugs in 26.1 Snapshot 10

-   [MC-91132](https://bugs.mojang.com/browse/MC-91132) No cross-platform CJK IME support
-   [MC-222949](https://bugs.mojang.com/browse/MC-222949) You can use tridents enchanted with riptide while riding entities
-   [MC-305369](https://bugs.mojang.com/browse/MC-305369) Trying to attach a leash to a fence outside its reach places a ghost leash knot and plays a sound
-   [MC-305471](https://bugs.mojang.com/browse/MC-305471) Cacti appear with seams on the edges and corners when using higher resolution texture packs with mipmaps enabled
-   [MC-305494](https://bugs.mojang.com/browse/MC-305494) Rabbits receive damage if they jump when there's a block above them
-   [MC-305507](https://bugs.mojang.com/browse/MC-305507) Baby cats' model is not scaled
-   [MC-306276](https://bugs.mojang.com/browse/MC-306276) Worried pandas no longer shake and hide their faces during thunderstorms
-   [MC-306300](https://bugs.mojang.com/browse/MC-306300) The riding positions of baby zombies, husks, drowned, piglins, zombified piglins, and zombie villagers are offset, causing them to visually float
-   [MC-306304](https://bugs.mojang.com/browse/MC-306304) The legs of baby zombies, husks, drowned, piglins, zombified piglins, and zombie villagers clip through their worn armor when their limbs move
-   [MC-306346](https://bugs.mojang.com/browse/MC-306346) Baby piglin and zombified piglin legs don't move the same way as their adult counterparts do
-   [MC-306361](https://bugs.mojang.com/browse/MC-306361) Hollow spaces don't render for a while when moving into a block in Spectator mode
-   [MC-306376](https://bugs.mojang.com/browse/MC-306376) Armor now appears incorrectly on small armor stands
-   [MC-306454](https://bugs.mojang.com/browse/MC-306454) The legs of baby striders detach from their bodies when attacked
-   [MC-306468](https://bugs.mojang.com/browse/MC-306468) The IME pre-edit window doesn't show up in the Creative mode inventory
-   [MC-306486](https://bugs.mojang.com/browse/MC-306486) Using an IME keyboard makes some inputs not register
-   [MC-306501](https://bugs.mojang.com/browse/MC-306501) Changing game rules from the world creation screen has no effect
-   [MC-306539](https://bugs.mojang.com/browse/MC-306539) Entities now appear darker than blocks on brightness values other than "Bright"
-   [MC-306565](https://bugs.mojang.com/browse/MC-306565) Farmers now sell 4 cookies instead of 18

---

# Minecraft 26.1 Snapshot 9

A snapshot on a Wednesday, how very nostalgic! We're releasing 26.1 Snapshot 9 today to address two issues introduced in yesterday's snapshot - in particular, a crash that would occur when any entity traveled outside of the vertical boundaries of the world. (That's a total edge-case, right?)

This snapshot also addresses noisy kittens and the pre-edit display showing incorrectly when using IME to input text in-game.

The sky is no longer the limit! Happy exploring!

## Fixed bugs in 26.1 Snapshot 9

-   [MC-305579](https://bugs.mojang.com/browse/MC-305579) Kittens repeatedly meow when snuggled up in bed
-   [MC-306456](https://bugs.mojang.com/browse/MC-306456) The game crashes when an entity is outside the world height limits
-   [MC-306479](https://bugs.mojang.com/browse/MC-306479) Entity shadows are elevated when a below;;_;;name scoreboard objective is active

---

# Minecraft 26.1 Snapshot 8

Get ready to meet the last baby mobs waddling into testing! This week's snapshot brings you the final gameplay features of our upcoming drop. Happy mining!

## Changes

-   Updated the visuals of more baby mobs
-   Deepslate can now be directly crafted into their cobbled, polished, brick, and tile variants in the Stonecutter
-   Stone can now be directly crafted into cobbled variants in the Stonecutter
-   Adult horse's blackdot markings have been updated to be visually closer to the new baby horse markings
-   Updated some of the sound assets for the adult sound variants
-   Fix a bug where Cat variant sounds `stray_ambient` and `purreow` weren't played

### Baby Mobs

-   Updated visuals for the following mobs:
    -   Panda
    -   Hoglin
    -   Zoglin
    -   Strider
    -   Snifflet
-   Hitboxes have been re-adjusted to be able to fit in spaces 1 block high and 0.5 blocks wide for the following mobs:
    -   Zombie
    -   Husk
    -   Drowned
    -   Piglin
    -   Zombified Piglin
    -   Villager
    -   Zombie Villager

### Creative Mode

-   Using Ctrl + Pick input as an operator on players and mannequins will now show the same results as executing the `/fetchprofile` command for this entity would

### User Interface

-   Input Method Editors (IME) candidates will now be shown in-game (on supported platforms, currently Windows and macOS) above currently edited text field
-   Fullscreen no longer uses exclusive mode

**Debug Screen**

-   Added a new entry called `detailed_memory` with additional information about used memory

### Default JVM Options

-   Decreased the initial heap size to 2GB

> **Developer's Note**: _The intention of this change is to reduce the amount of crashes we're seeing in the latest snapshots. If you're experiencing crashes, please refer to the [help article](https://help.minecraft.net/hc/en-us/articles/39083573916941-Fix-Minecraft-Java-Edition-Game-Crashes-by-Checking-Memory-Allocation) for more information on how to configure memory allocation._

## Technical Changes

-   The Data Pack version is now 99.2
-   The Resource Pack version is now 81.1

## Data Pack Version 99.2

-   Changes to the `minecraft:nbt` text component format

### Commands

**Changes to `/fetchprofile`**

-   Added a new `entity` subcommand that will print profile information from entity in world
    -   Syntax: `/fetchprofile entity <single entity selector>`
    -   If targeted entity does not have profile (currently only Players and Mannequins do) this command will fail
    -   Note that the profile is shown as-is - no additional resolving is done

### Text components

**`minecraft:selector`**

-   Field `selector` no longer accepts trailing data after a selector

**`minecraft:nbt`**

-   Tags resolved with the `minecraft:nbt` text component when the `interpret` field is set to `false` are now pretty-printed instead of being flattened into a single `text` component
-   Contents of the `nbt` and `block` fields are no longer silently rejected when parsing fails
-   Field `entity` no longer accepts trailing data after a selector
-   A new option called `plain` has been added to remove styling from pretty-printed text
    -   The `plain` and `interpret` options can't both be enabled at the same time

## Resource Pack Version 81.1

### UI Sprites

-   Added new UI sprites:
    -   `gui/sprites/widget/preedit.png` for IME preedit overlay background

### Entity Textures

-   Added new entity textures:
    -   `entity/hoglin/hoglin_baby.png`
    -   `entity/hoglin/zoglin_baby.png`
    -   `entity/strider/strider_baby.png`
    -   `entity/strider/strider_cold_baby.png`
    -   `entity/sniffer/snifflet.png`
    -   `entity/panda/aggresive_panda_baby.png`
    -   `entity/panda/brown_panda_baby.png`
    -   `entity/panda/lazy_panda_baby.png`
    -   `entity/panda/playful_panda_baby.png`
    -   `entity/panda/weak_panda_baby.png`
    -   `entity/panda/worried_panda_baby.png`
    -   `entity/panda/panda_baby.png`

## Fixed bugs in 26.1 Snapshot 8

-   [MC-98631](https://bugs.mojang.com/browse/MC-98631) The heights of shields in first person are different depending on what hand you have them held in
-   [MC-99647](https://bugs.mojang.com/browse/MC-99647) The "below;;_;;name" scoreboard display slot doesn't work with non-player entities
-   [MC-129886](https://bugs.mojang.com/browse/MC-129886) Trying to place a block underneath min;;_;;y does not give an error message
-   [MC-178713](https://bugs.mojang.com/browse/MC-178713) Bone meal can be used on certain plants at build height, but they don't grow
-   [MC-184432](https://bugs.mojang.com/browse/MC-184432) There is no warning when plants are bonemealed, but cannot grow above or below world height limits
-   [MC-184433](https://bugs.mojang.com/browse/MC-184433) When applying bone meal to grass / ferns / nether fungi at the upper build limit, there is no warning, and the taller part of the plant is cut off
-   [MC-254785](https://bugs.mojang.com/browse/MC-254785) Bone meal is used when clicked on a bamboo stalk with a block above it
-   [MC-264155](https://bugs.mojang.com/browse/MC-264155) Bone meal doesn't work on grass blocks beneath cave air or void air
-   [MC-305103](https://bugs.mojang.com/browse/MC-305103) The panorama sometimes spins too fast when saving or loading a world
-   [MC-305714](https://bugs.mojang.com/browse/MC-305714) "/time set " is unable to decrease time
-   [MC-305989](https://bugs.mojang.com/browse/MC-305989) Golden dandelions do not stop baby brown mooshrooms from aging
-   [MC-306019](https://bugs.mojang.com/browse/MC-306019) Items added to #cauldron;;_;;can;;_;;remove;;_;;dye by datapacks can't be undyed
-   [MC-306196](https://bugs.mojang.com/browse/MC-306196) Age-locked baby bees age while in the hive
-   [MC-306314](https://bugs.mojang.com/browse/MC-306314) The glowing effect is no longer visible
-   [MC-306319](https://bugs.mojang.com/browse/MC-306319) The content of the chat restrictions screen can shift off-center and overflow the edge of the game window when the game window is shrunken horizontally while the chat restrictions screen is open
-   [MC-306321](https://bugs.mojang.com/browse/MC-306321) The chat and chat restrictions screen don't update when changing the client chat option from that screen
-   [MC-306326](https://bugs.mojang.com/browse/MC-306326) Various block animations and particles in motion now jitter while the game is frozen
-   [MC-306333](https://bugs.mojang.com/browse/MC-306333) Grass blocks in dark forests no longer have a side overlay if Biome Blend is disabled
-   [MC-306342](https://bugs.mojang.com/browse/MC-306342) Stray adult cats play incorrect sounds
-   [MC-306345](https://bugs.mojang.com/browse/MC-306345) Baby zombies, gurgles, baby husks, and baby zombie villagers can no longer traverse one-block-high passages
-   [MC-306364](https://bugs.mojang.com/browse/MC-306364) Blocks rendered as block entities are now invisible in sections without regularly rendered blocks

---

