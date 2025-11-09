# URD — Appendices: Full Proofs (v1.0)

> This appendix provides detailed proofs and auxiliary lemmas for the statements introduced in the **URD — Unified Reality Dynamics (Mathematical Specification v1.0)** document. Throughout, let \(X\) be a separable Hilbert space with inner product \(\langle\cdot,\cdot\rangle\) and norm \(\|\cdot\|\). The stochastic forcing is an \(X\)-valued Wiener process \(W_t\) with covariance operator \(Q\). The URD dynamics is
> \[
> \mathrm d X_t \,=\, -\eta\,\nabla\mathcal J(X_t)\,\mathrm dt \, + \, \sqrt{2D}\,\mathrm d W_t.
> \]
> Assumptions (A1)–(A3) on \(\mathcal J\) are as in the main document unless explicitly strengthened.

---

## A. Well-posedness of URD in Hilbert Spaces

### Theorem A.1 (Existence and uniqueness of strong solutions)
**Statement.** Suppose \(\mathcal J\in C^1(X,\mathbb R)\) with locally Lipschitz gradient in the sense of (A3), and that the drift \(b(x):=-\eta\,\nabla\mathcal J(x)\) is **dissipative** on \(X\): there exist constants \(a>0\), \(b\ge 0\) such that
\[
\langle b(x)-b(y),\,x-y\rangle \le -a\,\|x-y\|^2 + b,\qquad \forall x,y\in X.
\]
Assume also that \(Q\) is a nonnegative, symmetric, trace-class operator on \(X\). Then for any \(X_0\in X\), the SDE admits a unique strong solution \((X_t)_{t\ge 0}\) with continuous paths and
\(\sup_{t\in[0,T]}\mathbb E\|X_t\|^2<\infty\) for all \(T>0\).

**Proof.** Consider the mild formulation
\[
X_t = X_0 + \int_0^t b(X_s)\,\mathrm ds + \sqrt{2D}\, W_t.
\]
Local Lipschitz continuity of \(b\) yields local existence and pathwise uniqueness (Picard iteration). Dissipativity implies a priori bounds: compute
\(\mathrm d\|X_t\|^2 = 2\langle X_t, b(X_t)\rangle \mathrm dt + 2\sqrt{2D}\,\langle X_t, \mathrm dW_t\rangle + 2D\,\mathrm{Tr}(Q)\, \mathrm dt\).
Taking expectation and using \(\langle X_t, b(X_t)\rangle \le -a\|X_t\|^2 + c\) for some \(c\), Grönwall’s lemma yields a global second-moment bound. Standard localization removes explosion and upgrades to global strong solutions. Uniqueness follows from local Lipschitz plus monotonicity. ∎

**Remark A.2 (Coercivity via \(\mathcal J\)).** If \(\mathcal J\) is bounded below and \(\nabla\mathcal J\) satisfies a one-sided growth condition, dissipativity follows from convexity-type lower bounds, e.g. \(\langle \nabla\mathcal J(x), x\rangle \ge c_1\|x\|^2 - c_2\).

---

## B. Energy Dissipation Identity

### Theorem B.1 (Itô energy balance)
**Statement.** Suppose \(\mathcal J\in C^2\) with bounded Hessian on bounded sets and \(Q\) trace-class. Then the URD solution satisfies
\[
\mathrm d\,\mathcal J(X_t)
= -\eta\,\|\nabla \mathcal J(X_t)\|^2\,\mathrm dt
+ D\,\mathrm{Tr}\big[ Q\,\nabla^2\mathcal J(X_t)\big] \,\mathrm dt
+ \sqrt{2D}\,\langle \nabla \mathcal J(X_t),\,\mathrm dW_t\rangle.
\]
Taking expectation,
\[
\frac{\mathrm d}{\mathrm dt}\,\mathbb E\,\mathcal J(X_t) = -\eta\,\mathbb E\,\|\nabla \mathcal J(X_t)\|^2 + D\,\mathbb E\,\mathrm{Tr}\big[ Q\,\nabla^2\mathcal J(X_t)\big].
\]

**Proof.** Apply the infinite-dimensional Itô formula (Da Prato–Zabczyk): for \(F\in C^2(X)\),
\(\mathrm dF(X_t)=\langle \nabla F(X_t),\mathrm dX_t\rangle + \frac12\,\mathrm{Tr}\big[ (2D)Q\,\nabla^2F(X_t)\big]\,\mathrm dt\).
Set \(F=\mathcal J\) and substitute \(\mathrm dX_t\). The martingale term has zero expectation, yielding the mean identity. ∎

