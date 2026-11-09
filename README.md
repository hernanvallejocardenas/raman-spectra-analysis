# Raman Spectra Analysis

This code takes messy instrument files and turns them into a clean list of vibration peaks, then checks those peaks against public reference values. In plain terms: Raman spectra are light-scattering measurements that show how molecules vibrate. Each vibration shows up as a peak at a particular wavenumber, measured in cm^-1. The code cleans up files in different formats, finds those peaks, and compares them with published NIST reference values for carbon tetrachloride (CCl4) and chloroform (CHCl3).

## What the code does

- `CleanData[importedData]` reads `.jdx` and `.xlsx` files and normalises them to a common format. Only those two formats are handled.
- `GetMajorPeaks[cleanData, sigma, relThreshold]` smooths each spectrum and picks out the major peaks above a relative threshold.
- `FindMatch[exptVal, compList]` matches each measured peak to the nearest computed peak.
- `CheckPresence[ramanVal, ftirList]` checks whether a Raman peak also appears in the FT-IR peak list. That is an overlap check only. It is not a symmetry analysis, and it does not determine whether a mode is Raman-allowed.

The notebook also runs an FT-IR cross-check on the same molecules and produces 8 plots comparing measured, computed, and FT-IR spectra.

## What the numbers say

- Measured peaks sit 20–30 cm^-1 below the NIST values across the board, about 3–4% at these wavenumbers. That is consistent with a systematic calibration offset, not an error in any single peak.
- The v1+v4 combination band appears at 773 cm^-1, overlapping the v3 band in the 760–790 cm^-1 region.
- The simple valence force-field model fails quantitatively. It uses a stretching force constant of about 434,000 dyne/cm and a bending force constant of about 33,000 dyne/cm, and it predicts v4 at 262.1 cm^-1 vs 314 observed (17% low) and v3 at 1113.6 cm^-1 vs ~773 observed (44% high). It cannot describe the asymmetric stretch. Those numbers are reported as a failed model, not as a success.

## How to run it

Open `raman-spectra-analysis.nb` in Mathematica and run it top to bottom. It loads the spectra from Wolfram Cloud, so a connection is needed.

Expected output: cleaned spectra for CCl4 and CHCl3, peak tables with NIST comparisons, the FT-IR cross-check table, the force-field model values above, and 8 plots.

## Files

- `raman-spectra-analysis.nb` — the analysis notebook
- `README.md` — this file

Code in this repo is under the MIT licence.
