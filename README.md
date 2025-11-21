#  AstroLab Data Analysis  
*A hands-on toolkit for data-driven astrophysics using real astronomical datasets*

![Zewail City Logo](Final/Zewail-City.png)

This repository presents a suite of Jupyter notebooks developed as part of the **Observational Astrophysics Laboratory** course at **Zewail City of Science and Technology**. Each notebook applies modern data analysis techniques to real observations from major astronomical surveys—primarily **Gaia DR3**, **SDSS**, and **Hipparcos**—to explore core concepts in stellar kinematics, galactic structure, galaxy photometry, and cosmology.

Designed for students, researchers, and enthusiasts, this project bridges theoretical astrophysics with practical computational analysis.


## Requirements

To run the notebooks, ensure you have a Python environment with the following packages:

```plaintext
numpy
pandas
matplotlib
seaborn
scipy
astropy
astroquery
xlrd          # for .xls file support
scikit-learn  # for regression in Hubble notebooks
```

> *Notebooks may also reference FITS files and CSV datasets included in the repository.*
## Notebooks Overview

| Notebook | Key Focus | Data Source |
|--------|----------|-------------|
| **`MilkyWay’s Galactic Disk Struc.ipynb`** | Vertical scale height of the Milky Way thin disk using Red Clump stars | Gaia DR3 |
| **`ADQL query + Bonus.ipynb`** | Querying Gaia DR3 via ADQL and basic astrometric analysis | Gaia DR3 |
| **`Hubble I.ipynb`** | Cepheid variables as standard candles; synthetic Hubble diagram | Simulated data |
| **`Hubble II.ipynb`** | Empirical estimation of the Hubble Constant using real galaxy data | Classic cosmology dataset |
| **`Pleiades and Hyades.ipynb`** | HR diagrams, distance modulus, and relative cluster ages | Hipparcos |
| **`Hyades.ipynb`** | Moving cluster parallax method vs. trigonometric parallax | Hipparcos |
| **`Galaxy Photometric & Stellar Kinematics I.ipynb`** | Surface brightness profile, scale length, and Tully–Fisher relation for M101 | M101 observational data |
| **`Galaxy Photometric & Stellar Kinematics II.ipynb`** | Schechter Luminosity Function with $V_{\text{max}}$ correction | SDSS |
| **`MilkyWay Galaxy Stellar Kinematics.ipynb`** | Vertical velocity dispersion ($\sigma_W$) across stellar populations | Gaia DR3 |
| **`Milky WayGalaxy’s Spectral Types.ipynb`** | Spatial distribution of O-type vs. G-type stars | SIMBAD |

Each notebook includes:
- Clear objectives and physical motivation  
- Step-by-step data processing  
- Visualizations (CMDs, HR diagrams, Hubble plots, Aitoff projections, etc.)  
- Physical interpretation and error analysis where applicable  

##  Educational Context

This work was completed as part of the **Observational Astrophysics Laboratory** course (PEU327) at **Zewail City of Science and Technology**, under the supervision of course instructors. The notebooks reflect a blend of classical astrophysical methods and modern computational workflows, emphasizing reproducibility and critical thinking.

---

## Acknowledgements

- **Zewail City of Science and Technology** for academic support and infrastructure.  
- **ESA’s Gaia mission**, **SDSS Collaboration**, and **Hipparcos Catalog** for publicly available, high-quality astronomical data.  
- **Astropy** and **astroquery** communities for enabling open, reproducible astronomy.

---

## License

This project is for educational and research purposes. Unless otherwise specified, all code and notebooks are licensed under the **MIT License**—feel free to use, adapt, and share with proper attribution.

> **Author**: Hazem Mohamed  
> **Affiliation**: B.Sc. in Physics (High-Energy Physics) with Minor in Information Engineering, Zewail City  
> **Contact**: s-hazem.elhakim@zewailcity.edu.eg  
