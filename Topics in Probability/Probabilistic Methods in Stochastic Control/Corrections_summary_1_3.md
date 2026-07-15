# Review and Correction Log

## Scope

This package reviews the three uploaded chapter fragments for:

- mathematical correctness and completeness;
- grammatical clarity and professional mathematical prose;
- LaTeX syntax, notation, portability, and layout;
- successful compilation as one self-contained document.

The original files are preserved unchanged in `originals/`. The files named `Chapter_1_corrected.tex`, `Chapter_2_corrected.tex`, and `Chapter_3_corrected.tex` contain the reviewed text. Original line numbers below refer to the uploaded source files, not to the corrected files.

## Compilation result

The corrected chapters compile through `Probability_notes_master.tex` with pdfLaTeX. The final document has 26 A4 pages. The final log contains no fatal errors, undefined control sequences, unresolved references, overfull boxes, underfull boxes, or LaTeX warnings. LaCheck reports no findings. Every rendered page was inspected for clipping, overlap, broken glyphs, and malformed display mathematics.

The global source cleanup also made the following changes:

1. Replaced every raw `$$...$$` display with an AMS-compatible display environment.
2. Standardized expectation, differential, transpose, trace, map, and set notation, including `\mathbb E`, `\mathrm d`, `\top`, `\operatorname{tr}`, `\mapsto`, and `\mathbb R`.
3. Standardized “càdlàg,” “submartingale,” “Itô,” “Feynman--Kac,” and “Hamilton--Jacobi--Bellman.”
4. Removed explicit spaces before display punctuation and repaired abbreviation spacing.
5. Broke long formulas into `aligned` or related environments where needed.
6. Defined all custom theorem environments in the standalone master file.

---

# Chapter 1 — Preliminaries

## Continuous-time stochastic processes

1. **Original lines 5–9: wording and notation.** “Random variables valued in” was changed to “random variables taking values in.” “For the aim of this book” was changed to “for the purposes of this book.” Split math fragments such as `$\mathcal X$ $=\mathbb R^d$` were consolidated into one expression, `\mathcal X=\mathbb R^d`.

2. **Original line 14: filtration definition.** A filtration is now defined as an increasing family of sub-\(\sigma\)-fields of \(\mathcal F\), not as “\(\sigma\)-fields of \(\mathcal F\).” The containment is written explicitly as
   \[
   \mathcal F_s\subseteq\mathcal F_t\subseteq\mathcal F,
   \qquad s\le t.
   \]

3. **Original lines 18–22: right-continuity.** The original definition used an intersection over \(s\ge t\), which is tautological because it includes \(s=t\). It was replaced by
   \[
   \mathcal F_{t+}:=\bigcap_{s>t}\mathcal F_s=\mathcal F_t.
   \]
   A finite-horizon convention at \(T\) was added.

4. **Original line 22: completeness.** The undefined symbol \(\bar T\) was removed. The class of null sets is now defined precisely, and completeness is stated through inclusion of all \(P\)-null subsets in \(\mathcal F_0\).

5. **Original lines 25–30: usual augmentation.** The augmentation now explicitly combines completion and right-continuity. The former informal phrase about “adding negligible sets” was replaced by a mathematical definition and explanatory remark.

6. **Original lines 33–40: measurability notions.** “When we consider path” was corrected to “when we consider a sample path.” Maps are written with `\mapsto`. List punctuation was repaired. The predictable \(\sigma\)-field is described using the standard left-continuous adapted generators, and “càd-làg” was standardized to “càdlàg.”

7. **Original lines 43–50: supermartingales.** The standard integrability condition \(X_t\in L^1\) is now imposed. The conditional-expectation inequality is stated for all \(s\le t\), almost surely. This avoids relying silently on an extended conditional-expectation convention.

8. **Original lines 53–58: local martingales.** “This notation” was corrected to “this notion.” The localizing sequence is required to increase to the horizon almost surely. The infinite-horizon and finite-horizon formulations are distinguished, and the prose describing the role of local martingales was rewritten.

9. **Original line 68: class \((DL)\).** The original statement confused class \((DL)\) with the stronger class \((D)\). The corrected definition fixes a finite deterministic bound \(a\) and requires uniform integrability of \(\{M_\tau:\tau\le a\}\). The martingale criterion is stated in the proper local class-\((DL)\) form.

