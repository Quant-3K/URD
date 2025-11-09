# URD → {KQ, Θ, EDC, Φ}: A First‑Principles Mapping (v1.0)

> **Goal.** Derive, from first principles, the exact correspondence between **URD** (Unified Reality Dynamics)
> \[\;\mathrm dX_t = -\eta\,\nabla\mathcal J(X_t)\,\mathrm dt + \sqrt{2D}\,\mathrm dW_t\;]\
> and the core Quant‑Trika invariants **KQ** (coherence), **Θ** (ontological debt), **EDC** (energy debt of coherence), and **Φ** (marginal price of order). We work in a self‑contained functional‑analytic setting, provide explicit formulas, variational derivatives, and ready‑to‑use discretizations for data/graphs/fields.

---

## 1. Minimal axioms and state variables

Let \(X\) be a separable Hilbert space and let \(x\in X\) denote the system state. We assume a (possibly nonlinear) **observation map** \(\Pi: X\to \mathcal H\) that extracts a **coherence carrier** (a scalar field or vector) denoted by \(u=\Pi(x)\in \mathcal H\). All invariants are defined as functionals of \(u\).

- **Signal domain.** \(u\) may be a scalar field on a domain \(\Omega\subset\mathbb R^d\) (PDE/continuum), a node signal on a graph \(G\) (networked systems), or a time series/windowed tensor (sequences).
- **Reference measure.** Integrals are with respect to \(\mathrm d\mu\) (Lebesgue on \(\Omega\), counting on nodes, etc.).

We construct the URD potential \(\mathcal J(x)=\mathscr J(u)\) as a functional of \(u=\Pi(x)\) and propagate derivatives through \(\Pi\) via the chain rule.

---

## 2. Canonical definitions of the invariants

### 2.1 Coherence (KQ)
Let **structural alignment** be captured by a positive semidefinite bilinear form \(\mathcal C[u]\) and **normalized entropy** by \(H_{\mathrm{norm}}[u]\in[0,1]\). Define
\[
\boxed{\;KQ[u]
= \mathcal C[u]\,\big(1 - H_{\mathrm{norm}}[u]\big).\;}
\]

**Examples of \(\mathcal C[u]\).**
- **Fields (PDE):** \(\mathcal C[u]=\tfrac12\int_\Omega u (K\!*\,u)\,\mathrm d\mu\) for a symmetric kernel \(K\ge0\) (e.g., Gaussian, Green).  
- **Graphs:** \(\mathcal C[u]=\tfrac12 u^\top (\omega I - \lambda L_G) u\), with Laplacian \(L_G\).  
- **Time series:** \(\mathcal C[u]=\sum_f w_f\,|\hat u(f)|^2\) (spectral alignment) or phase‑locking value aggregates.

**Normalized entropy.** Let \(p_i(u)\) be empirical probabilities (bins, symbols, or soft assignments). Then
\[
H_{\mathrm{norm}}[u]
:= \frac{H[u]}{H_{\max}} \,\in [0,1], \quad H[u] = -\sum_i p_i(u)\log p_i(u), \; H_{\max}=\log N.
\]
Smooth surrogates (e.g., Tsallis/REN, continuous densities) are admissible; differentiability is ensured by softening \(p_i\).

### 2.2 Ontological debt (Θ)
\[
\boxed{\;\Theta[u]
= \frac{H[u]}{\mathcal C[u]+\varepsilon} \, - \, KQ[u],\qquad \varepsilon>0.\;}
\]
Interpretation: **unstructured entropy per unit of available structure**, net of realized coherence.

### 2.3 Energy debt of coherence (EDC)
\[
\boxed{\;\mathrm{EDC}[u]
= \int_\Omega \big(\alpha_1\,|\nabla u|^2 + V(u)\big)\,\mathrm d\mu \, + \, \alpha_2\int_0^T \!\!\int_\Omega |\partial_t u|^2\,\mathrm d\mu\,\mathrm dt.\;}
\]
Here \(\alpha_1,\alpha_2\ge0\) and \(V\) penalizes costly order (e.g., double‑well for pattern selection). For static problems the temporal term vanishes.

