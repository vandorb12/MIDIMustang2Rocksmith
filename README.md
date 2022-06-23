# MIDIMustang2Rocksmith
Guide on generally setting up hardware and necessary software to get a RB3 Fender Mustang to operate in Rocksmith 2014 Remastered

## The obligatory blog post

To keep it short, the idea to use a RB3 Mustang in Rocksmith 2014 Remastered came around when I was reintroduced to Rocksmith and modding it when a user on Reddit by [VictoriousSponge](https://www.reddit.com/user/VictoriousSponge) posted how to use a software based "drop tune" effect to emulate the effect a handy, albeit extremely expensive piece of audio hardware that a company called Digitec makes. I enjoyed it, and I wanted to take it farther and push the limits.

**TL;DR** - My RB3 Mustang was mocking me in a corner, I had a creative spark with Reaper, and I like Rocksmith a lot.

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

    - OBS-ASIO by Andersama - Adds a new audio input type to OBS to accept ASIO [GitHub](https://github.com/Andersama/obs-asio)
    - RSMods by LovRom8 - The mods nobody asked for! This (almost) one click project makes it easy to set up RS_ASIO and other helpful mods [GitHub](https://github.com/Lovrom8/RSMods)
    - MidiMonitor by Robin Schmidt - Allows you easily see MIDI note_on/off events, MIDI channel info, expression parameters, etc [Website](https://plugins4free.com/dev/255/)

## Setup:

A lot of the necessary setup is based on other tutorials for RS_ASIO and ReaRoute. I'm including the general setup here just for flow. Please check out this awesome written tutorial from [lastpixel.tv](https://lastpixel.tv/low-latency-rocksmith-obs-streaming-with-software-effects/), or if you're visual use this [YouTube Video Tutorial](https://www.youtube.com/watch?v=gBlOokiYPUU) from DeathlySin/VictoriousSponge.

1. Start Reaper and create a new project. Give the project a name you can remember and save the project in a directory you can remember
2. Check your project preferences so that you're set to 48KHz sampling 

    ![Sample rate settings for project](/Images/projectSettings.png "File > Project Settings or Alt+Enter on Windows")

3. Check your Reaper Audio Device preferences, make sure you're using your ASIO drivers for your soundcard/interface. For my setup, I'm using my Focusrite Saffire Pro40

    ![Audio device settings](/Images/reaperPreferences_audioDevice.png "Options > Preferences or CTRL+P on Windows")    

    Note that the requested sample rate is 48KHz
4. Check your Reaper MIDI Device preferences, check that your MIDI interface can be seen by Reaper and is enabled. If it's not enabled, right click the MIDI input interface and enable it. My Focusrite Saffire Pro40 has a 1x1 MIDI 5 pin DIN input/output

    ![MIDI device settings](/Images/reaperPreferences_MIDIDevice.png "Options > Preferences or CTRL+P on Windows")

5. Add a new MIDI item by going to Insert > New MIDI Item. Change the track input from an audio input to a MIDI input, in my case Pro40 MIDI All channels. Add a VSTi instrument to the FX panel, and then change the routing so that it no longer goes through the Master Send and is sent through a stereo Hardware Output ReaRoute 1/ReaRoute 2. Record Enable the track with monitoring, and you should be able to see MIDI events come in when you play the RB3 Mustang.

    ![MIDI Track setup](/Images/reaper_track1Setup.png "Mutliple steps at once, I know. Check out lastpixel's tutorial if you need more help")

    You won't be able to hear anything because we turned off the Master Send. If you're troubleshooting, you can turn this back on in the track routing menu
6. Add a new audio track by going to Track > Insert New Track or `CTRL+T` on Windows. Set the track input to Stereo ReaRoute 1/ReaRoute 2. Turn on Record Enable and turn on Monitoring. In track routing, optionally add a stereo Hardware Output for ReaRoute 3/ReaRoute 4 (can be used for OBS streaming) 

    ![Rocksmith Track setup](/Images/reaper_track2Setup.png "Now we're getting somewhere")

7. Either using RS-Mods or editing the RS_ASIO config file, add the first stereo pair of ReaRoute as outputs and the second stereo pair as inputs

    ![RS_ASIO configuration](/Images/rsasioSettings.png "RS_ASIO is picky. It needs to saved exactly like this")

    ![RS-Mods RS_ASIO window](/Images/rsMods_rsasioSettings.png "It's all teal and stuff")

8. Boot up Rocksmith 2014 Remastered. You should now have audio from the synth you selected in Reaper going through the game! You're playing with plastic guitars now, you Guitar Hero, you!
9. Check your levels in Reaper so that you are not clipping your MIDI output. Adjust output gain as necessary so that it doesn't clip. Play all strings with a little force to max out the note velocity on each string
10. Don't forget to recalibrate and save your new Reaper project! 

## To Play:

1. Confirm the Windows can see your MIDI interface
2. Start Reaper and open up your saved project for playing a plastic guitar in Rocksmith 2014
3. Confirm that Reaper can see MIDI inputs from the RB3 Mustang
4. Start Rocksmith 2014
5. ???
6. Profit 

## Extras:

This is where we talk about extra bits and other ideas

### Effects:

   You gotta pick your poison when it comes to this. What do YOU want to sound like? Add a drop tuner, add compression, whatever to your MIDI FX chain! Avoid using any reverb, delay, and excessive overdrive/distortion going in to Rocksmith: use their tools for those effects.
### Streaming:

   If you continue on with [lastpixel's guide](https://lastpixel.tv/low-latency-rocksmith-obs-streaming-with-software-effects/), you can use Reaper's ReaRoute to route Rocksmith's audio via ultra-low latency ASIO from Reaper to OBS.
### Recording:

   Reaper is a DAW after all. Why not record your performance and become an overnight MIDI sensation? With MIDI, you can easily adjust your performance after the fact. Make it look like you really know what you're doing!

## Limitations:

Limitations with using this setup as a meaningful way of playing Rocksmith 2014 are plentiful. Here's a not exhaustive, but decent list of them:

- Batteries, you **HAVE** to use batteries. The RB3 Mustang does not have a DC power input. If you're going to be serious with this, invest in rechargeable AA batteries
- Rocksmith 2014, at least on Windows, is a 32bit application. I've had more luck running 32bit Reaper than I have with 64bit Reaper. ReaRoute might act funny or not at all with Rocksmith 2014 if you're not using Reaper 32bit
- The RB3 Mustang only has 17 frets when most guitars have 22 frets; this WILL limit the number of songs you can play
- There's no easy way to flip the strings for left handed players on the guitar itself
- You cannot bend notes like you can on a traditional guitar
    - According to the RB3 Mustang [manual](https://www.manualsdir.com/manuals/103077/rock-band-fender-mustang-pro-guitar-rock-band-3.html?page=8), selecting the right MIDI mapping feature will allow pitch bends based on the built in accelerometer position/orientation (limited to one semitone up/down), as well as an analog expression pedal connected to the 3.5mm jack on the RB3 Mustang. The former is difficult to control but fun, and the later I have not tested due to a lack of hardware
- You cannot mute or finger mute individual strings to prevent them from "ringing out"; playing octaves gets certainly annoying without learning how to chicken pick
- You cannot play palm mutes. Sorry, no chugga-wugga djent heroes here
- You cannot play harmonics of any kind, like bell, pinch, and harp
- If you are in the default Strum Mode on the RB3 Mustang, you cannot slide, hammer-on, pull-off, or tap
- When you are in Synth Mode, notes play when you press a fret button, and since you can't mute notes, the note plays
- In Synth Mode, you must set an initial note velocity by strumming before you can play a note on the fretboard
    - You can have up to 6 different note velocities, one on each string. Experiment!
- You can only tune up and down by octaves on the fly; for some reason Harmonix and MadCatz didn't think about people who like to play in different tunings
    - You can use something like Pitchproof by Aegean Music to access different standard tunings like C# Standard or Eb Standard [Website](https://aegeanmusic.com/pitchproof-specs)
- No drop tunings or slack tunings without some major MIDI intervention
    - Luckily, each string of the RB3 Mustang is mapped to a different MIDI channel, so with the right tools you can rectify this limitation: I just currently don't know how
- Depending on your interface and VSTi/Sampler, latency will increase, but it should not be TOO bad
- Remember that Rocksmith 2014 works by detecting the pitch of the notes out of your electric guitar or bass. For best results, use a sample or VSTi that mimics a plucked stringed instrument, like a harp, harpsichord, lute, etc
    - I've had some great success with e-pianos that have a defined attack and moderate decay
    - Avoid instruments that can play a note forever, like organs, woodwinds. They work, but strummed open strings will play forever until a fret is pressed
    - Avoid extremely distorted instruments that have an excessive amount of harmonics, instruments that modulate pitch a lot, or "spacey" pads

