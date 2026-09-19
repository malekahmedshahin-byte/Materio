import os
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# ==============================================================================
# 1. JUTE COMPOSITE DATASET GENERATOR (80,000 SAMPLES WITH GAUSSIAN NOISE)
# ==============================================================================
def generate_jute_dataset(n_samples=80000):
    np.random.seed(42)
    v_f = np.random.uniform(0.10, 0.50, n_samples)
    fiber_length = np.random.uniform(1.0, 10.0, n_samples)
    alkali_duration = np.random.uniform(0.0, 8.0, n_samples)
    fiber_angle = np.random.uniform(0, 90, n_samples)
    
    polymers = np.random.choice(['PP Polymer', 'PLA'], size=n_samples, p=[0.65, 0.35])
    matrix_modulus = np.where(polymers == 'PP Polymer', 1.50, 2.00)
    matrix_density = np.where(polymers == 'PP Polymer', 0.91, 1.24)
    
    e_fiber = 25.0
    jute_density = 1.45
    
    treatment_factor = 1.0 + 0.08 * alkali_duration - 0.008 * (alkali_duration ** 2)
    rad_angle = np.radians(fiber_angle)
    eta_o = np.cos(rad_angle) ** 4 + 0.12
    
    modulus_noise = np.random.normal(loc=0.0, scale=0.35, size=n_samples)
    modulus = (eta_o * e_fiber * v_f) + (matrix_modulus * (1 - v_f)) + modulus_noise
    modulus = np.clip(modulus, 1.0, 25.0)
    
    base_strength = 320.0 * treatment_factor
    strength_noise = np.random.normal(loc=0.0, scale=5.0, size=n_samples)
    strength = (eta_o * base_strength * v_f) + (35.0 * (1 - v_f)) + strength_noise
    strength = np.clip(strength, 15.0, 220.0)
    
    density_noise = np.random.normal(loc=0.0, scale=0.02, size=n_samples)
    density = (v_f * jute_density) + ((1 - v_f) * matrix_density) + density_noise
    density = np.clip(density, 0.8, 2.0)
    
    return pd.DataFrame({
        'Fiber_Type': 'Jute Fiber',
        'Polymer_Class': polymers,
        'Fiber_Volume_Fraction': np.round(v_f, 4),
        'Fiber_Length_mm': np.round(fiber_length, 2),
        'Alkali_Treatment_Hours': np.round(alkali_duration, 1),
        'Fiber_Angle_deg': np.round(fiber_angle, 1),
        'Matrix_Modulus_GPa': np.round(matrix_modulus, 2),
        'Target_Modulus_GPa': np.round(modulus, 2),
        'Target_Strength_MPa': np.round(strength, 2),
        'Composite_Density_gcc': np.round(density, 2)
    })

# ==============================================================================
# 2. ADVANCED COMPOSITE DATASET GENERATOR (120,000 SAMPLES WITH GAUSSIAN NOISE)
# ==============================================================================
def generate_advanced_dataset(n_samples=120000):
    np.random.seed(101)
    fiber_types = np.random.choice(['Glass', 'Carbon'], size=n_samples, p=[0.75, 0.25])
    v_f = np.random.uniform(0.15, 0.75, n_samples)
    fiber_length = np.random.uniform(2.0, 15.0, n_samples)
    fiber_angle = np.random.uniform(0, 90, n_samples)
    
    polymers = np.random.choice(['PEEK (Medical)', 'Epoxy', 'PLA'], size=n_samples, p=[0.45, 0.35, 0.20])
    
    matrix_mod_map = {'PEEK (Medical)': 3.80, 'Epoxy': 3.20, 'PLA': 2.00}
    matrix_den_map = {'PEEK (Medical)': 1.30, 'Epoxy': 1.15, 'PLA': 1.24}
    
    matrix_modulus = np.vectorize(matrix_mod_map.get)(polymers)
    matrix_density = np.vectorize(matrix_den_map.get)(polymers)
    
    fiber_modulus = np.where(fiber_types == 'Glass', 72.0, 230.0)
    fiber_strength = np.where(fiber_types == 'Glass', 2200.0, 4000.0)
    fiber_density = np.where(fiber_types == 'Glass', 2.54, 1.78)
    
    rad_angle = np.radians(fiber_angle)
    eta_o = np.cos(rad_angle) ** 4 + 0.05
    
    modulus_noise = np.random.normal(loc=0.0, scale=0.75, size=n_samples)
    modulus = (eta_o * fiber_modulus * v_f) + (matrix_modulus * (1 - v_f)) + modulus_noise
    modulus = np.clip(modulus, 1.5, 180.0)
    
    strength_noise = np.random.normal(loc=0.0, scale=12.0, size=n_samples)
    strength = (eta_o * fiber_strength * v_f * 0.12) + (45.0 * (1 - v_f)) + strength_noise
    strength = np.clip(strength, 20.0, 700.0)
    
    density_noise = np.random.normal(loc=0.0, scale=0.03, size=n_samples)
    density = (v_f * fiber_density) + ((1 - v_f) * matrix_density) + density_noise
    density = np.clip(density, 1.0, 3.0)
    
    return pd.DataFrame({
        'Fiber_Type': fiber_types,
        'Polymer_Class': polymers,
        'Fiber_Volume_Fraction': np.round(v_f, 4),
        'Fiber_Length_mm': np.round(fiber_length, 2),
        'Alkali_Treatment_Hours': 0.0,
        'Fiber_Angle_deg': np.round(fiber_angle, 1),
        'Matrix_Modulus_GPa': np.round(matrix_modulus, 2),
        'Target_Modulus_GPa': np.round(modulus, 2),
        'Target_Strength_MPa': np.round(strength, 2),
        'Composite_Density_gcc': np.round(density, 2)
    })

# ==============================================================================
# 3. VISUALIZATION GENERATOR
# ==============================================================================
def generate_visuals(df, filename='materio_dataset_visualization.png'):
    sns.set_theme(style="whitegrid")
    fig, axes = plt.subplots(2, 2, figsize=(14, 10))
    
    sns.scatterplot(
        data=df.sample(5000, random_state=42),
        x='Target_Modulus_GPa',
        y='Target_Strength_MPa',
        hue='Fiber_Type',
        alpha=0.6,
        ax=axes[0, 0]
    )
    axes[0, 0].set_title('Target Modulus vs Tensile Strength')
    
    sns.kdeplot(
        data=df,
        x='Composite_Density_gcc',
        hue='Fiber_Type',
        fill=True,
        common_norm=False,
        ax=axes[0, 1]
    )
    axes[0, 1].set_title('Density Distribution by Fiber Type')
    
    sns.boxplot(
        data=df,
        x='Polymer_Class',
        y='Target_Modulus_GPa',
        hue='Fiber_Type',
        ax=axes[1, 0]
    )
    axes[1, 0].set_title('Target Modulus across Polymer Classes')
    
    sns.scatterplot(
        data=df[df['Fiber_Type'] == 'Jute Fiber'].sample(2000, random_state=42),
        x='Alkali_Treatment_Hours',
        y='Target_Strength_MPa',
        hue='Fiber_Volume_Fraction',
        palette='viridis',
        ax=axes[1, 1]
    )
    axes[1, 1].set_title('Alkali Soaking Duration vs Strength (Jute)')
    
    plt.tight_layout()
    plt.savefig(filename, dpi=300)
    plt.close()

# ==============================================================================
# 4. README GENERATOR (AUTOMATED FILE CREATION WITHOUT EMOJIS OR UNICODE ART)
# ==============================================================================
def create_readme_file():
    readme_content = """<div align="center">

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
