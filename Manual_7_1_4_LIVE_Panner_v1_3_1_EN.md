# 7.1.4 LIVE Panner v1.3.1 User Manual

Version: Public Beta 1.3.1  
Device type: Max for Live Audio Effect  
Purpose: Route one audio track in Ableton Live to a 12-channel 7.1.4 speaker system.

## 1. Before Installation

Recommended environment:

- Ableton Live 12 Suite, or any Ableton Live version with Max for Live support.
- macOS.
- An audio interface with at least 12 physical outputs.
- Outputs 1/2 through 11/12 enabled in Ableton Live's Audio Output Config.

If your audio interface has fewer than 12 physical outputs, the device can still open, but you cannot fully test a complete 7.1.4 system.

## 2. Unzip and Copy Location

After unzipping, you should have this folder:

```text
LR_714_Panner_v1_3_1_Public_Beta
```

Recommended location inside your Ableton User Library:

```text
~/Music/Ableton/User Library/Presets/Audio Effects/Max Audio Effect/LR_714_Panner_v1_3_1_Public_Beta/
```

If your User Library is not in the default location, open Ableton Live and check:

```text
Settings / Preferences > Library > Location of User Library
```

Then place the full folder inside:

```text
Presets/Audio Effects/Max Audio Effect/
```

Important: Do not copy only `LR_714_Panner_v1_3_1.amxd`. This device needs the `.js` and `.maxpat` dependency files in the same folder. Keep the full folder intact.

## 3. Files in the Package

Keep these files together:

```text
LR_714_Panner_v1_3_1.amxd
BrowseRoutingInline_avenir.maxpat
RoutingObjects.maxpat
lr_714_gains_comfy.js
lr_714_pad_avenir_bigger.js
lr_714_meter_avenir.js
lr_714_testfreq.js
lr_logo.js
README_FIRST.txt
Manual_7_1_4_LIVE_Panner_v1_3_1_EN.md
Manual_LR_714_Panner_v1_3_1_CN.md
ReleaseNotes_v1_3_1_CN.txt
```

`LR_714_Panner_v1_3_1.amxd` is the Max for Live device that you drag into Live. The other files provide the user interface, routing, metering, test tone mapping, and panning logic.

## 4. Load the Device in Ableton Live

Method 1: Load from Live Browser.

```text
User Library > Presets > Audio Effects > Max Audio Effect > LR_714_Panner_v1_3_1_Public_Beta
```

Drag `LR_714_Panner_v1_3_1.amxd` onto an Audio Track.

Method 2: Drag from Finder.

Drag `LR_714_Panner_v1_3_1.amxd` from Finder directly onto the device area of an Audio Track in Ableton Live.

The device should be placed on the audio source track you want to pan in 7.1.4. For the first test, do not place it on a Return Track or the Master Track.

## 5. Set the Track Output to Sends Only

After loading the device, set the track output to:

```text
Audio To = Sends Only
```

Some users may call this "Send Only", but Ableton Live's English interface usually displays it as `Sends Only`.

Reason: 7.1.4 LIVE Panner sends audio directly to 12 output channels through its internal Max for Live output structure. If the same track also goes to `Main`, you may hear duplicated audio, incorrect spatial placement, or misleading level results.

Correct track state:

```text
Audio Track
Audio To: Sends Only
Monitor: Auto or In, depending on your source
```

## 6. Configure Audio Outputs in Live

In Ableton Live, open:

```text
Settings / Preferences > Audio > Output Config
```

Enable at least these output pairs:

```text
1/2
3/4
5/6
7/8
9/10
11/12
```

If your audio interface labels outputs with custom names, such as `15/16 BBL VCA` or `17/18 Manley`, those names may appear in Live's output menus. That is normal.

## 7. ROUTING Section

The right side of the device has a `ROUTING` section with three columns:

```text
PAIR | TYPE | CH
```

Meaning:

- `PAIR`: The internal output pair inside the device.
- `TYPE`: The routing type. For normal use, select `Ext. Out`.
- `CH`: The physical audio interface output pair.

Standard 12-channel routing:

```text
PAIR 1/2   TYPE Ext. Out   CH 1/2
PAIR 3/4   TYPE Ext. Out   CH 3/4
PAIR 5/6   TYPE Ext. Out   CH 5/6
PAIR 7/8   TYPE Ext. Out   CH 7/8
PAIR 9/10  TYPE Ext. Out   CH 9/10
PAIR 11/12 TYPE Ext. Out   CH 11/12
```

Ableton Live exposes external outputs as stereo pairs, so the ROUTING section shows six stereo pairs. Internally, the device still outputs 12 mono channels.

## 8. 7.1.4 Channel Order

The internal channel order is fixed:

```text
1  L
2  R
3  C
4  LFE
5  Ls
6  Rs
7  Lrs
8  Rrs
9  Ltf
10 Rtf
11 Ltr
12 Rtr
```

Output pair mapping:

```text
1/2   = L / R
3/4   = C / LFE
5/6   = Ls / Rs
7/8   = Lrs / Rrs
9/10  = Ltf / Rtf
11/12 = Ltr / Rtr
```

If your physical speaker wiring uses a different order, adjust the `CH` values in the ROUTING section to match your actual audio interface outputs.

## 9. TEST Section

The TEST section is used to check the audio interface channels and confirm that the device is producing output.

### TEST

Test signal switch.

- Off: No test signal is generated.
- On: The device generates an internal sine test tone.

For the first channel check, you can leave your music source stopped and use only TEST.

### VOL

Test signal level.

Range:

```text
0 = -inf dB
100 = 0 dB
```

