# AstroLab Data Analysis

This repository contains a collection of Jupyter notebooks developed for the 'AstroLab Data Analysis' project by Hazem-74. The project explores various fundamental concepts in astronomy and astrophysics, ranging from stellar kinematics and galactic structure to galaxy photometry and cosmological principles, utilizing real astronomical data from missions like Gaia and surveys like SDSS, as well as classic datasets.

## Requirements

To run these notebooks, you will need a Python environment with the following libraries installed:

*   `numpy`
*   `pandas`
*   `matplotlib`
*   `seaborn`
*   `scipy`
*   `astropy`
*   `astroquery`
*   `xlrd` (for reading .xls files)
*   `scikit-learn` (for `sklearn.linear_model.LinearRegression` and `sklearn.preprocessing.StandardScaler` in Hubble I.ipynb)

## Installation

1.  **Clone the repository:**
    First, clone the Hazem-74 repository to your local machine using Git:

    ```bash
    git clone https://github.com/Hazem-74/AstroLab-Data-Analysis.git
    ```

2.  **Navigate to the project directory:**

    ```bash
    cd AstroLab-Data-Analysis
    ```

3.  **Create a virtual environment (recommended):**

    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

4.  **Install the required packages:**

    ```bash
    pip install numpy pandas matplotlib seaborn scipy astropy astroquery xlrd scikit-learn
    ```

## Usage

To run the Jupyter notebooks:

1.  **Start Jupyter Lab or Jupyter Notebook:**

    ```bash
    jupyter lab
    # or
    jupyter notebook
    ```

2.  **Open the desired notebook** (`.ipynb` file) from the Jupyter interface in your web browser.

3.  **Run the cells** sequentially to execute the code and reproduce the analysis and plots.

## Notebook Summaries

Here's a summary of each Jupyter notebook, outlining its purpose, key methods, and main logic:

---

### `MilkyWay’s Galactic Disk Struc.ipynb`

*   **Purpose:** To determine the vertical scale height ($h_z$) of the Milky Way's galactic thin disk using astrometric data from Gaia DR3.
*   **Methods:**
    *   Calculates stellar distances from parallax values.
    *   Computes absolute G-band magnitudes ($M_G$).
    *   Generates Color-Magnitude Diagrams (CMD) for initial stellar population visualization.
    *   Identifies Red Clump (RC) stars using both histogram and Kernel Density Estimation (KDE) approaches to accurately determine their absolute magnitude.
    *   Compares the derived scale height using Main Sequence (MS) stars versus Red Clump (RC) stars.
    *   Fits a linear model to the logarithm of stellar density versus height ($z$) to extract the scale height.
*   **Main Logic:** The stellar density in the thin disk is modeled as an exponential decay with height: $\rho(z) \propto e^{-z/h_z}$. By taking the logarithm, $\log_{10} \rho(z)$ becomes linearly dependent on $z$. The slope of this linear relationship is used to directly calculate $h_z$. Red Clump stars are utilized due to their well-defined intrinsic luminosity, making them excellent standard candles for distance determination and thus reliable tracers of Galactic structure.

---

### `ADQL query + Bonus.ipynb`

*   **Purpose:** To demonstrate how to interact with the Gaia DR3 archive using ADQL (Astronomical Data Query Language) through Python's `astroquery.gaia` module, and perform basic data processing and visualization.
*   **Methods:**
    *   Loads metadata for the `gaiadr3.gaia_source` table.
    *   Constructs and executes an ADQL query to retrieve the top 10 stars with valid astrometric parameters (RA, Dec, parallax, proper motions).
    *   Computes distance and distance error from the parallax values.
    *   Visualizes the retrieved data using a Seaborn pairplot for quick correlational analysis.
*   **Main Logic:** This notebook provides a practical example of accessing large astronomical databases programmatically. It highlights the use of ADQL for precise data selection and demonstrates immediate post-query processing to derive physical quantities like distance, followed by exploratory data analysis.