10. **Original lines 70–84: Snell envelope.** The typo `\mathcal F_{t,T}` was corrected to the stopping-time set `\mathcal T_{t,T}`. The essential supremum is typeset with `\operatorname*{ess\,sup}`. The reward process is assumed to have the regularity needed for the theorem. The envelope is identified as the smallest càdlàg supermartingale dominating the reward. The former unconditional continuity claim was removed: continuity of the envelope is now tied to a continuous filtration and the stated jump assumptions. The first-contact stopping time has an explicit domain and terminal truncation.

## Stochastic calculus

11. **Original lines 92–104: Itô formula.** The domain and regularity of the test function are specified. Vector and matrix dimensions are made explicit. Every derivative is evaluated at \((t,X_t)\), and the stochastic term is oriented consistently:
    \[
    \nabla_x f(t,X_t)^\top\sigma_t\,\mathrm dW_t.
    \]
    The ambiguous unqualified Hessian notation was replaced by \(D_x^2f\).

12. **Original lines 107–115: infinitesimal generator.** The generator is now an operator acting on a test function, with one consistent spatial variable. The diffusion covariance is written as \(\sigma\sigma^\top\). The space-time generator is distinguished from the purely spatial operator.

13. **Original lines 119–140: Feynman--Kac theorem.** Bare `R` was replaced by `\mathbb R`. The equation now contains \(\mathcal A F\), not \(\mathcal A f\). The invalid `£^2` token was replaced by a dimensionally correct square-integrability condition involving \(\sigma^\top\nabla F\). Conditional expectation notation is defined. “stochasstic” was corrected to “stochastic,” and the state SDE now uses \(\mathrm ds\), not \(\mathrm dt\), under an \(s\)-indexed integral. Regularity and growth assumptions were added.

14. **Original lines 142–166: Kolmogorov equations.** The transition kernel now has the correct conditional form. The variable on which the backward generator acts is identified. The backward terminal condition and forward initial condition are stated distributionally. The undefined matrix \(C_{ij}\) was replaced by
    \[
    a_{ij}(t,x)=(\sigma\sigma^\top)_{ij}(t,x).
    \]
    The formal adjoint is written with this covariance, and the Fokker--Planck interpretation is stated accurately.

## Regularity estimates

15. **Original lines 170–177: Doob inequalities.** The stopping time is bounded, and the relevant terminal integrability is stated. The original second inequality had the \(p\)-th power outside the expectation; it is now
    \[
    \mathbb E\!\left[\left(\sup_{0\le u\le\tau}|X_u|\right)^p\right]
    \le \left(\frac p{p-1}\right)^p\mathbb E|X_\tau|^p.
    \]

16. **Original line 183: prose.** “The first above inequality and the theorem of convergence for martingales” was rewritten as “the first inequality above and the martingale convergence theorem.”

17. **Original lines 188–197: Kunita--Watanabe.** The opening grammar was repaired. Predictability and integrability of the integrands are stated. Angle brackets use `\langle` and `\rangle`. The vague and incorrect “product measure” sentence was replaced by a precise Radon--Nikodym density consequence relative to \(A=\langle M\rangle+\langle N\rangle\), with \(|c|\le\sqrt{ab}\).

18. **Original lines 201–211: Burkholder--Davis--Gundy.** The theorem is stated for \(M_0=0\), with the alternative of applying it to \(M-M_0\). The \(p\)-th power is placed inside the expectation. Proper bracket notation is used, the undefined `\overline{\mathbb T}` was removed, and the corollary now includes the integrability needed to upgrade a local martingale to a martingale.

19. **Original lines 215–237: SDE moment estimate.** Progressive measurability is stated where coefficients may be random. The integrability assumption on the inhomogeneous term is strengthened to the \(p\)-moment required by the conclusion. The estimate retains the actual \(\kappa\)-term rather than hiding it inside an unexplained constant.