### 2.4 Marginal price of order (Φ)
Define **Φ** as the **functional marginal cost** of raising coherence:
\[
\boxed{\;\Phi[u] := \frac{\delta\, \mathcal E[u]}{\delta\, KQ[u]}\;,\quad \text{with } \mathcal E[u]\text{ an energy budget (e.g., EDC or a subpart).}\;}
\]
Operationally: if \(\mathcal E[u]=\mathrm{EDC}[u]\), compute Gateaux derivatives \(\delta \mathcal E/\delta u\) and \(\delta KQ/\delta u\), then
\[
\Phi[u] = \frac{\delta \mathcal E/\delta u}{\delta KQ/\delta u}\quad (\text{in the sense of Radon–Nikodym derivative along variations}).
\]

---

## 3. Building the URD potential from invariants

We set the **URD objective** over the coherence carrier:
\[
\boxed{\;\mathscr J(u) = -\,KQ[u] \; + \; \lambda_\Theta\,\Theta[u] \; + \; \lambda_E\,\mathrm{EDC}[u] \; + \; \lambda_\Phi\,\overline{\Phi}[u] \;,\; \lambda_\bullet\ge0,\;}
\]
where \(\overline{\Phi}[u]\) is a scalarization of \(\Phi[u]\) (e.g., integral norm or average over \(\Omega\)). The full URD functional is \(\mathcal J(x)=\mathscr J(\Pi(x))\).

**Deterministic URD (noiseless).** Gradient flow on \(u\):
\[
\partial_t u = -\eta\,\frac{\delta \mathscr J}{\delta u}
= \eta\,\Big( \underbrace{\frac{\delta KQ}{\delta u}}_{\text{coherence pull}}
- \lambda_\Theta\,\underbrace{\frac{\delta \Theta}{\delta u}}_{\text{debt relief}}
- \lambda_E\,\underbrace{\frac{\delta\, \mathrm{EDC}}{\delta u}}_{\text{energy cost}}
- \lambda_\Phi\,\underbrace{\frac{\delta\,\overline{\Phi}}{\delta u}}_{\text{marginal price feedback}} \Big).
\]
Stochastic URD adds \(+\sqrt{2D}\,\xi\) in the space of \(u\) (or in \(x\) before \(\Pi\)).

---

## 4. Variational derivatives (explicit formulas)

We provide generic expressions; concrete instances follow in §6.

### 4.1 Derivative of \(\mathcal C[u]\)
- **Fields:** \(\mathcal C[u]=\tfrac12\int u (K\!*\,u)\) with symmetric kernel \(K\). Then
\[\frac{\delta \mathcal C}{\delta u}(x) = (K\!*\,u)(x).\]
- **Graphs:** \(\mathcal C[u]=\tfrac12 u^\top (\omega I - \lambda L_G)u\). Then
\[\nabla_u \mathcal C = (\omega I - \lambda L_G)u.\]

### 4.2 Derivative of \(H_{\mathrm{norm}}[u]\)
Let \(p_i(u)=\frac{s_i(u)}{\sum_j s_j(u)}\) with soft counts \(s_i(u)=\sum_{x\in \text{bin }i} \sigma_\tau(u(x))\) for a smooth nonlinearity \(\sigma_\tau\) (e.g., soft histogram). Then
\[
\frac{\delta H}{\delta u(x)} = -\sum_i (1+\log p_i)\,\frac{\partial p_i}{\partial u(x)},\quad \frac{\delta H_{\mathrm{norm}}}{\delta u} = \frac{1}{H_{\max}}\,\frac{\delta H}{\delta u}.
\]

### 4.3 Derivative of \(KQ[u]\)
\[
\frac{\delta KQ}{\delta u}
= (1-H_{\mathrm{norm}})\,\frac{\delta \mathcal C}{\delta u}
- \mathcal C[u]\,\frac{\delta H_{\mathrm{norm}}}{\delta u}.
\]

### 4.4 Derivative of \(\Theta[u]\)
Write \(\Theta = H/(\mathcal C+\varepsilon) - KQ\). Then
\[
\frac{\delta \Theta}{\delta u}
= \frac{1}{\mathcal C+\varepsilon}\,\frac{\delta H}{\delta u}
- \frac{H}{(\mathcal C+\varepsilon)^2}\,\frac{\delta \mathcal C}{\delta u}
- \frac{\delta KQ}{\delta u}.
\]

