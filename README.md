# Raman-Tensors
Calculates symmetry compositions in polarization resolved Raman scattering experiments

The goal of  this notebook is to calculate the contribution from each irreducible representations (irreps) given a set of scattering configurations in a Raman scattering experiment. In each experiment, the result depends on 3 things, what is the crystal symmetry, how the incident and scattered light polarization is oriented with respect to the crystalline axes. Raman tensors relate these 3 parameters to the scattering cross-section, i.e. I = |<es|M|ei>|^2. The crystal symmetry dictates the forms of tensors M, the vectors ei and es are the polarization vectors of the incident and scattered light, respectively.

The Raman tensors used here were tabulated in Cardona's Inelastic Light Scattering in Solids Vol. 2 Chap. 2. The forms of Raman tensors depend only on the point groups of the crystal lattice, and not on the space groups. Moreover, some point groups share the same irreps that are Raman active [1]. For example, Oh, Td and O groups all have 4 Raman active irreps, i.e. A1g, Eg, T1g and T2g for Oh group, and A1, E, T1 and T2 for Td/O groups. The addition of "g" in the irreps of Oh group simply implies the existence of inversion symmetry, and does not change the forms of the Raman tensors of the two groups. Therefore, we bundle these similar groups together in the analysis below, and label the irreps using a group within the bundle as representative, e.g. Oh in the example above.

For each point group and scattering plane, there exist a set of light polarization combinations that allows clean isolation of contributions from each irreps. For example, backscattering from the (001) plane of a sample with D4h point group symmetry couples to A1g, A2g, B1g and B2g irreps. For a single scattering geometry, such as HH [2], it will couple to both A1g and B1g irreps. But if we acquire data from HH, HV, HdHd, HdVd, RR, and RL, then we can isolate individual irreps, e.g., A1g = (HH+HdHd-RL)/2, and similarly for other irreps.

To use this calculator, follow these steps.
1, run the initialize cell.
2, select the relevant point group symmetry, and run the cell defining the tensors.
3, define the crystal surface normal vector, Ns. This is only important if you want to study the azimuthal dependence. Otherwise just input any random vector.
4, define the incident/scatter light polarization vector, ei/es, for each experimental configuration being performed. This calculates the composition of matrix elements in the defined configuration. For example, in the HH scattering geometry with H=(100) from crystal with Oh symmetry gives a^2+4b^2, that is A1g+4Eg1. 

[1] These point groups may have other irreps that are not Raman active, which we will disregard here.
[2] The first index refers to the polarization of the incident photon. In our convention, H means horizontal in the optics table coordinate, V means vertical, and R/L are circularly polarized. In most cases, the result can be greatly simplified if the linear polarization is aligned with one of the crystal axes, such as (100) or (110) in a cubic crystal. In these cases, we denote (110) as Hd for diagonal axis. 
