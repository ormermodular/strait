# Strait: disting NT manual

Version 0.1.3.

Strait is a stereo filter whose two sides can drift apart. One filter sits on the left and one on the right, and both follow the same controls, so a mono sound comes out as a matched pair. Then **SPREAD** pulls the two cutoffs apart, left up and right down, and the sound opens out into the stereo field. Put a slow LFO on SPREAD and the filtering sways between the speakers. **DRIFT** lets each side wander on its own, so the image never quite stands still. Choose low pass, band pass or high pass with **TYPE**, and blend the filter with the dry sound using **MIX**. Strait is aimed at ambient work and is deliberately simple: three pots, two pages, and every parameter takes CV through the disting NT's own mapping.

## Installing
Strait needs disting NT firmware **1.19 or newer**.

1. Get `strait-plugin.zip` from the latest release on the Strait GitHub page, or add Strait from the disting NT Plugin Gallery.
2. Unzip it onto the MicroSD card, so that `strait.o` ends up in `programs/plug-ins/ormermodular/`.
3. Restart the module, or rescan plug-ins from the settings menu.
4. Add an algorithm, then choose **Strait** (tagged Effect and Filter/EQ).

Strait is free. It is closed source, and made by Ormer Modular in Guernsey.

## The screen
The whole display belongs to Strait. There is no parameter line along the top; the screen is a small scene that shows what the filter is doing.

The online manual shows pictures of these screens:

- Page 1, low pass. The open water between the two shores is the passband.
- Page 1, band pass, with Spread to the right. Only a narrow channel stays open at each cutoff.
- Page 1, high pass. The middle fills in as an island and the water lies outside it.
- Page 2: Drift, Slope and Type. The second page dot is lit.
- Page 3: Mix, the dry/wet balance. The third page dot is lit.

It is a night sea seen from the shore. The **open water is what the filter lets through** and the **land is what it stops**. The picture reads from the centre line outward as low to high frequency, so the shores sit further out as the cutoff rises.

- The **left shore** is the left filter and the **right shore** is the right filter. Each has a small lamp tower.
- **FREQ** moves both shores. **SPREAD** pulls them apart in opposite directions, so the whole channel swings to one side.
- **TYPE** redraws the land. Low pass keeps the water between the shores. High pass fills that stretch in as an island, with the water outside it. Band pass leaves only a narrow channel at each cutoff.
- **RES** lights the lamps and narrows the band-pass channels. At self-oscillation, rings spread across the water.
- **SLOPE** sets how steeply the cliffs fall: gentle at 12 dB per octave, steep at 24.
- **DRIFT** makes each shore wander on its own. In its upper half the whole picture also weaves, like a worn tape.

Along the bottom, a label names what each pot does right now, with a small bar for its value. The three small squares at the bottom left are the page dots: the lit one is the page you are on.

## The pots
The three pots always edit three parameters, and which three depends on the page. **Push the centre pot** to step to the next page.

| Page | Left pot | Centre pot | Right pot |
|---|---|---|---|
| 1 | FREQ | RES | SPREAD |
| 2 | DRIFT | SLOPE | TYPE |
| 3 | MIX | | |

After a page change each pot stays silent until you turn it to the value it now owns, so nothing jumps. Flip pages freely while playing.

On page 1, **pushing the right pot returns SPREAD to centre**. This is labelled PUSH: CENTRE along the top edge of the screen. On page 2 the right pot push does nothing.

Strait leaves the rest of the module alone. Buttons 1 to 4, the left pot push and the left encoder push work as they do everywhere on the disting NT. The encoders and the right pot push do nothing while Strait's screen is showing; press button 2 for the parameter list, where they work as usual.

## Parameters
Every parameter is a normal disting NT parameter, so all of it can be mapped to CV, MIDI or i2c and automated through the module's own Mappings, like a built-in algorithm.

| Parameter | Range | Notes |
|---|---|---|
| Freq | about 16 Hz to 16.7 kHz | The cutoff, shown in Hz, for both sides together. |
| Res | 0.0 to 100.0% | Resonance, for both sides. Self-oscillation starts above about 90%. |
| Spread | -100.0 to +100.0% | Moves the two cutoffs in opposite directions, by up to an octave each. At 0 they are the same. |
| Drift | 0.0 to 100.0% | A slow, separate wander of each side's cutoff. At 0 it is off. |
| Slope | 12 or 24 dB/oct | Roll-off steepness. |
| Type | Low pass, Band pass, High pass | The filter response. |
| Mix | 0.0 to 100.0% | Dry/wet. 100% is the filter alone (the default), 0% is the input alone. |
| Left input | Input 1 | Audio in, left. |
| Right input | Input 2 | Set to None for mono: the left input then feeds both sides. |
| V/Oct input | None | Optional 1 V per octave pitch input for the cutoff. |
| Left output | Output 1 | Mode defaults to Replace. |
| Right output | Output 2 | Mode defaults to Replace. |