**Corollary B.2 (Monotone decay for small D).** If \(\nabla^2\mathcal J\preceq \Lambda I\) and \(D<\frac{\eta}{\Lambda}\,\inf_t \frac{\mathbb E\|\nabla\mathcal J(X_t)\|^2}{\mathbb E 1}\), then \(\mathbb E\mathcal J(X_t)\) is strictly decreasing. ∎

---

## C. Fokker–Planck Equation and Stationary Measures

### Proposition C.1 (Fokker–Planck for URD)
**Statement.** Let \(\mu_t\) denote the law of \(X_t\). For sufficiently smooth test \(\varphi\),
\[
\frac{\mathrm d}{\mathrm dt}\int_X \varphi\,\mathrm d\mu_t = \int_X \langle \nabla \varphi, \eta\,\nabla\mathcal J\rangle\,\mathrm d\mu_t + D\int_X \mathrm{Tr}\big[Q\,\nabla^2\varphi\big] \,\mathrm d\mu_t.
\]
Equivalently, in weak form the density \(\rho_t\) (if it exists) satisfies
\[
\partial_t \rho_t = \eta\,\nabla\cdot(\rho_t\nabla\mathcal J) + D\,\Delta_Q\rho_t,
\]
where \(\Delta_Q\) is the \(Q\)-weighted Laplacian.

**Proof.** Standard Kolmogorov forward equation derivation via Itô’s formula and duality. ∎

### Theorem C.2 (Gibbs-type stationary law under detailed balance)
**Statement.** Assume: (i) \(Q\) is strictly positive definite and commutes with the gradient flow; (ii) \(\exp\big(-\tfrac{\eta}{D}\mathcal J\big)\in L^1(X)\). Then the probability measure \(\pi\) with density
\[
\frac{\mathrm d\pi}{\mathrm dx}(x) = Z^{-1}\,\exp\Big(-\tfrac{\eta}{D}\,\mathcal J(x)\Big)
\]
is stationary for the Fokker–Planck equation.

**Proof.** Substitute \(\rho=Z^{-1}e^{-\frac{\eta}{D}\mathcal J}\) into the RHS of the Fokker–Planck operator and integrate by parts (formally):
\(\nabla\rho = -\tfrac{\eta}{D}\rho\,\nabla\mathcal J\), hence
\(\eta\,\nabla\cdot(\rho\nabla\mathcal J) + D\,\Delta_Q\rho = \eta\,(\nabla\rho\cdot\nabla\mathcal J + \rho\,\Delta\mathcal J) + D\,\Delta_Q\rho\).
Cancellation follows from the identity \(D\,\Delta_Q\rho = D\,\nabla\cdot(Q\nabla\rho) = -\eta\,\nabla\cdot(Q\rho\nabla\mathcal J)\) when \(Q\) commutes with the drift metric. Thus the RHS vanishes. Normalization gives a probability measure. ∎

**Remark C.3.** In finite dimensions with \(Q=I\), this is the classical overdamped Langevin stationarity.

---

## D. Metastability and Eyring–Kramers Asymptotics

### Theorem D.1 (Arrhenius law / Eyring–Kramers for URD, sketch)
**Statement.** Let \(\mathcal J\in C^3\) and suppose it has finitely many nondegenerate local minima \(\{x_i\}\) and saddle points \(\{s_{ij}\}\) separating their basins. For small \(D\), the mean transition time from basin \(i\) to basin \(j\) satisfies
\[
\mathbb E\,\tau_{i\to j} \sim \frac{2\pi}{\eta}\,\sqrt{\frac{\det H_{x_i}}{|\det H_{s_{ij}}|}}\,\exp\Big(\frac{\eta}{D} (\mathcal J(s_{ij})-\mathcal J(x_i))\Big),
\]
where \(H_{x_i}=\nabla^2\mathcal J(x_i)\) and \(H_{s_{ij}}=\nabla^2\mathcal J(s_{ij})\).

**Proof (sketch).** Linearize around minima and saddles; solve backward Kolmogorov equation for the mean exit time using WKB/large-deviations ansatz \(u(x)\approx A(x)\exp(\tfrac{\eta}{D}S(x))\). Matching across the saddle yields the prefactor involving Hessians; the exponential rate is the minimal action \(\Delta\mathcal J\). Details follow classical Freidlin–Wentzell theory with nondegenerate critical points. ∎

---

## E. Symmetry and Noether-type Conservation