---

### `Hubble II.ipynb`

*   **Purpose:** To reproduce Hubble's Law by analyzing the relationship between the recession velocities and distances of several galaxies, and to estimate the Hubble Constant ($H_0$).
*   **Methods:**
    *   Uses a predefined dataset of galaxy distances (in Mpc) and recession velocities (in km/s).
    *   Performs linear regression on the (distance, velocity) data points.
    *   Generates a Hubble Diagram, plotting velocity against distance, with the linear fit overlaid.
    *   Calculates and prints the estimated Hubble Constant from the slope of the fit.
*   **Main Logic:** Hubble's Law, $v = H_0 D$, describes the observed linear relationship between a galaxy's recession velocity ($v$) and its distance ($D$). The slope of this relationship directly corresponds to the Hubble Constant ($H_0$), a fundamental parameter in cosmology that describes the expansion rate of the universe.

---

### `Pleiades and Hyades.ipynb`

*   **Purpose:** To construct and compare Hertzsprung-Russell (HR) diagrams for the Pleiades and Hyades open star clusters using Hipparcos catalog data, and to use these diagrams to infer their relative ages and distances, as well as estimate the absolute distance to Pleiades.
*   **Methods:**
    *   Loads stellar data (B-V color index and apparent magnitude) for both the Pleiades and Hyades clusters.
    *   Plots individual HR diagrams for each cluster, and then a combined HR diagram to facilitate comparison.
    *   Generates 2D histogram-based Color-Magnitude Diagrams (CMDs) for higher density visualization.
    *   Applies the distance modulus equation to estimate the distance to Pleiades using a reference star from Hyades with a known absolute magnitude.
*   **Main Logic:** HR diagrams are essential tools for studying stellar evolution. The position of a star on the diagram indicates its evolutionary stage. By comparing the main sequence turn-off points and the apparent magnitude differences for stars of similar intrinsic luminosity, one can determine the relative ages (older clusters have lower turn-off points) and distances (closer clusters appear brighter) between clusters.

---

### `Galaxy Photometric & Stellar Kinematics II.ipynb`

*   **Purpose:** To reproduce the Schechter Luminosity Function (LF) for galaxies using data from the SDSS (Sloan Digital Sky Survey), analyzing properties such as absolute magnitude, maximum observable distance, and the faint-end slope ($\alpha$).
*   **Methods:**
    *   Derives the Schechter Luminosity Function mathematically in magnitude form.
    *   Loads SDSS galaxy data, including redshift and apparent magnitudes.
    *   Calculates distances to galaxies using Hubble's Law ($D = cz/H_0$).
    *   Computes absolute r-band magnitudes ($M_r$) for each galaxy.
    *   Determines the maximum observable distance ($d_{max}$) and corresponding volume ($V_{max}$) for each galaxy, accounting for the survey's apparent magnitude limit.
    *   Constructs the galaxy luminosity function by binning absolute magnitudes and weighting by $1/V_{max}$ to correct for selection biases.
    *   Corrects and marks the characteristic magnitude $M^*$ based on literature values.
    *   Fits a linear model to the faint-end of the luminosity function to estimate the faint-end slope ($\alpha$).
    *   Discusses systematic uncertainties inherent in LF determination (evolutionary effects, surface brightness limits, foreground contamination).
*   **Main Logic:** The Schechter function is a universally accepted model for describing the distribution of galaxy luminosities. By properly correcting for observational biases (like flux limits and survey volume), the notebook reconstructs the true underlying distribution of galaxy luminosities and fits the model parameters, which are crucial for understanding galaxy formation and evolution.

---

### `MilkyWay Galaxy Stellar Kinematics.ipynb`

