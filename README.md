<div align="center">

<img src="https://lh3.googleusercontent.com/d/1k9R-ev4AdtHP-sPLX_5h1TIaQg35ZtSX" width="120" style="border-radius: 24px;" alt="Materio App Icon"/>

# MATERIO

### AI-Driven Inverse Design Engine for Advanced Composite Materials

A mobile computational framework for mapping target mechanical performance to optimal constituent formulations, fiber geometry, and manufacturing pre-treatments.

<br/>

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Android%20APK-3DDC84.svg?style=for-the-badge&logo=android&logoColor=white" alt="Android APK" />
  <img src="https://img.shields.io/badge/ML-PyTorch%20%7C%20XGBoost-FF6F00.svg?style=for-the-badge" alt="Machine Learning" />
  <img src="https://img.shields.io/badge/Dataset-200K%20Samples-008050.svg?style=for-the-badge" alt="Dataset" />
  <img src="https://img.shields.io/badge/Architecture-Inverse%20Surrogate-6F42C1.svg?style=for-the-badge" alt="Architecture" />
  <img src="https://img.shields.io/badge/License-MIT-CC0000.svg?style=for-the-badge" alt="License" />
</p>

</div>

---

## Executive Summary

Materio replaces conventional trial-and-error physical prototyping with an inverse computational pipeline. By utilizing a dual-dataset synthetic engine comprising 200,000 calibrated micromechanical records, Materio predicts material composition and process parameters directly from user-specified physical targets.

<br/>

<table width="100%">
  <tr>
    <td align="center" width="33%"><b>80,000 Samples</b><br/><sub>Bio-Composite (Jute)</sub></td>
    <td align="center" width="33%"><b>120,000 Samples</b><br/><sub>Advanced Synthetic (Glass/Carbon)</sub></td>
    <td align="center" width="33%"><b>~50% Physical Accuracy</b><br/><sub>Calibrated Baseline</sub></td>
  </tr>
</table>

<br/>

<table width="100%">
  <thead>
    <tr>
      <th width="30%" align="center">1. Target Physical Inputs</th>
      <th width="10%" align="center">➔</th>
      <th width="30%" align="center">2. Materio Inverse Engine</th>
      <th width="10%" align="center">➔</th>
      <th width="30%" align="center">3. Computed Recipe Outputs</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>• Target Modulus<br/>• Target Tensile Strength<br/>• Max Composite Density</td>
      <td align="center">➔</td>
      <td align="center"><b>Surrogate Model Lookup & Domain Optimization</b></td>
      <td align="center">➔</td>
      <td>• Fiber Type & Polymer Matrix<br/>• Volume Fraction & Fiber Angle<br/>• Alkali Soak Duration & Fiber Length</td>
    </tr>
  </tbody>
</table>

---

## Download App & Screenshots

Directly download and install the Materio Android Application (APK) on your device to calculate composite material recipes on the go.

<br/>

<div align="center">

### 📱 Application Screenshots

<table width="100%">
  <tr>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1RMG8wrCch8u1VwA4nzIMl4RU3921x-B7" width="100%" alt="Materio Screen 1"/></td>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1u_EzmHTJtB9i8o9pAIxAWm25ZDMvRg5G" width="100%" alt="Materio Screen 2"/></td>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1Fhz_IeHLHc2RooA70Lz9zA_0GD63twUN" width="100%" alt="Materio Screen 3"/></td>
  </tr>
  <tr>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1zv2zcJQ-ksvcGdDUBNv5UMhvtVCkl4bB" width="100%" alt="Materio Screen 4"/></td>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1EMkLWcxvkGSsSqcb_FLUeZ4MIZ0nSE-V" width="100%" alt="Materio Screen 5"/></td>
    <td align="center" width="33%"><img src="https://lh3.googleusercontent.com/d/1j6cr2DGAZD399rRC6uLIQQzWHSF4blTW" width="100%" alt="Materio Screen 6"/></td>
  </tr>
</table>

<br/>

### 📥 Direct APK Download

