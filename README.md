# MIDIMustang2Rocksmith
Guide on generally setting up hardware and necessary software to get a RB3 Fender Mustang to operate in Rocksmith 2014 Remastered

## The obligatory blog post

To keep it short, the idea to use a RB3 Mustang in Rocksmith 2014 Remastered came around when I was reintroduced to Rocksmith and modding it when a user on Reddit by [VictoriousSponge](https://www.reddit.com/user/VictoriousSponge) posted how to use a software based "drop tune" effect to emulate the effect of some handy, albeit extremely expensive hardware that a company called Digitec makes. I enjoyed it, and I wanted to take it farther and push the limits.

TL;DR - My RB3 Mustang was mocking me in a corner, I had a creative spark with Reaper, and I like Rocksmith a lot.

## Requirements:
Presented in no particular order because reasons.

- PC or MacOS with Rocksmith 2014 Remastered **NOTE** <em>MacOS is currently untested and is theoretically possible. Guide only focuses on Windows because that's what I have on hand</em>
- Rock Band 3 Fender Mustang Pro Guitar or Rock Band 3 Squire Stratocaster Pro Guitar in MIDI mode
- Male to Male 5 Pin DIN MIDI cable of an acceptable length for your needs
- An audio interface that can accept MIDI through a 5 Pin DIN or a dedicated MIDI interface that can accept a 5 Pin DIN
- Cockos Reaper with ReaRoute installed. Install both the 32bit and 64bit versions [Download](https://www.reaper.fm/purchase.php)
- RS_ASIO by mdias [GitHub](https://github.com/mdias/rs_asio)
- Sampler or VSTi ideally something string-like with a strong attack and an adjustable sustain (limitations in a different section)

### Optional:

The following are optional, but will assist greatly with game streaming, effects, or analysis.

- OBS-ASIO by Andersama - Adds a new audio input type to OBS to accept ASIO [GibHub](https://github.com/Andersama/obs-asio)
- RSMods by LovRom8 - The mods nobody asked for! This (almost) one click project makes it easy to set up RS_ASIO and other helpful mods [GitHub](https://github.com/Lovrom8/RSMods)
- MidiMonitor by Robin Schmidt - Allows you easily see MIDI note_on/off events, MIDI channel info, expression parameters, etc [Website](https://plugins4free.com/dev/255/)

## Setup:

A lot of the necessary setup is based on other tutorials for RS_ASIO. I'm including the general setup here just for flow.

1. Start Reaper 32bit and create a new project. Give the project a name you can remember and save the project in a directory you can remember
2. Check your project preferences so that you're set to 48KHz sampling ![](../Images/projectSettings.png "File > Project Settings")

## Limitations (Leave for end)

Limitations with using this setup as a meaningful way of playing Rocksmith 2014 are plentiful. Here's a not comprehensive, but decent list:

- Batteries, you have to use batteries. The RB3 Mustang does not have a DC power input. If you're going to be serious with this, invest in rechargeable AA batteries
- You cannot bend notes like you can on a traditional guitar
    - According to the RB3 Mustang [manual](https://www.manualsdir.com/manuals/103077/rock-band-fender-mustang-pro-guitar-rock-band-3.html?page=8), selecting the right MIDI mapping feature will allow pitch bends based on the built in accelerometer position/orientation (limited to one semitone up/down), as well as an analog expression pedal connected to the 3.5mm jack on the RB3 Mustang. The former is difficult to control but fun, and the later I have not tested due to a lack of hardware
- You cannot mute or finger mute strings or to prevent them from "ringing out"; playing octaves gets certainly annoying without learning how to chicken pick
- You cannot play palm mutes. Sorry, no chugga-wugga djent heroes here
- You cannot play harmonics of any kind, like bell, pinch, and harp
- If you are in the default Strum Mode on the RB3 Mustang, you cannot slide, hammer-on, pull-off, or tap
- When you are in Synth Mode, notes play when you press a fret button, and since you can't mute notes, the note plays
- You can only tune up and down by octaves on the fly; for some reason Harmonix and MadCatz didn't think about people who like to play in different tunings
    - You can use something like Pitchproof by Aegean Music to access different tunings like C# Standard or Eb Standard [Site](https://aegeanmusic.com/pitchproof-specs)
- No drop tunings or slack tunings without some major MIDI intervention
    - Luckily, each string of the RB3 Mustang is mapped to a different MIDI channel, so with the right tools you can rectify this limitation I just currently don't know how
- Depending on your interface and VSTi/Sampler, latency will increase, but it should not be TOO bad
- Remember that Rocksmith 2014 works by detecting the notes out of your electric guitar or bass. For best results, use a sample or VSTi that mimics a plucked stringed instrument, like a harp, harpsichord, lute, etc
    - I've had some great success with e-pianos that have a defined attack and moderate decay
    - Avoid instruments that can play a note forever, like organs, woodwinds