20. **Original lines 241–259: stability estimate.** The original supremum estimate with \(e^{2\beta_0(s-t)}\) was false, especially when \(\beta_0<0\), because the supremum includes the initial time. The corrected chapter separates:
    - the endpoint estimate
      \[
      \mathbb E|X_s^{t,x}-X_s^{t,y}|^2
      \le e^{2\beta_0(s-t)}|x-y|^2;
      \]
    - the supremum estimate
      \[
      \mathbb E\!\left[\sup_{t\le u\le s}|X_u^{t,x}-X_u^{t,y}|^2\right]
      \le Ce^{C(s-t)}|x-y|^2.
      \]

21. **Original lines 254–257: sentence order.** The monotonicity constant \(\beta_0\) is introduced before it is used. The dangling phrase “whose existence is guaranteed by the assumptions” was removed.

22. **Original lines 260–273: proofs of estimates.** The former “proof” merely quoted Gronwall. The corrected proof explains the required sequence: Itô formula, BDG, Young’s inequality, absorption of the martingale term, and Gronwall. The endpoint estimate is derived separately by taking expectations before a supremum is introduced.

23. **Additional Chapter 1 grammar.** Awkward phrases such as “for the aim of this book,” “trends of stochastic processes,” “come to,” “from the view of,” “propose the useful result,” and “we can have an estimate” were rewritten as standard mathematical prose. Broken sentences were joined, articles were restored, and punctuation was normalized.

24. **Chapter 1 layout.** Long theorem statements and covariance inequalities were reflowed. The final source compiles with no overfull or underfull boxes; no `\sloppy` suppression was used.

---

# Chapter 2 — The Classical PDE Approach

## Problem setup

1. **Original lines 5–14: model description.** The state is described as taking values in \(\mathbb R^n\), and the filtered probability-space tuple is kept in one math environment. The coefficient assumption is correctly stated as Lipschitz continuity in the state variable, uniformly in the control—not “Lipschitz in \(A\).”

2. **Original lines 18–29: controlled-state notation.** The state now displays its dependence on the control as \(X^{t,x,\alpha}\). This prevents ambiguity when different controls are compared. The limit notation was simplified from `h\downarrow0^{+}` to `h\downarrow0`, and the restriction \(t+h\le T\) is included.

3. **Original lines 30–50: payoff assumptions.** “Let \(f\) and \(g\) two measurable functions” was corrected. The terminal-reward assumptions are displayed clearly. The distinction between an extended-valued well-defined objective and a finite value function is explained, and the growth conditions are stated in a form compatible with the moment estimates.

4. **Original line 56: Markov control.** The singular/plural mismatch was repaired. A Markov control is now defined through a measurable feedback map \(a:[0,T]\times\mathbb R^n\to A\), with \(\alpha_s=a(s,X_s^{t,x,\alpha})\).

5. **Original lines 61–93: discount factor.** The unused parameter \(\beta\) is now incorporated through
   \[
   D(t,s)=e^{-\beta(s-t)}.
   \]
   All finite- and infinite-horizon formulas use consistent time arguments. “Discount rate” and “discount factor” are no longer conflated. Time-dependent Markov controls and stationary controls are distinguished.

## Dynamic programming principle

6. **Original lines 97–114: DPP formulation.** The former simultaneous `\sup_\theta` and `\inf_\theta` presentation was replaced by the standard identity for an arbitrary admissible stopping time \(\theta\). This removes the tautology caused by allowing \(\theta=t\) and states the content of the principle directly.

7. **Original lines 116–160: measurable pasting.** The continuation control after \(\theta\) is treated as a shifted and concatenated control, not merely as “the Markovian structure.” The random-initial-state continuation functional is clarified. The invalid pathwise selection \(\alpha^{\varepsilon,\omega}\) is replaced by explicit measurable-selection/stability assumptions. The overlapping cases at \(s=\theta\) are removed. The proof now explains the two DPP inequalities and the role of concatenation.

## HJB equation

8. **Original line 163: spelling.** “Deriviation” was corrected to “Derivation.”

9. **Original lines 166–188: short-time argument.** The constant control on \([t,t+h]\) is introduced cleanly. The full drift integrand is grouped correctly. The stochastic integral is handled by localization and integrability. The limit is justified through continuity and dominated convergence rather than being mislabeled as an application of the mean-value theorem.