[<img src="https://img.shields.io/badge/Download-Materio%20APK-008050?style=for-the-badge&logo=android&logoColor=white" height="45" />](https://apkpure.com/materio/com.abdulmalek.nty)

<sub>Direct APK Download Link: [https://apkpure.com/materio/com.abdulmalek.nty](https://apkpure.com/materio/com.abdulmalek.nty)</sub>

</div>

---

## System Architecture

<table width="100%">
  <tr>
    <td align="center"><b>Input: Target Mechanical Inputs</b> (Modulus, Strength, Density)</td>
  </tr>
  <tr><td align="center">↓</td></tr>
  <tr>
    <td align="center"><b>Preprocessing & Feature Normalization</b></td>
  </tr>
  <tr><td align="center">↓</td></tr>
  <tr>
    <td align="center"><b>Surrogate ML Inverse Engine</b></td>
  </tr>
  <tr><td align="center">↓</td></tr>
  <tr>
    <td align="center"><b>Material Domain Classification</b></td>
  </tr>
  <tr>
    <td>
      <table width="100%">
        <tr>
          <td width="50%" align="center"><b>Bio-Composite Path</b><br/>➔ Jute Optimization Model</td>
          <td width="50%" align="center"><b>Advanced Synthetic Path</b><br/>➔ Glass / Carbon Optimization Model</td>
        </tr>
      </table>
    </td>
  </tr>
  <tr><td align="center">↓</td></tr>
  <tr>
    <td align="center"><b>Constituent & Process Recipe Output</b></td>
  </tr>
  <tr><td align="center">↓</td></tr>
  <tr>
    <td align="center"><b>Manufacturing Workflow & Recipe Generation</b></td>
  </tr>
</table>

<br/>

<details>
<summary><b>Click to expand System Core Workflow Breakdown</b></summary>

<br/>

1. **Target Specification:** User inputs structural constraints (E<sub>c</sub>, σ<sub>c</sub>, ρ<sub>c</sub>).
2. **Surrogate Search Space:** The model queries high-dimensional surrogate response surfaces generated via modified Cox-Krenchel and Halpin-Tsai micromechanics.
3. **Parametric Resolution:** Outputs the required fiber volume fraction (V<sub>f</sub>), orientation angle (θ), fiber length (L<sub>f</sub>), matrix polymer class, and chemical treatment duration (t<sub>alkali</sub>).
4. **Recipe Synthesis:** Generates automated step-by-step pre-treatment instructions.

</details>

---

## Dataset Specifications

Materio is powered by a high-density, two-tier synthetic dataset containing 200,000 samples generated using physical micromechanics formulations and Gaussian noise injection.

<table width="100%">
  <thead>
    <tr>
      <th>Subset Identifier</th>
      <th align="center">Sample Count</th>
      <th>Primary Fiber</th>
      <th>Matrix Selection</th>
      <th>Key Features & Constraints</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Bio-Composite</b></td>
      <td align="center">80,000</td>
      <td>Jute Fiber</td>
      <td>PP, PLA</td>
      <td>Volume Fraction: 10–50%, Alkali Duration: 0–8 hrs, Fiber Length: 1–10 mm</td>
    </tr>
    <tr>
      <td><b>Advanced Composite</b></td>
      <td align="center">120,000</td>
      <td>Glass, Carbon</td>
      <td>PEEK, Epoxy, PLA</td>
      <td>Volume Fraction: 15–75%, Fiber Angle: 0–90 deg, Fiber Length: 2–15 mm</td>
    </tr>
  </tbody>
</table>

<br/>

<details>
<summary><b>Click to view Data Features & Schema</b></summary>

<br/>

<table width="100%">
  <thead>
    <tr>
      <th>Feature Column</th>
      <th>Data Type</th>
      <th>Value Range / Categories</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>Fiber_Type</b></td><td>Categorical</td><td>Jute Fiber, Glass, Carbon</td><td>Reinforcement material type</td></tr>
    <tr><td><b>Polymer_Class</b></td><td>Categorical</td><td>PP Polymer, PLA, PEEK (Medical), Epoxy</td><td>Matrix polymer base</td></tr>
    <tr><td><b>Fiber_Volume_Fraction</b></td><td>Float</td><td>0.1000 - 0.7500</td><td>Volume ratio of fiber to total composite</td></tr>
    <tr><td><b>Fiber_Length_mm</b></td><td>Float</td><td>1.00 - 15.00</td><td>Chopped fiber length in millimeters</td></tr>
    <tr><td><b>Alkali_Treatment_Hours</b></td><td>Float</td><td>0.0 - 8.0</td><td>Chemical wash soak duration (NaOH)</td></tr>
    <tr><td><b>Fiber_Angle_deg</b></td><td>Float</td><td>0.0 - 90.0</td><td>Fiber alignment relative to load axis</td></tr>
    <tr><td><b>Matrix_Modulus_GPa</b></td><td>Float</td><td>1.50 - 3.80</td><td>Elastic modulus of unreinforced polymer</td></tr>
    <tr><td><b>Target_Modulus_GPa</b></td><td>Float</td><td>Continuous Target</td><td>Desired composite elastic modulus</td></tr>
    <tr><td><b>Target_Strength_MPa</b></td><td>Float</td><td>Continuous Target</td><td>Desired composite tensile strength</td></tr>
    <tr><td><b>Composite_Density_gcc</b></td><td>Float</td><td>Continuous Target</td><td>Final composite mass density</td></tr>
  </tbody>
</table>

</details>

---

## Theoretical Micromechanics Base

The synthetic generation engine incorporates physical orientation and length efficiency factors to calibrate prediction boundaries.

### Elastic Modulus Prediction

> **E<sub>c</sub> = η<sub>o</sub> × η<sub>l</sub> × E<sub>f</sub> × V<sub>f</sub> + E<sub>m</sub> × (1 - V<sub>f</sub>)**

Where:
* **η<sub>o</sub> = cos⁴(θ) + K<sub>transverse</sub>** represents the Krenchel orientation factor.
* **E<sub>f</sub>** and **E<sub>m</sub>** denote fiber and matrix elastic moduli, respectively.
* **V<sub>f</sub>** is the fiber volume fraction.

### Chemical Surface Modification Factor
For natural plant fibers, interfacial bond strength is modeled as a non-linear function of alkali soaking time:

> **f(t<sub>alkali</sub>) = 1.0 + 0.08 × t<sub>alkali</sub> - 0.008 × (t<sub>alkali</sub>)²**

---

## Interactive Feature Matrix

<details>
<summary><b>View Supported Polymer Matrix Properties</b></summary>

<br/>

<table width="100%">
  <thead>
    <tr>
      <th>Polymer Class</th>
      <th align="center">Modulus (GPa)</th>
      <th align="center">Density (g/cc)</th>
      <th>Typical Application</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>Polypropylene (PP)</b></td><td align="center">1.50</td><td align="center">0.91</td><td>Lightweight Bio-Composites</td></tr>
    <tr><td><b>Polylactic Acid (PLA)</b></td><td align="center">2.00</td><td align="center">1.24</td><td>Biodegradable Structures</td></tr>
    <tr><td><b>Epoxy System</b></td><td align="center">3.20</td><td align="center">1.15</td><td>Structural Aerospace/Automotive</td></tr>
    <tr><td><b>PEEK (Medical Grade)</b></td><td align="center">3.80</td><td align="center">1.30</td><td>High-Performance Medical Implants</td></tr>
  </tbody>
</table>

</details>

<br/>

<details>
<summary><b>View Supported Reinforcement Fiber Types</b></summary>

<br/>

<table width="100%">
  <thead>
    <tr>
      <th>Fiber Type</th>
      <th align="center">Modulus (GPa)</th>
      <th align="center">Tensile Strength (MPa)</th>
      <th align="center">Density (g/cc)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td><b>Jute Fiber</b></td><td align="center">25.0</td><td align="center">320–450</td><td align="center">1.45</td></tr>
    <tr><td><b>E-Glass Fiber</b></td><td align="center">72.0</td><td align="center">2200</td><td align="center">2.54</td></tr>
    <tr><td><b>Carbon Fiber</b></td><td align="center">230.0</td><td align="center">4000</td><td align="center">1.78</td></tr>
  </tbody>
</table>

</details>

---

## License

This project is licensed under the MIT License - see the LICENSE file for details.
