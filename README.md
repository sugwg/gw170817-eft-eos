# Measuring the viewing angle of GW170817 with electromagnetic and gravitational waves

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

This notebook is a companion to [Capano et al. (arxiv:19XX.YYYYYY)](https://arxiv.org/abs/19XX.YYYYYY). It demonstrates how to read and use our gravitational-wave frame data, equation of state files, and posterior proability density files from the parameter estimation.

We encourage use of these data in derivative works. If you use the material provided here, please cite the paper using the reference:
```
@article{Capano:2019xxx,
Fill in once available
}
```

## Contents




## Acknowledgements

We thank Bruce Allen, Wolfgang Kastaun, and Brian Metzger for valuable discussions.

### Funding

This work was supported by U.S. National Science Foundation grants
PHY-1430152 (SR),
PHY-1707954 (DAB, SD);
U.S. Department of Energy grant DE-FG02-00ER41132 (SR);
NASA Hubble Fellowship grant \#HST-HF2-51412.001-A awarded by the Space Telescope Science Institute, which is operated by the Association of Universities for Research in Astronomy, Inc., for NASA, under contract NAS5-26555 (BM); and the U.S. Department of Energy, Office of Science, Office of Nuclear Physics, under Contract DE-AC52-06NA25396, the Los Alamos National Laboratory (LANL) LDRD program, and the NUCLEI SciDAC program (IT). 
DAB, SD, and BM thank the Kavli Institute for Theoretical Physics (KITP) where portions of this work were completed. KITP is supported in part by the National Science Foundation under Grant No. NSF PHY-1748958. 
Computational resources have been provided by Los Alamos Open Supercomputing via the Institutional Computing (IC) program, by the National Energy Research Scientific Computing Center (NERSC), by the J\"ulich Supercomputing Center, by the ATLAS Cluster at the Albert Einstein Institute in Hannover, and by Syracuse University. 

### Authors contributions:
Conceptualization, DAB, CDC, BK, BM, SR, IT;
Data curation, DAB, CDC;
Formal analysis, CDC, SMB, IT, SD;
Funding acquisition: DAB, BK, BM, SR, IT;
Methodology: DAB, CDC, SD, BK, BM, SR, IT;
Project administration: DAB, CDC, BK, IT;
Resources: DAB, BK, IT;
Software: SMB, CDC, SD, SK, BM, IT;
Supervision: DAB, BK, SR;
Validation: DAB, SMB, CDC, SD, IT;
Visualization: SMB, CDC, BM;
Writing--original draft: DAB, SMB, CDC, IT;
Writing--review and editing: DAB, SMB, CDC, SD, BK, BM, SR, IT.
