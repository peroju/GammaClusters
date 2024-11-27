# GammaClusters
A golden sample of local galaxy clusters for detection of diffuse $\gamma$-ray emission.

Clusters of galaxies are the largest gravitationally-bound systems in the Universe ($M\sim 10^{15} M_{\odot}$). They are dominated by dark matter (DM; ∼ 85% in mass) and permeated by the intracluster medium (ICM; ∼ 10−15% in mass), whose physical properties are shaped by the hierarchical growth of structures through the merging of subclusters and the smooth accretion of surrounding matter. Accordingly, galaxy clusters are expected to be both DM reservoirs and storage rooms for the cosmic-ray protons (CRp) that accumulate along the cluster’s formation
history. Therefore, they are excellent targets to search for signals of DM annihilation and decay at $\gamma$-ray energies and are predicted to be sources of large-scale $\gamma$-ray emission due to hadronic interactions in the ICM. The search for diffuse $\gamma$-ray emission from galaxy clusters has been going on for over two decades, both using space-based observations in the GeV band and observations at energies > 100 GeV. However, this signal is still to be detected.

In this repository we present a sample of clusters specially suited to target for search diffuse $\gamma$-ray. Together with the detailed description of the emission models for DM and CR induced $\gamma$-rays, we provide comprehensive tutorial notebooks to analyze the models and change the parameters to produce new models if desidered.

