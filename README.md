# Raman Spectra Analysis

I wrote this in Mathematica for a physical chemistry lab, to analyze Raman spectra of carbon tetrachloride and chloroform and work out their vibrational modes.

The notebook takes raw spectra in a few different formats (.jdx, .xlsx, .txt), cleans them up, finds the peaks, and matches them against the NIST reference values. The main pieces are a cleaning function that handles the different file formats, a peak finder that smooths the data and picks out the real peaks, and a matching function that assigns each peak to a vibrational mode and checks whether the mode is actually allowed to show up in Raman.

A few things that came out of it. The v1+v4 combination band lands at 773 cm^-1, right on top of the v3 band around 760-790, which is the Fermi resonance, and both modes have the same T2 symmetry, so that checks out. I also built a simple valence force field model for CCl4 and solved for the stretching and bending force constants (about 434,000 and 33,000 dyne/cm). The model gets v4 roughly right but misses v3 badly, which is expected, it can't handle the asymmetric stretch. And the measured peaks sit about 20-30 cm^-1 below the NIST values across the board, which looks like a calibration offset in the instrument rather than a problem with any one peak.

The spectra were collected by our lab group, so some of the files are from my lab partner. The analysis is mine.

Open Lab7-1_2.nb in Mathematica and run it. It imports the data from Wolfram Cloud, so you'll need a connection.
