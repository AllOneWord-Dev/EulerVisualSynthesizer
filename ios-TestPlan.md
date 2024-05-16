# Euler Visual Synthesizer QA Plan (iOS)


## Intro

Euler Visual Synthesizer for iOS is an application for exploring the beautiful world of mathematical periodic functions with modern rendering techniques and effects. It is an application for “playing” presets created by the full desktop application for macOS. 

Presets are organized into collections called Banks. A bank can contain up to 32 presets. The base iOS app comes with a single bank named “EVS Showcase” of 16 presets. There are two additional banks available for in-app purchases:

* Townsend ’94 - Includes a collection of energetic presets designed to be synchronized to energetic / dance music.
* King St. Garage - Includes a collection of slowly evolving and dynamic presets that are designed for more down-tempo style music accompaniment.

The macOS app is used to design custom presets and banks - which can be shared with both the iOS and tvOS apps using your iCloud account. The base version of the macOS app comes with an additional 3 banks. The pro version of the macOS app includes the ability to interact with the presets using MIDI controllers as well as the ability to move the render view to an external window / external monitor for fullscreen playback support. The Pro version comes with 9 Banks, including the Townsend ’94 and King St. Garage banks that are available for in-app purchases for iOS and tvOS (i.e., if you purchase the Pro version of the desktop app, there is no need to also purchase those two banks for iOS and tvOS).

## iOS UI Overview

![iOS UI](https://raw.githubusercontent.com/AllOneWord-Dev/EulerVisualSynthesizer/main/docs/iOS-UI-Overview.png)

*Note: The main screen including UI Overlay only supports lanscape orientation for mobile. For iPad, both orientations are supported.*

## Test Plan

####Launch App

* Verify last played preset in last chosen bank is playing
* Verify UI overlay can be displayed by single tap on screen
* Verify UI overlay times out after 5s of no interactivity
* Verify layout of UI overlay matches UI Overview image

####Transport Controls

* Verify Rewind button changes presets
* Verify Forward button changes presets
* Verify play/pause button toggles play/pause state and icon updates appropriately

####Playback Mode Controls

* Verify when no shuffle mode is selected, the currently playing presets continues playing until user manually changes presets.
* Verify sequential mode: Choose the Sequential mode button. Choose a duration, and verify that presets of the current bank are played sequentially for that duration
* Verify shuffle mode (random): Choose the Shuffle mode button. Choose a duration and verify that presets of the current bank are played in a random order

####Tempo Controls



* Verify tapping on the Tempo Source button brings up a chooser menu and you can choose between Global, Preset, and Bank as the source of the Tempo.
* Play some music and tap the red BPM LED along to the tempo of the playing music - tap at least 4 times - verify that the tempo is updated as you tap.

*Tempo Notes*

* *It may be difficult to verify all of the tempo controls if you don't have access to the macOS Desktop App.*
* *Not all presets in EVS Showcase are synchronized to tempo. However, presets in the Townsend '94 and King St. Garage banks should be synchronized to tempo.*


####Interactivity

* Click on the pan icon to enter interactivity mode. 
* Verify interactivity mode does not automatically time out (it must be manually closed using X (close) button)
* Each preset has its own interactivity designed specifically for that preset. However, single finger pan should produce independent modifications to the preset in the X and Y axis. 
* By default, pinch is set to zoom - but can be overriden by the preset designer.
* By default, two-finger rotate is set to rotate - but can be overriden by the preset designer.
* Two Finger Pan is automatically assigned to 3D orbit of preset. (Really only useful for presets that designed as a 3D shape).
* Verify interactivity mode can be closed by taping the X (close) button

####Main Menu - Library

* If you have not added either of the in-app purchase banks, verify the only bank shown is the included "EVS Showcase" bank.
* After purchasing Townsend '94 and King St. Garage, verify those banks are also displayed in the Library collection.
* Verify choosing a bank be tapping on one of the banks in the Library collection list.
* Verify the presets now playing are part of that bank.


**Note: TestFlight users are NOT charged when making in-app purchase transactions. A sandbox user is automatically created for each TestFlight user and that sandbox user is used for all in-app purchases.**

####Main Menu - Cloud

There are 3 possible Rows that can be displayed when choosing the Cloud page.

* The top row displays banks available for in-app purchases. Once you have purchased all of the banks, this row will no longer be displayed.
* The next possible row displayed is the row of all banks available to download from your iCloud account. Banks will only show up in this row if you have the macOS Desktop app and have shared / uploaded banks using the Bank Manager of the macOS Desktop app.
* The last possible row displayed is the row of banks that you have downloaded to your device. Selecting Banks in this row, will move this bank from downloaded banks to banks in your iCloud. Note: Selecting a bank in this row, only deletes the bank from your local library on your iOS device. It does not delete the Bank from your iCloud account.


####Main Menu - Settings

Playback Mode / Playback duration selections are available here as well as the main UI.

If you have an A12X or later device, there is an optional Playback Quality selector. You can choose from two different modes "Quality" and "Performance". Quality mode is roughly 2x the resolution of Performance mode. On most devices A12X or later, most presets will run at or close to 60fps in Performance mode. Quality mode really starts puchsing the limits of performance for even the most recent devices.

TestFlight builds display the FPS on the render screen, so you can track performance of presets on different devices.

**For testers interested in creating their own presets / banks, and testing the iCloud Bank sharing features, please send me a message and I can add you to the macOS Desktop app TestFlight list.**

[Contact Developer](mailto:alloneword.software@gmail.com)
