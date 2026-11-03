# Strait: disting NT manual

Version 1.0.0.

Strait is a stereo filter for the Expert Sleepers disting NT whose two sides can drift apart. One filter sits on the left and one on the right, and both follow the same controls, so a mono sound comes out as a matched pair. Then **SPREAD** pulls the two cutoffs apart, left up and right down, and the sound opens out into the stereo field. Put a slow LFO on SPREAD and the filtering sways between the speakers. **DRIFT** lets each side wander on its own, so the image never quite stands still. Choose low pass, band pass or high pass with **TYPE**, and blend the filter with the dry sound using **MIX**. Strait is aimed at ambient work and is deliberately simple: three pots over three pages, and every parameter takes CV through the disting NT's own mapping.

## The screen
The online manual shows the live screen, with sliders for the pots, so you can see how the scene answers each control.

The whole display belongs to Strait. There is no parameter line along the top; the screen is a small scene that shows what the filter is doing. It is a night sea seen from the shore. The **open water is what the filter lets through** and the **land is what it stops**. The picture reads from the centre line outward as low to high frequency, so the shores sit further out as the cutoff rises.

- The **left shore** is the left filter and the **right shore** is the right filter. Each has a small lamp tower.
- **FREQ** moves both shores. **SPREAD** pulls them apart in opposite directions, so the whole channel swings to one side.
- **TYPE** redraws the land. Low pass keeps the water between the shores. High pass fills that stretch in as an island, with the water outside it. Band pass leaves only a narrow channel at each cutoff.
- **RES** lights the lamps and narrows the band-pass channels. At self-oscillation, rings spread across the water.
- **SLOPE** sets how steeply the cliffs fall: gentle at 12 dB per octave, steep at 24.
- **DRIFT** makes each shore wander on its own. In its upper half the whole picture also weaves, like a worn tape.

Along the bottom, a label names what each pot does right now, with a small bar for its value. The three small squares at the bottom left are the page dots: the lit one is the page you are on.

## The three knobs
Page 1 holds the three controls you play most. They are the three pots as soon as you add Strait.

### FREQ

The cutoff, for both sides together, shown in Hz from about 16 Hz to 16.7 kHz. The V/Oct input and any CV mapped to Freq add to it.

### RES

Resonance, for both sides. It rises smoothly and stays stable across the whole range, including when the cutoff is modulated at audio rate. The band-pass response keeps its level as resonance rises: its peak at the cutoff grows as the band narrows, so turning Res up sharpens the sound without thinning it out.

In the top tenth of its travel (above about 90%) the filter begins to oscillate on its own and makes a clean sine tone on each side, at the cutoff. The tone starts by itself, even with nothing patched; turn Res down to stop it. It follows the V/Oct input closely, so Strait can be played as a pair of sine oscillators, and Spread tunes the two tones apart. Low pass and high pass give the tone at about 5 V peak. Band pass is quieter.

> **Note.** Resonant peaks can be louder than the signal going in. Anything above 10 V is gently limited, so a hot input at high resonance cannot run away.

### SPREAD

Moves the two cutoffs in opposite directions, by up to an octave each, so the two sides can be two octaves apart. At 0 they are the same. With SPREAD at 0 and DRIFT at 0, the left and right filters are identical, and the left and right outputs are exactly the same, sample for sample, whenever the two inputs carry the same signal. Move either parameter and the two sides part company.

If **Right input** is set to None it copies the left input. A mono source patched only to the left input therefore comes out in stereo as soon as SPREAD or DRIFT moves.

## Other controls
Everything else sits on pages 2 and 3, or on the module itself.

