# NanoVNA for Beginners: Measuring and Understanding Antennas

A NanoVNA is one of the most useful tools you can add to a radio or electronics workbench. It helps you inspect and tune antennas, find resonant frequencies, view SWR across an entire frequency range, examine impedance, measure filters, and track down problems in coaxial cables and RF components.

The NanoVNA is small, affordable, and surprisingly capable. Even so, it is not a device that you simply connect and trust without preparation. Useful results depend on selecting the correct frequency range, calibrating at the correct point, using the correct port, and understanding what the displayed traces actually mean.

This guide therefore does not try to explain every menu item. It answers the more useful question:

> **I can see this curve. What does it mean for my antenna, and what should I do next?**

---

## What Is a NanoVNA?

![Figure 1: NanoVNA overview with ports and controls](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/f5ada94be0.png)

*Figure 1: NanoVNA overview with ports and controls*

VNA stands for Vector Network Analyzer. The name sounds more complicated than the basic idea.

In simple terms, the NanoVNA generates a very small radio-frequency signal and measures what happens to it. It records both magnitude and phase. From this information it calculates values such as SWR, impedance, return loss, S11, S21, and points on a Smith Chart.

You can use a NanoVNA to:

- check the resonant frequency of an antenna,
- tune a dipole or vertical antenna,
- assess the match to a 50-ohm system,
- find several resonances on a multiband antenna,
- inspect filters and attenuators,
- compare a system before and after an adjustment,
- investigate cables, connectors, and RF components.

Keep realistic expectations. A NanoVNA is not a calibrated high-end laboratory analyzer. For amateur radio, CB, Meshtastic, SDR projects, antenna building, and many electronics experiments, however, it is an excellent practical instrument.

Its results are only as reliable as the measurement setup. Loose connectors, unnecessary adapters, unsuitable cables, or an incorrect calibration can contribute more error than the device under test. Especially at VHF and UHF, keep the connection chain short, clean, mechanically stable, and unchanged.

---

## What Does the NanoVNA Measure?

![Figure 2: Signal path from the NanoVNA through the coax to the antenna and back](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/cd57317574.png)

*Figure 2: Signal path from the NanoVNA through the coax to the antenna and back*

When checking an antenna, the NanoVNA sends a signal through the coaxial cable to the antenna.

A matched antenna accepts most of the power presented at its feed point. A mismatch causes part of the signal to be reflected back toward the NanoVNA. The analyzer measures this reflection.

From the same basic measurement it can calculate several views:

- SWR,
- S11 LOGMAG,
- return loss,
- resistance R,
- reactance X,
- complex impedance R + jX,
- Smith Chart,
- phase.

These displays do not contradict one another. They show the same electrical behavior from different perspectives.

---

## Understanding S11 and S21

![Figure 3: S11 reflection measurement compared with S21 transmission measurement](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/c7cef7afb1.png)

*Figure 3: S11 reflection measurement compared with S21 transmission measurement*

Many NanoVNA models label the first connector Port 1 or CH0. The second may be labeled Port 2 or CH1. S11 and S21 are measurement terms, not merely connector names.

### S11: What Comes Back?

For an antenna measurement, you normally use Port 1.

S11 describes reflection at the input. It can be used to determine:

- how strongly an antenna reflects,
- the SWR,
- resonant frequencies,
- impedance,
- whether the load appears capacitive or inductive.

A useful rule is:

> **Connect the antenna to Port 1 and display S11.**

### S21: What Passes Through?

For a transmission measurement, connect the device under test between Port 1 and Port 2.

S21 describes how much signal travels from the first port to the second. It is useful for:

- low-pass, high-pass, and band-pass filters,
- attenuators,
- coaxial cables,
- traps and notches,
- suitable balun and common-mode choke test fixtures.

For beginners:

> **Antennas are usually measured with S11. Filters and transmission paths are usually measured with S21.**

---

## Choosing a Useful Frequency Range

Set the frequency range before calibration. It should cover the frequencies you actually want to investigate.

For a 40-meter antenna, select a range around the 40-meter band. For an 868 MHz antenna, choose a suitable range around the intended operating frequency.

A very wide sweep may look convenient, but it has drawbacks:

- narrow resonances may be missed,
- details are less clear,
- the available measurement points are spread over a larger range.

A reliable workflow uses two passes:

1. Run a broader sweep to obtain an overview.
2. Narrow the range around the area of interest and recalibrate.

