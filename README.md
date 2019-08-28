# GW170817: Stringent constraints on neutron-star radii from multimessenger observations and nuclear theory

**Collin D. Capano<sup>1,2</sup>, Ingo Tews<sup>3</sup>, Stephanie M. Brown<sup>1,2</sup>, Ben Margalit<sup>4,5,6</sup>, Soumi De<sup>6,7</sup>, Sumit Kumar<sup>1,2</sup>, Duncan A. Brown<sup>6,7</sup>, Badri Krishnan<sup>1,2</sup>, Sanjay Reddy<sup>8,9</sup>**

**<sup>1</sup>Albert-Einstein-Institut, Max-Planck-Institut für Gravitationsphysik, Callinstraße 38, 30167 Hannover, Germany**

**<sup>2</sup>Leibniz Universität Hannover, 30167 Hannover, Germany**

**<sup>3</sup>Theoretical Division, Los Alamos National Laboratory, Los Alamos, NM 87545, USA**

**<sup>4</sup>Department of Astronomy and Theoretical Astrophysics Center, University of California, Berkeley, CA 94720, USA**

**<sup>5</sup>NASA Einstein Fellow**

**<sup>6</sup>Kavli Institute for Theoretical Physics, University of California, Santa Barbara, CA 93106, USA**

**<sup>7</sup>Department of Physics, Syracuse University, Syracuse NY 13244, USA**

**<sup>8</sup>Institute for Nuclear Theory, University of Washington, Seattle, WA 98195-1550, USA**

**<sup>9</sup>JINA-CEE, Michigan State University, East Lansing, MI, 48823, USA**

## License