| Control | What it does |
|---|---|
| Left, centre and right pot, turn | Edit the three parameters of the current page. After a page change each pot stays silent until you turn it to the value it now owns, so nothing jumps. |
| Centre pot, push | Step to the next page: 1, 2, 3, then back to 1. |
| Right pot, push | On page 1, return SPREAD to centre (labelled PUSH: CENTRE along the top edge of the screen). On pages 2 and 3 it does nothing. |
| Both encoders, right encoder push | Do nothing while Strait's screen is showing, so they never change a parameter you cannot see. |
| Button 2 | Switch to the NT's parameter list, where every value can be edited, including routing. |
| Buttons 1, 3 and 4, left pot push, left encoder push | The NT's own. The left pot push and left encoder push take you back to the overview. |

### DRIFT

A slow, separate wander of each side's cutoff. At 0 it is off. It is smoothed, so a slow LFO or a stepped CV on it glides instead of clicking.

### SLOPE

12 dB per octave by default, which is gentle and suits ambient work. At 24 dB per octave a second, fixed stage follows the filter for a steeper roll-off. All the resonance stays in the first stage, so the self-oscillating tone is just as clean. Changing Slope while a sound is playing never clicks: going to 24 dB the second stage is brought up for a moment first and then faded in, and going back to 12 dB it fades out.

### TYPE

Chooses which response comes out: low pass, band pass or high pass. Strait runs all three at once and picks one, so changing Type while a sound is playing never restarts the filter. The change crossfades over a few milliseconds, which keeps a stepped CV, an LFO or a pot sweep on Type free of clicks. At 24 dB per octave there is a short extra delay (about a fiftieth of a second) before a change is heard, while the filter gets ready.

### MIX

Blends the dry input with the filtered sound, as a plain linear balance: at 100% you hear only the filter, at 0% only the input, and in between the two are added in proportion. The dry sound is the input as patched, so with **Right input** set to None the right side's dry sound is the left input too. At 0% the output is exactly the input, sample for sample, and the filter keeps running underneath, so bringing Mix back up never starts from silence. Mix is smoothed, so a pot move or a CV on it never clicks. A band-pass or high-pass mixed with the dry sound gives the familiar phase-coloured, comb-like tones, which is part of the fun.

## On the disting NT
### Installing

Strait needs disting NT firmware **1.19 or newer**.

1. Get `strait-plugin.zip` from the latest release on the Strait GitHub page, or add Strait from the disting NT Plugin Gallery.
2. Unzip it onto the MicroSD card, so that `strait.o` ends up in `programs/plug-ins/ormermodular/`.
3. Restart the module, or rescan plug-ins from the settings menu.
4. Add an algorithm, then choose **Strait** (tagged Effect and Filter/EQ).
5. Every input and output starts on None, so Strait takes no bus until you route it: on the **Routing** page set Left input, and Left output (and Right output for stereo).

### Pages

The three pots always edit three parameters, and which three depends on the page. Push the centre pot to step to the next page.

| Page | Left pot | Centre pot | Right pot |
|---|---|---|---|
| 1, The sound | FREQ | RES | SPREAD |
| 2, Character | DRIFT | SLOPE | TYPE |
| 3, Balance | MIX |  |  |

### Parameters

Every parameter is a normal disting NT parameter, so all of it can be mapped to CV, MIDI or i2c and automated through the module's own Mappings, like a built-in algorithm. The first seven are on the Strait page; the rest are on the Routing page, in the order the disting NT's routing pages use.

| Parameter | Default | Notes |
|---|---|---|
| Freq | 1.05 kHz | The cutoff, from about 16 Hz to 16.7 kHz, shown in Hz, for both sides together. |
| Res | 0.0% | Resonance, 0.0 to 100.0%. Self-oscillation starts above about 90%. |
| Spread | 0.0% | -100.0 to +100.0%. Moves the two cutoffs in opposite directions, by up to an octave each. |
| Drift | 0.0% | 0.0 to 100.0%. A slow, separate wander of each side's cutoff. |
| Slope | 12 dB/oct | 12 or 24 dB/oct. Roll-off steepness. |
| Type | Low pass | Low pass, Band pass or High pass. |
| Mix | 100.0% | Dry/wet, 0.0 to 100.0%. 100% is the filter alone, 0% is the input alone. |
| Left input | None | Audio in, left. With None Strait is fed silence (it can still sing at high Res). |
| Right input | None | Set to None for mono: the left input then feeds both sides. |
| Left output | None | Set to None and the left side writes nothing. |
| Right output | None | Set to None and both sides are summed into the left output. |
| Output mode | Replace | Replace overwrites the output buses, Add sums onto them. One setting for both outputs. |
| V/Oct input | None | Optional 1 V per octave pitch input for the cutoff. |

