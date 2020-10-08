**Data reduction of time-of-flight data taken on BL4A (MagRef) treated using a Continuous Wave (CW) approach**

The CW approach calculates the reflectivity for a fixed neutron beam wavelength (or small bin of wavelengths). The process is applied to each wavelength bin to yield a collection of reflectivities curves that have the same form but differ by a multiplicative constant. A region of overlap of wavevector transfer is identified. The curves are scaled such that their integrals in the overlap region are the same. Then the curves are added together to produce one curve. The CW approach to produce R(Q) differs from the traditional approach presently used by every pulsed source in that normalization by the spectrum of the incident neutron beam is never done, i.e., the spectrum is not needed!

To obtain R(Q) execute the following steps:

1. Define a working directory
2. In this directory make a sub-directory called &quot;input&quot;
3. In /input put the NumPy binary files of event mode data and metadata logs obtained using the Jupyter notebook &quot;BL4A\_get\_single\_event\_batch&quot; [T.R. Charlton and M.R. Fitzsimmons, _Code to obtain single event data from Spallation Neutron Source Beamline-4A (MagRef)_ (2020) [https://doi.org/10.5281/zenodo.3967680](https://doi.org/10.5281/zenodo.3967680)]
4. Run the Jupyter notebook &quot;CW\_reduction\_batch&quot; after making changes to the code as instructed in the notebook. This notebook produces a set of files tagged with &quot;\_output&quot;. Each file contains 4 columns: wavelength, 2theta, net signal (above background), variance of the net signal.
5. Run the Jupyter notebook &quot;CW\_assemble\_batch&quot; after making changes to the code as instructed in the notebook. This notebook reads the &quot;\_output&quot; files (still located in the working directory!), calculates Q, performs constant Q-binning to yield R(Q) and its standard deviation. These results are written in a file &quot;RvsQ…&quot; as Q, R, dR, dQ. This file can be directly imported into GenX.

On the Zenodo website, I have provided data collected from a ~50 nm Pt film on a Si substrate (&quot;input.zip). The data were taken using 60 Hz pulses and a wavelength band of roughly 4-7 Å in 100 steps of 2theta. Each file contains corresponds to one of the 2theta steps. The files are numbered 36366 through 36662 with extensions of &quot;.npz&quot;. As an example, these files should be placed on your &quot;/input&quot; sub-directory of your working directory.

After running the CW\_reduction\_batch notebook, I ran the CW\_assemble\_batch notebook. Then I moved the output files from CW\_reduction\_batch into the &quot;/results&quot; sub-directory. The output of the CW\_assemble\_batch notebook remains in the working directory as &quot;RvsQ…&quot;.

M.R. Fitzsimmons (10.07.2020)

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4072377.svg)](https://doi.org/10.5281/zenodo.4072377)