![Creative Commons License](https://i.creativecommons.org/l/by-sa/3.0/us/88x31.png "Creative Commons License")

This work is licensed under a [Creative Commons Attribution-ShareAlike 3.0 United States License](http://creativecommons.org/licenses/by-sa/3.0/us/).

## Introduction

This repository is a companion to [Capano et al. (arxiv:1908.10352)](https://arxiv.org/abs/1908.10352). It contains the Livingston glitch-removed gravitational-wave frame data, the equation of state files, and the posterior probability density files from the parameter estimation.

We encourage use of these data in derivative works. If you use the material provided here, please cite the paper using the reference:
```
@article{Capano:2019,
      author         = "Capano, Collin D. and Tews, Ingo and Brown, Stephanie M. and
                        Margalit, Ben and De, Soumi and Kumar, Sumit and Brown, Duncan
                        A. and Krishnan, Badri and Reddy, Sanjay",
      title          = "{GW170817: Stringent constraints on neutron-star radii from
                         mutimessenger observations and nuclear theory}",
      year           = "2019",
      eprint         = "1908.10352",
      archivePrefix  = "arXiv",
      primaryClass   = "astro-ph.HE",
      SLACcitation   = "%%CITATION = ARXIV:1908.10352;%%"
}
```

## Contents

 * [eos_data](https://github.com/sugwg/gw170817-eft-eos/tree/master/eos_data) contains the equation of state data using chiral effective field theory computed to either nuclear saturation density [nsat](https://github.com/sugwg/gw170817-eft-eos/tree/master/eos_data/nsat) or twice nuclear saturation density [2nsat](https://github.com/sugwg/gw170817-eft-eos/tree/master/eos_data/2nsat). Each realization of an equation of state is provided in a single plain-text file. The three columns in these files correspond to radius (km), mass (solar masses), and dimensionless tidal polarizability (Lambda) for each equation of state.
 * [frame_data](https://github.com/sugwg/gw170817-eft-eos/tree/master/frame_data) contains the glitch-removed Livingston data used for the gravitational-wave parameter estimation.
 * [posterior_data](https://github.com/sugwg/gw170817-eft-eos/tree/master/posterior_data) contains the posteriors for the equations of state computed to either nuclear saturation density [nsat](https://github.com/sugwg/gw170817-eft-eos/tree/master/posterior_data/nsat) or twice nuclear saturation density [2nsat](https://github.com/sugwg/gw170817-eft-eos/tree/master/posterior_data/2nsat). For each of the two families of equations of state, the primary results are available in the directory `uniform_mass_prior`. This directory contains three files: `posterior.hdf` contains the gravitational-wave posterior, `posterior_mthresh.hdf` contains the posterior with the threshold mass cut applied, and `posterior_mthresh_maxmass.hdf` contains the posterior with both the threshold mass cut and maximum neutron star mass cut applied. The directories called `dns_mass_prior` contains the same data for the double neutron star mass prior.

## Reading posterior samples

The posterior samples are in the `samples` group in the posterior data hdf files. These may be read in a python environment using an installation of h5py. For example,
```
>>> import h5py
>>> fp = h5py.File('posterior_data/2nsat/uniform_mass_prior/posterior_mthresh_maxmass.hdf', 'r')
>>> fp['samples/radius_1p4'][:]
array([10.66445588, 10.33877226, 10.81947201, ..., 11.53508902,
     11.22292423, 11.77858514])
```

Provided parameters are:
 * `mass1`: The source-frame mass of the larger object, in solar masses.
 * `mass2`: The source-frame mass of the smaller object, in solar masses.
 * `spin1z`: The dimensionless spin of the larger object.
 * `spin2z`: The dimensionless spin of the smaller object.
 * `eos`: The equation of state index. The corresponding equation of state is
   in the eos directory, with the name of the text file corresponding to the
   index. Note: the eos indices are stored as floats; to find the appropriate
   EOS file, take the integer part. For example, `450.87` corresponds to EOS
   `450`.
 * `tc`: The geocentric GPS time of the signal merger.
 * `inclination`: The inclination of the binary's orbital angular momentum with
   respect to the line of sight, in radians. An inclination of 0 (pi)
   corresponds to a face-on (face-away) orientation.
 * `polarization`: The polarization angle of the gravitational wave.
 * `loglikelihood`: The natural log of the likelihood of each sample.

The following parameters are calculated from the equation of state associated
with each sample. As such, there are only 2000 unique values of the following,
even though the total number of samples may be larger.
 * `lambda1`: The dimensionless tidal polarizability of the larger object.
 * `lambda2`: The dimensionless tidal polarizability of the smaller object.
 * `radius1`: The radius of the larger object, in km.
 * `radius2`: The radius of the smaller object, in km.
 * `radius_1p4`: The radius of a 1.4 solar mass neutron star with the same
   equation of state.
 * `radius_1p6`: The radius of a 1.6 solar mass neutron star with the same
   equation of state.
 * `p1p9`: The pressure in the core of a 1.9 solar mass neutron star with the
   same equation of state, in MeV / cubic fm.
 * `p2nsat`: The pressure at twice nuclear saturation density, as determined
   by the equation of state, in MeV / cubic fm.
 * `p4nsat`: The pressure at four times nuclear saturation density, as
   determined by the equation of state, in MeV / cubic fm.
 * `pmax`: The maximum pressure supported by the equation of state, in
   MeV / cubic fm.
 * `cs_sq_1p9`: The speed of sound in the core of a 1.9 solar mass neutron star
   with the same equation of state.
 * `cs_sq_max`: The maximum speed of sound supported by the equation of state.
 * `max_mass`: The maximum neutron star mass supported by the equation of
   state, in solar masses.

In addition, the threshold mass for prompt collapse is provided
(`threshold_mass`), in solar masses. This is calculated using equation 3 of the
supplementary material. To account for systematic error in that fit, a random
draw from a normal distribution with a standard deviation of 0.05 is added to
each threshold mass sample. As a result, there are more than 2000 unique
values of the threshold mass, even though it is calculated from the equation
of state parameters.


## Acknowledgements

We thank Bruce Allen, Wolfgang Kastaun, and Brian Metzger for valuable discussions.

### Funding

This work was supported by U.S. National Science Foundation grants
PHY-1430152 (SR),
PHY-1707954 (DAB, SD);
U.S. Department of Energy grant DE-FG02-00ER41132 (SR);
NASA Hubble Fellowship grant \#HST-HF2-51412.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555 (BM); and the U.S. Department of Energy, Office of Science, Office of Nuclear Physics, under Contract DE-AC52-06NA25396, the Los Alamos National Laboratory (LANL) LDRD program, and the NUCLEI SciDAC program (IT). 
DAB, SD, and BM thank the Kavli Institute for Theoretical Physics (KITP) where portions of this work were completed. KITP is supported in part by the National Science Foundation under Grant No. NSF PHY-1748958. 
Computational resources have been provided by Los Alamos Open Supercomputing via the Institutional Computing (IC) program, by the National Energy Research Scientific Computing Center (NERSC), by the Jülich Supercomputing Center, by the ATLAS Cluster at the Albert Einstein Institute in Hannover, and by Syracuse University. The gravitational-wave data used in this work was obtained from the Gravitational Wave Open Science Center (GWOSC) at [https://www.gw-openscience.org](https://www.gw-openscience.org). GWOSC is a service of LIGO Laboratory, the LIGO Scientific Collaboration and the Virgo Collaboration. LIGO is funded by the National Science Foundation. Virgo is funded by the French Centre National de Recherche Scientifique (CNRS), the Italian Istituto Nazionale della Fisica Nucleare (INFN) and the Dutch Nikhef, with contributions by Polish and Hungarian institutes.

### Authors contributions:
Conceptualization, DAB, CDC, BK, BM, SR, IT;
Data curation, DAB, CDC, IT;
Formal analysis, CDC, SMB, IT, SD;
Funding acquisition: DAB, BK, BM, SR, IT;
Methodology: DAB, CDC, SD, BK, BM, SR, IT;
Project administration: DAB, CDC, BK, IT;
Resources: DAB, BK, IT;
Software: DAB, SMB, CDC, SD, SK, BM, IT;
Supervision: DAB, BK, SR;
Validation: DAB, SMB, CDC, SD, IT;
Visualization: SMB, CDC, BM;
Writing--original draft: DAB, SMB, CDC, IT;
Writing--review and editing: DAB, SMB, CDC, SD, BK, BM, SR, IT.