The macros run at 0.1% resolution and every audible target glides inside the filter, so mapped steps and fast automation stay clean.

### Mappings and CV

Map any parameter to CV with the disting NT's Mappings. By default a mapping covers the parameter's whole range, so a full-range CV sweeps Res from 0 to 100%, or Spread from far left to far right. The parameters are smoothed, so a slow LFO or a stepped CV on Freq, Spread, Res, Drift or Mix glides instead of clicking.

The **V/Oct input** is separate from the mappings. It adds to the cutoff at 1 V per octave, sample by sample and without smoothing, so it can be driven at audio rate for frequency modulation. A tracked pitch CV there, with Res above 90%, makes Strait a pair of sine oscillators.

## Field notes
### A mono pad, opened out

Left input to the pad, Right input None, Left and Right output to a stereo pair. Low pass, Res around 30%, Spread at +40%. Map a slow LFO to Spread and the filtering sways between the speakers while the pad itself stays put.

### A pair of sine oscillators

Res above 90%, low pass, a pitch CV into the V/Oct input. The tone starts by itself, so Left input can stay None. A little Spread detunes the two sides against each other, and a lot of it makes two separate notes.

### A slow, unsteady stereo image

Spread at 0 and Drift around 40%. The two sides start identical and then wander apart on their own, slowly, so the centre stays where it is and the edges breathe.

### Comb-tinged texture

Band pass or high pass with Mix at about 50%. The dry sound and the filtered sound add with different phase, which gives a hollow, comb-like colour. Sweep Freq with an LFO.

### A filter that follows a player

Map an envelope or the output of an envelope follower to Freq, and the cutoff rises and falls with the playing. Add Spread from a second source to move the two sides independently.

## Troubleshooting
**Nothing comes out.** Every input and output starts on None. On the Routing page choose a bus for Left input and for Left output.

**There is a tone and nothing is patched.** Res is in the self-oscillating part of its range. Turn it down.

**Left and right sound the same.** That is by design when Spread and Drift are both at 0. Turn Spread or Drift.

**The right output is silent.** The right side is fed from Right input, or from the left input if Right input is None. Check that Left input is routed to the bus carrying your signal, and that Right output is not set to None (which sums both sides into the left output).

**The pots do nothing after a page change.** Each pot stays silent until you turn it to the value it now owns. Turn it past that value and it takes over.

**A saved preset will not load.** Presets saved with an earlier pre-release version of Strait cannot be loaded. Add a fresh Strait and set it up again.

**Strait does not appear in the algorithm list.** Check the firmware is 1.19 or newer and that `strait.o` is in `programs/plug-ins/ormermodular/` on the card.

## Specifications
| | |
|---|---|
| Format | disting NT algorithm, free, closed source |
| Version | 1.0.0 |
| Firmware | 1.19 or newer |
| Cutoff | about 16 Hz to 16.7 kHz, plus V/Oct and CV |
| Slope | 12 or 24 dB per octave |
| Type | low pass, band pass or high pass |
| Spread | up to one octave either way, two octaves between the sides |
| Inputs | stereo audio in (right copies left when None), V/Oct |
| Outputs | one stereo pair |
| CPU | about 8% at 12 dB per octave, about 10% at 24 dB per octave |
| Levels | audio nominally 5 V peak; peaks above 10 V gently limited |
| Sample rates | any |
