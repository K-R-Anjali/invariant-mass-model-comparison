# Breakdown of Gaussian Assumptions Near Kinematic Boundaries

**A Comparative Study of Truncated Gaussian and Crystal Ball Models**

This repository contains the analysis code and simulation configurations used to study the breakdown of Gaussian assumptions in invariant mass distributions near kinematic boundaries. The project focuses on the invariant mass reconstruction of electron pairs ($e^+e^-$) in high energy physics analyses, demonstrating how standard Gaussian models fail when subjected to hard selection cuts (like trigger thresholds) and how the Truncated Gaussian model provides a physically consistent alternative.

## 👥 Authors
- **K Anjali Ranjith** - *Department of Physics, IIT Hyderabad* (PH24MSCST11014@iith.ac.in)
- **Reddy Rewat** - *Energy Science and Technology, IIT Hyderabad* (GS25MTECH14304@iith.ac.in)

## 📌 Abstract
In high energy physics analyses, invariant mass distributions are routinely modeled using Gaussian functions under the assumption of symmetric detector resolution. This assumption breaks down in the presence of selection cuts, such as trigger thresholds, which introduce asymmetric truncations. 

We present a systematic study using the Delphes fast-simulation framework, spanning mass hypotheses from 1 to 10 GeV. We fit three statistical models:
1. **Standard Gaussian**
2. **Truncated Gaussian**
3. **Crystal Ball Function**

We compare their performance using $\chi^2/\text{NDF}$, Akaike Information Criterion (AIC), and Bayesian Information Criterion (BIC). Results show that while all models perform comparably in the symmetric 2-6 GeV range, the standard Gaussian fails catastrophically near the 6.5 GeV and 1 GeV boundaries. The Truncated Gaussian successfully handles the asymmetric boundary conditions, providing significantly improved fit quality.

## ⚙️ Prerequisites and Dependencies
To reproduce the analysis and run the fitting scripts, you will need the following frameworks installed:
- **[MadGraph5_aMC@NLO](https://launchpad.net/mg5amcnlo)** - Matrix-element event generator (used for generating the initial $e^+e^-$ Monte Carlo samples).
- **[Delphes 3](https://cp3.irmp.ucl.ac.be/projects/delphes)** - Modular framework for fast simulation of a generic collider experiment.
- **[ROOT](https://root.cern/)** (compiled with `RooFit` support) - Object-oriented data analysis framework.


## 🚀 Running the Analysis

The main analysis macro is implemented in ROOT using `RooFit`. 

To execute the macro, run the following command in your terminal:
```bash
root -l -b -q trigger_massfit_modelcomparison.C
```

### What the script does:
1. Reads the simulated Delphes ROOT files.
2. Applies offline kinematic selections (e.g., $p_T^e > 4$ GeV, $|\eta| < 1.2$, $1 < M_{ee} < 6.5$ GeV).
3. Constructs the invariant mass histograms.
4. Performs maximum likelihood fits using the three statistical models.
5. Automatically generates output plots and saves fit summary statistics (including $\chi^2/\text{NDF}$, AIC, and BIC) as a CSV file to the output directory.

## 📁 Repository Structure
- `trigger_massfit_modelcomparison.C` : Main ROOT macro performing the event selection and statistical fits.
- `trigger_massfit_modelcomparison_output/` : Directory containing the auto-generated output histograms and summary CSVs.
- `ieee_draft.tex` : The LaTeX source code for the formal write-up of our methodology and findings.
- `Output images/` : Directory containing high-resolution fit plots and resolution/efficiency graphs used in the paper.

## 📈 Key Findings
- **2-6 GeV Range**: All models perform well. Detector resolution $\sigma$ scales linearly.
- **Boundary Proximity (6.5 GeV)**: Standard Gaussian $\chi^2/\text{NDF}$ spikes catastrophically ($\sim 1460$). Truncated Gaussian $\chi^2/\text{NDF}$ drops by a factor of 5, accurately modeling the physical boundary.
- **Crystal Ball**: Not statistically preferred in either regime for modeling trigger-induced truncations.