Calibration applies to the selected sweep. If you change the start and stop frequencies substantially, calibrate again.

---

## Calibration: The Most Important Step

![Figure 4: Clear OSL and SOLT calibration sequence](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/8689768173.png)

*Figure 4: Clear OSL and SOLT calibration sequence*

Calibration teaches the NanoVNA how the analyzer, connectors, and measurement chain behave up to the chosen reference plane.

Without a suitable calibration, the analyzer cannot properly separate the behavior of the device under test from systematic errors in the measurement setup.

### For Antennas: Open, Short, and Load

For a basic one-port S11 antenna measurement, you normally need:

1. **Open:** an open circuit,
2. **Short:** a short circuit,
3. **Load:** an accurate 50-ohm termination.

This is an OSL calibration.

A simple sequence is:

1. Set the required frequency range.
2. Reset the old calibration.
3. Attach Open at the future reference plane and measure it.
4. Attach Short and measure it.
5. Attach the 50-ohm Load and measure it.
6. Complete and save the calibration.
7. Confirm that correction is active.

### For Transmission Measurements: Add Thru

For S21, you also need a defined connection between the two ports. This step is called **Thru**.

Open, Short, Load, and Thru are commonly grouped under the term SOLT calibration. Thru is generally not required for a simple S11 antenna measurement, although firmware workflows differ between NanoVNA models.

### Do Not Change the Setup After Calibration

> **Anything changed between calibration and measurement can invalidate the calibration.**

If you add an adapter, substitute a cable, or insert another connector, recalibrate.

Connectors should be secure and repeatable, but not overtightened. If values change when a connector is touched, investigate the mechanical connection before blaming the software or antenna.

---

## Understanding the Reference Plane

![Figure 5: Calibration at the analyzer compared with calibration at the end of the test cable](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/31166bb5d8.png)

*Figure 5: Calibration at the analyzer compared with calibration at the end of the test cable*

The reference plane is the point from which the corrected measurement is considered to begin.

If you calibrate directly at the NanoVNA port and then add a test cable and several adapters, those items become part of the measured system. They may transform the displayed impedance and introduce loss or additional mismatch.

If the entire test cable is fitted first and Open, Short, and Load are applied at its far end, the reference plane moves to that end.

For precise antenna tuning, place the reference plane as close to the antenna feed point as practical.

That is not always convenient. You can either:

- bring the NanoVNA close to the feed point, or
- use a fixed, known measurement chain and keep all conditions consistent.

When measuring through a long feed line, you do not see only the antenna. The line transforms impedance, adds attenuation, and may make the result look smoother or better than the match directly at the feed point.

---

## Making the First Antenna Measurement

![Figure 6: NanoVNA screen with sweep, trace, marker, and resonance point](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/1e60b1a9cb.png)

*Figure 6: NanoVNA screen with sweep, trace, marker, and resonance point*

After calibration, remove the calibration standard and connect the antenna without changing the remainder of the measurement chain.

For an initial overview, enable one or more of these displays:

- SWR,
- S11 LOGMAG,
- Smith Chart.

Enable a marker and move it along the trace. The marker reports the frequency and the value at the selected point.

Do not simply choose the lowest point on the entire screen. Ask:

- Is the minimum inside the intended operating range?
- What is the SWR at the operating frequency?
- How low is S11 LOGMAG?
- What impedance is displayed?
- Is reactance X close to zero?

The combination of these values is more useful than any single number.

---

## Understanding SWR

![Figure 7: SWR curves with a practical quality scale](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/fb7f355b71.png)

*Figure 7: SWR curves with a practical quality scale*

SWR means Standing Wave Ratio. It indicates mismatch between the connected load and the analyzer's reference impedance, normally 50 ohms.

An SWR of 1:1 is the theoretical ideal. In practice, chasing an extremely low value is not always necessary.

As a rough guide:

- **1.0 to 1.2:** excellent,
- **1.2 to 1.5:** very good,
- **1.5 to 2.0:** good for many applications,
- **2.0 to 3.0:** possibly usable, depending on the radio and application,
- **above 3.0:** investigate carefully.

These values are not universal approval limits. The acceptable value depends on the transmitter, the required bandwidth, and the application.

Most importantly:

> **A good SWR proves a good match. It does not automatically prove that the antenna radiates efficiently.**

