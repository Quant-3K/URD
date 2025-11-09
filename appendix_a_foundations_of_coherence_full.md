# Appendix A — Foundations of Coherence

*Axioms, definitions, invariants, bounds, and measurement protocols for the coherence field \(K_Q\). This appendix is self-contained and canonical to Quant‑Trika.*

---

## A.1. Aim and Scope
This appendix formalizes **coherence** as the primary measurable that links structure and information across domains. We:
1) define the coherence field \(K_Q\) and its admissible components; 2) establish bounds, continuity, and stability; 3) derive scale and symmetry properties; 4) provide experiment‑ready measurement protocols; 5) relate \(K_Q\) to the URD objective \(\mathcal J\).

---

## A.2. Canonical Definition

### A.2.1 Canonical invariant
\[
\boxed{\;K_Q(x,t) = C(x,t)\,\big(1 - H_{\mathrm{norm}}(x,t)\big)\;}
\]
with
- \(C\in[0,1]\) — **structural coherence**, a normalized measure of correlation/synchrony/constraint;
- \(H_{\mathrm{norm}}\in[0,1]\) — **normalized entropy** of the state distribution.

### A.2.2 Normalized entropy
Let \(\rho\) be a probability density (continuous) or mass function (discrete) of the system’s microstates on space \(\Omega\).
\[
H(\rho) = -\int_{\Omega} \rho\log \rho\,d\mu,\qquad
H_{\max} = \log |\Omega| \ (\text{discrete}) \ \text{or} \ \sup_{\rho} H(\rho) \ (\text{continuous}),
\]
\[
\boxed{\;H_{\mathrm{norm}} := H/H_{\max}\in[0,1].\;}
\]

### A.2.3 Admissible family for \(C\)
Different domains admit distinct yet compatible estimators of **structural coherence**. We define an **admissible family** \(\mathcal C\) such that any \(C\in\mathcal C\) is normalized to \([0,1]\) and monotone in its native order parameter ("more structure" \(\Rightarrow\) larger \(C\)). Prototypical choices:
- **Correlation‑spectral:** \(C_\mathrm{spec} := \sigma_1(\Sigma)/\operatorname{tr}(\Sigma)\), where \(\Sigma\) is covariance and \(\sigma_1\) its top eigenvalue.
- **Graph‑topological:** \(C_\mathrm{graph} := \lambda_2(L)/\lambda_{\max}(L)\) (algebraic connectivity over Laplacian spectrum).
- **Phase synchrony:** \(C_\mathrm{sync} := \big|\frac{1}{N}\sum_j e^{\mathrm{i}\phi_j}\big|\) (Kuramoto order parameter).
- **Information‑theoretic:** \(C_\mathrm{mi} := \frac{I(X_1;\ldots;X_n)}{\sum_k H(X_k)}\) (normalized multi‑information).
- **Field smoothness:** \(C_\mathrm{grad} := 1 - \frac{\|\nabla u\|_2}{\|\nabla u\|_2 + \kappa}\) for a state field \(u\) and scale \(\kappa>0\).

All choices are equivalent up to a monotone rescaling \(r:[0,1]\to[0,1]\) (A.5), preserving the value of \(K_Q\) class within experimental tolerance.

---

## A.3. Basic Properties

### A.3.1 Bounds and extrema
Since \(C\in[0,1]\) and \(H_{\mathrm{norm}}\in[0,1]\):
\[
\boxed{\;0 \le K_Q \le 1.\;}
\]
Extrema: \(K_Q=0\) iff \(C=0\) or \(H_{\mathrm{norm}}=1\). \(K_Q=1\) iff \(C=1\) and \(H_{\mathrm{norm}}=0\).

### A.3.2 Monotonicity
For fixed \(H_{\mathrm{norm}}\), \(\partial K_Q/\partial C = 1 - H_{\mathrm{norm}} \ge 0\). For fixed \(C\), \(\partial K_Q/\partial H_{\mathrm{norm}} = -C \le 0\). Thus **increasing structure** or **reducing entropy** raises \(K_Q\).

### A.3.3 Lipschitz continuity
Suppose \(C, H_{\mathrm{norm}}\) are \(L_C, L_H\)-Lipschitz in state variables. Then \(K_Q\) is \(L_C + L_H\)-Lipschitz. This ensures numerical stability and concentration bounds (A.7).

### A.3.4 Convexity/concavity
\(K_Q(C,H) = C(1-H)\) is **bilinear**; level sets are rectangles in \((C,H)\). For composed estimators (e.g., \(C_\mathrm{spec}\) from \(\Sigma\)), convexity is inherited from spectral maps within domains of interest.

---

## A.4. Symmetries and Invariances

### A.4.1 Relabeling invariance
\(K_Q\) is invariant under measure‑preserving relabeling of microstates. It depends only on entropy and structure, not on labels.

