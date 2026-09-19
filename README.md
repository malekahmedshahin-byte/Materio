<div align="center">

# MATERIO

### AI-Driven Inverse Design Engine for Advanced Composite Materials

A computational framework for mapping target mechanical performance to optimal constituent formulations, fiber geometry, and manufacturing pre-treatments.

[Documentation](#system-architecture) | [Quick Start](#quick-start) | [Dataset Specs](#dataset-specifications) | [License](#license)

<br/>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-0052CC.svg?style=for-the-badge&logo=python&logoColor=white" alt="Python 3.10+" />
  <img src="https://img.shields.io/badge/ML-PyTorch%20%7C%20XGBoost-FF6F00.svg?style=for-the-badge" alt="Machine Learning" />
  <img src="https://img.shields.io/badge/Dataset-200K%20Samples-008050.svg?style=for-the-badge" alt="Dataset" />
  <img src="https://img.shields.io/badge/Architecture-Inverse%20Surrogate-6F42C1.svg?style=for-the-badge" alt="Architecture" />
  <img src="https://img.shields.io/badge/License-MIT-CC0000.svg?style=for-the-badge" alt="License" />
</p>

---

</div>

## Executive Summary

Materio replaces conventional trial-and-error physical prototyping with an inverse computational pipeline. By utilizing a dual-dataset synthetic engine comprising 200,000 calibrated micromechanical records, Materio predicts material composition and process parameters directly from user-specified physical targets.

```mermaid
graph LR
    subgraph Inputs["Target Physical Requirements"]
        A[Target Modulus]
        B[Target Tensile Strength]
        C[Max Composite Density]
    end

    subgraph Engine["Materio Inverse Engine"]
        D[Surrogate Model Lookup]
    end

    subgraph Outputs["Computed Recipe Parameters"]
        E[Fiber Type & Polymer Matrix]
        F[Volume Fraction & Fiber Angle]
        G[Alkali Soak Duration & Fiber Length]
    end

    Inputs --> Engine --> Outputs


System Architecture:

graph TD
    A[Target Mechanical Inputs: Modulus, Strength, Density] --> B[Preprocessing & Feature Normalization]
    B --> C[Surrogate ML Inverse Engine]
    
    C --> D{Material Domain Classification}
    
    D -->|Bio-Composite Path| E[Jute Optimization Model]
    D -->|Advanced Synthetic Path| F[Glass / Carbon Optimization Model]
    
    E --> G[Constituent & Process Recipe Output]
    F --> G
    
    G --> H[Manufacturing Workflow & Recipe Generation]

<details>
<summary><b>Click to expand System Core Workflow Breakdown</b></summary>
Target Specification: User inputs structural constraints (E_c, \sigma_c, \rho_c).
Surrogate Search Space: The model queries high-dimensional surrogate response surfaces generated via modified Cox-Krenchel and Halpin-Tsai micromechanics.
Parametric Resolution: Outputs the required fiber volume fraction (V_f), orientation angle (\theta), fiber length (L_f), matrix polymer class, and chemical treatment duration (t_{alkali}).
Recipe Synthesis: Generates automated step-by-step pre-treatment instructions.
</details>
Dataset Specifications
Materio is powered by a high-density, two-tier synthetic dataset containing 200,000 samples generated using physical micromechanics formulations and Gaussian noise injection.

Subset IdentifierSample CountPrimary FiberMatrix SelectionKey Features & Constraints
Bio-Composite80,000Jute FiberPP, PLAV_f: 10–50%, Alkali Duration: 0–8 hrs, Fiber Length: 1–10 mm
Advanced Composite120,000Glass, CarbonPEEK, Epoxy, PLAV_f: 15–75%, Fiber Angle: 0\text{--}90^\circ, Fiber Length: 2–15 mm

<details>
<summary><b>Click to view Data Features & Schema</b></summary>
Feature ColumnData TypeValue Range / CategoriesDescription
Fiber_TypeCategoricalJute Fiber, Glass, CarbonReinforcement material type
Polymer_ClassCategoricalPP Polymer, PLA, PEEK (Medical), EpoxyMatrix polymer base
Fiber_Volume_FractionFloat0.1000 - 0.7500Volume ratio of fiber to total composite
Fiber_Length_mmFloat1.00 - 15.00Chopped fiber length in millimeters
Alkali_Treatment_HoursFloat0.0 - 8.0Chemical wash soak duration (NaOH)
Fiber_Angle_degFloat0.0 - 90.0Fiber alignment relative to load axis
Matrix_Modulus_GPaFloat1.50 - 3.80Elastic modulus of unreinforced polymer
Target_Modulus_GPaFloatContinuous TargetDesired composite elastic modulus
Target_Strength_MPaFloatContinuous TargetDesired composite tensile strength
Composite_Density_gccFloatContinuous TargetFinal composite mass density

</details>
Theoretical Micromechanics Base
The synthetic generation engine incorporates physical orientation and length efficiency factors to calibrate prediction boundaries.
Elastic Modulus Prediction
E_c = \eta_o \eta_l E_f V_f + E_m (1 - V_f)

Where:
\eta_o = \cos^4(\theta) + K_{transverse} represents the Krenchel orientation factor.
E_f and E_m denote fiber and matrix elastic moduli, respectively.
V_f is the fiber volume fraction.
Chemical Surface Modification Factor
For natural plant fibers, interfacial bond strength is modeled as a non-linear function of alkali soaking time:



Interactive Feature Matrix
<details>
<summary><b>View Supported Polymer Matrix Properties</b></summary>
Polymer ClassModulus (GPa)Density (g/cc)Typical Application
Polypropylene (PP)1.500.91Lightweight Bio-Composites
Polylactic Acid (PLA)2.001.24Biodegradable Structures
Epoxy System3.201.15Structural Aerospace/Automotive
PEEK (Medical Grade)3.801.30High-Performance Medical Implants

</details>
<details>
<summary><b>View Supported Reinforcement Fiber Types</b></summary>

Fiber TypeModulus (GPa)Tensile Strength (MPa)Density (g/cc)
Jute Fiber25.0320–4501.45
E-Glass Fiber72.022002.54
Carbon Fiber230.040001.78
</details>
Project Repository Layout
graph TD
    Root[materio/] --> Data[data/]
    Root --> Src[src/]
    Root --> Notebooks[notebooks/]

    Data --> JuteCSV[jute_composite_dataset_80k.csv]
    Data --> AdvCSV[advanced_composite_dataset_120k.csv]
    Data --> CombCSV[materio_dataset_200k.csv]

    Src --> GenData[generate_datasets.py]
    Src --> Models[inverse_solver.py]

    Notebooks --> EDA[01_eda.ipynb]
    Notebooks --> Train[02_train.ipynb]

License
This project is licensed under the MIT License - see the LICENSE file for details.

