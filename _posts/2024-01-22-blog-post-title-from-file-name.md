## Study Octopus: compare with VASP
1.	The parameters of the same meaning compared with VASP
Octopus	VASP
SymmetriesTolerance	SYMPREC
Smearing	SIGMA
SmearingFunction = fermi_dirac	ISMEAR=0
MixField = density [potential]	IMIX > 0 [4]
ExtraStates [0]	NBANDS[max(NELECT/2+NIONS/2,NELECT*0.6]
XCfunctional	GGA
KPointsUseSymmetries	ISYM>0
SymmetrizeDensity	ISYM=2 or 3
%KPointsGrid
  6 | 4 | 2
%	KPOINTS file row # 4
%ReducedCoordinates
"Ga" | 0.6666666666666666 | 0.3333333333333333 | 0.4990837100000000
"Ga" | 0.3333333333333333 | 0.6666666666666666 | 0.9990837100000001
"N"  | 0.6666666666666666 | 0.3333333333333333 | 0.8759162900000000
"N"  | 0.3333333333333333 | 0.6666666666666666 | 0.3759162900000002
%	POSCAR
Direct mode coordinate
Preconditioner	MIXPRE

2.	The difference of VASP and Octopus
Octopus	VASP
You can customize periodic dimension with PeriodicDimensions, which will use different solver. The lattice of aperiodic dimension is not used in calculation. Theoretically, there is no need to use large size of vacuum. But 10 A vacuum used in the example to generate real-space grid and determine the reduced coordinates of atoms. And the potential cutoff is default to set as double size of the lattice parameter.
Need to carefully set the coordinates of the atoms along the aperiodic directions, which must be centered around 0.	Periodic of all 3 dimensions. Using a large size of vacuum to eliminate the interaction between atoms of far distance
ConvRelDens[1e-6]: convergence criterion of density. 	EDIFF: convergence criterion of energy.
BoxShape: parallelepiped for periodic systems; More choices are available.	Do not have this choice
%LatticeParameters
 lx | ly | lz
% set the total length of lattice parameters 	Do not have this parameter
% Spacing
lx/6 | ly/8 | lx/16
% set the mess density because Octopus integral in the real space	VASP has LREAL to choose whether project to real space. Not recommended for small unit cell.
%Species
"Ga" | species_pseudo | file | "Ga.psp8"
"N" | species_pseudo | file | "N.psp8"
% Set the normalized pseudopotential, download from abinit/QE, or create with generator	Do not have this parameter. VASP use PAW
FilterPotentials: filter the pseudopotentials so that they no longer contain Fourier components larger than the mesh itself. This is very useful to decrease the egg-box effect, and so should be used in all instances where atoms move	Do not have this parameter