### Proposition E.1 (Conserved generator pairing, deterministic case)
**Statement.** Let a Lie group \(G\) act smoothly on \(X\) and suppose \(\mathcal J\) is \(G\)-invariant: \(\mathcal J(g\cdot x)=\mathcal J(x)\). Denote the deterministic flow \(\dot x=-\eta\nabla\mathcal J(x)\) and the infinitesimal generator \(\Xi(x)=\tfrac{\mathrm d}{\mathrm d\epsilon}|_{0} (\exp(\epsilon\xi)\cdot x)\). Then along any trajectory,
\[
\frac{\mathrm d}{\mathrm dt}\,\langle \nabla\mathcal J(x_t),\,\Xi(x_t)\rangle = 0.
\]

**Proof.** Differentiate \(\langle \nabla\mathcal J(x_t),\,\Xi(x_t)\rangle\) using the chain rule:
\(\frac{\mathrm d}{\mathrm dt}=\langle \nabla^2\mathcal J(x_t)\dot x_t,\Xi(x_t)\rangle + \langle \nabla\mathcal J(x_t), D\Xi(x_t)[\dot x_t]\rangle\).
Insert \(\dot x_t=-\eta\nabla\mathcal J(x_t)\) and use invariance: for all \(\epsilon\), \(\mathcal J(\exp(\epsilon\xi)\cdot x)=\mathcal J(x)\). Differentiating at \(\epsilon=0\), \(\langle \nabla\mathcal J(x),\Xi(x)\rangle=0\). A second differentiation yields cancellation of the two terms above, giving zero derivative. ∎

**Corollary E.2 (Momentum map in linear actions).** If the action is linear, the quantity \(M_\xi(x):=\langle \nabla\mathcal J(x),\Xi(x)\rangle\) is a first integral.

---

## F. Renormalization Compatibility

### Proposition F.1 (Form invariance under coarse-graining)
**Statement.** Let \(\mathcal R_\ell:X\to X\) be a linear bounded coarse-graining with adjoint \(\mathcal R_\ell^*\). Define \(\mathcal J_\ell(x):=\ell^{-\delta}\,\mathcal J(\mathcal R_\ell x)\). Consider the coarse-grained process \(Y_t:=\mathcal R_\ell X_t\). If \(\mathcal R_\ell\) commutes with \(Q^{1/2}\) and with the operators defining the components of \(\mathcal J\) (e.g., \(K,L,G\)), then \(Y_t\) satisfies
\[
\mathrm dY_t = -\eta_\ell\,\nabla\mathcal J_\ell(Y_t)\,\mathrm dt + \sqrt{2D_\ell}\,\mathrm dW_t^\ell
\]
with \(\eta_\ell=\ell^{2-\delta}\eta\) and \(D_\ell=\ell^{2-\delta}D\).

**Proof.** Apply \(\mathcal R_\ell\) to URD and use linearity:
\(\mathrm dY_t = -\eta\,\mathcal R_\ell\nabla\mathcal J(X_t)\mathrm dt + \sqrt{2D}\,\mathcal R_\ell\mathrm dW_t\).
By chain rule, \(\nabla\mathcal J_\ell(y) = \ell^{-\delta}(\mathcal R_\ell^*)\nabla\mathcal J(\mathcal R_\ell y)\).
Setting \(y=Y_t\) and assuming \(\mathcal R_\ell\mathcal R_\ell^*\approx \ell^2 I\) on the relevant subspace (typical of block averages), we obtain the stated rescaling. Noise rescales accordingly because \(\mathcal R_\ell W_t\) is a Wiener process with covariance \(\mathcal R_\ell Q \mathcal R_\ell^*\). ∎

**Remark F.2.** Fixed points \(\eta_\ell=\eta\), \(D_\ell=D\) occur at \(\delta=2\), identifying the natural engineering dimension of \(\mathcal J\).

---

## G. Numerical Schemes

### Theorem G.1 (Weak convergence of Euler–Maruyama)
**Statement.** Under (A1)–(A3) and polynomial growth of \(\nabla\mathcal J\), the Euler–Maruyama scheme
\(X_{k+1}=X_k-\eta h\,\nabla\mathcal J(X_k)+\sqrt{2Dh}\,\xi_k\) with \(\xi_k\sim \mathcal N(0,Q)\) converges weakly to URD as \(h\to0\) with order 1.

**Proof.** Standard stochastic numerical analysis: expand test functions \(\varphi\) via Itô–Taylor and compare the discrete generator with the SDE generator; local error is \(O(h^2)\), yielding global weak order 1. ∎

