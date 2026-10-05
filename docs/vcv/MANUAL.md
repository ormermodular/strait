# Strait: VCV Rack manual

Version 2.0.0, 8 HP.

Strait is a stereo filter whose two sides can drift apart. One filter sits on the left and one on the right, and both follow the same controls, so a mono sound comes out as a matched pair. Then **SPREAD** pulls the two cutoffs apart, left up and right down, and the sound opens out into the stereo field. Put a slow LFO on SPREAD and the filtering sways between the speakers. **DRIFT** lets each side wander on its own, so the image never quite stands still. Low pass, band pass and high pass are all available at once, on separate left and right outputs. There is no mode switch. Strait is aimed at ambient work and is deliberately simple: three dials, a few small knobs, and every control that matters takes CV.

## The panel
**Knobs**

- **FREQUENCY**: The cutoff, for both sides together. It runs from about 16 Hz to 16.7 kHz and the value is shown in Hz when you hover over it. The arc round the dial marks its travel.
- **RES**: Resonance, for both sides. Turned up, the filter rings and sharpens around the cutoff. In the top tenth of its travel (above about 90%) the filter starts to oscillate by itself and makes a clean sine tone at the cutoff on each side, which follows V/OCT. The short dashes round the dial mark its travel.
- **SPREAD**: Pulls the two cutoffs apart. At centre, left and right share one cutoff. Turn it right and the left cutoff rises while the right falls, by up to an octave each, so the two sides end up two octaves apart. Turn it left and they swap. Movement is smoothed, so a slow LFO glides rather than steps. The long dash at the top marks the centre.
- **DRIFT**: A slow, independent wander of each side's cutoff. At zero it is off, and left and right stay identical. Low settings give a gentle slow swell; higher settings add random wandering. Each side moves on its own, so the stereo image shimmers. The wander stays within about half an octave.
- **RES depth**: Sets how much the RES CV input below it moves resonance. Centre is off, turning right adds the CV, turning left inverts it.
- **FREQ depth**: Sets how much the FREQ CV input below it moves the cutoff. Centre is off. At full right, 1 V moves the cutoff up one octave; turning left inverts it.
- **SPREAD depth**: Sets how much the SPREAD CV input below it moves SPREAD. Centre is off. At full right, a signal of plus or minus 5 V sweeps SPREAD across its whole range; turning left inverts it.
- **DRIFT depth**: Sets how much the DRIFT CV input below it adds to DRIFT. Centre is off. At full right, 10 V gives the full DRIFT range; turning left inverts it.

**Inputs**

- **V/OCT**: A 1 V/octave pitch input for the cutoff, not attenuated. 0 V leaves the cutoff where FREQUENCY puts it, and each volt moves it up an octave. Use it to play the filter, or to play the self-oscillation as a pair of tracking sine oscillators.
- **RES CV**: CV for resonance, through the RES depth knob above it. 10 V is the full range at full depth. It adds to the RES knob.
- **FREQ CV**: CV for the cutoff, through the FREQ depth knob above it. At full depth, 1 V per octave. It adds to FREQUENCY and V/OCT, and it works at audio rate, so the cutoff can be frequency modulated.
- **SPRD CV**: CV for SPREAD, through the SPREAD depth knob above it. At full depth, plus or minus 5 V covers the whole range. It adds to the SPREAD knob. Good for a slow LFO that makes the filtering sway between the speakers.
- **DRIFT CV**: CV for DRIFT, through the DRIFT depth knob above it. 10 V is the full range at full depth. It adds to the DRIFT knob.
- **IN L**: Left audio input. A polyphonic cable is summed to one signal.
- **IN R**: Right audio input. If nothing is plugged in here it copies IN L, so a mono source still comes out in stereo once SPREAD or DRIFT is moved. A polyphonic cable is summed to one signal.

**Outputs**

- **LP L**: Low-pass output, left. Passes what is below the cutoff.
- **LP R**: Low-pass output, right. Passes what is below the cutoff.
- **BP L**: Band-pass output, left. Passes a band around the cutoff, at unity gain at the cutoff when RES is at zero. As RES rises the band narrows and its peak at the cutoff rises with it, so the overall level of the sound stays steady instead of falling away.
- **BP R**: Band-pass output, right. Passes a band around the cutoff, at unity gain at the cutoff when RES is at zero. As RES rises the band narrows and its peak at the cutoff rises with it, so the overall level of the sound stays steady instead of falling away.
- **HP L**: High-pass output, left. Passes what is above the cutoff.
- **HP R**: High-pass output, right. Passes what is above the cutoff.

## How it works
Each side has a state-variable filter, which gives the low-pass, band-pass and high-pass responses together from the same cutoff. The six outputs are the three responses for the left side and for the right side.

