# Interior Regularity for the Infinity Laplacian with Bounded Forcing

The infinity Laplacian is

```math
\Delta_\infty u=\langle D^2u\,Du,Du\rangle.
```

The interior regularity assertion considered here allows general bounded forcing.

> [!NOTE]
> **Theorem (Bounded forcing).**
>
> For every integer $`d\ge2`$, there exist $`\alpha_d\in(0,1/3]`$ and $`C_d<\infty`$ such that every bounded continuous viscosity function satisfying $`|\Delta_\infty u|\le M`$ in $`B_R(x_0)\subset\mathbb R^d`$ belongs to $`C^{1,\alpha_d}(B_{R/2}(x_0))`$ and satisfies
>
> ```math
> \|Du\|_{L^\infty(B_{R/2}(x_0))}
> +R^{\alpha_d}[Du]_{C^{0,\alpha_d}(B_{R/2}(x_0))}
> \le C_d\left(\frac{\mathrm{osc}_{B_R(x_0)}u}{R}+(RM)^{1/3}\right).
> ```

Here the viscosity bound means that every upper $`C^2`$ test satisfies $`\Delta_\infty\phi\ge-M`$, and every lower test satisfies $`\Delta_\infty\phi\le M`$. Tests with zero gradient are included. In particular, the theorem applies to continuous right-hand sides $`f`$ with $`\|f\|_\infty\le M`$, without a modulus of continuity in the estimate. The constants depend only on the dimension.

This repository presents a proposed paper proof for formalization. A proof sketch follows; the [PDF manuscript](PDF/infinity-laplacian-bounded-forcing.pdf) contains the detailed argument, including the Liouville rigidity step. Lean formalization has not been carried out.

## Proof sketch

### 1. Obtain local slope bounds and linear blow-ups

Normalize to $`|\Delta_\infty u|\le1`$ on $`B_1`$ with oscillation at most one, and introduce the lift $`U(y,b)=u(y)+b`$. The lift preserves the viscosity inequalities and supplies a nonzero slope direction.

Quadratic perturbations of radial cones give

```math
L_r^\pm(u;z)\le L_R^\pm(u;z)+3(MR)^{1/3},
\qquad
L_r^\pm(u;z)=\frac1r\max_{|h|\le r}\{\pm(u(z+h)-u(z))\}.
```

These estimates imply local Lipschitz continuity. At a fixed center the two limiting slopes agree. Every convergent first-order blow-up is infinity harmonic, attains its Lipschitz constant on a line, and is therefore linear.

### 2. Make flatness uniform over centers and small scales

For a sequence converging to an affine function, a three-point viscosity comparison controls the midpoint defect at every separation. Its penalty uses $`r-r^{3/2}/8`$ and a quadratic term for the midpoint displacement. The theorem of sums gives a lower bound $`-4M_0`$ for the relevant Hessian quadratic form. Its leading negative term is of order $`-r^{-1/2}`$, which contradicts that bound as $`r\to0`$.

Combining this comparison with the fixed-center blow-ups gives a uniform modulus of affine approximation on cylinders of axial radius $`r`$ and transverse radius $`\sqrt\lambda\,r`$, with fitting error $`\lambda r`$. Let $`b(s)`$ be the supremum of the bad parameters at relative radii at most $`s`$. Then $`b(s)\to0`$.

### 3. Extract the entire limiting equation

If $`b`$ has no positive power bound, select bad parameters $`\lambda_i`$ and scales $`r_i`$ such that

```math
\lambda_i\to0,
\qquad \frac{r_i}{\lambda_i}\to0,
```

while a fixed multiple of $`\lambda_i`$ is good at all neighboring centers and comparable or smaller radii. Orient the last axis along a fitting slope of norm $`c_i`$ and set

```math
U_i\bigl(z_i+r_i(\sqrt{\lambda_i}x,t)\bigr)
=U_i(z_i)+r_ic_i\bigl(t+\lambda_i v_i(x,t)\bigr).
```

The rescaled viscosity operator is

