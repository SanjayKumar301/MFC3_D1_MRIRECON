# MFC3_AIE24_D1_MRIRECON

## An Accelerated Alternating Direction Method of Multipliers (ADMM) for MRI Reconstruction with Total Variation Regularisation

> **Course:** 22MAT220 – Mathematics for Computing 3  
> **Semester:** 3 | **Batch:** AIE 2024 | **Group:** D-1

---

##  Team Members

| Name | Roll Number |
|---|---|
| Arjun | CB.SC.U4AIE24305 |
| Dhakshin N | CB.SC.U4AIE24313 |
| Sanjay Kumar S | CB.SC.U4AIE24354 |
| Kneev S Jain | CB.SC.U4AIE24364 |

---

##  Project Overview

Magnetic Resonance Imaging (MRI) is one of the most powerful non-invasive medical imaging techniques for visualizing internal structures of the human body — especially soft tissues. However, a major limitation of MRI is its **slow data acquisition process**, requiring a large amount of frequency-domain data (k-space) to be collected. Long acquisition times lead to patient discomfort and motion artifacts that reduce image quality.

This project addresses that limitation by implementing a **compressed sensing (CS)** approach combined with an **Accelerated ADMM (Alternating Direction Method of Multipliers)** optimization algorithm. The method enables accurate, high-quality MRI image reconstruction from **undersampled k-space data**, dramatically reducing scan time while preserving structural detail.

**Total Variation (TV) regularization** is applied to suppress noise and artifacts, ensuring sharp edge preservation during reconstruction.

---

##  Problem Statement

- Full k-space sampling is required for high-quality MRI, but it results in long acquisition times.
- Undersampling k-space speeds up the scan but introduces noise, artifacts, and loss of structural detail.
- **Goal:** Reconstruct high-quality MRI images from undersampled k-space data while preserving structural information and minimizing noise.

---

##  Repository Structure

```
MFC3_AIE24_D1_MRIRECON/
│
├── Project.mlx               # Main MATLAB Live Script — full ADMM reconstruction pipeline
├── DATASET.mlx               # Dataset loading and preprocessing script
│
├── Papers/                   # Reference papers used in this project
│   ├── Base Paper.pdf        # Primary reference paper
│   ├── 1705.06869v1.pdf      # arXiv paper on compressed sensing / MRI reconstruction
│   ├── JZZ09.pdf             # Supporting paper on optimization algorithms
│   ├── s11042-016-3770-y.pdf # Springer paper on image reconstruction / signal processing
│   └── s41597-024-03525-4.pdf# Nature Scientific Data — dataset/methodology reference
│
├── PPT.pptx                  # Project presentation slides
├── Project.pdf               # Project report (PDF)
├── Analog Computing Report.pdf # Supplementary report on Damped Harmonic Oscillator (analog computing)
└── README.md                 # This file
```

---

##  Dataset

| Property | Details |
|---|---|
| **Dataset** | Modified Shepp–Logan Phantom |
| **Type** | Synthetic MRI phantom |
| **Size** | 256 × 256 pixels |
| **Represents** | Simplified model of the human head with varying tissue densities |

The **Shepp–Logan Phantom** simulates a cross-sectional view of the human brain. It consists of multiple ellipses representing tissues with varying intensities and contrasts. It is widely used as a benchmark in MRI reconstruction research.

---

##  Methodology

### 1. Compressed Sensing (CS)
Instead of collecting the full k-space data, CS exploits the **sparsity** of MRI images in a transform domain (e.g., Total Variation). By using a random undersampling mask, we collect far fewer measurements while still being able to reconstruct the full image.

### 2. ADMM Optimization
The **Alternating Direction Method of Multipliers (ADMM)** is an optimization framework that breaks the reconstruction problem into smaller, more manageable subproblems:
- **S-update:** Updates the image estimate in the frequency domain.
- **T-update:** Applies Total Variation denoising in the image domain.
- **Dual variable update:** Enforces consistency between the two subproblems.

The accelerated version uses **adaptive parameter updates** for faster convergence and greater stability.

### 3. Total Variation (TV) Regularization
TV regularization penalizes the gradient of the image, promoting **piecewise smoothness** while preserving sharp edges — critical for diagnostic MRI image quality.

---

##  How to Run

### Prerequisites
- MATLAB R2022b or later
- Image Processing Toolbox
- Signal Processing Toolbox

### Steps

**Step 1 — Load and Preprocess the Dataset**
```
Open DATASET.mlx in MATLAB and run all sections.
This loads the Shepp–Logan phantom, applies the undersampling mask,
and prepares the k-space data for reconstruction.
```

**Step 2 — Run the Reconstruction Pipeline**
```
Open Project.mlx in MATLAB and run it section by section.
The script will:
  - Load preprocessed k-space data
  - Apply the ADMM reconstruction algorithm
  - Display the sampling mask, zero-filled reconstruction, and ADMM result
  - Plot the ADMM convergence curve
  - Compute evaluation metrics (PSNR, SSIM)
```

**Step 3 — View Results**
The output visualizes three images side by side:
- **Ground Truth** — the original phantom
- **Zero-Filled** — naive reconstruction from undersampled data
- **ADMM Reconstruction** — the result from our algorithm

---

##  Results

The ADMM reconstruction significantly outperforms the zero-filled baseline, recovering structural detail lost due to undersampling. The convergence plot confirms stable and rapid convergence of the algorithm across iterations.

---

##  References

| Paper | Description |
|---|---|
| Base Paper | Primary reference forming the foundation of the MRI reconstruction approach |
| 1705.06869v1 | arXiv paper on compressed sensing and MRI reconstruction |
| JZZ09 | Supporting paper on optimization algorithms |
| s11042-016-3770-y | Springer — image reconstruction and signal processing in MRI |
| s41597-024-03525-4 | Nature Scientific Data — dataset and methodology validation |

---

##  Additional Report

The **Analog Computing Report** documents a supplementary project on solving a **Damped Harmonic Oscillator** ODE using an analog computer circuit built with LM741 operational amplifiers. The circuit was powered and visualized using the **ADALM2000 (M2K)** and Scopy software. This demonstrates the mathematical connection between differential equations, signal processing, and physical circuit design.

---

*Submitted as part of 22MAT220 – Mathematics for Computing 3 | Amrita Vishwa Vidyapeetham*