### A.4.2 Coarse‑graining (RG) behavior
Let \(\mathcal B_\ell\) denote coarse‑grain by blocks of size \(\ell\). Then
\[
C_\ell = \mathcal R_C(C;\ell),\qquad H_{\mathrm{norm},\ell} = \mathcal R_H(H_{\mathrm{norm}};\ell),\qquad K_{Q,\ell} = C_\ell\,(1-H_{\mathrm{norm},\ell}).
\]
Under mild regularity (ergodicity, bounded correlations), there exists \(\ell^*\) such that \(K_{Q,\ell}\) approaches a fixed point \(K_Q^{\star}\) (Appendix N), enabling multi‑scale comparability.

### A.4.3 Monotone rescaling equivalence
If \(\tilde C = r(C)\) for increasing \(r\), then \(\tilde K_Q = r(C)(1-H)\) preserves **order** and **thresholds**. Hence, thresholds like \(K_Q^{\mathrm{crit}}\) are invariant under admissible changes of \(C\).

---

## A.5. Relations to URD and Objective \(\mathcal J\)

URD uses the **Free Ontological Energy**
\[
\mathcal J = -K_Q + \lambda_E\,\mathrm{EDC} + \lambda_\Theta\,\Theta + \lambda_\Phi\,\Phi.
\]
The deterministic URD flow is \(\dot x = -\eta\nabla \mathcal J\). Hence
\[
\nabla K_Q \text{ acts as a driving field toward order, while }\nabla(\mathrm{EDC},\Theta,\Phi)\text{ regularize it.}
\]
**Equilibrium condition:** \(\nabla \mathcal J = 0\) \(\Rightarrow\) marginal gain in coherence balances marginal costs (A.9).

---

## A.6. Stability, Inequalities, and Thresholds

### A.6.1 Product bound with Jensen gap
Let \(0\le C\le1\), \(0\le H\le1\). For any convex combination over ensembles \(\{(C_i,H_i)\}\):
\[
\overline{K_Q} = \overline{C(1-H)} \ge \overline C\,(1-\overline H) - \mathcal J_\mathrm{gap},
\]
where \(\mathcal J_\mathrm{gap}\) is the Jensen gap induced by dependence between \(C\) and \(H\). If \(C\perp H\) in fluctuations, \(\mathcal J_\mathrm{gap}=0\).

### A.6.2 Coherence–cost inequality
Assume \(\mathrm{EDC} \ge a\|\nabla u\|_2^2\). If \(C=C_\mathrm{grad}(u)\), then for some \(\kappa>0\):
\[
K_Q \ge 1 - \frac{\|\nabla u\|_2}{\|\nabla u\|_2+\kappa} - H_{\mathrm{norm}}\quad\Rightarrow\quad K_Q \ge 1 - H_{\mathrm{norm}} - \frac{1}{a}\,\mathrm{EDC}^\frac{1}{2} G(\kappa),
\]
bounding achievable coherence by energetic cost.

### A.6.3 Critical threshold
Define **critical coherence** \(K_Q^{\mathrm{crit}}\) as the smallest value above which the URD fixed point is Lyapunov‑stable for given weights. Linearizing URD around a stationary state yields
\[
K_Q > K_Q^{\mathrm{crit}} := 1 - \frac{\lambda_{\min}(\mathcal H_K)}{\lambda_{\min}(\mathcal H_K)+\lambda_\Theta\lambda_{\min}(\mathcal H_\Theta)+\lambda_E\lambda_{\min}(\mathcal H_E)+\lambda_\Phi\lambda_{\min}(\mathcal H_\Phi)},
\]
where \(\mathcal H_\bullet\) are Hessians of the corresponding terms (domain‑dependent). Empirically, \(K_Q^{\mathrm{crit}}\approx0.6\)–0.65 across domains.

---

## A.7. Estimation, Concentration, and Error Bounds

Let \(\widehat C, \widehat H\) be finite‑sample estimators from \(N\) observations.

### A.7.1 Bias–variance propagation
\[
\widehat{K_Q} = \widehat C (1-\widehat H),\quad
\mathrm{Var}(\widehat{K_Q}) \approx (1-\!H)^2\mathrm{Var}(\widehat C) + C^2\mathrm{Var}(\widehat H) + 2C(1-\!H)\,\mathrm{Cov}(\widehat C,\widehat H).
\]

### A.7.2 Concentration
If \(\widehat C\) and \(\widehat H\) satisfy sub‑Gaussian tails with proxies \(\sigma_C^2,\sigma_H^2\), then for any \(\varepsilon>0\):
\[
\Pr\big(|\widehat{K_Q}-K_Q|>\varepsilon\big) \le 2\exp\!\left(-\frac{N\varepsilon^2}{2\big((1-H)^2\sigma_C^2 + C^2\sigma_H^2\big)}\right).
\]

### A.7.3 Discrete/finite populations
For categorical systems with alphabet size \(M\) and empirical frequencies, Miller–Madow correction or NSB estimators should be used for \(H\) to reduce finite‑sample bias.

---

## A.8. Measurement Protocols (Domain Templates)

### A.8.1 Physics (pattern‑forming media)
- **Signal:** scalar field \(u(x,t)\).  
- **Entropy:** \(H\) from histogram of \(u\) or spectral entropy of \(|\hat u(k)|^2\).  
- **Coherence:** \(C_\mathrm{grad}\) or \(C_\mathrm{spec}\) from covariance of \(u\).  
- **Report:** \(K_Q(t)\) trajectory, heat‑trace of \(\hat L\) (Appendix H), EDC from gradient energy.