10. **Original lines 195–205: equality for an optimal control.** The distinction between equality along an optimal trajectory and a pointwise HJB identity is made explicit. A measurable feedback selector is introduced before a pointwise maximizer is used.

11. **Original lines 209–214: Hamiltonian.** The symmetric-matrix space is defined. Every covariance is written as \(\sigma(x,a)\sigma(x,a)^\top\). “programing” was corrected to “programming.”

12. **Original lines 222–243: selector and feedback SDE.** `\operatorname*{arg\,max}` replaces the malformed `\arg \max`. Attainment and measurable selection are stated as assumptions. `v(T,.)` was changed to `v(T,\cdot)`. The missing time argument in the running reward was restored. Most importantly, the drift differential omitted in the original feedback SDE was restored:
    \[
    \mathrm dX_s^*
    =b(s,X_s^*,a^*(s,X_s^*))\,\mathrm ds
    +\sigma(s,X_s^*,a^*(s,X_s^*))\,\mathrm dW_s.
    \]

## Verification theorems

13. **Original lines 283–296: theorem description.** “There exists constants” was corrected. Bare `R^n` was replaced by `\mathbb R^n`. The result is accurately described as a supersolution verification bound rather than a generic PDE comparison principle.

14. **Original lines 298–308: localization.** Drift terms are grouped under one integral. The stray variable \(z\) in \(z\wedge\tau_n\) was replaced by the intended process-time variable. The stopped stochastic-integral process has a consistent index range.

15. **Original lines 310–337: missing time arguments and moments.** Every occurrence of the running reward now contains its time argument. The polynomial-growth exponent is matched with the required state moments. Uniform integrability is stated where localization limits are taken; dominated convergence is not invoked without its hypotheses.

16. **Original lines 339–377: optimal-feedback verification.** The terminal condition is `w(T,\cdot)=g`. The feedback process notation and punctuation were repaired. Every running-reward argument is complete, and admissibility of the selected feedback is an explicit assumption.

17. **Original lines 380–425: infinite-horizon verification.** Grammar was corrected, and the gradient is written as \(Dw(X_u)\) for a time-independent function. A stray period was removed. The terminal term is treated with a limsup and the stated transversality condition, rather than being discarded incorrectly by dominated convergence. The former claim that the condition forces the term to “decay to zero” was removed: the condition only controls its asymptotic sign for the verification inequality.

18. **Original lines 426–458: optimal infinite-horizon feedback.** The role of the liminf condition is stated precisely. Redundant wording around the measurable selector was removed, and equality is derived by applying the HJB equation along the feedback trajectory.

## Applications

19. **Original lines 461–494: quadratic transaction costs.** The position and trading-rate variables are now consistent. The chapter uses \(q\) for the position and \(u=\dot q\) for the control. The HJB term is
    \[
    \sup_u\left\{mq-\frac{\gamma\sigma^2}{2}q^2
    -\frac\lambda2u^2+\mathcal L^\mu V+V_qu\right\}.
    \]
    The optimizer is \(u^*=V_q/\lambda\), and the optimized contribution is \((V_q)^2/(2\lambda)\). Ambiguous notation such as `\partial_\phi V^2` was removed. The prose now says that the running reward is quadratic, not that all model coefficients are quadratic.

20. **Original line 496: spelling.** “Stochasic” was corrected to “Stochastic.”

21. **Original lines 497–520: singular control generator.** The missing factor \(1/2\) was restored in the generator of \(\mathrm dX_s=a\,\mathrm dW_s\):
    \[
    \partial_tv+\frac12a^2\partial_{xx}v.
    \]
    The local Itô calculation and Hamiltonian now agree.

22. **Original lines 531–551: concave-envelope example.** The false statement that a call payoff equals its concave envelope was removed. A call payoff is convex and has no finite concave majorant on all of \(\mathbb R\); with unbounded volatility control, its value is unbounded. The corrected chapter uses \(g(x)=-|x|\) as a finite, concave, nonsmooth payoff and supplies a separate terminal-discontinuity example. Concave-envelope notation is standardized. The HJB is expressed as the appropriate variational inequality.

