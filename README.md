# Basic Basic Revolution: The Graphical

**v1.0**

Made by **StephenM**,
for the **TI-84 Plus CE** Calculator.

Want features? Encountered a bug? Go to the link below!

**Cemetech forum topic:** <https://ceme.tech/t19568>

The **SourceCoder 3** project is available right here: <https://sc.cemetech.net/?hash=RsJvFZyeHJoRQ5wYsvTrUP5DeoP+>.

***THIS PROJECT WAS INSPIRED BY DANCE DANCE REVOLUTION OF
KONAMI GROUP CORPORATION. I AM IN NO WAY ASSOCIATED WITH
THE ORIGINAL CREATORS OR DEVELOPERS OF THE DDR SERIES.***

*Please know that this game requires at least **61-64 kb** of available RAM. A `GarbageCollect` is also recommended.*

---

## Installation

Using your favorite linking program *(TI-Connect, TiLP, etc...)* transfer the files `BBRG.8xp` and `ZBBRGMEN.8xp` to your calculator.

To play the game, run `prgmBBRG`.

## Information

Much improved over the original **Basic Basic Revolution**, this new sequel titled **Basic Basic Revolution: The Graphical** brings many new features! No more shall you see boring home-screen text, since this version has some quite impressive and colorful graphics if I say so myself.

### Description

Basically, arrows come from the bottom of the screen, and you have to jump on the corresponding arrow on the pad to the beat, or in this case, press the corresponding arrow key.

*(Note: a few things had to be compromised due to the fact that you can't play audio on the CE.)*

To start playing, there are two options. Either generate a completely randomized chart of maximum length and speed, or load in a pre-made chart from a list in RAM. You can access these options from the main menu by selecting **Play**.

For making those charts, see the section labeled under **Information -> Chart Editor**.

### Scoring system

If you get perfect timing on a note, you get +5 points on your score, and only +1 point if you get early or late timing. As for missing a note, that's a bit more complicated. In both Easy and Hard difficulties, there is a mistake counter. Whenever you make a mistake, that counter increments. If that counter is greater than the level rank *(displayed next the difficulty in the intro screen of a chart)*, you lose. **However**, in Easy difficulty, when you hit a note, the counter resets, while in Hard difficulty, it does not.

### Achievements

They were originally planned to be implemented in the first release *(this version)* but I believe I pushed the release date long enough *(seriously, 2 months?)* so it will be postponed to a future update.

Sorry about that!

### Chart Editor

As of the time of upload of this, there isn't a chart editor. Please go to the link at the top of the page for more updates. To manually create charts, see the section labeled under **Formats -> Charts**.

---

## Controls

### Menus

| Key           | Action                 |
| ------------- | ---------------------- |
| `2nd`/`enter` | Select item            |
| Up/Down       | Change cursor position |

### Gameplay

| Key            | Action    |
| -------------- | --------- |
| Arrow keys     | Play note |
| `mode`/`clear` | Pause     |

### High score menu

*not to be mistaken with the 'Menus' section.*

| Key                       | Action             |
| ------------------------- | ------------------ |
| `f1`/`f2` *or* Left/Right | Previous/next page |
| Up/Down                   | Go back            |

---

## Formats

This section contains information about how the game handles
data in lists. Currently this only includes the chart format for manual
creation of charts. Save list format isn't included to prevent
cheating by modifying the save file.

### Charts

Type: Complex list.

1. **Signature + version *i***
	`1470391873+1i`
	(you can recall finance variable `C/Y` to get
	the real part if you have just run `prgmBBRG`)

2. **Chart name** (length 10 chars, charset: standard ASCII)
	`XXXXXXXXXX+XXXXXXXXXXi`
	Each character is two digits, where a space
	character (' ') is 01, and `~` is 95, and `00`
	is for padding at the end.
	e.g "Scarlet!" is encoded as:
	`5268668377+7085020000i`

3. **Speed + config *i***
	The real part is used for the speed, which can be any number between 0 and 1, where 1 is the fastest. Anything >1 is discouraged, since it causes note skipping. Don't use anything less than or equal to 0, since you will not be able to progress in the chart at all.
    
    The imaginary part holds the track configuration. It is ten digits long, and each digit represents something. It can be represented as `1ABBCD0000`, where:
    - `A` is the difficulty and can be one of two digits:
        - `0` for hard mode. The mistake counter is *not* reset when you get a correct note.
        - `1` for easy mode. The mistake counter is reset when you get a correct note.
    - `BB` is the difficulty rank, and can be anything from `01` to `99`. The number represents how much the mistake counter should be before you lose.
        *(Note: rank `00` is invalid.)*
    - `C` is how many notes to go back when missing a note or continuing the game from a pause. Range: `0` to `9`.
    - `D` is the combo counter mode, And can hold one of two values:
        - `0`: Increment the combo counter no matter the note timing *(Early, Perfect, Late)*.
        - `1`: Increment the combo counter only on perfect note timing.
    
4. **Unused**
	May be used for color customization in later updates.

5. and onwards: **Note data**
	There are 5 IDs:

	- `0`: Empty
	- `1`: Left
	- `2`: Up
	- `3`: Down
	- `4`: Right
	
	Other values will crash the game.
    
	Also, please add padding zeroes at the beginning and end of the note data, since the game currently can't handle notes on the very edges.
		
- Last element: **Checksum**
	Just set it as `sum(LISTNAME)`.

---

## Changelog

- v1.0 | May 31, 2024
	Initial Release.