A 50-ohm dummy load can show an excellent SWR, but it is not a useful antenna. Feed-line loss can also make the SWR observed at the analyzer look artificially better.

SWR is a convenient starting point, not a complete diagnosis.

---

## LOGMAG: Reflection in Decibels

![Figure 8: The same antenna measurement shown as SWR and S11 LOGMAG](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/227c266879.png)

*Figure 8: The same antenna measurement shown as SWR and S11 LOGMAG*

LOGMAG means logarithmic magnitude. In an S11 measurement, it displays the magnitude of the reflection coefficient in decibels.

Typical S11 LOGMAG values are negative:

- **0 dB:** complete reflection,
- **-6 dB:** substantial reflection,
- **-10 dB:** often a useful starting point,
- **-15 dB:** good match,
- **-20 dB:** very good match,
- **-30 dB:** excellent match, provided the setup can measure it reliably.

The more negative the S11 LOGMAG value, the smaller the measured reflection.

### LOGMAG and Return Loss

Keep the sign convention clear:

- **S11 LOGMAG** is commonly displayed as a negative value, such as **-20 dB**.
- **Return loss** is commonly stated as a positive magnitude, in this example **20 dB**.

They describe the same reflection with opposite signs.

LOGMAG does not replace SWR. It presents the same reflection information on a logarithmic scale. Differences between good matches are often easier to compare in decibels.

Approximate examples:

- 10 dB return loss corresponds to an SWR of 1.92,
- 15 dB return loss corresponds to an SWR of 1.43,
- 20 dB return loss corresponds to an SWR of 1.22.

LOGMAG is especially helpful when locating resonances, secondary dips, and small before-and-after changes.

---

## Resistance and Reactance

![Figure 10: Resistance and reactance in capacitive, resonant, and inductive regions](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/90f3b22d16.png)

*Figure 10: Resistance and reactance in capacitive, resonant, and inductive regions*

Antenna impedance has two parts:

> **Z = R + jX**

where:

- **R** is resistance,
- **X** is reactance.

In a 50-ohm system, an impedance close to **50 + j0 ohms** is very well matched.

### Resistance R

A resistance of 50 ohms at the target frequency is ideal for a 50-ohm system. A different value does not automatically make the antenna unusable. A suitable matching network or transformer may improve the match.

### Reactance X

Reactance indicates whether the impedance at the selected frequency is capacitive or inductive:

- **X < 0:** capacitive,
- **X = 0:** purely resistive, or resonant,
- **X > 0:** inductive.

The shortcut “negative X means the antenna is too short” or “positive X means it is too long” is not a universal rule. It may be a rough guide for certain simple antennas close to their intended resonance. Multiband antennas, loaded antennas, matching networks, and feed-line transformations can behave differently.

A safer process is:

1. Find the resonant frequency.
2. Compare it with the desired operating frequency.
3. Only then decide whether a simple radiator should be lengthened or shortened.

---

## Smith Chart Without Fear

![Figure 11: Simplified Smith Chart for beginners](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/5083222b9c.png)

*Figure 11: Simplified Smith Chart for beginners*

The Smith Chart combines resistance and reactance in a single view.

For a beginner, four rules are enough:

- **Center:** 50 ohms with zero reactance, or 50 + j0 ohms,
- **above the horizontal center line:** inductive,
- **below the horizontal center line:** capacitive,
- **closer to the center:** a better match to 50 ohms.

Along the horizontal center line, X is zero. To the left of center the resistance is below 50 ohms; to the right it is above 50 ohms.

The Smith Chart shows something SWR alone cannot: two points can have the same SWR but very different impedances. The chart shows the direction of the mismatch.

You do not need to calculate circles for initial measurements. Watch where the marker appears and how it moves when the antenna is changed.

---

## Finding Resonance and Evaluating Bandwidth

![Figure 9: Resonance below target, on target, and above target](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b4a385e38d.png)

*Figure 9: Resonance below target, on target, and above target*

Resonance occurs where reactance X crosses zero. For a simple, low-loss antenna, an SWR minimum or a clear minimum in the S11 LOGMAG trace is often nearby.

These points do not always coincide exactly. An antenna can be resonant at X = 0 while its resistance is far above or below 50 ohms. It is then resonant but not optimally matched.

At the marker, check together:

- frequency,
- SWR,
- S11 LOGMAG,
- R,
- X,
- position on the Smith Chart.

### Bandwidth Requires a Defined Criterion