23. **Original line 551: cross-reference.** The claim that viscosity solutions appear in “the next chapter” was removed because the supplied next chapter concerns BSDEs. The corrected text refers to the viscosity formulation without an incorrect chapter pointer.

24. **Additional Chapter 2 grammar.** Articles, subject-verb agreement, punctuation, and standard phrases were corrected throughout. Examples include “the existence … for every \(\alpha\),” “state equation,” “let \(f\) be,” “the Feynman--Kac formula,” “from one problem to another,” and “suppose that \(v\in C^{1,2}\).” Informal abbreviations such as “s.t.” were replaced by full prose.

25. **Chapter 2 layout.** Long Hamiltonians, stopping-time expressions, and verification displays were reflowed with AMS environments. The corrected file has no raw `$$` and produces no box warnings.

---

# Chapter 3 — The BSDE Approach

## First-order necessary conditions

1. **Original line 3: assumptions and dimensions.** The state dimension remains \(n\), while the Brownian dimension remains \(d\), avoiding the original collision. Random coefficient fields are required to be progressively measurable when they depend on \(\omega\). The terminal quantity is called a reward to match the maximization convention.

2. **Original line 6: constrained variation.** The original statement that the first variation is zero at an optimum was false for boundary points of a convex control set. The corrected text states that every feasible one-sided directional derivative is nonpositive, with equality only under two-sided interior variations.

3. **Original lines 8–17: perturbation notation and moments.** The state notation is unified. The convex perturbation is
   \[
   \alpha^\varepsilon=(1-\varepsilon)\alpha+\varepsilon\alpha',
   \qquad 0\le\varepsilon\le1.
   \]
   “can be derive” was corrected. The moment condition on the direction \(\beta\) is stated at the order needed by the variational estimates.

4. **Original lines 19–75: first-variation proof.** The fourth-moment and uniform-integrability requirements used in the remainder estimates are made explicit. Excessive invisible delimiters were removed. The dimensionally incorrect stray `\mathrm dt` on the left side of the supremum estimate was deleted. The proof now identifies the BDG, Young, and Gronwall steps.

5. **Original lines 77–85: directional versus Gâteaux derivative.** “Gateaux” was corrected to “Gâteaux,” and the map arrow is `\mapsto`, not `\hookrightarrow`. A one-sided limit is accurately called a directional derivative. The text reserves “Gâteaux derivative” for a two-sided linear derivative on an appropriate open domain.

6. **Original lines 91–114: terminal perturbation.** Every terminal expansion now uses \(V_T^\varepsilon\), not \(V_t^\varepsilon\). Malformed nested invisible delimiters were replaced by ordinary grouped expressions. The dominated-convergence hypotheses are stated.

## Adjoint equation and necessary condition

7. **Original lines 118–126: Hamiltonian order.** The argument order is fixed once and used throughout:
   \[
   H(t,x,a,y,z)
   =b(t,x,a)^\top y
   +\operatorname{tr}(\sigma(t,x,a)^\top z)
   +f(t,x,a).
   \]
   The adjoint BSDE uses the same order.

8. **Original lines 131–145: sign of the duality formula.** The original formula had the wrong minus sign. For the maximized reward convention, the corrected derivative is
   \[
   D J(\alpha;\beta)
   =\mathbb E\int_0^T
   D_aH(t,X_t,\alpha_t,Y_t,Z_t)\cdot\beta_t\,\mathrm dt.
   \]

9. **Original line 148: proof of duality.** The proof no longer says that the result follows “directly” without explanation. It applies Itô’s product formula to \(Y_t^\top V_t\), identifies the quadratic-covariation term, and explains the cancellation of the \(D_xb\) and \(D_x\sigma\) contributions. “Ito” was corrected to “Itô.”

10. **Original lines 151–156: pointwise condition.** A generic action is denoted by \(a\), rather than reusing \(\alpha\). The maximum-principle inequality is
    \[
    D_aH(t,X_t,\hat\alpha_t,Y_t,Z_t)
    \cdot(a-\hat\alpha_t)\le0.
    \]
    The use of spike variations and measurable selection to pass from an integrated inequality to an almost-everywhere pointwise condition is stated.