## Contents
- : master table of the _golden sample_ of galaxy clusters with its properties;
- : description of the parameters of the  master table;
- : folder cointaining the DM spatial models as FITS files for the baseline annihilation model for our sample;
- : folder cointaining the DM spatial models as FITS files for the baseline decay model for our sample;
- : folder containing the CR spatial (FITS) and spectral models (.txt) for different CR models for our sample;
- : DM spectral tables from [CosmiXs](https://github.com/ajueid/CosmiXs) modified to be readable by `gammapy`;
- : tutorial notebook for creting the intensity maps for DM models;
- : tutorial notebook for creating the intensity maps for CR models;
- : tutorial notebook on examples on how to analyze the models with `gammapy`.

## Environment and dependencies
The models have been generated using the softwares:
- `MINOT` (python package, https://github.com/remi-adam/minot)
- `CLUMPY 3.1.1` (C++ software, https://clumpy.gitlab.io/CLUMPY/v3.1.1/)

The tutorial notebooks have been developed for Jupyter Notebook using `python 3.9.19`. To create the intensity maps containing the emission models we use the python package:
- `gammapy 1.1` (https://gammapy.org/)

Some packages already included in `gammapy` that we also use are:
- `numpy`
- `matplotlib`
- `astropy`
- `healpy`

All of these softwares and packages can be installed with `conda env` and/or `pip install` (please check instructions for each one individually).

## Sample selection
The sample contains 48 galaxy clusters is build following the steps described in [1], but here we provide some insight on the selection criteria. All of the that clusters were selected fullfill the following criteria:
- $z<0.1$, since the DM-induced flux decays as $1/d_L^2$ where $d_{L}$ its luminosity distance;
- separation between each cluster, at least 2 deg, where their angular extension is defined as $\theta_{200} = R_{200}/d_L$, where $R_{200}$ is the radius within which the mean cluster density is 200 times the critical density of the Universe at the cluster’s redshift;
- $|b|> 20$ deg, where $b$ is galactic latitude, to avoid contamination from the galactic diffuse emission from the galactic plane.

Another key ingredient for selection of clusters is their estimation on the mass, since the emission models depend a lot on it. For our sample, their $M_{500}$ masses are obtained from the X-ray catalogue MCXC (https://heasarc.gsfc.nasa.gov/W3Browse/rosat/mcxc.html), and extrapolated up to $M_{200}$. This sample of clusters contains some objects that have already been previously considered interesting for the search of diffuse $\gamma$-ray emission, with searches campaings perfomed [joint](https://arxiv.org/abs/1308.5654) and [individually](https://arxiv.org/abs/1510.00004), and by satellite-based (e.g., [_Fermi_-LAT](https://arxiv.org/abs/1507.08995)) and ground-based telescopes (e.g., [HESS](https://arxiv.org/abs/1205.5283), [MAGIC](https://arxiv.org/abs/1806.11063)). In the following, we assume for the computation of the $\gamma$-ray emission that clusters are self-similar objects.

## CR Models
The prediction of the diffuse $\gamma$-ray emission induced by CR in the ICM requires the detailed modelling of the physical components at play, their interactions, and the underlying radiative processes. This prediction (model) is done using the free sotware [`MINOT`](https://github.com/remi-adam/minot). Here we provide a short description on the assumptions and parametrizations used, but for further details please check `MINOT` repository, [2] and [3]. 

We compute the observable properties of the ICM (radio synchrotron, thermal Sunyaev-Zel’dovich effect, X-ray thermal bremsstrahlung, inverse-Compton, $\gamma$-rays from hadronic interactions, and neutrino emission) given the user-defined physical state of the cluster. Clusters are assumed to be spherically symmetric. The parameters of the models are calibrated using external data assuming different scenarios (baseline, pure hadronic and pure leptonic). This includes the thermal gas density and pressure, the magnetic field strength and the CR spatial and spectral distributions. 

The models that we have used can be find in the folder *X* of this repository.

### CR protons (CRp)
The $\gamma$-ray emission induced by hadronic interactions is directly related to the spatial and spectral distribution of CRp in the ICM. They are modeled according to a radial profile and
a canonical power-law:

<img width="300" alt="imagen" src="https://github.com/user-attachments/assets/d97d09c8-69cc-4865-8940-09e6dc5807fd">

The radial profile assumes a scaling with respect to the gas density ($n_{gas}$), described with $\eta_{CRp}$. We also consider that the CRp profile is scaled with respect to the thermal pressure profile, and thus related to the thermal energy. The value $\alpha_{CRp}$ is related to the acceleration of CR. $A_{CRp}$ is computed given the value of the CRp to thermal energy ratio, $X_{CRp}(R) = U_{CRp}(R)/U_{th}(R)$, (where $U$ represent the energy for each subindex) by integrating the equation accordingly. The thermal energy is computed by integrating the pressure profile.

According to the results of numerical simulations and cosmic-ray transport description, some range for the values for this parametrization are:

- $X_{CRp}(R_{500})\sim$ [0.0 - 5.0%];
- $\alpha_{CRp}\sim$ [2.0 - 4.0];
- $\eta_{CRp}\sim$ [0.0 - 5.0].

These limits are defined according to realistic physical expectations of the parameter values. The $\gamma$-ray flux decreases when increasing $\alpha_{CRp}$ and the profile gets
more compact when increasing $\eta_{CRp}$. For a fixed normalization at $R_{500}$, the flux also increases with $\eta_{CRp}$ because of the increased proton-proton collision rate due to the spatial overlap of the CR and the target gas.

Then the hadronic production of $\gamma$-ray is computed by integrating the collision rate of protonproton interactions multiplied by the energy distribution of $\gamma$-rays produced per collision, over the energy of the CR.

### CR electrons (CRe)
The CRe are modeled accounting for two contributions: the primary electrons that are independent from the CRp, and the secondary electrons that are produced from hadronic interactions assuming stationarity. The primary electrons, whenever considered, are modeled similarly to the CRp. Leptonic $\gamma$-ray emission arises via the inverse-Compton (IC) scattering of CRe (secondaries, but
also primary CRe whenever considered) onto cosmic microwave background (CMB) photons. Our IC estimates are based on analytical approximations.

## DM Models
For the computation of the induced $\gamma$-ray emission from DM, we assume that all the DM is composed by Weakly Interacting Massive Particles (WIMPs), which can very weakly interact with the known particles of the Standard Model (SM). Here we provide a short description on the assumptions and parametrizations used, but for further details please check `CLUMPY` [documentation](https://clumpy.gitlab.io/CLUMPY/v3.1.1/), `gammapy` [documentation](https://gammapy.org/), [1], [3] and [4]. 

The expected $\gamma$-ray flux from either the annihilation of two WIMPs or its decay, for a given astrophysical objetc, can be computed as:

<img width="300" alt="Captura de pantalla 2024-11-27 a las 11 25 09" src="https://github.com/user-attachments/assets/189a09c4-33d6-4071-abf8-19c78014fea8">

where $d\Phi_{\gamma}/dE$ is the DM-induced $\gamma$-ray flux. $d\phi_{\gamma}/dE$ term is the “particle physics term”, containing the spectral information of the emission. $D(\Delta\Omega, l.o.s)$ and $J(\Delta\Omega, l.o.s)$ are the astrophysical D-factor (decay), and J-factor (annihilation), computed along the line of sight ($l.o.s.$) and within a given solid angle $\Delta\Omega$. This computation assumes that the spatial distribution of the DM signal is independent of energy. These terms are defined as:

<img width="300" alt="Captura de pantalla 2024-11-27 a las 11 25 24" src="https://github.com/user-attachments/assets/4e1f4cbc-fdc4-4686-a7ed-2063ae837fa5">

where $m_{\chi}$ is the DM mass, $dN_{\gamma}/dE$ is the WIMP photon spectrum, $<\sigma v>$ is the thermally-averaged annihilation cross-section and $\tau$ is the DM particle lifetime; and for the spatial components:

<img width="300" alt="Captura de pantalla 2024-11-27 a las 11 25 44" src="https://github.com/user-attachments/assets/1bcfd1d9-9210-4298-a449-a6d6602670a7">

where $\Delta\Omega = 2\pi(1−\cos\alpha_{int})$, where $\alpha_{int}$ is the integration angle, i.e., the angle between the $l.o.s$ and the direction that points toward the center of the cluster, and $\rho_{tot}(r)$ the DM density profile. $\rho_{tot}(r)$ describes the DM distribution inside the object. For each cluster, we model $\rho_{tot}(r)$ as a combination of the DM distribution in the mail halo of the cluster and an averaged contribution accounting for the distribution in the substructures. For modelling the distribution of subhalos, we use the knowledge from the results of numerical N-body cosmological simulation, pointing to a parametrization taking into account the subhalo mass function and the position of the subhalo inside the main halo. However, there are still significant uncertainties related to the properties of the subhalo population like  the minimum mass to form clumps or the impact oftidal stripping on subhalo survival. We recall that the contribution of substructure is only important for the case of DM  annihilation. For further explanation on how we constructed the contribution for substructures, please check [1]. 

For the spatial component, we elaborate our models using `CLUMPY`. The spatial models that we have used can be find in the folder *X* of this repository. To compute the DM-induced emission, we need to choose also the spectral parameters as the $m_{\chi}$ and the annihhilation/decay channel. We perform this step using `gammapy` and making use of the results of [5] for $dN_{\gamma}/dE$, which can be found in the repository [CosmiXs](https://github.com/ajueid/CosmiXs), which can be done using the tutorial notebook *XX*.

### Note about the use of CosmiXs

## Important literature
[1] Constraining the dark matter contribution of $\gamma$-rays in Cluster of galaxies using _Fermi_-LAT data. M. di Mauro, J. Pérez-Romero, M. A. Sánchez-Conde, N. Fornengo. Phys. Rev. D 107, 083030. [https://arxiv.org/abs/2303.16930]

[2] MINOT: Modeling the intracluster medium (non-)thermal content and observable prediction tools. R. Adam _et atl._. A&A 644, A70 (2020). [https://arxiv.org/abs/2009.05373]

[3] Prospects for $\gamma$-ray observations of the Perseus galaxy cluster with the Cherenkov Telescope Array. CTAO Consortium. JCAP10(2024)004. [https://arxiv.org/abs/2309.03712]

[4] CLUMPY v3: $\gamma$-ray and $\nu$ signals from dark matter at all scales. M. Hütten, C. Combet, D. Maurin. CPC 235, 336 (2019). [https://arxiv.org/abs/1806.08639]

[5] CosmiXs: Cosmic messenger spectra for indirect dark matter searches. C. Arina _et al._. JCAP03(2024)035. [https://arxiv.org/abs/2312.01153]


## Ackowledgements
This repository is supported by Judit Pérez-Romero, with the collaboration of R. Adam and M. A. Sánchez-Conde. This repository is supported by the European Union's Horizon Europe research and innovation programme under the Marie Skłodowska-Curie Postdoctoral Fellowship Programme, SMASH co-funded under the grant agreement No. 101081355.

### Reference
In case you use models, data or codes from this repository in your research, please cite us to acknowledge its use. 