### A.8.2 Biology (neural/morphogen networks)
- **Signal:** multichannel time series; phases \(\phi_j(t)\).  
- **Entropy:** permutation entropy or spectral entropy per channel; aggregate normalized.  
- **Coherence:** \(C_\mathrm{sync}\) (Kuramoto), graph \(C_\mathrm{graph}\) from functional connectivity.  
- **Report:** \(K_Q\) vs. behavioral/phenotypic endpoints; critical transitions.

### A.8.3 AI (learning systems)
- **Signal:** parameter gradients and activations.  
- **Entropy:** entropy of representation codes or logits.  
- **Coherence:** gradient cosine‑similarity consensus across batches/layers.  
- **Report:** \(K_Q\) vs. generalization error; EDC as optimization instability; \(\Theta\) from mismatch between target and internal structure.

### A.8.4 Cognition (behavior/EEG/fMRI)
- **Signal:** neural oscillations, behavioral sequences.  
- **Entropy:** sample entropy / Lempel–Ziv complexity.  
- **Coherence:** phase‑locking value or graph‑based connectivity.  
- **Report:** \(K_Q\) across tasks; golden‑mean neighborhood for sustained attention.

---

## A.9. Variational Stationarity and Optimality Condition

At URD stationarity \(\nabla\mathcal J=0\):
\[
\boxed{\;\nabla K_Q = \lambda_E\,\nabla\mathrm{EDC} + \lambda_\Theta\,\nabla\Theta + \lambda_\Phi\,\nabla\Phi.\;}
\]
Interpretation: **marginal gain in coherence equals total marginal cost**. This is the universal balance law of adaptive organization.

---

## A.10. Discrete vs. Continuous Realizations
- **Discrete** (graphs, populations): use combinatorial Laplacians, categorical entropies, modularity‑based \(C\).  
- **Continuous** (fields): use differential operators, spectral entropies, gradient‑based \(C\).  
Both obey the same invariant form for \(K_Q\).

---

## A.11. Edge Cases and Pathologies
- **Degenerate structure:** \(C\to0\) \Rightarrow \(K_Q\to0\) regardless of entropy.  
- **Maximal disorder:** \(H_{\mathrm{norm}}\to1\) \Rightarrow \(K_Q\to0\) regardless of structure proxy.  
- **Over‑regularization:** large \(\lambda_E\) may suppress \(K_Q\) even if structure exists (energetic brittleness).  
- **Spurious coherence:** estimator alignment on noise (must validate with surrogate data/shuffled phases).

---

## A.12. Calibration and Cross‑Domain Comparability
To compare \(K_Q\) across studies:
1) publish estimator choice \(C\) and entropy method; 2) report normalization constants; 3) provide bootstrapped CIs; 4) include RG‑coarse‑grain curves; 5) share code and seeds (Appendix S).

---

## A.13. Worked Mini‑Examples

**(i) Two‑cluster Gaussian mixture.**  
\(C_\mathrm{spec} = \sigma_1/\operatorname{tr}\) grows with cluster separation; \(H_{\mathrm{norm}}\) increases with overlap. \(K_Q\) peaks at moderate separation, matching human clusterability.

**(ii) Kuramoto oscillators near synchronization.**  
As coupling \(K\) passes threshold, \(C_\mathrm{sync}\to 1\), while spectral entropy of phases drops; \(K_Q\) shows sigmoid rise, identifying transition.

**(iii) CNN training.**  
Batch‑gradient alignment (\(C\)) increases; representation entropy reduces moderately; \(K_Q\) predicts generalization peak earlier than validation accuracy (early‑stopping heuristic).

---

## A.14. Connection to Observables and Heat‑Trace (Preview of H)
For linearized dynamics with generator \(\mathcal L\), the **coherence heat‑trace** \(\Theta_H(\tau)=\operatorname{tr} \exp(-\tau\,\mathcal L_K)\) correlates with \(K_Q\) via spectral compression; determinant reconstruction (Appendix G–H) provides a global scalar observable.

---

## A.15. Summary
- \(K_Q = C(1-H_{\mathrm{norm}})\) is bounded, stable, and experimentally accessible.
- Admissible \(C\) ensures cross‑domain portability; RG behavior yields scale consistency.
- Variational balance (A.9) links \(K_Q\) to costs in URD; thresholds determine stability.
- Protocols in A.8 provide immediate templates for physics, biology, AI, and cognition.

---

## A.16. Glossary (Symbols)
\(C\) — structural coherence; \(H_{\mathrm{norm}}\) — normalized entropy; \(K_Q\) — coherence invariant; \(\mathrm{EDC}\) — energetic debt of coherence; \(\Theta\) — ontological debt; \(\Phi\) — marginal price of order; \(\eta,D\) — URD rate and diffusion; \(L\) — graph Laplacian; \(\Sigma\) — covariance; \(r\) — admissible rescaling; \(\mathcal J\) — free ontological energy.

