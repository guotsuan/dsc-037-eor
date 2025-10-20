# DSC-037: Cable Reflection Systematics for EoR Science

This repository hosts three exploratory Jupyter notebooks produced for the
[DSC-037](https://confluence.skatelescope.org/x/0rs6F) data-science challenge.  The
material concentrates on steps 3 and 4 of the challenge workflow, where the goal is
to assess the spectral smoothness of calibrated visibilities and to derive delay power
spectra that highlight cable-reflection systematics in SKA-Low pathfinder data.

## Notebook overview

| Notebook | Focus | Key capabilities |
| --- | --- | --- |
| `plot_vis_for_mwa_lofar.ipynb` | Challenge step 3: visibility inspection | Loads visibilities from LOFAR Measurement Sets (via `casacore`) or UVFITS/pyuvdata-compatible files and plots amplitude and phase versus time and frequency for individual baselines. Interactive controls let you choose polarisations, antennas, and plotting axes to verify temporal and spectral smoothness. |
| `bl-avg_delayps_per_antenna.ipynb` | Challenge step 4: delay power spectra per antenna | Builds time- and redundancy-averaged delay power spectra for all baselines that include a selected antenna. Uses `pyuvdata` to read visibilities and `hera_pspec` to form delay transforms, with options to filter by polarisation, time range, and maximum baseline length. |
| `time-avg_delayps_across_blens.ipynb` | Challenge step 4: delay spectra across baseline lengths | Aggregates time-averaged delay power spectra across all baselines shorter than a configurable threshold, enabling cylindrical averaging by baseline-length bin. Mirrors the configuration controls of the per-antenna notebook but emphasises exploring different redundant groups. |

Each notebook begins with dataset metadata inspection, followed by configuration
cells that let you select time/frequency windows, polarisation products, target
antennas or baseline-length limits, and plotting preferences.  Subsequent sections
load the visibilities, prepare them for analysis, and render the diagnostic plots
inline.

## Dataset prerequisites

All workflows assume access to the Murchison Widefield Array (MWA) dataset made
available through Rucio for the challenge (see
https://confluence.skatelescope.org/x/tnTGEg).  The dataset characteristics are:

- Integration time: 8 s
- Total duration: 112 s
- Bandwidth: 28 MHz centred on 65 MHz
- 384 frequency channels of width 44 kHz
- Direction-independent calibration and sky-model subtraction applied
- Calibration solutions distributed alongside the visibilities
- Approximate download size: 1.9 GB

LOFAR data
TODO

## Software requirements

All notebooks rely on a standard scientific Python stack plus packages commonly used
for radio-interferometric data analysis:

- `numpy`
- `matplotlib`
- `astropy`
- `pyuvdata`
- `hera_pspec`
- `python-casacore` (required only when reading Measurement Sets)


## Additional resources

The following challenge documentation provides broader context and detailed walkthroughs:

- Chronological walkthrough: https://confluence.skatelescope.org/x/osw6F
- Implementation notes and software design: https://confluence.skatelescope.org/x/n8LMF
- Source repository on GitHub: https://github.com/uksrc-developers/dsc-037-eor
- Jira tickets: [TEAL-1128](https://jira.skatelescope.org/browse/TEAL-1128),
  [TEAL-1129](https://jira.skatelescope.org/browse/TEAL-1129)

Questions about the notebooks can be directed to the Teal team members listed within
the notebook headers.