Bandwidth is the frequency span over which a chosen requirement is satisfied. For example:

- SWR below 2:1,
- return loss above 10 dB,
- S11 LOGMAG below -10 dB.

Place two markers at the two threshold crossings. The difference between their frequencies is the bandwidth for that criterion.

A narrow curve is not automatically bad, and a wide curve is not automatically good. Required bandwidth depends on the application. Loss can also broaden the curve without making the antenna more efficient.

---

## Tuning a Dipole

![Figure 12: Dipole before and after careful adjustment](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/2e604b30c7.png)

*Figure 12: Dipole before and after careful adjustment*

For a simple center-fed dipole:

- resonance **below** the desired frequency usually means the dipole is too long,
- resonance **above** the desired frequency usually means the dipole is too short.

Suppose the target is 7.1 MHz but resonance appears at 6.8 MHz. The dipole is too long.

Shorten both legs equally and only in small steps, then measure again.

> **Cutting is permanent. Folding the wire back is safer during initial tuning.**

A practical sequence is:

1. Install the antenna at its intended height and in its intended surroundings.
2. Measure resonance.
3. Adjust both sides evenly and carefully.
4. Return the antenna to the original position.
5. Measure again.
6. Compare the before-and-after traces.

Do not touch the antenna during measurement. Hands, ladders, metal objects, and nearby buildings can all change the result.

---

## End-Fed and Multiband Antennas

An end-fed antenna often has several usable resonances. Start with a broad sweep to find them, then inspect each desired band with a narrower range.

An adjustment in one place may affect several bands. After every change, recheck all frequency ranges you intend to use.

The measurement can also be influenced by:

- the transformer,
- radiator length,
- installation shape,
- height,
- counterpoise,
- feed line,
- common-mode current.

A single low SWR point is not enough for a complete assessment.

---

## Vertical Antennas

Radials or another form of counterpoise are part of the vertical antenna system.

Changes in radial:

- number,
- length,
- angle,
- height,
- ground clearance,
- surroundings

can alter both resonance and impedance.

Measure the antenna as close as possible to its final installation. A vertical on a workbench can behave very differently after installation outdoors.

---

## Testing Coax, Connectors, and Filters

For the transmission loss of a cable or filter, use S21 with the device under test connected between Port 1 and Port 2.

Use a suitable two-port calibration with a defined Thru.

### Filters

S21 LOGMAG can show:

- the passband,
- the stopband,
- insertion loss,
- transitions and cutoff frequencies,
- unwanted secondary responses.

### Coaxial Cable

A suitable S21 measurement can show cable attenuation across frequency. A simple S21 sweep does not automatically tell you where damage is located. Fault location needs additional methods such as a time-domain display and a known velocity factor.

### Connectors and Adapters

If touching a connector changes the trace, suspect a mechanical issue:

- loose contact,
- damaged socket,
- contamination,
- unsuitable adapter,
- mechanical stress on the NanoVNA port.

Keep the adapter chain as short and consistent as possible.

---

## Interpreting Results Correctly

A single attractive curve is not a complete diagnosis.

### Good Resonance but Poor SWR

An antenna can be resonant because X is near zero, but its resistance may differ greatly from 50 ohms.

It is resonant, but not well matched to the 50-ohm system.

### Good SWR but Poor Antenna Performance

A low SWR can also result from losses. A lossy cable or inefficient arrangement can attenuate reflected energy and improve the reading at the analyzer.

The analyzer then sees a good match, but that does not guarantee efficient radiation.

### Several Minima

Several minima may represent useful multiband resonances. They may also be caused by the installation, feed line, surroundings, or unintended resonances.

Do not judge only the depth of a minimum. Also examine:

- its frequency,
- marker impedance,
- Smith Chart position,
- measurement repeatability.

---

## Common Mistakes

![Figure 13: Common NanoVNA measurement errors with causes and solutions](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/4c7a6129cc.png)

*Figure 13: Common NanoVNA measurement errors with causes and solutions*

### No Calibration or Incorrect Calibration

**Symptom:** unusual values, an unstable trace, or implausible impedance.

**Solution:** set the frequency range, reset calibration, and recalibrate at the correct reference plane.

### Frequency Range Too Wide

**Symptom:** a coarse trace and overlooked minima.

**Solution:** perform a broad scan first, then narrow the range and recalibrate.

### Measurement Chain Changed After Calibration

