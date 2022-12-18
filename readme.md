# marbastlib
A library collecting MX and Choc style footprints, as well as various other parts used to design custom keyboards. It is maintained by [ebastler](https://github.com/ebastler/) and [MarvFPV](https://github.com/marvfpv). It is made in/for KiCAD 6.0 stable version. KiCAD 5.x is not supported, and KiCAD 6.99 nightly is not tested. You can use my (significantly smaller) [legacy lib](https://github.com/ebastler/kicad-keyboard-parts.pretty) for KiCAD 5.x.

We try to offer 3D models for as many footprints in this library as possible, creating our own models where none exist. All components for which we have models available have them linked into the footprint - please place the submodule either directly into your kicad project folder, or one level above. The models will show up correctly in either case.

For now I would recommend using the ~~`untested` branch, as many footprints are untested, but most of them are almost certain to work~~ `main` branch, as most relevant footprints have been tested and moved over. If you need anything not yet tested, switch to `untested`, proceed with caution, and let me know (preferably with pictures of the PCB) after you tested it so we can move it to `main`. Please double-check the dimensions before ordering. We will update the `main` branch whenever we prototype new footprints from this lib. To select a specific branch for a submodule, add it as usual with `git submodule add https://github.com/ebastler/marbastlib`, then edit `.gitmodules` to look like this:

    [submodule "marbastlib"]
	    path = marbastlib
	    url = https://github.com/ebastler/marbastlib
	    branch = untested

The third line has to be added and will determine the branch your submodule is following. After this, initialize and update it to the latest remote branch with `git submodule update --init --remote`.

### **We do not assume any responsibility for broken PCBs or damaged derived from errors in this library. Use at your own risk, and please open an issue or pull-request if you encounter any errors.**

## Update notes:
Update note (27.10.2022): Osprey prototypes arrived - this means, choc hotswap footprints, as well as Hirose FH33 are now tested, and I added symbol + 3D model for JST ACH 2pin low profile connectors.

Update note (23.08.2022): Added Alps RKJXU1210006 (PSP-3000) thumbstick footprint/3D model, added Hirose FH33 series FFC/FPC connectors, added footprint for Alps SKQG type switches with pre-assigned 3d model, and made some general changes to get footprint and 3D model names more coherent. Moved nRF52840_moko_mk08 and MAX17048 from `untested` to `main` after receiving new prototypes. MX hotswap sockets received a new 3d model that is closer to the actual shape and new silkscreen outlines that have been confirmed to be more accurate in a minor not listed update since the last one. Exposed copper rings on choc HS footprints (assembly side only) to be in line with their MX counterparts, after some manufacturers complained about these footprints. From now on all symbols are marked as tested and present in any lib, only footprints may not be.

Update note (31.05.2022): Moved LED_6028R symbols and Choc solder and LED footprints, as well as SW_SKHLLCA010, SW_SSSS213100 and SW_SSSS223900 footprints from `untested` to `main` after receiving new prototypes.

Update note (03.04.2022): Added Hi-Tek 725 series ("Space Invader") and Alps SKCM/CKCL (and Alps/MX combo) footprints. The available footprints were made off official datasheets, but are most likely still missing sizes (stepped caps lock for alps, for example). These will be added later on, should need arise.

Update note (04.03.2022): Recreated `untested`/`specialty` from `main` after changes. All SMD parts that had pads on B.Cu were flipped to F.Cu. This will require you to flip them after adding them, but the pick and place assembly files will now list the correct layer for hotswap sockets and revmount LEDs, which were previously designated as "top side" despite being bottom sided. I also added dedicated symbol libs for choc and MX (solder/hotswap 1u switch, stab, SK6812MINI-E, common anode 6028 revmount) with pre-assigned footprints to make placing those parts in large numbers faster. 

Update note (17.01.2022): Flattened the commit history after a cleanup to make the library easier to maintain. This should not have any impact on working with it. Removed the 2x1.6mm crystal footprint as it exists within KiCAD 6 base libs. Changed silkscreen layers for hotswap sockets. Moved MX hotswap footprints and HRO Type-C M-14 from `untested` to `main`, after they were confirmed working on a prototype. Updated the readme to include an explanation how to switch submodule branches.

Update note (11.12.2021): Dedicated SK6812 MINI-E footprints have been removed, and the SK6812 MINI-E symbol has been adapted to fit 6028R footprints. The pin numbering between 6028R and SK6812 MINI-E differs, so please take care to only use the updated symbol with these footprints, or your pinout will be wrong. The symbol included in marbastlib-mx will work, together with any of the 6028R footprints.

## Symbol Libs
### marbastlib-mx
* MX_SW_solder - switch symbol with pre-assigned 1u solder footprint
* MX_SW_HS - switch symbol with pre-assigned 1u hotswap footprint
* MX_Stab - a symbol used to place keyboard stabilizers. Pre-assigned 6.25u stabilizer.
* MX_SK6812MINI-E - symbol with preassigned footprint for reverse mount adressable SK6812MINI-E RGB LEDs
* MX_LED_6028R - symbol with preassigned footprint for reverse mount 6028 RGB LEDs
* [*SPECIALTY*] MX_SW_ULP - symbol for the MX ultra low profile switch including a pin for the mounting pads


### marbastlib-choc
* choc_SW_solder - switch symbol with pre-assigned 1u solder footprint
* choc_SW_HS - switch symbol with pre-assigned 1u hotswap footprint
* choc_Stab - a symbol used to place keyboard stabilizers. Pre-assigned 2u stabilizer.
* choc_SK6812MINI-E - symbol with preassigned footprint for reverse mount adressable SK6812MINI-E RGB LEDs
* choc_LED_6028R - symbol with preassigned footprint for reverse mount 6028 RGB LEDs

### marbastlib-various
* BAV70_Small - a smaller version of the regular BAV70 symbol(easier to use in keyboard matrices)
* TP4056 - a cheap and easily available 1S battery charging chip
* DW01A - a cheap and easily available 1S battery protection chip
* FS8205 - a dual MOSFET used in the DW01A ref implementation
* joystick_analog - symbol for a analog, dual pot thumbstick, comes pre-assigned with a PSP-1000 thumbstick footprint
* TXB0101 - a bidirectional levelshifter
* nRF52840_holyiot_18010 - a symbol for the holyiot 18010 nRF52840 BLE module
* WS2812B-MINI - symbol with preassigned footprint for WS2812B-MINI
* WS2812_2020 - symbol with preassigned footprint for WS2812B-2020 and WS2812C-2020
* SK6812MINI-E - symbol with preassigned footprint for reverse mount adressable SK6812MINI-E RGB LEDs
* SRV05-4 - symbol with attached footprint of the popular SRV05 - difference to default: pad spacing is large enough to allow 2 traces between them
* AVR_TC2030 - symbol for AVR ISP programming connector with pre-assigned TC2030 footprint
* JTAG_TC2030 - symbol for JTAG programming connector with pre-assigned TC2030 footprint
* LED_6028R - symbol with preassigned footprint for reverse mount 6028 RGB LEDs
* STM32WB5MMG - a small form factor package including STM32WB chip and antenna
* MAX77751 - a 1S LiIon battery management chip
* IS31FL3741A - a 39x9 LED multiplex driver
* MAX17048 - a small shunt-less fuel gauge by Maxim Integrated
* nRF52840_moko_mk08 - a symbol for the Moko MK08 nRF52840 BLE module

## Footprint libs
### marbastlib-choc (untested only)
All switch and stab footprints in this lib include plate cuts on User.Eco2, as well as placement hints for both choc (User.Eco1) and MX (User.Drawings) switch spacing. LED and Stab footprints are not standalone, but intended to be combined with a switch footprint.
* SW_choc - solder-footprints for Kailh Choc (v1 only) switches
* SW_choc_HS - hotswap-footprints for Kailh Choc (v1 only) switches
* [**UNTESTED**] STAB_choc_2u - footprint for Kailh Choc 2u stabilizers
* [**UNTESTED**] STAB_choc_6.25u - footprint for Kailh Choc 6.25u stabilizers
* LED_choc_6028R(-FLIPPED) - add-on footprint for Kailh Choc with [6028](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E RGB LEDs
* [*SPECIALTY*] SW_choc_Reversible_1u - reversible footprints for Kailh Choc (v1 only) switches
* [*SPECIALTY*] SW_choc_MxCombo_1u - combo footprints for Kailh Choc (v1 only) and Cherry MX style switches
* [*SPECIALTY*] LED_choc_WS2812_2020-E(-FLIPPED) - experimental add-on footprint for Kailh Choc with reverse mounted WS2812_2020 - hand soldering only, use with caution
* [*SPECIALTY*] PLATE_choc - experimental footprint intended to be added to a choc switch so the switch footprint can be snapped off - allowing the PCB to double-function as a plate

### marbastlib-mx
All switch and stab footprints in this lib include plate cuts on User.Eco2, as well as placement hints for MX switch spacing (User.Drawings). LED and Stab footprints are not standalone, but intended to be combined with a switch footprint.
* SW_MX - solder-footprints for Cherry MX switches
* SW_MX_HS - hotswap-footprints for Cherry MX switches
* LED_MX_3mm(-FLIPPED) - add-on footprint for Cherry MX switches with 3mm single color LEDs
* STAB_MX - footprint for Cherry MX PCB-mount stabilizers
* STAB_MX_P - footprint for Cherry MX PCB-mount stabilizers with plated screw holes
* LED_MX_6028R(-FLIPPED) - add-on footprint for Cherry MX switches with [6028](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E RGB LEDs
* [*SPECIALTY*] SW_MX_Reversible_1u - reversible solder-footprints for Cherry MX switches
* [*SPECIALTY*] LED_MX_WS2812_2020-E(-FLIPPED) - experimental add-on footprint for Cherry MX switches with reverse mounted WS2812_2020 - hand soldering only, use with caution
* [*SPECIALTY*] PLATE_MX - experimental footprint intended to be added to a Cherry MX switch so the switch footprint can be snapped off - allowing the PCB to double-function as a plate
* [*SPECIALTY*] SW_MX_ULP_1u - footprint for the MX ultra low profile switch by cherry

### marbastlib-hitek
Since all stabs are plate-mount, only switch footprints are included. No dedicated footprints are available for ISO enter or similarly uncommon shapes. Use a `marbastlib-mx.pretty` stab footprint for alignment help if needed.
* [**UNTESTED**] SW_HiTek - solder-footprints for HiTek 725 series switches
* [**UNTESTED**] SW_HiTek_Mount - solder-footprints for HiTek 725 series switches including drills for the mounting screws for these switches

### marbastlib-alps
Since all stabs are plate-mount, only switch footprints are included. No dedicated footprints are available for ISO enter or other stabilized sizes. Use a `marbastlib-mx.pretty` stab footprint for alignment help if needed. Remember to add stabilizers from the MX library for combo footprints, if you plan to use them with MX PCB mount stabilizers as well.
* [**UNTESTED**] SW_Alps - solder-footprints for Alps SKCM/SKCL series switches
* [**UNTESTED**] SW_Alps_MX - combined solder-footprints for Alps SKCM/SKCL and Cherry MX series switches

### marbastlib-various
* SOT-23-6-routable - variation of the default SOT-23-6, with enough spacing for 2 traces between the pads and clearer pin 1 marking
* nRF52840_holyiot_18010 - 3 different footprints for the holyiot 18010 nRF52840 BLE module
* nRF52840_moko_mk08 - a footprint for the Moko MK08 nRF52840 BLE module
* SW_ESP3020 - footprint for ESP3020 SMD 2-way-switches
* LED_WS2812_2020 - footprint for WS2812B-2020 and WS2812C-2020
* [**UNTESTED**] ANT_2.4_IFA - Bluetooth IFA antenna, designed following a guide of Cypress: https://www.cypress.com/file/136236/download'
* SW_MSK12C02-HB - footprint for MSK12C02-HB SMD 1-pole, 2-position switch
* SW_SKHLLCA010 - footprint for Alps SKHLLCA010 THT pushbutton
* SW_SSSS213100 - footprint for Alps SSSSS213100 THT 1-pole, 2-position switch
* SW_SSSS223900 - footprint for Alps SSSS223900 THT 2-pole, 3-position switch
* SW_SPST_SKQG_WithStem - copy of the default kicad lib's SKQG footprint, but with rounded pads and pre-assigned 3d model
* ROT_Alps_EC11E-Switch - Improved version of the original kicad EC11E footprint with pre-assigned 3d model
* [**UNTESTED**] PNT_psp1000 - footprint for a PSP-1000 thumbstick
* [**UNTESTED**] PNT_RKJXU1210006 - Alps RKJXU1210006 slide-thumbstick (used in PSP-3000 models)
* LED_6028R - footprint for [6028 RGB LEDs](https://www.alibaba.com/product-detail/SMD-6028-Smd-Led-RGB-color_60283039151.html) and adressable SK6812MINI-E reverse mount RGB LEDs
* [*SPECIALTY*] LED_WS2812_2020_rearmount - experimental footprint for reverse mounted WS2812_2020 - hand soldering only, use with caution
* [**UNTESTED**] MAX77751 - a 1S LiIon battery management chip
* [**UNTESTED**] QFN-60_EP_7x7_Pitch0.4mm - footprint needed for IS31FL3741A
* [**UNTESTED**] STM32WB5MMG - a small form factor package including STM32WB chip and antenna
* CON_TC2030_Outlined - footprint for a Tag-Connect TC2030 header
* USB_C_Receptacle_HRO_TYPE-C-31-M-14 - footprint for a HRO Koreaparts mid-mount USB-C 2.0 receptacle
* [**UNTESTED**] CON_MJ-4PP-9 - footprint for a 3.5mm TRRS connector
* [**UNTESTED**] CON_MJ-4PP-9_Reversible - reversible footprint for a 3.5mm TRRS connector
* ProMicro - footprint for an Arduino Pro Micro (or other compatible MCU breakout board)
* ProMicroReversible - reversible footprint for an Arduino Pro Micro (or other compatible MCU breakout board)
* SplitkbTentingPuck - footprint for a splitkb Tenting Puck
* SW_kailh_big_1u - footprint for a Kailh x Novelkeys Big Switch
* CON_FH33J-4S-0.5SH - 4pin 0.5mm pitch FFC/FPC connector from Hirose (FH33 series)
* CON_FH33J-10S-0.5SH - 10pin 0.5mm pitch FFC/FPC connector from Hirose (FH33 series)
* CON_FH33J-12S-0.5SH - 12pin 0.5mm pitch FFC/FPC connector from Hirose (FH33 series)
* CON_JST_ACH_BM02B - 2pin low profile 1.25mm pitch connector, well suited for battery. Copy of the default kicad lib's ACH footprint with pre-assigned 3d model

## 3D Models
Many of these were provided by someone else. I do not hold any rights for those and owe the original designers big thanks. These models are NOT covered by the license applied to the rest of the repo. If no source is provided, I designed the model myself, using datasheet specs as far as possible. If your file is in this repo and you would like it gone, please contact me. I included them to make it easier to use the models directly from the library, but will respect the original designer's/copyright holder's wishes.

 * SK6812Mini-E
 * WS2812B-2020
 * MJ-4PP-9
 * Seiko Epson FA-128
 * MSK12C02-HB
 * Moko MK08A
 * JST BM02B-ACHSS (source: JST)
 * WS2812 Mini / SK6812 Mini ([source](https://grabcad.com/library/smd-ws2812b-led-1))
 * 1206 SMD polyfuse ([source](https://grabcad.com/library/0zcj0075af2e-1))
 * JST SH (2, 4, 5, 6, 8 pins) ([source](https://grabcad.com/library/jst-sh-smd-connectors-1/details?folder_id=3903823))
 * HRO TYPE-C-31-M-12 ([source](https://grabcad.com/library/type-c-31-m-12-1))
 * HRO TYPE-C-31-M-14 ([source](https://grabcad.com/library/hro-usb-type-c-31-m-14-1))
 * holyiot 18010 nRF52840 (thanks darryldh)
 * Alps EC11E and EC11N series 3D models ([source](https://tech.alpsalpine.com/e/products/cad.html))
 * Alps SKHLLCA010 ([source](https://tech.alpsalpine.com/prod/e/html/tact/snapin/skhl/skhllca010_3dcad.html))
 * Alps SSSS213100 ([source](https://tech.alpsalpine.com/prod/e/html/switch/slide/ssss2/ssss213100_3dcad.html))
 * Alps SSSS223900 ([source](https://tech.alpsalpine.com/prod/e/html/switch/slide/ssss2/SSSS223900_3dcad.html))
 * Kailh Hotswap socket (MX style) ([source](https://grabcad.com/library/kailh-pg1511-hotswap-socket-1))
 * Kailh Hotswap socket (Choc style) ([source](https://grabcad.com/library/kailh-1350-socket-2))
 * PSP-1000 Thumbstick (thanks [Hendrik](https://github.com/HendrikRoth))
 * Alps RKJXU1210006 Thumbstick ([source](https://tech.alpsalpine.com/e/products/detail/RKJXU1210006/))
