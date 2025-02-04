CASTEP writes output data in a variety of files. Some of these will be in human readable ASCII format (i.e. plaintext) and can be read with commands such as `less` or `more` on linux, or with a simple text editor (textedit, notepad etc). Other files will be in binary format and are designed to be read or processed with an external program.


## Groundstate


* `.castep`
ASCII. Castep's main outputfile.

* `.bib`
ASCII. Bibtex file containing citations to the methods CASTEP has used in the calculation.

* `.check`
Binary. This checkpoint file contains the results of the calculation including the groundstate charge density and wavefunctions. It is typically a very large file. Will be read by CASTEP when performing a continuation calculation. Also read by postprocessing software such as c2x.

* `.check_bak`
Binary. backup of the checkpoint file.

* `.cst_esp`
Binary. Electrostatic potential.

* `.usp`
ASCII. Pseudoptential data, written for each species. See the page on [reading usp headers](/documentation/Pseudopotentials/reading_headers)

* `.uspso`
ASCII. Pseudoptential data, written for each species. This is the J-dependant version of the `.usp`. See the page on [reading usp headers](/documentation/Pseudopotentials/reading_headers)


* `.bands`
ASCII. Kohn-Sham eigenvalues at the requested k-points. Can be used to plot band structures or density of states. Note that the eigenvalues are given in atomic units (Hartree).

* `.den_fmt`
ASCII. Charge density. Only written if `write_formatted_density : T `.

* `.pot_fmt`
ASCII. Groundstate potential. Only written if `write_formatted_potential : T `.

* `.chdiff`
Binary. Difference between the groundstate charge density and a superposition of atomic densities. Only written if `calculate_densdiff : T`

* `.chdiff_fmt`
ASCII. same data as `.chdiff` in human readable format. Only written if `calculate_densdiff : T` and `write_formatted_density : T `.

* `.xrd_sf`
ASCII. X-ray structure factors. See the [documentation page](documentation/XRD/overview)

## Geometry Optimisation

* `*.geom`
ASCII. State of the system (coordinates, unit cell etc) at each step of the geometry optimisation. See for specification. Can be used to animate the geometry optimisation - can be read with Jmol.

## Molecular Dynamics

* `*.md`
ASCII. State of the system (coordinates, unit cell etc) at each step of the molecular dynamics simulation. Same format as the `.geom` file.  See for specification. Can be used to animate the geometry optimisation - can be

## Spectral

* `.pdos_bin`
Binary. Matrix elements used for plotting a projected density of states. Used by Optados.

* `.ome_bin`
Binary. Matrix elements used for calculating optical properties. Used by Optados.

* `.dome_bin`
Binary. Diagonal elements of the optical matrix elements. Used by Optados to plot densities of states / spectral properties using adaptive smearing.

* `.elnes_bin`
Binary. Matrix elements used for plotting the core-loss spectrum. Used by Optados.

* `.orbitals`
Binary. Kohn-Sham states at each kpoints. Used by `orbital2bands` to make a reorganised `.bands` file for a cleaner looking bandstructure.

## Phonon

* `.phonon`
ASCII. Phonon eigenvalues and eigenvectors.

## Magres

* `.magres`
ASCII. Contain the NMR tensors (depending on `magres_task` shielding, EFG or J). Read by MagresView or the Soprano python libraries.

* `_current.dat`
ASCII. Written if `MAGRES_WRITE_RESPONSE=True`. Used to compute NICS (nucleus independent chemical shifts) see https://www.ccpnc.ac.uk/docs/nics

## Transition state search

* `.ts`
ASCII. See the specification in the [documentation pages](/documentation/Transition_State_Search/neb)
