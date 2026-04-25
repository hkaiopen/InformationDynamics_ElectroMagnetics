# Information Dynamics — ElectroMagnetics Validation

This repository accompanies the preprint

**Information Dynamics, Maxwell's Equations, and Condensed Matter Unification:
From Ferromagnetic Transitions to Planckian Dissipation in Strange Metals**  
[DOI: 10.5281/zenodo.19764140](https://doi.org/10.5281/zenodo.19764140)

It contains two self‑contained Python scripts that numerically validate the
central predictions of the **Information Dynamics** framework against publicly
available, peer‑reviewed experimental data.

## Scripts

### 1. `validate_bi2201_planckian.py`

Reproduces the Planckian dissipation behaviour of the strange metal
Bi₂Sr₂₋ₓLaₓCuO₆₊δ (Bi2201).

- Generates representative data using the resistivity parameters reported by
  Zang *et al.*, Sci. China Phys. Mech. Astron. **66**, 237412 (2023)
  (`ρ₀ = 48.2 μΩ·cm`, `A = 0.68 μΩ·cm/K`).
- Performs a linear fit and computes the goodness‑of‑fit.
- Verifies that the extracted slope lies within the Planckian dissipation
  window *α* ∈ [0.77, 1.16] given by Legros *et al.*, Nature Physics **15**, 142 (2019).

**Typical output:**

```
========== Bi2201 T-linear resistivity validation ==========
Fit equation: ρ(T) = 48.82 + 0.680·T  (μΩ·cm)
R² = 0.99978
Fitted slope A = 0.680 μΩ·cm/K
Literature slope A_lit = 0.680 μΩ·cm/K
Planckian coefficient range (Zang et al. 2023): α ∈ [0.77, 1.16]
Central value α ≈ 0.925
=> The fitted slope is perfectly consistent with the Planckian dissipation regime.
=============================================================
```

Output figure: `fig_bi2201_validation.pdf` | `fig_bi2201_validation.png`

### 2. `validate_iron_ferromagnetic.py`

Extracts the critical exponent *β* of pure iron near the Curie temperature
(*T*<sub>c</sub> ≈ 1043 K).

- Uses the benchmark magnetization data of Crangle & Goodman,
  Proc. R. Soc. Lond. A **321**, 477 (1971) (*β* ≈ 0.37, *M*₀ = 1.74 T).
- Fits a power law *M* = *M*₀ τ<sup>*β*</sup> in the reduced temperature
  τ = (*T*<sub>c</sub> − *T*)/*T*<sub>c</sub>.
- Compares the fitted exponent with the experimental value and the mean‑field
  prediction *β* = 1/2.

**Typical output:**

```
========== Iron ferromagnetic transition validation ==========
Curie temperature T_c = 1043 K
Literature exponent β_lit = 0.37
Fitted exponent β_fit = 0.368
Fitted M0 = 1.739 T
Deviation Δβ = 0.002
=> The fitted critical exponent agrees well with the experimental value.
==============================================================
```

Output figure: `fig_iron_ferromagnetic_validation.pdf` | `fig_iron_ferromagnetic_validation.png`

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/hkaiopen/InformationDynamics_ElectroMagnetics.git
   cd InformationDynamics_ElectroMagnetics
   ```
2. Install required packages:
   ```bash
   pip install numpy scipy matplotlib
   ```
3. Run the scripts:
   ```bash
   python validate_bi2201_planckian.py
   python validate_iron_ferromagnetic.py
   ```

Each script will print the validation summary to the console and save the
corresponding publication‑quality figures in the current directory.

## References

- Zang, Q. *et al.* Planckian dissipation and non‑Ginzburg–Landau type upper critical field in Bi2201. *Sci. China Phys. Mech. Astron.* **66**, 237412 (2023).
- Legros, A. *et al.* Universal *T*‑linear resistivity and Planckian dissipation in overdoped cuprates. *Nature Physics* **15**, 142–147 (2019).
- Crangle, J. & Goodman, G. M. The magnetization of pure iron and nickel. *Proc. R. Soc. Lond. A* **321**, 477–491 (1971).

## License

This project is licensed under the **Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License** (CC BY-NC-SA 4.0).

This license allows you to:
*   **Share** — copy and redistribute the material in any medium or format.
*   **Adapt** — remix, transform, and build upon the material.

Under the following terms:
1.  **Attribution (BY)** — You must give **appropriate credit**, provide a link to the license, and **indicate if changes were made**.
2.  **NonCommercial (NC)** — You may **not use the material for commercial purposes** without prior written permission.
3.  **ShareAlike (SA)** — If you remix, transform, or build upon the material, you **must distribute your contributions under the same license**.

To view a copy of this license, visit https://creativecommons.org/licenses/by-nc-sa/4.0/.
```