- **FREQUENCY** sets the cutoff for both sides. The **V/OCT** input and the **FREQ CV** input add to it.
- **RES** sets the resonance for both sides. **RES CV** adds to it.
- **SPREAD** moves the two cutoffs in opposite directions, by up to an octave each. At centre they are the same.
- **DRIFT** adds a slow, separate wander to each side's cutoff. At zero it is off.

The knobs are smoothed, so FREQUENCY and SPREAD glide rather than step and a slow LFO or a stepped CV never clicks. The FREQ CV and V/OCT inputs themselves are not smoothed, so either can be driven at audio rate for frequency modulation.

## A matched pair
With SPREAD at centre and DRIFT at zero, the left and right filters are identical, and the left and right outputs are exactly the same, sample for sample, whenever the two inputs carry the same signal. Move either control and the two sides part company.

If **IN R** has no cable it copies **IN L**. A mono source patched only to IN L therefore comes out in stereo as soon as SPREAD or DRIFT moves. A polyphonic cable into IN L or IN R is summed to a single signal. Strait is a stereo module, not a polyphonic one, and the CV and V/OCT inputs read the first channel of a polyphonic cable.

## Resonance and self-oscillation
Resonance rises smoothly with RES and stays stable across the whole range, including at audio-rate modulation. In the top tenth of its travel (above about 90%) the filter begins to oscillate on its own and makes a clean sine tone on each side, at the cutoff. The tone follows V/OCT closely, so Strait can be played as a pair of sine oscillators, and SPREAD tunes the two tones apart. The low-pass and high-pass outputs give the tone at about 5 V peak (10 V peak to peak). The band-pass output is quieter.

The band-pass output keeps its level as resonance rises. Its peak at the cutoff grows as the band narrows, so turning RES up sharpens the sound without thinning it out.

The tone starts by itself, even with nothing patched. Turn RES down to stop it.

> **Note.** Resonant peaks can be louder than the signal going in. Anything above 10 V is gently limited, so a hot input at high resonance cannot run away.

## Slope
The filters are 12 dB per octave by default, which is gentle and suits ambient work. Choose 24 dB per octave from the right-click menu for a steeper roll-off. In 24 dB mode a second, fixed stage follows each output. All the resonance stays in the first stage, so the self-oscillating tone is just as clean.

## CV and patching
Four small knobs sit above four CV jacks. Each knob sets how much of its CV is applied, and works in both directions: centre is off, right adds the CV, and left inverts it. **A CV does nothing until its depth knob is turned off centre.**

| Input | Full depth | Adds to |
|---|---|---|
| RES CV | 10 V = the whole RES range | RES |
| FREQ CV | 1 V per octave | FREQUENCY and V/OCT |
| SPRD CV | plus or minus 5 V = the whole SPREAD range | SPREAD |
| DRIFT CV | 10 V = the whole DRIFT range | DRIFT |

**V/OCT** has no depth knob. It is a 1 V per octave input, not attenuated, and 0 V leaves the cutoff where FREQUENCY puts it.

## Right-click menu
- **Slope**: 12 dB per octave (default) or 24 dB per octave.
- **Panel**: follow Rack's dark-panels setting (default), or force the silver or the black panel. The choice is saved with the patch.

## Installing
Strait is free. Open the VCV Library, find Strait by Ormer Modular, and subscribe. It appears in Rack's module browser the next time Rack starts. It needs VCV Rack 2, the Free or the Pro edition, on Windows, macOS (Intel or Apple silicon) or Linux.

## Troubleshooting
**A CV input has no effect.** Check its depth knob. It starts at centre, which is off.

**There is a tone and nothing is patched.** RES is in the self-oscillating part of its range. Turn it down.

**Left and right sound the same.** That is by design when SPREAD is at centre and DRIFT is zero. Turn SPREAD or DRIFT.

**The right output is silent.** The right side is fed from IN R, or from IN L if IN R is empty. Check that something is patched to IN L.

**The panel colour is not what I expected.** Strait follows Rack's dark-panels setting. Force either panel from the right-click menu.

## Specifications
| | |
|---|---|
| Width | 8 HP |
| Version | 2.0.0 |
| Format | VCV Rack 2 plugin, free, closed source |
| Cutoff | about 16 Hz to 16.7 kHz, plus V/OCT and CV |
| Slope | 12 or 24 dB per octave |
| Outputs | low pass, band pass and high pass, each left and right |
| SPREAD | up to one octave either way, two octaves between the sides |
| Inputs | IN L, IN R (copies IN L), V/OCT, and four CV inputs |
| Polyphony | not polyphonic; polyphonic audio cables are summed |
| Levels | audio nominally 5 V peak; peaks above 10 V gently limited |
| Sample rates | any |
