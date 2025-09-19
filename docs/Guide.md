---
slug: /
title: MIDI Converter Guide
---

## Introduction
Rhythmiga 2 is rhythm game based on the Theatrhythm game series developed indieszero, specifically, the latest entry Theatrhythm Final Bar Line. This guide focuses on how to create MIDI files that can be converted into beatmaps. Rhythmiga 2 uses the beatmaps to create the on-screen notes the player interacts with. If the rules set-forth in this guide are not properly followed it can lead to a broken beatmap. A basic understanding of music theory and of how to use a MIDI editor is required.
## Quick Reference
### Lane
- Lane 1 Keys: B
- Lane 2 Keys: A
- Lane 3 Keys: F
- Lane 4 Keys: C

### Trigger Types
- Tap/Long Trigger
	- MIDI Octave: C4 – B4
- Arrow Trigger
	- North
		- MIDI Octave*: C0 – B0
	- Northeast
		- MIDI Octave*: C1 – B1
	- East
		- MIDI Octave*: C2 – B2
	- Southeast:
		- MIDI Octave*: C3 – B3
	- South:
		- MIDI Octave*: C5 – B5
	- Southwest:
		- MIDI Octave*: C6 – B6
	- West:
		- MIDI Octave*: C7 – B7
	- Northwest:
		- MIDI Octave*: C8 – B8

### Double Arrow Trigger
	Use the MIDI Octave for one arrow and the Channel number for the second arrow.
	North:
		Channel: 2
	Northeast
		Channel: 3
	East
		Channel: 4
	Southeast:
		Channel: 5
	South:
		Channel: 6
	Southwest:
		Channel: 7
	West:
		Channel: 8
	Northwest:
		Channel: 9

### Tables
|  			Trigger Type 		               |  			Direction 		 |  			MIDI Octave* 		 |  			MIDI Note Number 		 |   
|------------------------------|-------------|----------------|--------------------|
|  			Tap 		                        |  			   			 		       |  			C4-B4 		        |  			60-71 		            |   
|  			Long 		                       |  			   			 		       |  			C4-B4 		        |  			60-71 		            |   
|  			Arrow/ Long w/ One Arrow  			 		 |  			↑ 		         |  			C0–B0 		        |  			12-23 		            |   
|  			   			 		                        |  			↗ 		         |  			C1-B1 		        |  			24-35 		            |   
|  			   			 		                        |  			→ 		         |  			C2-B2 		        |  			36-47 		            |   
|  			   			 		                        |  			↘ 		         |  			C3-B3 		        |  			48-59 		            |   
|  			   			 		                        |  			↓ 		         |  			C5-B5 		        |  			72-83 		            |   
|  			   			 		                        |  			↙  			 		       |  			C6-B6 		        |  			84-95 		            |   
|  			   			 		                        |  			←  			 		       |  			C7-B7 		        |  			96-107 		           |   
|  			   			 		                        |  			↖ 		         |  			C8-B8 		        |  			108-119 		          |   
|  			Trigger Type 		                       |  			Direction 		 |  			Channel Number 		 |   |   |
|  			Second Arrow/ Long w/ Double 			Arrow 		 |  			↑ 		         |  			2 		              |   |   |
|  			   			 		                                |  			↗ 		         |  			3 		              |   |   |
|  			   			 		                                |  			→ 		         |  			4 		              |   |   |
|  			   			 		                                |  			↘ 		         |  			5 		              |   |   |
|  			   			 		                                |  			↓ 		         |  			6 		              |   |   |
|  			   			 		                                |  			↙  			 		       |  			7 		              |   |   |
|  			   			 		                                |  			←  			 		       |  			8 		              |   |   |
|  			   			 		                                |  			↖ 		         |  			9 		              |   |   |
*Depending on the octave numbering of the MIDI editor this number may go down by one.

## Offset in the editor

Rhythmiga 2 requires sixteen beats of offset to give the game time to create the triggers. When creating the MIDI, leave a space of sixteen beats at the start of the track and the song. In 4/4 time this the equivalent of one measure, however depending on the time signature of the song this will vary. It is advised to count sixteen beats instead of relying on the measure marks in the MIDI editor to avoid problems.

