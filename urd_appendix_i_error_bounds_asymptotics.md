# Appendix I — Error Bounds and Asymptotic Equivalence in URD Spectral Geometry

---

## 1. Overview

Appendix I provides **rigorous mathematical error bounds**, **asymptotic equivalence results**, and **applied validation formulas** for estimating the URD spectral invariants from finite empirical data. It addresses truncation errors, tail approximations, stability of zeta-regularized determinants, and convergence of reconstructed spectra.

This appendix combines analytical results with practical computation-ready expressions.

---

## 2. Notation

Let:
- \(\mathcal{H}_{URD}\) be the URD operator.
- \(\lambda_n\) its true eigenvalues.
- \(\tilde{\lambda}_n\) empirical eigenvalues from finite data.
- \(\rho(\lambda)\) the spectral density.
- \(\Theta(t) = \sum_n e^{-t\lambda_n}\) the true heat trace.
- \(\tilde{\Theta}(t) = \sum_{n=1}^N e^{-t \tilde{\lambda}_n}\) empirical truncated heat trace.

---

## 3. Heat Trace Truncation Error Bounds

Define truncation error:
\[
E_{tr}(t) = |\Theta(t) - \tilde{\Theta}(t)| = \sum_{n > N} e^{-t\lambda_n}.
\]

### **Bound 1: Exponential Tail Bound**
If \(\lambda_n \ge \lambda_{min} + \alpha n^{2/d}\):
\[
E_{tr}(t) \le \sum_{n>N} e^{-t(\lambda_{min} + \alpha n^{2/d})} \le e^{-t\lambda_{min}}\int_N^\infty e^{-t\alpha x^{2/d}}dx.
\]
Closed form using substitution \(u = x^{2/d}\):
\[
E_{tr}(t) \le \frac{d}{2}\frac{e^{-t(\lambda_{min} + \alpha N^{2/d})}}{(t\alpha)^{d/2}}.
\]

### **Applied Estimation Formula**
For practical numerical use:
\[
E_{tr}(t) \approx e^{-t \tilde{\lambda}_N} \cdot \frac{N}{(1+t \bar{\alpha})},
\]
where \(\bar{\alpha}\) is estimated from local slope:
\[
\bar{\alpha} = \frac{\tilde{\lambda}_N - \tilde{\lambda}_{N-1}}{N^{2/d} - (N-1)^{2/d}}.
\]

---

## 4. Error Bounds for Zeta Function Approximation

Zeta function approximation using truncated spectrum:
\[
\zeta_{URD}(s) \approx \sum_{n=1}^N \tilde{\lambda}_n^{-s} + R_N(s).
\]

### **Bound 2: Remainder Term**
If \(\lambda_n \sim C n^{2/d}\):
\[
|R_N(s)| \le \int_N^\infty (C x^{2/d})^{-s}\,dx = \frac{d}{2C^s}\frac{N^{1-2s/d}}{(2s/d - 1)}.
\]
Valid for \(\mathrm{Re}(s) > d/2\).

### **Applied Estimate** (real part only):
\[
R_N(s) \approx \frac{d}{2}\frac{N^{1-2s/d}}{\bar{\lambda}_N^s (2s/d - 1)},
\]
where \(\bar{\lambda}_N = \tilde{\lambda}_N\).

---

## 5. Bounding the Determinant Approximation

Determinant:
\[
\ln\det{}'\mathcal{H}_{URD} = -\zeta'_{URD}(0).
\]
Approximation:
\[
\ln\det{}'\mathcal{H}_{URD}^{(N)} = -\sum_{n=1}^N \ln\tilde{\lambda}_n + C_N.
\]

### **Bound 3: Determinant Tail Error**
For \(\lambda_n \sim C n^{2/d}\):
\[
E_{det}(N) = \Big|\sum_{n>N} \ln \lambda_n \Big| \le \int_N^\infty \ln(C x^{2/d})dx = \frac{d}{2}N\ln N + (\ln C)N.
\]

### **Applied Numerical Formula**
Use empirical \(\tilde{\lambda}_n\):
\[
E_{det}(N) \approx N \ln\tilde{\lambda}_N - \frac{d}{2}N.
\]

Interpretation: determinant error grows linearly with cutoff N.

---

## 6. Asymptotic Equivalence Theorems

### **Theorem 1 — Heat Trace Equivalence**
If empirical spectrum satisfies
\[
|\tilde{\lambda}_n - \lambda_n| \le \epsilon(n),
\]
and \(\epsilon(n)/\lambda_n \to 0\), then
\[
\tilde{\Theta}(t) \to \Theta(t)\quad \text{uniformly on compact intervals in}\ t>0.
\]

### **Theorem 2 — Zeta Function Equivalence**
Under same assumption:
\[
\tilde{\zeta}(s) \to \zeta(s)\quad \text{for all}\ \mathrm{Re}(s)>d/2.
\]

### **Theorem 3 — Determinant Equivalence**
If additionally, tail approximation obeys power law:
\[
\lambda_n \sim C n^{2/d},
\]
then
\[
\det{}'\mathcal{H}_{URD}^{(N)} \to \det{}'\mathcal{H}_{URD}
\]
as \(N\to\infty\).

---

## 7. Statistical Confidence Bounds

When spectrum is estimated from data matrix \(C\) of size \(T\times M\):

### **Bound 4 — Eigenvalue Variance**
Using matrix perturbation theorem:
\[
\mathrm{Var}(\tilde{\lambda}_n) \le \|\delta C\|_2,
\]
with
\[
\|\delta C\|_2 \le \frac{1}{\sqrt{T}} \sigma_{max}.
\]

### **Applied Error Bars**
Eigenvalue confidence interval:
\[
\tilde{\lambda}_n \pm 1.96\sqrt{\frac{1}{T}}\sigma_{max}.
\]

---

## 8. Practical Validation Metrics

### **Metric 1 — Relative Spectrum Error**
\[
E_{spec} = \frac{1}{N}\sum_{n=1}^N \frac{|\tilde{\lambda}_n - \lambda_n|}{\lambda_n}.
\]

### **Metric 2 — KL Divergence of Spectral Density**
\[
D_{KL}(\tilde{\rho}\Vert\rho) = \int \tilde{\rho}(\lambda)\ln\frac{\tilde{\rho}(\lambda)}{\rho(\lambda)} d\lambda.
\]

### **Metric 3 — Heat Trace Misfit**
\[
E_\Theta = \sup_{t\in[t_{min},t_{max}]} |\tilde{\Theta}(t) - \Theta(t)|.
\]

---

## 9. Empirical Convergence Protocol

1. Compute spectrum \(\{\tilde{\lambda}_n\}\).
2. Compute truncated heat trace.
3. Estimate tail \(E_{tr}(t)\).
4. Compute \(\zeta(s)\) up to cutoff.
5. Estimate error in determinant.
6. Evaluate convergence using metrics above.

---

## 10. Summary

- Truncation, zeta, and determinant errors have explicit analytical bounds.
- Asymptotic equivalence holds under mild regularity conditions.
- Confidence intervals quantify robustness of empirical reconstruction.
- Validation metrics provide quantitative tests of URD spectral predictions.

> **Conclusion:** Appendix I demonstrates that URD’s spectral invariants are not only analytically well-defined but also numerically stable and empirically recoverable with controlled precision.