*   **Purpose:** To analyze the vertical stellar kinematics (W velocity and velocity dispersion) of different stellar populations within the Milky Way, utilizing high-precision astrometric data from Gaia DR3.
*   **Methods:**
    *   Calculates stellar distances from parallax and absolute G-band magnitudes.
    *   Plots a 2D Color-Magnitude Diagram (CMD) to visualize stellar populations.
    *   Computes the vertical velocity component ($W$) for each star, representing its motion perpendicular to the Galactic plane.
    *   Categorizes stars into distinct samples: Main Sequence (MS), Red Giant Branch (RGB), and younger Blue MS stars.
    *   Generates histograms of $W$ velocities for each stellar sample.
    *   Calculates the mean $W$ velocity (an estimate of the Sun's vertical motion relative to these populations) and the velocity dispersion ($\sigma_W$) for the entire dataset and each stellar subgroup.
    *   Compares these kinematic properties across different stellar populations and discusses the implications of age and Galactic heating.
*   **Main Logic:** Stellar kinematics reveals insights into the dynamic processes shaping the Milky Way. Velocity dispersion acts as a tracer of stellar age and the amount of "kinematic heating" stars have experienced from gravitational interactions. Younger, more recently formed stars (like Blue MS) are expected to have lower velocity dispersions and be more confined to the Galactic plane, while older populations (like RGB) show higher dispersions due to longer exposure to gravitational perturbations.

---

### `Galaxy Photometric & Stellar Kinematics I.ipynb`

*   **Purpose:** To conduct a photometric analysis of the Messier 101 (Pinwheel) spiral galaxy, deriving its surface brightness profile, fundamental photometric parameters, and estimating its circular velocity.
*   **Methods:**
    *   Loads B-band surface brightness data ($\mu_B$ in mag/arcsec$^2$) as a function of radius ($r$ in arcminutes) for M101.
    *   Plots the surface brightness profile, inverting the y-axis to represent brighter magnitudes upwards.
    *   Fits a linear model to the logarithm of the brightness profile (representing an exponential disk: $\mu_B(r) = \mu_0 + 1.086 \cdot r/h$).
    *   Calculates the central surface brightness ($\mu_0$), radial scale length ($h$), and the $R_{25}$ radius (where $\mu_B = 25$ mag/arcsec$^2$).
    *   Computes the total apparent B magnitude ($m_{tot,B}$) and central luminosity density ($I_{0,B}$).
    *   Converts the radial scale length to physical units (kpc) and determines the galaxy's absolute B magnitude ($M_B$) and B-band luminosity in solar units.
    *   Estimates the circular velocity ($v_{circ}$) using the empirical Tully-Fisher relation ($M_B = a - b \log_{10}(v_{circ})$).
    *   Calculates the time it would take for a star at $R_{25}$ to move 1 arcsecond due to orbital rotation and contrasts this with historical, erroneous claims of rapid proper motion by van Maanen.
*   **Main Logic:** Spiral galaxies often exhibit an exponential disk surface brightness profile. By fitting this profile, key structural parameters like scale length and central brightness can be derived. These photometric properties are then linked to kinematic properties (like circular velocity) through empirical relations such as the Tully-Fisher relation, providing insights into the galaxy's mass and dynamics. The comparison with van Maanen's claims highlights the precision required in astrometry.

---

### `Milky WayGalaxy’s Spectral Types.ipynb`

*   **Purpose:** To investigate the spatial distribution of different stellar spectral types (specifically O-type and G-type stars) within the Milky Way, utilizing data queried from the SIMBAD astronomical database.
*   **Methods:**
    *   Queries the SIMBAD database for a list of specified stars, retrieving their Right Ascension (RA), Declination (Dec), apparent magnitude ($m_V$), and spectral type.
    *   Calculates Galactic coordinates (longitude $l$ and latitude $b$) from the equatorial coordinates.
    *   Estimates stellar distances using the distance modulus formula (from $m_V$ and provided absolute magnitudes $M_V$).
    *   Generates Aitoff projection plots to visualize the distribution of these stars in both ICRS (equatorial) and Galactic coordinate systems.
    *   Creates histograms of Galactic latitude ($b$) and perpendicular distance from the Galactic plane for O-type and G-type stars.
*   **Main Logic:** Stellar spectral type is a proxy for stellar mass, temperature, and crucially, lifespan. O-type stars are very massive, hot, and short-lived, implying they are typically found in active, young star-forming regions, and thus expected to be closely confined to the Galactic plane. G-type stars (like our Sun) are less massive, much longer-lived, and therefore have had more time to migrate or be dynamically heated, leading to a potentially broader distribution, both in latitude and distance from the plane. The notebook explores these expected differences.

---

### `Hubble I.ipynb`

*   **Purpose:** To analyze hypothetical Cepheid variable star data to illustrate how these "standard candles" are used to determine distances to galaxies, and to visualize the relationship between distance and recession velocity as defined by Hubble's Law.
*   **Methods:**
    *   Loads synthetic data representing mean apparent magnitudes and corresponding distances for a sample of Cepheid variables in various galaxies.
    *   Performs linear and polynomial regression analyses on the (magnitude, distance) relationship, demonstrating different fitting techniques.
    *   Generates a series of plots for comprehensive data visualization: scatter plots, histograms of magnitudes and distances, boxplots, and pairplots (including a version with categorical distance grouping).
    *   Applies Hubble's Law ($v = H_0 d$) using a given Hubble Constant ($H_0$) to calculate recession velocities.
    *   Constructs a Hubble Diagram, plotting recession velocity against distance, with a theoretical Hubble Line.
*   **Main Logic:** Cepheid variable stars are crucial `standard candles` in astronomy; their well-understood period-luminosity relationship allows for precise distance measurements to galaxies up to tens of megaparsecs. These distances, combined with velocities derived from redshift, are fundamental for determining the Hubble Constant and thus the expansion rate and age of the Universe. This notebook focuses on the data analysis and visualization aspects of this cosmological distance ladder.

---

### `Hyades.ipynb`

*   **Purpose:** To determine the convergence point, space velocity vectors, and distances to stars within the Hyades open cluster using the `moving cluster parallax` method, and to compare these results with distances derived from direct trigonometric parallax.
*   **Methods:**
    *   Loads Hipparcos proper motion, radial velocity, and parallax data for Hyades cluster stars.
    *   Converts Right Ascension (RA) and Declination (Dec) to degrees, and proper motions to consistent units.
    *   Simulates the extrapolated trajectories of Hyades stars over a range of time steps to identify a common "convergence point" on the sky, using the mean of final RA and Dec positions.
    *   Calculates the angular separation ($\theta$) between each star's current position and the derived convergence point.
    *   Computes the total proper motion ($\mu_t$) for each star.
    *   Calculates distances to individual stars using the `moving cluster parallax` formula, $d = \frac{v_r \tan\theta}{4.74047 \mu_t}$, along with detailed uncertainty propagation for these distances.
    *   Computes the total space velocities ($V$) for each star.
    *   Compares the derived moving cluster parallax distances ($d_{msc}$) and their uncertainties with distances calculated from trigonometric parallax ($d_{TP} = 1/p$) and their respective uncertainties.
    *   Calculates the average distance and space velocity of the cluster's center of mass and compares these to established literature values (Perryman et al., 1998).
*   **Main Logic:** The `moving cluster parallax` method is a classic technique that exploits the common space motion of stars within a cluster. By projecting their proper motions forward, they appear to converge at a single point on the sky. The geometry of this convergence, combined with radial velocities, allows for direct distance determination. This method historically provided a crucial rung on the cosmic distance ladder, especially before highly accurate trigonometric parallaxes were available for many stars. The notebook compares its effectiveness and precision against modern trigonometric parallax measurements.

---

## Acknowledgements

This project was developed within the context of **Zewail City of Science and Technology**. The presence of the `Zewail-City.png` image in the notebook headers acknowledges this affiliation.