11. **Original lines 157–164: Hamiltonian inequality.** The inequality was reversed in the original. Because the control problem is a maximization problem, the corrected condition is
    \[
    H(t,X_t,\hat\alpha_t,Y_t,Z_t)
    \ge H(t,X_t,a,Y_t,Z_t).
    \]
    The equivalence with the first-order condition is tied to concavity in the control.

## Sufficient conditions

12. **Original lines 166–180: theorem statement.** Candidate-control notation is consistent. Joint concavity is stated for \((x,a)\mapsto H(t,x,a,\hat Y_t,\hat Z_t)\). The maximum condition holds for almost every time, almost surely.

13. **Original lines 182–205: proof notation and missing differential.** The admissible-control set has one symbol. Running-reward differences are grouped under the integral, and every Hamiltonian has the correct argument order. The missing `\mathrm dt` in the drift-pairing integral was restored.

14. **Original lines 208–217: sign of the concluding bracket.** The original called the crucial concavity bracket nonpositive, which contradicts the desired inequality. It is correctly shown to be nonnegative, yielding \(J(\hat\alpha)\ge J(\alpha)\).

## Connection with dynamic programming

15. **Original lines 218–243: notation and prose.** “The connection” and “state equation” replace incomplete phrases. Hamiltonian order is consistent, and all covariance matrices use \(\sigma\sigma^\top\). “is solution” was corrected to “is a solution.”

16. **Original lines 259–289: undefined Hamiltonian and tensor contraction.** The undefined \(\mathcal H\) was replaced by the defined Hamiltonian \(H\). The third-derivative contraction is written componentwise rather than as an invalid ordinary matrix trace:
    \[
    \frac12\sum_{j,k=1}^n
    (\sigma\sigma^\top)_{jk}
    \partial_{x_jx_kx_i}^3v.
    \]

17. **Original lines 292–295: terminal condition typo.** `v(T,.)=.g(.)` was replaced by `v(T,\cdot)=g(\cdot)`.

## Mean--variance portfolio optimization

18. **Original lines 318–338: setup and sign convention.** Raw display delimiters inside prose were removed. The squared terminal loss is written unambiguously as \(\mathbb E[(X_T-\lambda)^2]\). Duplicate “that” was removed. The subsection explicitly notes that it is a minimization problem and adapts the preceding maximum-principle sign convention accordingly.

19. **Original line 340: grammar.** “Let \(\hat\alpha\) a candidate” was corrected to “Let \(\hat\alpha\) be a candidate.”

20. **Original line 377: terminal condition.** The second affine-adjoint ODE now has the correct terminal condition
    \[
    \psi(T)=-2\lambda,
    \]
    rather than repeating \(\varphi(T)\).

21. **Original lines 413–427: auxiliary problem and optimizer.** “auxillary” was corrected to “auxiliary.” The text now identifies the exact scalar function maximized by \(\lambda_m\).

22. **Original lines 462–475: convex duality and variance identity.** The original referred to maximizing the number \(V(m)\) and minimizing the number \(\widetilde V(\lambda_m)\); both were replaced by the actual functions of \(\lambda\) and \(q\). The crucial sign is corrected:
    \[
    V(m)=\widetilde V(\lambda_m)-(m-\lambda_m)^2.
    \]
    Hence
    \[
    V(m)
    =\mathbb E[(\hat X_T^{\lambda_m}-\lambda_m)^2]
    -(\mathbb E[\hat X_T^{\lambda_m}]-\lambda_m)^2
    =\operatorname{Var}(\hat X_T^{\lambda_m}).
    \]

## Exponential-utility optimization

23. **Original lines 478–496: market and admissibility.** The run-on sentence defining the model was split. The lower-bound admissibility condition is described as a deterministic lower bound when that convention is used, and the broader supermartingale admissibility alternative is noted. Punctuation around the utility and objective was repaired.

24. **Original lines 498–520: martingale optimality principle.** “satisfying the following properties” replaces the fragmentary introduction. `(i i)` was corrected to `(ii)`. Determinism of \(J_0\) is tied to the usual triviality of \(\mathcal F_0\). The value is not asserted before the martingale candidate has been established.

