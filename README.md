# Accelarated PCS solvers

Scripts (in python2.7 and C) for the experiments from the paper Papez, Grigori, Stompor 2020: "Accelerating linear system solvers for time domain component separation of cosmic microwave background data", submitted to Astronomy & Astrophysics. The paper is available from https://hal.inria.fr/hal-02470964.

The scripts are prepared to be run from NERSC's Cori machine; but any other machine can be used after properly updating the paths.

The experiments require simulated data, which are not freely available due to an extensive memory they require. Nevertheless, they can be demanded on "jan@papez.org". Any user can use the codes for any other data, which satisfy the requirements described below.

After copying the scripts, the C-code matrix_operations.c must be compiled to generate a shared library. The compile commands are for Mac OS and Cori machine given in the very bottom of matrix_operations.c.

# Data description

signal
*  values of signal components in observed pixels (3 components: cmb, dust, sync): cmb_observed.txt, dust_observed.txt, sync_observed.txt; 3 matrices of size (N_pix,3)
*  sequence of mixing parameters: sampled_betas.npy

noise
*  for each frequency: inverse spectrum and 2 noise realizations (for horizontal and vertical scans), all vectors of length N_t

pointing
*  index of the observed pixel in time t, indices should be in [0, N_pix-1] for horizontal and vertical scans; 2 vectors of length N_t
*  Q and U weights for horizontal and vertical scans; 2x2 vectors of length N_t, can be shortened if periodic 