**Symptom:** different results after changing an adapter or cable.

**Solution:** assemble the complete measurement chain first, then calibrate again.

### Antenna Measured in an Unsuitable Environment

**Symptom:** major changes when the antenna moves or a person approaches it.

**Solution:** measure in the intended operating position and away from disturbing objects.

### Looking Only at SWR

**Symptom:** good SWR but unclear or unexpected impedance.

**Solution:** also examine S11 LOGMAG, R, X, and the Smith Chart.

### Moving the Connector or Antenna During Measurement

**Symptom:** jumping or strongly varying traces.

**Solution:** secure the setup, remove strain from the connectors, and avoid touching anything during the sweep.

---

## Practical Recipe: Check an Antenna Step by Step

1. Set the desired frequency range.
2. Assemble the complete measurement chain.
3. Calibrate at the intended reference plane.
4. Connect the antenna to Port 1.
5. Display S11 LOGMAG or SWR.
6. Place a marker on the relevant minimum.
7. Read frequency, SWR, and S11 in dB.
8. Check R and X at the same marker.
9. Examine the position on the Smith Chart.
10. Change the antenna only in small steps.
11. Measure again after every adjustment.
12. Compare traces under identical conditions.

---

## Quick Reference

![Figure 15: Printable NanoVNA quick-reference card](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/70eea94b4c.png)

*Figure 15: Printable NanoVNA quick-reference card*

### Calibration for an Antenna Measurement

**Set frequency range → Reset → Open → Short → Load → Done → Save**

### Additional Step for S21

**Perform Thru and use the appropriate two-port calibration.**

### S11 LOGMAG and Return Loss

| S11 LOGMAG | Return Loss | Assessment |
|---:|---:|---|
| -6 dB | 6 dB | weak match |
| -10 dB | 10 dB | usually usable |
| -15 dB | 15 dB | good |
| -20 dB | 20 dB | very good |
| -30 dB | 30 dB | excellent if measured reliably |

### Approximate SWR Comparison

| SWR | Return Loss |
|---:|---:|
| 3.0 | 6.0 dB |
| 2.0 | 9.5 dB |
| 1.5 | 14.0 dB |
| 1.2 | 20.8 dB |
| 1.1 | 26.4 dB |

### Which Display Should You Use?

| Task | Useful Display |
|---|---|
| Quick overview | SWR |
| Compare reflection in dB | S11 LOGMAG |
| Confirm resonance | X and S11 |
| Evaluate impedance | R + jX |
| See mismatch direction | Smith Chart |
| Measure filters | S21 LOGMAG |
| Measure cable attenuation | S21 LOGMAG |
| Determine bandwidth | Two markers and a defined threshold |

---

## The Recommended NanoVNA Workflow

![Figure 14: Recommended workflow from frequency selection to verification](https://raw.githubusercontent.com/gh4chris/nanoNVA-de/main/images/b8e89fa70c.png)

*Figure 14: Recommended workflow from frequency selection to verification*

1. Set the desired frequency range.
2. Assemble the complete measurement chain.
3. Calibrate at the correct reference plane.
4. Connect the device under test without changing the chain.
5. Use SWR or S11 LOGMAG for an overview.
6. Place the marker at the point of interest.
7. Examine frequency, R, X, and the Smith Chart together.
8. Make only one change at a time.
9. Measure again under the same conditions.
10. Compare the before-and-after results.

This workflow avoids most beginner mistakes. More importantly, it teaches you not only to look at curves, but to use them to decide what to do next.

The NanoVNA does not do the thinking for you. It makes visible what is actually happening in an antenna, feed line, or RF component. That is its greatest value.

---

## Sources and Further Reading

- [NanoVNA practical measurement guide - NextTechWorld](https://nexttechworld.com/de/amateurfunk/nanovna-praxisguide/)
- [NanoVNA setup guide: calibration, SWR, Smith Chart, and antenna testing - SDRStore](https://www.sdrstore.eu/nanovna-setup-guide-calibration-swr-smith-chart-antenna-testing/?sl=de)
- [Measuring SWR with a NanoVNA - VESAB PDF](https://www.vesab.de/wpvesab/wp-content/uploads/SWR_messen_V01_2022_10_13.pdf)
- [NanoVNA antenna testing - Björn's Techblog](https://www.bjoerns-techblog.de/2019/11/nanovna-der-antenne-unter-den-rock-geschaut/)
