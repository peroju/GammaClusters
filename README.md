# GammaClusters
A golden sample of local galaxy clusters for detection of $\gamma$-ray emission.

Clusters of galaxies are the largest gravitationally-bound systems in the Universe ($M\sim 10^{15} M_{\odot}$). They are dominated by dark matter (DM; ∼ 85% in mass) and permeated by the intracluster medium (ICM; ∼ 10−15% in mass), whose physical properties are shaped by the hierarchical growth of structures through the merging of subclusters and the smooth accretion of surrounding matter. Accordingly, galaxy clusters are expected to be both DM reservoirs and storage rooms for the cosmic-ray protons (CRp) that accumulate along the cluster’s formation
history. Accordingly, they are excellent targets to search for signals of DM annihilation and decay at $\gamma$-ray energies and are predicted to be sources of large-scale $\gamma$-ray emission due to hadronic interactions in the ICM. The search for diffuse $\gamma$-ray emission from galaxy clusters has been going on for over two decades, both using space-based observations in the GeV band and observations at energies > 100 GeV. However, this signal is still to be robustly detected.

In this repository we present a sample of clusters specially suited to target for search diffuse $\gamma$-ray. Together with the detailed description of the emission models for DM and CR induced 
$\gamma$-rays, we provide comprehensive tutorial notebooks to analyze the models and change the parameters to produce new models if desidered.

## Contents

## Environment and dependencies
The models have been generated using the softwares:
- MINOT (python package, https://github.com/remi-adam/minot)
- CLUMPY 3.1.1 (C++ software, https://clumpy.gitlab.io/CLUMPY/v3.1.1/)

The tutorial notebooks have been developed for Jupyter Notebook using Python 3.9.19. The create the intensity maps containing the emission models we use the python package:
- gammapy 1.1 (https://gammapy.org/)

Some packages already included in `gammapy` that we also use are:
- `numpy`
- `matplotlib`
- `astropy`
- `healpy`

All of this softwares and packages can be installed with `conda env` and/or `pip install` (please check each one individually).

## Sample selection

## CR Models

## DM Models

## Important literature
[1] Prospects for $\gamma$-ray observations of the Perseus galaxy cluster with the Cherenkov Telescope Array. CTAO Consortium. JCAP10(2024)004. [https://arxiv.org/abs/2309.03712]

[2] Constraining the dark matter contribution of $\gamma$-rays in Cluster of galaxies using Fermi-LAT data. M. di Mauro, J. Pérez-Romero, M. A. Sánchez-Conde, N. Fornengo. Phys. Rev. D 107, 083030. [https://arxiv.org/abs/2303.16930]

## Ackowledgements
This repository is supported by Judit Pérez-Romero, with the collaboration of R. Adam and M. A. Sánchez-Conde. This repository is supported by the European Union's Horizon Europe research and innovation programme under the Marie Skłodowska-Curie Postdoctoral Fellowship Programme, SMASH co-funded under the grant agreement No. 101081355.