## MIDI Octave Numbers

There is no MIDI standard convention for numbering the octaves on the keyboard. The MIDI specifications only requires that note number 60 be a C. This can typically be thought of as Middle C, but it does not have to be. Therefore, depending on the MIDI editor or keyboard the octave number of Middle C can vary. The two most common conventions place Middle C (note number 60) at octave 3 “C3” or octave 4 “C4”. Rhythmiga 2’s MIDI Converter tool relies on Middle C as well to properly determine the trigger types. Due to this variance, it is important to find out which octave number Middle C is in the MIDI editor.

For example, if the MIDI editor has Middle C (note number 60) as “C3” then the arrow North trigger will be “C-1” and arrow Down trigger will be “C4”.

As a reference, FL Studio uses the “C4” standard; MidiEditor and signal use the “C3” standard. An online MIDI parser can help determine which standard the MIDI editor uses.

## MIDI Channels
There are sixteen MIDI channels in the MIDI specifications, numbered 1 to 16. MIDI channels are used to connect multiple instruments to a single MIDI controller. For the purpose of this guide, MIDI channels are used to determine the direction of the second arrow in the Double Arrow Trigger. By default a track is set to Channel 1 in a MIDI editor, therefore Double Arrow Triggers begin at Channel 2, using Channel 1 will create an Arrow Trigger.

## Lanes
Rhythmiga 2 uses a four lane, top-to-bottom system to display the triggers on the screen. The lane-note relationship is determine by the key pressed, regardless of the octave the key is in. From top to bottom the order is as follows: B, A, F, and C.

Lane 1 --- B
Lane 2 --- A
Lane 3 --- F
Lane 4 --- C

A Tap trigger on Lane 4 would correspond to the key “C4”, an Arrow trigger pointing to the West on Lane 2 would be key “A7”, to give two examples. There are no special cases, therefore, for convenience each lane can be named after the key it is associated with.

Lane 1 → Lane B
Lane 2 → Lane A
Lane 3 → Lane F
Lane 4 → Lane C

![Lanes](/img/Lanes.jpg)


## Differentiating Tap Triggers from Long Triggers
Before discussing the ways in which the triggers need to be drawn in the MIDI editor, how to get the MIDI Converter tool to distinguish between Tap triggers and Long Triggers needs to be addressed. Rhythmiga 2 uses the amount of beats a key is pressed to find out whether the trigger should be pressed once (Tap trigger) or pressed and held down (Long Trigger). At the simplest level, a Tap Trigger is one beat long and a Long Trigger is any note longer than one beat. One beat, for the purpose of creating a Rhythmiga 2 beatmap, is the equivalent of one sixteenth note. A sixteenth note is the smallest beat Rhythmiga 2 can recognize. 

Depending on the MIDI editor, the best way to ensure the note drawn is a sixteenth note is to set the grid snapping function to a subdivision of 16 and then reduce the length of the note the smallest form the editor will allow. This note of the shortest duration can then be considered a sixteenth note.

This section will not delve into the music theory, suffice to say, this principle extends to creating Arrow Triggers and other variations of Long Triggers.

![TapvsLong](/img/Tap%20and%20Long.jpg)

The picture above shows one measure using a subdivision for every sixteenth beat. In 4/4 time, one measure contains 16 beats. Therefore, the “C4” will be a Tap Trigger because it is only one beat long, while the “F4”, “A4”, and “B4” will be Long Triggers.

## Triggers

### Tap Trigger
A Tap Trigger is a trigger the player has to press one time, or tap. To create a Tap Trigger, add one sixteenth note of the corresponding key in the octave range of 4 (“C4”, “F4”, “A4”, or “B4”).

![Tap](/img/Tap%20Triggers.jpg)

### Long Trigger
A Long Trigger is a trigger the player has to press, hold, and then release. To create a Long Trigger, add a note of any length that is not one sixteenth of the corresponding key in the octave range of 4 (“C4”, “F4”, “A4”, or “B4”).