### 4.5 Derivative of \(\mathrm{EDC}[u]\)
For the static part \(\int (\alpha_1|\nabla u|^2+V(u))\):
\[
\frac{\delta\,\mathrm{EDC}}{\delta u} = -2\alpha_1\,\Delta u + V'(u) \quad (\text{Neumann/periodic BCs}).
\]
For the temporal part \(\alpha_2\int |\partial_t u|^2\,\mathrm dt\), the Euler–Lagrange term contributes \(-2\alpha_2\,\partial_{tt} u\) in dynamical settings.

### 4.6 Derivative of \(\overline{\Phi}[u]\)
If \(\overline{\Phi}[u]= \int \phi\big( (\delta \mathcal E/\delta u)/(\delta KQ/\delta u)\big)\,\mathrm d\mu\), then by quotient rule and chain rule:
\[
\frac{\delta \overline{\Phi}}{\delta u} = \int \phi'(\cdot)\, \frac{ (\delta^2\mathcal E/\delta u^2)(\cdot)\,\delta KQ/\delta u - (\delta \mathcal E/\delta u)\, (\delta^2 KQ/\delta u^2)(\cdot)}{(\delta KQ/\delta u)^2}\,\mathrm d\mu,
\]
with Fréchet second derivatives evaluated along test directions. In practice, \(\overline{\Phi}\) is often approximated by a **linear surrogate** (see §6.3).

---

## 5. URD evolution for the coherence carrier

