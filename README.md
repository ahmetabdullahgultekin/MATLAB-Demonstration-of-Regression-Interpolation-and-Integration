# MATLAB Demonstration – Regression, Interpolation & Numerical Integration

This repository contains the submission package for **MATH 2059 Numerical Methods – Homework 4**. The assignment explores three classical numerical analysis topics using MATLAB and Excel.

> Author: **Ahmet Abdullah Gültekin**

---

## 📂 Contents

| File | Type | Purpose |
|------|------|---------|
| `HW4.pdf` | PDF | Problem sheet provided by the instructor. |
| `AhmetAbdullah_GÜLTEKİN_150121025_hw_4.xlsx` | Excel workbook | Live MATLAB‑compatible spreadsheets solving each part (regression, interpolation, integration) with embedded charts & formulas. |
| `AhmetAbdullah_GÜLTEKİN_150121025_hw_4_report.docx` | Word report | Step‑by‑step derivations, screenshots of MATLAB outputs, error discussion and conclusion. |

---

## 🧩 Covered Topics

1. **Polynomial & Exponential Regression**  
   * Least‑squares fit via built‑in `polyfit`, `fit` and manual normal‑equations.  
   * R², RMSE comparison between models.
2. **Lagrange & Newton Interpolation**  
   * Construction of the interpolating polynomial for a given data set.  
   * Error bound verification and graphical overlay.
3. **Composite Numerical Integration**  
   * Trapezoidal, Simpson’s 1/3 and Simpson’s 3/8 rules.  
   * Convergence study doubling `n` and comparing to `integral()` ground truth.

Each section in the Excel file has:
* Raw data table.  
* Formula columns (e.g., ∑xi, ∑xi²).  
* Embedded MATLAB code snippets (via `xlswrite` / `readmatrix` in `.m` helper not shared).  
* Automatically updating plots.

---

## 🔧 How to Reproduce in MATLAB
Although the primary calculations are in Excel, you can replicate them in MATLAB:
```matlab
%% Load the same data used in regression
T = readtable('AhmetAbdullah_GÜLTEKİN_150121025_hw_4.xlsx', 'Sheet','Regression');

x = T.x; y = T.y;

%% Polynomial regression of degree 2
p2 = polyfit(x, y, 2);
y_hat = polyval(p2, x);
rmse = sqrt(mean((y - y_hat).^2));
```
For interpolation and integration, copy the node vectors from the corresponding Excel sheets and use `interp1`, `polyint`, `trapz`, etc.

---

## 📈 Sample Results
| Task | Value | Exact | Relative Error |
|------|-------|-------|----------------|
| Simpson 1/3 (`n = 8`) | 1.51789 | 1.51809 | 0.013 % |
| Polynomial fit degree 2 R² | **0.9987** | – | – |

*(See full tables in the report.)*

---

## ✍️ Extending Ideas
1. Implement **Chebyshev nodes** to reduce Runge phenomenon in high‑order interpolation.
2. Compare regression residuals against **robust (Huber/LAD)** fitting.
3. Add **Romberg** and **Gauss–Legendre** quadrature for higher‑order integration accuracy.


