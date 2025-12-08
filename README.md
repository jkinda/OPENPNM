# OPENPNM - Pore Network Modeling Studies

A collection of Jupyter notebooks for pore network modeling simulations using OpenPNM framework.

## 📋 Overview

This repository contains computational studies on porous media transport phenomena using the [OpenPNM](https://openpnm.org/) (Open Pore Network Modeling) Python package. OpenPNM is a comprehensive framework for performing pore network simulations of porous materials, enabling the prediction of transport properties and multiphase flow behavior.

## 🎯 Purpose

The notebooks in this repository explore:
- Permeability and transport property calculations in porous media
- Mercury intrusion porosimetry (MIP) simulations
- Drainage and imbibition processes
- Single and multiphase flow in pore networks
- Diffusion and advection-diffusion transport
- Network extraction from imaging data

## 📁 Repository Structure

```
OPENPNM/
├── notebooks/          # Jupyter notebooks with simulations and analyses
├── data/              # Input data files (images, networks, experimental data)
└── README.md          # This file
```

## 🔧 Installation

### Prerequisites

- Python 3.8 or higher
- Anaconda or Miniconda (recommended)

### Setup Instructions

1. **Clone this repository:**
   ```bash
   git clone https://github.com/jkinda/OPENPNM.git
   cd OPENPNM
   ```

2. **Create a conda environment:**
   ```bash
   conda create -n openpnm python=3.10
   conda activate openpnm
   ```

3. **Install OpenPNM and dependencies:**
   ```bash
   conda install -c conda-forge openpnm
   ```
   
   Or using pip:
   ```bash
   pip install openpnm
   ```

4. **Install additional packages:**
   ```bash
   pip install jupyter numpy scipy matplotlib pandas
   ```

5. **Optional - Install PoreSpy for image analysis:**
   ```bash
   conda install -c conda-forge porespy
   ```

## 📓 Notebooks

### Available Notebooks

| Notebook | Description | Key Features |
|----------|-------------|--------------|
| `notebook_name_1.ipynb` | Description of first notebook | - Feature 1<br>- Feature 2 |
| `notebook_name_2.ipynb` | Description of second notebook | - Feature 1<br>- Feature 2 |
| `notebook_name_3.ipynb` | Description of third notebook | - Feature 1<br>- Feature 2 |

> **Note:** Update this table with actual notebook names and descriptions.

### Running the Notebooks

1. **Start Jupyter:**
   ```bash
   jupyter notebook
   ```

2. **Navigate to the `notebooks/` directory**

3. **Open and run any notebook**

## 📊 Example Workflow

A typical pore network modeling workflow includes:

```python
import openpnm as op
import numpy as np

# 1. Create or import network
pn = op.network.Cubic(shape=[10, 10, 10], spacing=1e-4)

# 2. Define geometry
geo = op.geometry.StickAndBall(network=pn, pores=pn.Ps, throats=pn.Ts)

# 3. Define phase properties
water = op.phases.Water(network=pn)

# 4. Define physics
phys = op.physics.Standard(network=pn, phase=water, geometry=geo)

# 5. Run algorithm (e.g., permeability)
perm = op.algorithms.StokesFlow(network=pn, phase=water)
perm.set_value_BC(pores=pn.pores('left'), values=200000)
perm.set_value_BC(pores=pn.pores('right'), values=100000)
perm.run()

# 6. Calculate effective permeability
K_eff = perm.calc_effective_permeability()
print(f'Effective permeability: {K_eff:.3e} m²')
```

## 🧪 Applications

This repository can be adapted for various porous media studies:

### Civil Engineering & Construction Materials
- **Concrete durability:** Chloride penetration, carbonation depth
- **Moisture transport:** Capillary absorption, drying processes
- **Freeze-thaw durability:** Ice formation in pore networks
- **Alkali-silica reaction:** Transport in degraded concrete

### Geotechnical Engineering
- **Soil permeability:** Saturated and unsaturated flow
- **Contaminant transport:** Advection-diffusion in soils
- **Consolidation:** Coupled hydro-mechanical behavior

### Materials Science
- **Battery electrodes:** Ion transport in porous electrodes
- **Fuel cells:** Gas diffusion layers, catalyst layers
- **Membrane technology:** Filtration and separation processes
- **Composite materials:** Resin flow in fiber networks

## 📚 Key Concepts

### Pore Network Model Components

1. **Network Topology:** Defines pore and throat connectivity
2. **Geometry Models:** Pore/throat size distributions, shapes
3. **Phase Properties:** Fluid viscosity, density, surface tension
4. **Physics Models:** Transport mechanisms, capillary pressure
5. **Algorithms:** Percolation, transport solvers, drainage

### Common Algorithms

- **Percolation:** Invasion processes, breakthrough analysis
- **Stokes Flow:** Single-phase permeability calculations
- **Fickian Diffusion:** Diffusive transport
- **Advection Diffusion:** Combined transport mechanisms
- **Reactive Transport:** Chemical reactions in porous media

## 🔬 Data Sources

The `data/` folder contains:
- Pore network structures (extracted or synthetic)
- 3D imaging data (micro-CT, X-ray tomography)
- Experimental validation data
- Material property databases

## 📖 Documentation & Resources

### OpenPNM Resources
- **Official Documentation:** [openpnm.org](https://openpnm.org/)
- **GitHub Repository:** [PMEAL/OpenPNM](https://github.com/PMEAL/OpenPNM)
- **Examples:** [OpenPNM Examples](https://github.com/PMEAL/OpenPNM/tree/dev/examples)
- **Discussions:** [GitHub Discussions](https://github.com/PMEAL/OpenPNM/discussions)

### Scientific Background
- **Pore Network Modeling Review:**
  - Blunt, M.J. et al. (2013). "Pore-scale imaging and modelling." *Advances in Water Resources*, 51, 197-216.
  
- **OpenPNM Package:**
  - Gostick, J. et al. (2016). "OpenPNM: A pore network modeling package." *Computing in Science & Engineering*, 18(4), 60-74. [DOI: 10.1109/MCSE.2016.49](https://doi.org/10.1109/MCSE.2016.49)

### Related Tools
- **PoreSpy:** [Image analysis for porous media](https://github.com/PMEAL/porespy)
- **OpenFOAM:** Direct numerical simulation (DNS)
- **GeoDict:** Commercial pore-scale modeling
- **Palabos:** Lattice Boltzmann simulations

## 🛠️ Troubleshooting

### Common Issues

**Problem:** OpenPNM import fails
```
Solution: Ensure conda environment is activated and OpenPNM is installed:
conda activate openpnm
conda list openpnm
```

**Problem:** Jupyter kernel not found
```
Solution: Install ipykernel in your environment:
conda install ipykernel
python -m ipykernel install --user --name openpnm --display-name "Python (OpenPNM)"
```

**Problem:** Network visualization issues
```
Solution: Install ParaView for advanced visualization:
conda install -c conda-forge paraview
```

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/YourFeature`)
5. Open a Pull Request

### Contribution Guidelines
- Add documentation to new notebooks
- Include references for implemented models
- Test notebooks before submitting
- Use consistent coding style (PEP 8)

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

> **Note:** If using OpenPNM in publications, please cite:
> 
> Gostick, J., Aghighi, M., Hinebaugh, J., Tranter, T., Hoeh, M.A., Day, H., Spellacy, B., Sharqawy, M.H., Bazylak, A., Burns, A., Lehnert, W., and Putz, A. (2016). "OpenPNM: a pore network modeling package." *Computing in Science & Engineering*, 18(4), pp. 60-74. DOI: [10.1109/MCSE.2016.49](https://doi.org/10.1109/MCSE.2016.49)

## 👤 Author

**[Your Name/Username]**
- GitHub: [@jkinda](https://github.com/jkinda)
- Institution: Ecole Polytechniaue de Ouagadougou

## 🙏 Acknowledgments

- The OpenPNM development team at the Porous Materials Engineering and Analysis Lab (PMEAL)
- University of Waterloo, Department of Chemical Engineering
- [Add your funding sources or collaborators]

## 📬 Contact

For questions, suggestions, or collaboration opportunities:
- Open an issue on GitHub
- Contact via email: your.email@example.com

---

**Last Updated:** December 2025

## 🔖 Version History

- **v0.1.0** (2025-12) - Initial repository setup
- Add your version updates here

---

*This repository is for research and educational purposes. Results should be validated against experimental data for engineering applications.*