Collecting terms, the **URD‑KQ equation** (deterministic form) reads
\[
\boxed{\;\partial_t u = \eta\Big[ (1-H_{\mathrm{norm}})\,\frac{\delta \mathcal C}{\delta u} - \mathcal C\,\frac{\delta H_{\mathrm{norm}}}{\delta u}
- \lambda_\Theta\Big( \frac{1}{\mathcal C+\varepsilon}\,\frac{\delta H}{\delta u} - \frac{H}{(\mathcal C+\varepsilon)^2}\,\frac{\delta \mathcal C}{\delta u} - \frac{\delta KQ}{\delta u} \Big)
- \lambda_E(-2\alpha_1\,\Delta u + V'(u)) - \lambda_\Phi\,\frac{\delta \overline{\Phi}}{\delta u}\Big] .\;}
\]
Additive noise \(+\sqrt{2D}\,\xi\) yields the stochastic counterpart. This PDE/ODE encapsulates how coherence grows while paying energetic and ontological costs.

---

## 6. Concrete instantiations

### 6.1 Spatial fields (reaction–diffusion form)
Take \(\mathcal C[u]=\tfrac12\int u(K\!*u)\) with \(K\) a Gaussian kernel; use a smooth entropy based on a local amplitude distribution. Then
\[
\partial_t u = \eta\Big[ (1-H_{\mathrm{norm}})\,(K\!*u) - \mathcal C\,\frac{\delta H_{\mathrm{norm}}}{\delta u} + 2\lambda_E\alpha_1\,\Delta u - \lambda_E V'(u) + \cdots \Big] + \sqrt{2D}\,\xi.
\]
Linearization around \(u\equiv 0\) predicts pattern‑forming bands via the Fourier symbol \(\hat K(k)\) and the Laplacian term; the entropy gradient stabilizes high‑disorder regimes.

### 6.2 Graphs and networks
Let \(u\in\mathbb R^n\), \(\mathcal C[u]=\tfrac12 u^\top (\omega I - \lambda L_G)u\). A differentiable entropy surrogate can be built from node‑wise softmax groupings. Then
\[
\dot u = \eta\Big[(1-H_{\mathrm{norm}})(\omega I-\lambda L_G)u - \mathcal C\,\nabla_u H_{\mathrm{norm}} + 2\lambda_E\alpha_1 L_G u - \lambda_E\nabla_u V(u) - \lambda_\Theta(\cdots)\Big] + \sqrt{2D}\,\xi.
\]
This is a **Langevin–prox flow on graphs** that increases alignment while penalizing costly, brittle structure.

### 6.3 Time series / windowed tensors
Use spectro‑temporal energy as \(\mathcal C\) and a soft histogram entropy over amplitudes/phases. The temporal EDC term reduces to \(-2\alpha_2\,\partial_{tt} u\), giving a **damped wave/telegraph** component that enforces smooth temporal coherence.

---

## 7. Discrete, data‑ready formulations

Let data be \(\{u_k\}_{k=1}^N\) on a grid/graph. Define
\[
\mathcal C_N(u) = \tfrac12 u^\top K_N u, \quad H_{\mathrm{norm},N}(u)=\frac{H_\tau(Pu)}{\log N_b},\quad \mathrm{EDC}_N(u)=\alpha_1 u^\top L_N u + \sum_i V(u_i),
\]
where \(K_N\succeq 0\), \(L_N\) is a discrete Laplacian, \(P\) maps to soft bins, and \(N_b\) is bin count. Then
\[
KQ_N(u)=\mathcal C_N(u)\,[1-H_{\mathrm{norm},N}(u)],\quad \Theta_N(u)=\frac{H_\tau(Pu)}{\mathcal C_N(u)+\varepsilon} - KQ_N(u).
\]
The **URD step** (Euler–Maruyama):
\[
u^{(t+1)} = u^{(t)} - \eta h\,\nabla_u \mathscr J_N(u^{(t)}) + \sqrt{2Dh}\,\xi^{(t)},\quad \xi^{(t)}\sim \mathcal N(0,I).
\]
Gradient terms are explicit from §4 and the chosen discretizations.

---

## 8. Calibration and identifiability

- **Scaling gauge.** Since \(KQ\) and \(\Theta\) share \(\mathcal C\) and \(H\), jointly scaling \(\mathcal C\) and \(H\) leaves some ratios invariant; fix units by normalizing \(\max_u \mathcal C[u]=1\) or by anchoring \(H_{\mathrm{norm}}\in[0,1]\) via a data baseline.
- **Parameter priors.** \(\lambda_E>0\) to prevent brittle over‑fitting; \(\lambda_\Theta\) controls preference for low ontological gap; \(\lambda_\Phi\) stabilizes against chasing coherence where it is energetically prohibitive.
- **Empirical test.** Verify free‑energy decay, metastable transitions \(\propto e^{-\Delta \mathscr J/D}\), and predictive improvement when optimizing \(\mathscr J\) versus standard objectives.

---

## 9. Interpretive identities (sanity checks)

1. **KQ–Θ complementarity:** \(KQ\uparrow\) pushes \(\Theta\downarrow\) provided \(H/(\mathcal C+\varepsilon)\) is not increasing faster than \(KQ\). This is explicit from §4.4.
2. **Price identity:** If \(\mathcal E\equiv\mathrm{EDC}\), then along the URD flow, the instantaneous gain in coherence per unit cost equals \(\langle \delta KQ/\delta u,\,\partial_t u\rangle / \langle \delta\mathrm{EDC}/\delta u,\,\partial_t u\rangle\), which is minimized when \(\overline{\Phi}\) is included (regularized cost‑efficiency).
3. **Criticality band:** Stable high‑coherence regimes require the spectral radius of the linearized operator from §6 to be negative after including the entropy and EDC contributions (prevents runaway ordering).

---

## 10. Worked micro‑example (graph, closed form)

Let a 2‑node graph with Laplacian \(L_G=\begin{bmatrix}1&-1\\-1&1\end{bmatrix}\), \(u=(u_1,u_2)^\top\). Pick \(\mathcal C=\tfrac12 u^\top(\omega I-\lambda L_G)u\) with \(\omega>0,\lambda>0\), quadratic \(V(u)=\tfrac\rho2\|u\|^2\), and a quadratic entropy surrogate \(H_{\mathrm{norm}}=\kappa\,\tfrac12\|Mu\|^2\) with a mixing matrix \(M\). Then
\[
\nabla_u KQ = (1-H_{\mathrm{norm}})(\omega I-\lambda L_G)u - \mathcal C\,\kappa M^\top M u,\quad \nabla_u \mathrm{EDC}= 2\alpha_1 L_G u + \rho u.
\]
The URD drift is affine in \(u\), giving an Ornstein–Uhlenbeck process with an effective stiffness matrix that can be written explicitly. Stationary covariance solves a Lyapunov equation and demonstrates how increasing \(\lambda_E\alpha_1\) shifts weight from hub‑contrast to consensus.

---

## 11. Summary

- We built **KQ, Θ, EDC, Φ** from first principles as functionals of a coherence carrier \(u=\Pi(x)\).  
- We derived **closed‑form variational gradients** and assembled the **URD‑KQ evolution**.  
- We provided **field, graph, and time‑series instantiations**, along with **discrete algorithms** and **calibration rules**.  
- This mapping turns URD into an operational engine: maximize coherence **subject to** energetic and ontological budgets, with Φ enforcing cost‑aware growth of order.