25. **Original lines 523–560: completing the square.** The prose was corrected to “constructed by completing the square” and “the conditions are satisfied.” The generator and optimizer are presented consistently:
    \[
    f(t,z)=-z\frac{b_t}{\sigma_t}
    -\frac1{2\eta}\left|\frac{b_t}{\sigma_t}\right|^2,
    \qquad
    \hat\alpha_t=\frac{Z_t}{\sigma_t}
    +\frac{b_t}{\eta\sigma_t^2}.
    \]

26. **Original lines 563–574: wording.** “The value function to problem” became “The value function for the problem,” and “given from above” became “given above.”

27. **Original lines 575–582: sign of the optimal process.** Since \(C^{\hat\alpha}=-1\), the original identity \(J^{\hat\alpha}=M^{\hat\alpha}\) was wrong. The corrected process is
    \[
    J_t^{\hat\alpha}=-M_t^{\hat\alpha}.
    \]
    The stochastic-exponential formula therefore carries the required leading minus sign. Its martingale property still follows because the negative of a true martingale is a martingale.

28. **Original lines 560 and 575–582: admissibility gap.** The corrected theorem assumes an admissibility class strong enough to make the candidate family a supermartingale and requires that the candidate optimizer belongs to that class. It no longer treats a deterministic lower bound for the optimal wealth as automatic from square integrability.

29. **Original line 585: interpretation.** The strategy is not \(Z\) itself. The liability-hedging component is \(Z_t/\sigma_t\), and the myopic component is \(b_t/(\eta\sigma_t^2)\). The change of measure is generated by the market price of risk \(b_t/\sigma_t\), not by \(Y\). The role of \(Y\) is described as the liability-adjusted certainty equivalent under the corresponding martingale measure.

30. **Additional Chapter 3 grammar.** Commas, articles, subject-verb agreement, and standard terminology were repaired throughout. Examples include “on the right-hand side,” “the dominated convergence theorem,” “any solution … the adjoint processes,” “risk-free,” “can also be solved,” “are sought in the form,” and “maximizer/minimizer.”

31. **Chapter 3 layout.** The variational SDEs, maximum-principle identities, tensor formulas, and stochastic exponentials were reflowed. The corrected source has no raw `$$`, malformed invisible delimiters, control characters, or box warnings.

---

# Highest-priority mathematical corrections

1. Chapter 1 right-continuity now uses an intersection over strictly later times, \(s>t\).
2. The Snell-envelope stopping-time set and continuity assumptions are corrected.
3. The Feynman--Kac equation uses \(\mathcal AF\), and the invalid `£^2` token is removed.
4. The Doob and BDG supremum powers are inside the expectations.
5. The false SDE supremum stability bound is replaced by separate endpoint and supremum estimates.
6. The Chapter 2 optimal feedback SDE includes the missing drift differential \(\mathrm ds\).
7. The singular-control generator includes the missing factor \(1/2\).
8. The false call-payoff/concave-envelope example is replaced by mathematically valid examples.
9. The Chapter 3 Hamiltonian derivative formula has the correct positive sign.
10. The Hamiltonian maximum inequality points in the correct direction.
11. The sufficient maximum-principle proof uses a nonnegative concavity bracket.
12. The mean--variance affine adjoint has \(\psi(T)=-2\lambda\).
13. The mean--variance conjugacy identity subtracts the squared mean discrepancy, producing a variance.
14. The exponential-utility candidate satisfies \(J^{\hat\alpha}=-M^{\hat\alpha}\), not \(+M^{\hat\alpha}\).

# Files in the package

- `Probability_notes_master.tex`: self-contained master document.
- `Chapter_1_corrected.tex`: reviewed Chapter 1 fragment.
- `Chapter_2_corrected.tex`: reviewed Chapter 2 fragment.
- `Chapter_3_corrected.tex`: reviewed Chapter 3 fragment.
- `Probability_notes_corrected.pdf`: compiled reviewed notes.
- `originals/`: untouched uploaded source files.
- `checks/latexmk.log`: full compilation transcript.
- `checks/lacheck.txt`: LaCheck output.
- `checks/Source_checks.txt`: source-level sanity checks.
- `checks/Compilation_report.txt`: concise build and visual-verification report.