Start at a low level for the first test. Raise the level only after confirming that the routing and speaker wiring are correct.

### HZ

Test signal frequency.

Control range:

```text
20 Hz to 20000 Hz
```

Knob center:

```text
1000 Hz
```

Recommended initial test frequency:

```text
1000 Hz
```

## 10. XY / Z Panning Window

The central window shows the 7.1.4 sound field position.

Displayed labels:

```text
L / R / C / LFE
Ls / Rs
Lrs / Rrs
Ltf / Rtf
Ltr / Rtr
```

The yellow ball represents the current spatial center.

Operation:

- Drag the yellow ball inside the XY window to change the X / Y position.
- Use the `Z` knob to control height.
- The XY window updates when the X / Y / Z knobs change.

Coordinate meaning:

```text
X = left/right position, -1.00 is left, 0.00 is center, 1.00 is right
Y = front/back position, 1.00 is front, 0.00 is center, -1.00 is rear
Z = height position, 0.00 is base layer, 1.00 is upper height layer
```

## 11. SHAPE / SPACE Control Section

This version keeps six core controls:

```text
Spread / Focus / LFE
X / Y / Z
```

These are the main controls recommended for automation and MIDI mapping.

### Spread

Controls the spatial spread of the sound.

Range:

```text
0 to 100
```

Higher values distribute the sound more widely across nearby speakers. Lower values keep the sound closer to the current spatial center.

### Focus

Controls how concentrated the spatial image is.

Range:

```text
0 to 100
```

Higher values make the energy more focused, and the yellow range circle in the XY window becomes smaller. Lower values make the energy looser, and the yellow range circle becomes larger.

### LFE

Controls the send level to the LFE channel.

Range:

```text
0.00 to 1.00
```

Important: LFE is an independent send amount, not a full bass management crossover. In live use, start from 0 and raise it slowly to avoid excessive LFE output.

### X

Left/right position control for MIDI mapping and automation.

Range:

```text
-1.00 to 1.00
```

### Y

Front/back position control for MIDI mapping and automation.

Range:

```text
-1.00 to 1.00
```

### Z

Height control for MIDI mapping and automation.

Range:

```text
0.00 to 1.00
```

## 12. Meter Section

The meter shows the 12 output channels:

```text
L R C LFE Ls Rs Lrs Rrs Ltf Rtf Ltr Rtr
```

The green fill shows current level. The yellow line is a visual reference / peak-style indicator.

Important: This meter shows the signal inside the device before the final hardware output. It is not the same as the acoustic sound pressure level from your speakers.

## 13. Automation and MIDI Mapping

Recommended controls for automation and MIDI mapping:

```text
Spread
Focus
LFE
X
Y
Z
```

Ableton MIDI mapping steps:

1. Press `Cmd + M` to enter MIDI Map Mode.
2. Click the target control in the device, such as `X`.
3. Move the knob or fader on your MIDI controller.
4. Press `Cmd + M` again to exit MIDI Map Mode.

For automation recording, record the `X / Y / Z` knobs directly instead of only dragging the XY window.

## 14. First Full Test Procedure

Use this order for the first test:

1. Unzip the full `LR_714_Panner_v1_3_1_Public_Beta` folder.
2. Place the full folder inside Ableton User Library's Max Audio Effect directory.
3. Open Live and create one Audio Track.
4. Drag `LR_714_Panner_v1_3_1.amxd` onto that Audio Track.
5. Set the track's `Audio To` to `Sends Only`.
6. Open Live's `Output Config` and confirm that 1/2 through 11/12 are enabled.
7. In the device's ROUTING section, set all output pairs from 1/2 through 11/12 to `Ext. Out` with matching channels.
8. Turn TEST on.
9. Raise VOL slowly.
10. Set HZ to 1000 Hz for the first check.
11. Move X / Y / Z and watch the 12-channel meter.
12. Confirm that each physical audio interface output and speaker position is correct.

## 15. Troubleshooting

### The device opens as a blank panel

The dependency files are probably not in the same folder as the `.amxd`. Unzip the package again, keep the full folder intact, and open the `.amxd` from that folder.

### TEST produces no sound

Check these items in order:

```text
TEST is on
VOL is above 0
Audio To is set to Sends Only
ROUTING is set to Ext. Out
CH is assigned to real audio interface outputs
Live Output Config has the required outputs enabled
The physical audio interface outputs are connected to speakers
The track is not muted
```

### The meter moves, but the speakers are silent

The device is producing signal. The issue is usually in ROUTING, Live Output Config, the audio interface output assignment, or the physical speaker wiring.

### Only paired outputs such as 1/2 and 3/4 are visible

This is how Ableton Live displays external outputs. Live manages external outputs as stereo pairs, while the device still outputs 12 mono channels internally.

### LFE looks too high

First confirm that you are using v1.3.1. Then set the LFE knob to 0 and raise it slowly. The LFE channel is channel 4, which is the right side of the `3/4` output pair.

### Audio comes from both Main and the surround outputs

Set the track's `Audio To` to `Sends Only`.

### ROUTING shows No Output

First set `TYPE` to `Ext. Out`, then set `CH` to the correct audio interface output pair.

## 16. Public Beta Feedback

When reporting an issue, include as much of this information as possible:

```text
Ableton Live version
macOS version
Audio interface model
Number of audio interface outputs
Screenshot of Live Output Config
Screenshot of the device ROUTING section
Exact steps that caused the issue
Whether TEST produces sound
Whether the meter reacts
```

This makes it faster to identify whether the issue is in the device, Live routing, audio interface settings, or physical speaker wiring.