```math
D^2v_i[(D_xv_i,1+\lambda_i\partial_tv_i)],
```

with forcing bound $`r_i/(\lambda_i c_i^3)\to0`$. Comparisons between fitting slopes supply compactness. The limit is a nonaffine entire solution of

```math
D^2v[(D_xv,1)]=0.
```

At every center and every $`S>0`$, it has parameters $`p,a`$ for which

```math
\left|v(x+h,t+\ell)-v(x,t)-p\cdot h
-\left(a-\frac{|p|^2}{2}\right)\ell\right|\le256S
```

whenever $`|\ell|\le S`$ and $`|h-p\ell|\le S`$.

### 4. Prove rigidity of the entire limit

The sheared fits give logarithmic bounds on their parameters and uniform subquadratic spatial growth after centering. Define the forward and backward quadratic envelopes

```math
\mathcal P_\ell v(x,t)=\sup_y\left(v(y,t+\ell)-\frac{|y-x|^2}{2\ell}\right),
\qquad
\mathcal M_\ell v(x,t)=\inf_y\left(v(y,t-\ell)+\frac{|y-x|^2}{2\ell}\right).
```

Their forward and backward slopes are monotone and have a common small-length limit. A maximal horizontal Jensen defect produces a barycentric envelope touching the solution from below, with a positive unshifted gap and a finite slope at the contact.

A fair walk between forward and backward optimizing points propagates this contact. The drift of the envelope difference controls the squared velocity discrepancies. A logarithmic velocity bound and the occupation estimates for the time walk localize infinitely many shrinking contact frames around the same terminal point, where the common slope is finite.

In a limit of these frames, both envelope slopes are constant at every positive length. Equality in the quadratic costs forces the optimizing paths onto one line and makes the limit affine. The positive barycentric gap survives compactness and contradicts affinity. This proves the Liouville theorem and rules out the nonaffine limit from Step 3.

### 5. Recover the gradient estimate

Rigidity implies $`b(s)\le Bs^\gamma`$ for some $`0<\gamma\le1`$. The affine fits contain balls of radius comparable to $`r^{1+\gamma/2}`$. Comparing successive slopes gives convergence at rate $`r^{\gamma/2}`$ and a uniform Taylor remainder of order $`1+\alpha_d`$, where

```math
\alpha_d=\frac{\gamma}{2+\gamma}\in(0,1/3].
```

Comparing these remainders at two centers proves Hölder continuity of the gradient. Rescaling with

```math
A=\mathrm{osc}_{B_R(x_0)}u+R^{4/3}M^{1/3}
```

gives the stated estimate.

## Normalized operator

For $`\Delta_\infty^{\mathrm N}u=\langle D^2u\,Du,Du\rangle/|Du|^2`$, the same exponent yields

```math
\|Du\|_{L^\infty(B_{R/2}(x_0))}
+R^{\alpha_d}[Du]_{C^{0,\alpha_d}(B_{R/2}(x_0))}
\le C_d\left(\frac{\mathrm{osc}_{B_R(x_0)}u}{R}+RM\right).
```

At zero gradient, the upper-test convention is $`\lambda_{\max}(D^2\phi)\ge-M`$ and the lower-test convention is $`\lambda_{\min}(D^2\phi)\le M`$. A normalized cone comparison first bounds the Lipschitz constant by $`L_0\lesssim\mathrm{osc}u/R+RM`$. The function then satisfies the unnormalized bound $`|\Delta_\infty u|\le ML_0^2`$, to which the main theorem applies.

## Detailed manuscript

- [PDF manuscript](PDF/infinity-laplacian-bounded-forcing.pdf)
- [Timestamp proof](PDF/infinity-laplacian-bounded-forcing.pdf.ots)

## Conclusion

The proposed proof gives a dimension-dependent positive Hölder exponent for the gradient under the two viscosity inequalities with bounded forcing. The example $`u(x)=|x_1|^{4/3}`$ prevents an exponent greater than $`1/3`$ in this generality; the endpoint $`\alpha=1/3`$ is not asserted.

Draft 1, 12 October 2026.