The macros run at 0.1% resolution and every audible target glides inside the filter, so mapped steps and fast automation stay clean.

## A matched pair
With SPREAD at 0 and DRIFT at 0, the left and right filters are identical, and the left and right outputs are exactly the same, sample for sample, whenever the two inputs carry the same signal. Move either parameter and the two sides part company.

If **Right input** is set to None it copies the left input. A mono source patched only to the left input therefore comes out in stereo as soon as SPREAD or DRIFT moves.

## Mix
**Mix** blends the dry input with the filtered sound, and works as a plain linear balance: at 100% you hear only the filter, at 0% only the input, and in between the two are added in proportion. The dry sound is the input as patched, so with **Right input** set to None the right side's dry sound is the left input too. At 0% the output is exactly the input, sample for sample, and the filter keeps running underneath, so bringing Mix back up never starts from silence. Mix is smoothed, so a pot move or a CV on it never clicks.

A band-pass or high-pass mixed with the dry sound gives the familiar phase-coloured, comb-like tones, which is part of the fun.

## Type and slope
**Type** chooses which response comes out: low pass, band pass or high pass. Strait runs all three at once and picks one, so changing Type while a sound is playing never restarts the filter. The change crossfades over a few milliseconds, which keeps a stepped CV, an LFO or a pot sweep on Type free of clicks. At 24 dB per octave there is a short extra delay (about a fiftieth of a second) before a change is heard, while the filter gets ready.

**Slope** is 12 dB per octave by default, which is gentle and suits ambient work. At 24 dB per octave a second, fixed stage follows the filter for a steeper roll-off. All the resonance stays in the first stage, so the self-oscillating tone is just as clean. Changing Slope while a sound is playing never clicks: going to 24 dB the second stage is brought up for a moment first and then faded in, and going back to 12 dB it fades out.

## Resonance and self-oscillation
Resonance rises smoothly with Res and stays stable across the whole range, including when the cutoff is modulated at audio rate. In the top tenth of its travel (above about 90%) the filter begins to oscillate on its own and makes a clean sine tone on each side, at the cutoff. The tone follows the V/Oct input closely, so Strait can be played as a pair of sine oscillators, and Spread tunes the two tones apart. Low pass and high pass give the tone at about 5 V peak. Band pass is quieter.

The band-pass response keeps its level as resonance rises. Its peak at the cutoff grows as the band narrows, so turning Res up sharpens the sound without thinning it out.

The tone starts by itself, even with nothing patched. Turn Res down to stop it.

> **Note.** Resonant peaks can be louder than the signal going in. Anything above 10 V is gently limited, so a hot input at high resonance cannot run away.

## CV and modulation
Map any parameter to CV with the disting NT's Mappings. By default a mapping covers the parameter's whole range, so a full-range CV sweeps Res from 0 to 100%, or Spread from far left to far right.

The **V/Oct input** is separate from the mappings. It adds to the cutoff at 1 V per octave, sample by sample and without smoothing, so it can be driven at audio rate for frequency modulation. A tracked pitch CV there, with Res above 90%, makes Strait a pair of sine oscillators.

The parameters themselves are smoothed, so a slow LFO or a stepped CV on Freq, Spread, Res, Drift or Mix glides instead of clicking.

## Troubleshooting
**There is a tone and nothing is patched.** Res is in the self-oscillating part of its range. Turn it down.

**Left and right sound the same.** That is by design when Spread and Drift are both at 0. Turn Spread or Drift.

**The right output is silent.** The right side is fed from Right input, or from the left input if Right input is None. Check that something is patched to Input 1.

**The pots do nothing after a page change.** Each pot stays silent until you turn it to the value it now owns. Turn it past that value and it takes over.

**Strait does not appear in the algorithm list.** Check the firmware is 1.19 or newer and that `strait.o` is in `programs/plug-ins/ormermodular/` on the card.

## Specifications
| | |
|---|---|
| Format | disting NT algorithm, free, closed source |
| Version | 0.1.3 |
| Firmware | 1.19 or newer |
| Cutoff | about 16 Hz to 16.7 kHz, plus V/Oct and CV |
| Slope | 12 or 24 dB per octave |
| Type | low pass, band pass or high pass |
| Spread | up to one octave either way, two octaves between the sides |
| Inputs | stereo audio in (right copies left when None), V/Oct |
| Outputs | one stereo pair |
| CPU | about 6% at 12 dB per octave, 12 to 15% at 24 dB per octave |
| Levels | audio nominally 5 V peak; peaks above 10 V gently limited |
| Sample rates | any |
