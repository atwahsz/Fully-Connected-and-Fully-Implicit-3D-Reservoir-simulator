In reservoir simulation, the fully implicit method (FIM) is the state-of-the-art. The majority of commercial and academic simulators are successful because they are inherently stable due to the fact that the timestep is not restricted and is chosen for practical reasons; they also have no unexpected oscillations in the solution due to CFL violations; and they also have extremely efficient linear and nonlinear solver options.
On the other hand, the disadvantages include the fact that it requires a nonlinear solution with complete Jacobian construction, the nonlinear solution is not always convergent, and it can be computationally expensive if timesteps are not set carefully.

For two-phase flow, under isothermal condition, the mass-balance equation reads
$$
\frac{\partial}{\partial t}\left(\phi \rho_{j} s_{j}\right)+\operatorname{div}\left(\rho_{j} \mathbf{v}_{j}\right)=\rho_{j} \tilde{q}_{j}, \quad j=o, w
$$
Using nonlinear unknowns $x=\{p, s\}$, the discretized form of conversation equations can be written in residual form as:
$$
\begin{aligned}
r_{o, i} &=\frac{V_{i}}{\Delta t}\left[(\phi \rho(1-s))_{i}^{n+1}-(\phi \rho(1-s))_{i}^{n}\right]-T_{o, i+1 / 2}\left(p_{i+1}-p_{i}\right)+T_{o, i-1 / 2}\left(p_{i}-p_{i-1}\right)+T_{o}^{w}\left(p_{i}-p^{w}\right) \\
r_{w, i} &=\frac{V_{i}}{\Delta t}\left[(\phi \rho s)_{i}^{n+1}-(\phi \rho s)_{i}^{n}\right]-T_{w, i+1 / 2}\left(p_{i+1}-p_{i}\right)+T_{w, i-1 / 2}\left(p_{i}-p_{i-1}\right)+T_{w}^{w}\left(p_{i}-p^{w}\right)
\end{aligned}
$$
Transmissibility in Eq. 2 and Eq. 3 are defined as
$$
T_{j, i+1 / 2}=\left(\frac{k_{x} A}{\Delta x}\right)_{i+1 / 2}\left(\rho_{j} \frac{k_{r j}}{\mu_{j}}\right)_{i+1 / 2}=\Gamma_{i+1 / 2} \beta_{j, i+1 / 2}
$$
