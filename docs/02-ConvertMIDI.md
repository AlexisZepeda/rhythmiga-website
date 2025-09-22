---
title: Convert MIDI to RHY
---

## RHY File

A RHY file (.rhy) is the beatmap, created from using a MIDI file. What a RHY file really is, is a MIDI stripped down to the bare essential information Rhythmiga 2 needs to accurately recreate the notes in the MIDI file. With binary serialization it makes for a smaller file size at the cost of the readability.

## Load MIDI to Rhythmiga 2

When you have prepared the MIDI file, it is ready to be turned into a RHY file for Rhythmiga 2. Open Rhythmiga 2 and go to the MIDI Converter tool. First load the MIDI file by pressing the Load MIDI button, then select the MIDI from the directory you placed it in. Once the MIDI file has been converted the Save RHY button will be enabled, allowing you to create the RHY file, however it is advised to add the Song Name, Artist Name, and Difficulty first.

## Song Information

### Song Name

(Required)

The song name is the name that will appear in the Song Select menu. While not every beatmap the song will have needs to have the song name, it is strongly recommended to add the song name to at least one beatmap.

### Artist Name

(Optional)

The artist name is not required. However, if you wish for the artist name to appear in the Song Select menu, it is recommended to add the artist name to at least one beatmap.

### Difficulty

(Required)

The difficulty is the most important selection to add to the RHY file. Without it, the game cannot determine where to place the beatmap, therefore make sure to select between Easy, Medium, and Hard.

## Save RHY File

With all the necessary song information completed you can press the Save RHY button to create the file. Remember where it was saved as you will need it when the time comes to import the RHY file.