![Long](/img/Long%20Triggers.jpg)

### Arrow Trigger
An Arrow Trigger is a trigger the player has to press the associated arrow button one time. For instance, if the Arrow Trigger points to the South then the player has to press the South arrow button. The Arrow Trigger can use all eight cardinal directions, as such, each direction requires one octave range. The table below summarizes how to create an Arrow Trigger for each cardinal direction.
|  			Direction 		 |  			MIDI Octave 		 |
|-------------|---------------|
|  			↑ 		         |  			C0–B0 		       |
|  			↗ 		         |  			C1-B1 		       |
|  			→ 		         |  			C2-B2 		       |
|  			↘ 		         |  			C3-B3 		       |
|  			↓ 		         |  			C5-B5 		       |
|  			↙  			 		       |  			C6-B6 		       |
|  			←  			 		       |  			C7-B7 		       |
|  			↖ 		         |  			C8-B8 		       |

Example:
Arrow Trigger with a Southwest direction in Lane A should be a sixteenth note of key “A6”.
Just as a Tap Trigger, an Arrow Trigger needs to be one sixteenth note.

![Arrow](/img/Arrow%20Trigger.jpg)

### Long Arrow Trigger
A Long Arrow Trigger is the combination of a Long Trigger and an Arrow Trigger. The player has to press and hold the trigger, but on release press the associated arrow. In other words, a Long Arrow Trigger is a Long Trigger with an Arrow Trigger at the end. Therefore, to create a Long Arrow Trigger is a combination of a Long Trigger and an Arrow Trigger. Add a note of any length that is not a sixteenth note in the octave range of the desired direction (Use the Arrow Trigger direction table for reference.)

![LongArrow](/img/Long%20Arrow%20Trigger.jpg)

Example:
Long Arrow Trigger with an East direction in Lane F should be a “F2” key of any length.

### Double Arrow Trigger
A Double Arrow Trigger is a trigger variation of Arrow Trigger which has the player press two arrows one time. One direction is created in the same manner as an Arrow Trigger (See Arrow Trigger table above) while the second direction requires changing the channel number of the note.
|  			Trigger Type 		                       |  			Direction 		 |  			Channel Number 		 |
|--------------------------------------|-------------|------------------|
|  			Second Arrow/ Long w/ Double 			Arrow 		 |  			↑ 		         |  			2 		              |
|  			   			 		                                |  			↗ 		         |  			3 		              |
|  			   			 		                                |  			→ 		         |  			4 		              |
|  			   			 		                                |  			↘ 		         |  			5 		              |
|  			   			 		                                |  			↓ 		         |  			6 		              |
|  			   			 		                                |  			↙  			 		       |  			7 		              |
|  			   			 		                                |  			←  			 		       |  			8 		              |
|  			   			 		                                |  			↖ 		         |  			9 		              |

By default all notes in the MIDI editor are in Channel 1, therefore Channel 2 is where the Double Arrow Trigger begins. Just as a Tap Trigger and Arrow Trigger, a Double Arrow Trigger needs to be one sixteenth note.

![DoubleArrowTrigger](/img/Double%20Arrow%20Trigger.jpg)

Example:
A Double Arrow Trigger with a North and South direction in Lane C should be the key “C0” in Channel 6, or the key “C5” in Channel 2.
Note: The order of the octave range and the channel number does not matter.

### Long Double Arrow Trigger
A Long Double Arrow Trigger is the combination of a Long Trigger and a Double Arrow Trigger. The player has to press and hold the trigger, but on release press the two associated arrows. Essentially, a Long Double Arrow Trigger is a Long Trigger with a Double Arrow Trigger at the end. To create a Long Double Arrow Trigger, add a note longer than a sixteenth note in the octave range and Channel number of the desired direction. (See Double Arrow Trigger table above.)

![LongDoubleArrow](/img/Long%20Double%20Arrow%20Trigger.jpg)

Example:
A Long Double Arrow Trigger with an East and West direction in Lane B should be the key “B2” and Channel 8.

### Export

Export the .mid and use the MIDI Converter in Rhythmiga 2 to create a .rhy file.