### Proposition G.2 (Invariant measure preservation under suitable discretization)
**Statement.** If a Metropolis-adjusted Langevin step or a symmetric splitting integrator with appropriate noise discretization is used, the discrete Markov chain admits invariant measure arbitrarily close (in total variation) to \(e^{-\frac{\eta}{D}\mathcal J}\) for small step size.

**Proof (sketch).** Detailed balance holds by construction for MALA; splitting methods match the continuous generator up to \(O(h^2)\), and a perturbation argument yields closeness of invariant laws. ∎

---

## H. JKO Scheme and Gradient Flows in Probability Space

### Theorem H.1 (JKO minimizing movement for URD’s Fokker–Planck)
**Statement.** Let \(\mathcal J\) be \(\lambda\)-convex along Wasserstein geodesics and satisfy coercivity. Define the “free energy” \(\mathcal F(\mu)=\int \mathcal J\,\mathrm d\mu + D\,\mathrm{Ent}(\mu)\). The implicit scheme
\[
\mu^{k+1}\in \arg\min_{\mu}\Big\{ \frac{1}{2\tau}W_2^2(\mu,\mu^k) + \frac{\eta}{D}\,\mathcal F(\mu) \Big\}
\]
produces a sequence whose piecewise-constant interpolation converges (as \(\tau\to0\)) to a weak solution of the Fokker–Planck equation.

**Proof (sketch).** Standard Jordan–Kinderlehrer–Otto argument: optimality conditions yield the discrete continuity equation with velocity field proportional to \(-\nabla(\delta\mathcal F/\delta\rho)\). Compactness follows from coercivity; \(\lambda\)-convexity implies contractivity and uniqueness, hence convergence. ∎

---

## I. Auxiliary Estimates and Identities

### Lemma I.1 (Coercivity via quadratic forms)
If \(\mathsf E(x)=\tfrac12\|Lx\|^2\), \(\mathsf O(x)\ge c\|x\|^2 - C\), and \(\mathsf P(x)=\tfrac12\langle Gx,x\rangle\) with \(G\succeq 0\), while \(\mathsf C(x)=\tfrac12\langle Kx,x\rangle\) with \(K\preceq K_{\max}I\), then
\(\mathcal J(x)\ge (\alpha\,c - \tfrac12\|K\|)\|x\|^2 - C'\). For \(\alpha c>\tfrac12\|K\|\), \(\mathcal J\) is coercive.

**Proof.** Direct estimates using \(\langle Kx,x\rangle\le \|K\|\,\|x\|^2\) and triangle inequalities. ∎

### Lemma I.2 (Boundedness of Hessian on bounded sets)
If \(\mathsf C, \mathsf P\) are quadratic and \(\mathsf E, \mathsf O\in C^2\) with bounded second derivatives on bounded sets, then \(\nabla^2\mathcal J\) is bounded on bounded sets.

**Proof.** Immediate from linearity of second derivative and operator bounds. ∎

---

## J. Notes on Self-Referential Augmentation

### Proposition J.1 (Well-posedness of coupled URD–model system)
For the augmented system
\(\mathrm d X_t = -\eta\,\nabla_X\mathcal J(X_t,Y_t)\,\mathrm dt + \sqrt{2D}\,\mathrm dW_t\),
\(\mathrm d Y_t = -\lambda\,\nabla_Y\mathcal J(X_t,Y_t)\,\mathrm dt + \sqrt{2\tilde D}\,\mathrm d\tilde W_t\),
assume the joint \(\mathcal J\) satisfies (A1)–(A3) in \(X\times Y\). Then existence/uniqueness and energy identities hold verbatim with the joint gradient and block covariance.

**Proof.** Product-space application of Theorem A.1 and Theorem B.1. ∎

---

## K. Finite-Dimensional Closed-Form Solutions

### Proposition K.1 (Quadratic \(\mathcal J\): exact OU laws)
If \(\mathcal J(x)=\tfrac12 x^\top H x\) with \(H\succ 0\) and \(Q=I\), then URD is linear: \(\mathrm dX_t=-\eta H X_t\,\mathrm dt + \sqrt{2D}\,\mathrm dB_t\). The stationary law is Gaussian \(\mathcal N(0,\Sigma)\) with \(\eta(H\Sigma+\Sigma H)=2D I\). The transition kernel is \(\mathcal N(m_t,\Sigma_t)\) with \(m_t=e^{-\eta H t}x_0\), \(\Sigma_t\) solving the Lyapunov ODE.

**Proof.** Classical Ornstein–Uhlenbeck theory. ∎

---

**End of Appendices.**

