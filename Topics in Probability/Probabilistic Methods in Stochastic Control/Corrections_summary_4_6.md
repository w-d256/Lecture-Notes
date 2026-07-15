# LaTeX Note Review — Chapters 4–6

This document records the mathematical, grammatical, notational, and compilation corrections applied to the uploaded sources. **Line numbers refer to the original uploaded files**, preserved under `original/`. Repeated purely mechanical changes—such as replacing raw `$$...$$`, normalizing punctuation, and standardizing differential notation—are grouped once rather than repeated for every occurrence. The unified patches in `diffs/` record every literal source edit.

## Build and QA result

- The corrected standalone master compiles successfully with pdfLaTeX through `latexmk`.
- Final output: 24 pages.
- Fatal errors: 0.
- Undefined control sequences: 0.
- LaTeX/package warnings: 0.
- Overfull or underfull boxes: 0.
- LaCheck findings: 0.
- Raw `$$...$$` displays in corrected chapters: 0.
- Hidden control characters, tabs, trailing whitespace, and unresolved TODO markers: 0.
- All 24 pages were rasterized and visually inspected for clipping, overlap, missing glyphs, broken delimiters, and malformed equations.

## Global source and compilation corrections

1. **Added the missing `mathrsfs` dependency.** Chapter 6 uses `\mathscr`, but the original controlled build did not load the package that defines it. The standalone master now loads `mathrsfs`.
2. **Replaced every raw `$$...$$` display** with `\[...\]`, `equation`, or an AMS alignment environment. This removes fragile display-math behavior and gives consistent spacing and diagnostics.
3. **Standardized probability and expectation notation** to `\mathbb P` and `\mathbb E`.
4. **Standardized stochastic differentials** to `\mathrm d t`, `\mathrm d s`, and `\mathrm d B_t`, with the integration variable matching the integral.
5. **Standardized transposes** to `{}^\top` instead of ambiguous prime notation.
6. **Standardized mappings and limits** using `\mapsto`, `\longrightarrow`, and properly delimited domains/codomains.
7. **Normalized mathematical punctuation and spacing:** no spaces before commas or periods, correct spacing after abbreviations, punctuation placed outside display delimiters, and consistent use of `\text{...}` inside formulas.
8. **Normalized terminology and capitalization:** “Itô,” “BSDE,” “FBSDE,” “Brownian,” “Lipschitz,” “Gâteaux,” “BMO,” “Feynman–Kac,” “well posed/well-posed,” and consistent sentence capitalization.
9. **Protected mathematics in PDF bookmarks.** The Chapter 5 title now uses `\texorpdfstring` for the symbol `Z`, eliminating hyperref bookmark warnings.
10. **Reflowed long equations and prose** into `aligned`, `split`, and shorter paragraphs, eliminating every overfull/underfull box in the final build.
11. **Removed malformed or invisible delimiter constructions**, unmatched brackets, an unclosed display, and a hidden control character found during the clean rebuild.
12. **Made the master truly standalone.** It supplies the theorem environments and package dependencies expected by the chapter fragments and starts the chapter counter at 4.

# Chapter 4 — Backward Stochastic Differential Equations

## Definitions and the Lipschitz existence theorem

1. **Lines 4–20 — filtration and function spaces.** The Brownian filtration is now stated to satisfy the usual conditions; this is needed for the martingale-representation step used later. `\mathcal S^2` is defined using continuous adapted processes, rather than only progressive measurability, and `\mathcal H^2` includes the correct dimensions and integrability. The generator assumptions now explicitly include progressive measurability and
   \[
   \mathbb E\int_0^T |f(t,0,0)|^2\,\mathrm dt<\infty.
   \]
   The introductory grammar was also repaired (“one-dimensional BSDE,” singular/plural agreement, and complete sentences).

2. **Lines 29–34 — definition of a solution.** The solution pair is now required to lie in `\mathcal S^2\times\mathcal H^2`, and the integral identity is stated for every time, almost surely. The dimensions of `Y` and `Z` are consistent with the Brownian dimension.

3. **Lines 40–100 — fixed-point space and proof.** The original proof used `\mathcal S^2(0,T)^m` with an undefined `m` and a weighted time-`L^2` norm that does not provide the intended `\mathcal S^2` fixed-point space. The map is now constructed on the complete space `\mathcal H^2\times\mathcal H^2`; martingale representation produces `(Y,Z)`, and the resulting `Y` is then shown to belong to `\mathcal S^2`.

4. **Lines 40–100 — notation and adaptation defects.** The typo `(Y,z)` was changed to `(Y,Z)`. The original estimate applied Doob’s inequality to `\int_t^T Z_s\,\mathrm dB_s`, which is not an adapted process in `t`; the proof now estimates the adapted martingale arising from conditional expectation. Itô’s identity starts at an arbitrary `t`, uses `\bar Y_s` consistently, localizes the stochastic integral before taking expectations, and uses Young’s inequality with valid constants.

5. **Line 129 — wrong stochastic integration variable.** An integral over `s` ended in `\mathrm dW_t`; it now ends in `\mathrm dB_s`.

## Comparison, positivity, and a priori estimates

6. **Lines 155–188 — malformed strict-comparison assumption.** The source fragment `f^1(t, .,)<.f^2...` was replaced by a precise condition. The strict-comparison statement now distinguishes strict terminal inequality on an event of positive probability from strict generator inequality on a set of positive `\mathrm dt\otimes\mathrm d\mathbb P` measure.

7. **Lines 155–188 — strictness at time zero.** To infer a deterministic strict inequality at time zero, the corrected statement records the need for a trivial `\mathcal F_0` (or an equivalent deterministic-initial-value assumption). The divided-difference argument in `z` is written correctly for vector-valued `z`, rather than treating it as a scalar quotient.

8. **Lines 193–197 — positivity statement.** The malformed expression `Y_t\ge0,0\le t...` was repaired. Nonnegativity is separated from strict positivity, and the strict condition is stated in terms of positive probability/positive product measure rather than an unquantified pointwise phrase.

9. **Lines 201–220 — data notation.** “wit possible” was corrected, the Brownian-motion notation was made consistent, and the inhomogeneous generator term is now the process `f_t(0,0)`, not the ambiguous `f(0,0)`. Norm definitions and their domains are explicit.

10. **Lines 217–251 — running maximum and missing expectation.** The running maximum is defined before use. The original a priori/stability display omitted an expectation on its right-hand side; the corrected inequality is dimensionally and probabilistically consistent. Its proof now explicitly uses Itô, BDG, Young, and Gronwall estimates.

## Stability and `L^p` solutions

11. **Lines 319–334 — broken theorem/display structure.** An unmatched theorem/math environment and malformed delimiters were repaired. The convergence theorem now states terminal-data convergence in `L^2`, convergence of generators at fixed `(y,z)` in the appropriate product-measure sense, and the uniform Lipschitz bound required for stability.

12. **Lines 319–334 — unjustified use of uniform continuity.** The original proof invoked uniform continuity although only Lipschitz continuity was assumed. The corrected proof uses approximation by simple processes, the common Lipschitz constant, and uniform integrability.

13. **Lines 360–407 — wrong `L^p` data norm.** For the `\mathcal L^{1,p}` regime, the source used
    \[
    \left(\int_0^T |f_t(0,0)|^2\,\mathrm dt\right)^{p/2},
    \]
    which is an `L^2`-in-time datum. It is replaced by the matching quantity
    \[
    \left(\int_0^T |f_t(0,0)|\,\mathrm dt\right)^p.
    \]

14. **Lines 360–407 — dimensional and exponent errors.** The estimate involving the inhomogeneous generator now retains the factor involving `Y` before applying Young’s inequality; the bare term in the original was dimensionally wrong. `I_p^2` was corrected to `I_p^p`. The truncation argument now identifies the approximating data and applies Fatou’s lemma only after the uniform estimate has been established.

## Decoupled FBSDEs and nonlinear Feynman–Kac

15. **Lines 412 onward — filtration typo and notation.** `\mathrm F^t` was corrected to `\mathbb F^t`. State and backward processes now carry consistent superscripts, including the random-initial-state notation `\mathscr X^{t,\eta}`.

16. **Lines 462–463 — both BSDE signs were reversed.** The backward equation is now written in the standard integral form
    \[
    Y_s=g(X_T)+\int_s^T f(r,X_r,Y_r,Z_r)\,\mathrm dr
       -\int_s^T Z_r\,\mathrm dB_r.
    \]

17. **Markov representation theorem — overstatement of `Z`.** The corrected theorem first asserts the safe decoupling-field identity `Y_s^{t,x}=u(s,X_s^{t,x})`. A pointwise Markov representation for `Z` is asserted only under additional differentiability/regularity, and otherwise only in the appropriate `\mathrm dt\otimes\mathrm d\mathbb P` sense.

18. **Markov proof — random initial conditions and flow.** The proof now uses Brownian increments after the starting time, establishes the result first for simple random variables, passes by stability, and invokes flow uniqueness correctly.

19. **Line 527 — unmatched closing bracket.** The extra bracket was removed.

20. **Around line 540 — undefined increment notation.** Undefined objects such as `X_{t_1,t}` and `Y_{t_1,t}` were replaced by the actual process increments. The time-stability estimate now has the correct supremum interval and expectation structure.

21. **Line 609 — wrong time index in the variational equation.** The coefficients in the integrals used `\nabla X_t^\varepsilon`; they now use `\nabla X_s^\varepsilon`, matching the integration variable.

22. **Line 629 — missing time argument in the decoupling field.** `u(x)` was corrected to `u(0,x)` in the initial-time statement and to `u(t,x)` in the general statement.

23. **Nonlinear Feynman–Kac generator.** Covariance matrices are consistently written as `\sigma\sigma^\top`, and the PDE operator is dimensionally explicit.

24. **Line 684 — nonexistent reflected component.** The source called `(Y,Z,K)` the BSDE solution even though no reflection term `K` appears. It now states `(Y,Z)`.

25. **Classical-solution statement.** Differentiability and polynomial-growth assumptions are stated at the point where Itô’s formula and the representation of `Z` require them.

26. **Continuity proof.** A reversed supremum interval and a nested/misplaced expectation were replaced by the standard state- and time-stability estimates.

27. **Viscosity proof — wrong process label, comparison time, and generator comparison.** The source mislabeled the test-function process and compared at time `0` instead of the contact time `t`. More importantly, its pointwise inequality did not compare the two BSDE generators at the same `(Y,Z)`. The corrected proof subtracts `\varphi(s,X_s)` from the stopped BSDE, obtains a shifted Lipschitz generator `F` with `F(s,0,0)\le-\delta`, compares with the zero-terminal shifted BSDE, and uses the linear representation under an equivalent measure to obtain the required strict contradiction at `t`.

28. **Chapter-wide prose corrections.** Repaired missing verbs/articles, fragments, plural disagreement, inconsistent “Brownian motion” symbols, misplaced punctuation, and informal phrases such as “it is easy” where the argument actually required a named estimate. These edits are individually visible in the Chapter 4 patch.

# Chapter 5 — Quadratic BSDEs

## Assumptions and exponential estimate

1. **Title/bookmark correction.** The mathematical symbol `Z` in the title is protected with `\texorpdfstring`, so the printed title remains mathematical while the PDF bookmark contains valid text.

2. **Assumptions Q1–Q3.** Progressive measurability of the random generator is now stated explicitly. The continuity, growth, and derivative assumptions are separated and quantified. The derivative remark now clearly states when the differentiable formulation implies the quadratic-growth/Lipschitz conditions.

3. **Around line 66 — wrong derivative.** The stochastic term produced by Itô’s formula for the exponential transform used `\partial_y f`; it must use the derivative `\partial_y\varphi` of the transform. This is corrected.

4. **Line 74 — missing absolute value.** The growth factor `1+y` was changed to `1+|y|`.

5. **Lines 75 and 88 — exponential-parameter typos.** `e^{\lambda_t}` was corrected to `e^{\lambda t}`, and the stopped estimate uses the stopping time `t_0` rather than the unrelated variable `t`.

6. **Line 115 — wrong integration differential.** An integral indexed by `s` ended in `\mathrm dt`; it now ends in `\mathrm ds`.

7. **Exponential-transform proof.** The smoothing function now has both the lower and upper bounds used later in the terminal estimate. The stopping times, localization, sign choices, conditional expectation, and passage to the limit are written explicitly. This prevents the stochastic integral from being discarded before it has been shown to be a true martingale.

## BMO and comparison

8. **Line 125 — incorrect BMO norm.** The original definition took a supremum over deterministic times. The BMO norm must take the essential supremum over stopping times. The corrected text gives both the conditional quadratic-variation form and the equivalent conditional-energy form for Brownian stochastic integrals.

9. **Lines 128–145 — stochastic exponential and consequences.** The Doléans exponential is defined explicitly. The John–Nirenberg/reverse-Hölder consequences are stated in stopping-time form and with the exponents and conditional expectations properly quantified. The previously undefined running maximum `\mathcal E_T^*` is now defined before its moment estimate.

10. **Lines 153–184 — missing proof.** The source literally contained “Proof to be added.” The package supplies the proof: linearize in `y` and `z`, show the `z` coefficient generates a BMO martingale, change measure by Girsanov, and obtain the conditional representation that yields comparison.

## Monotone stability and existence

11. **Lines 188–283 — wrong functional-analytic justification.** The text relied on “separable dual space.” The required fact is reflexivity of `L^2`; a bounded sequence has a weakly convergent subsequence. The corrected proof distinguishes subsequence convergence from convergence of the full sequence.

12. **Lines 188–283 — index and syntax errors.** `\xi^n` and `\xi_n` are standardized, and the malformed text `$$.and` is removed.

13. **Lines 188–283 — invalid monotone-convergence step for `Z`.** Monotonicity of `Y^n` does not make the quadratic-energy terms in `Z^n` monotone. The corrected proof first obtains a uniform BMO bound, hence uniform integrability of `\int|Z^n|^2`, and then applies a convex exponential test function to `Y^m-Y^n`.

14. **Lines 188–283 — strong `\mathcal H^2` convergence.** The convex-function estimate now directly bounds `\|Z^m-Z^n\|_{\mathcal H^2}^2` by factors containing `\varphi'(Y^m-Y^n)`. Those factors vanish while the energy variables remain uniformly integrable, proving that `(Z^n)` is Cauchy. The limiting-generator passage is then split into a local-Lipschitz term and a fixed-argument convergence term, each justified separately.

15. **Lines 287–349 — malformed process space.** The expression `L^2(\mathcal F\times\mathbb R^{1\times d})` was not a well-defined stochastic-process space. It is replaced by `\mathcal H^2` with the filtration and dimensions already defined.

16. **Lines 287–349 — approximation order.** The infimal-convolution and truncation sequence is now defined in an order that preserves monotonicity and the quadratic bounds. The limiting argument cites the preceding monotone-stability theorem with its hypotheses checked.

17. **Lines 287–349 — uniqueness of `Z`.** Once `Y` is identified, uniqueness of `Z` is obtained from the difference BSDE/Itô isometry rather than asserted without explanation.

## General stability

18. **Lines 354–433 — wrong hard-coded reference.** “BSDE (4.0.3)” was removed because it is not a reliable label in this chapter fragment. The equation is identified by its displayed data instead.

19. **Lines 354–433 — base-solution notation.** The reference pair is consistently `(Y^0,Z^0)`, rather than switching superscripts and indices.

20. **Lines 354–433 — missing absolute values.** Absolute values were inserted in the BDG/moment expressions where powers of signed quantities were being used as norms.

21. **Lines 354–433 — transfer from the Girsanov measure.** The proof now records the uniform reverse-Hölder and negative-moment bounds on the density required to transfer estimates back to `\mathbb P`.

22. **Lines 354–433 — convergence in `\mathcal S^p`.** Running-supremum convergence is derived from the difference BSDE and BDG, rather than inferred only from pointwise convergence.

23. **Chapter-wide prose corrections.** Repaired incomplete sentences, spacing in abbreviations, inconsistent capitalization, missing articles, and punctuation around displayed equations. Every literal instance appears in the Chapter 5 patch.

# Chapter 6 — Fully Coupled Forward–Backward SDEs

## Setup and local solvability

1. **Introductory dimensions and norms.** The dimensions of `X`, `Y`, `Z`, and the Brownian motion are now fixed once and used consistently. The data quantity `I_0` is defined from the correct inhomogeneous coefficients, and assumptions F1–F3 have explicit quantifiers and integrability.

2. **Lines 44–118 — inconsistent Picard input.** The backward generator was fed the input pair `(\boldsymbol y,\boldsymbol z)`, while the difference equation and intended contraction require the output pair `(Y,Z)` at that stage. The mapping and proof now use one consistent construction.

3. **Line 83 — malformed coefficient.** `C\varepsilon-\delta_0+\varepsilon` was repaired to the intended Young-inequality coefficient `C\varepsilon^{-1}\delta_0+\varepsilon`.

4. **Line 106 — malformed norm delimiter.** The unmatched opening delimiter was corrected.

5. **Line 114 — lost data dependence.** The original bound ended by setting the estimate equal to an unspecified constant `C`, dropping both the initial state and the inhomogeneous data. The corrected estimate retains `C(|x|+I_0)`.

6. **Local a priori estimate.** The state term `|x|` is retained throughout, and the choice of the short time horizon is tied to the Lipschitz constants in the contraction factor.

7. **Around line 126 — malformed coefficient difference.** The expression `(|\Delta b_t|+|\Delta f_t|)(\widetilde\Theta_t)` was replaced by
   \[
   |\Delta b_t(\widetilde\Theta_t)|
   +|\Delta f_t(\widetilde\Theta_t)|.
   \]

## Decoupling fields and patching

8. **Around line 150 — missing superscripts.** The generator used an undefined `\Theta_r`; it now uses the process tuple belonging to the solution being discussed.

9. **Around line 179 — malformed function definition.** `\mapsto` was incorrectly used where a function type was being declared, the terminal symbol `\varphi` was undefined, and spacing was missing. The decoupling field is now defined as a map with a specified domain/codomain and terminal relation `Y_{t_2}=u(t_2,X_{t_2})`.

10. **Decoupling-field regularity.** “Lipschitz. continuous” was corrected, and the Lipschitz constant is distinguished from the time interval on which the field exists.

11. **Uniqueness remark.** The argument is now stated for arbitrary starting states and uses local uniqueness, rather than silently assuming all solutions start from the same deterministic point.

12. **Around line 201 — differential mismatch.** An integral in `r` ended in `\mathrm ds`; it now ends in `\mathrm dr`.

13. **Grid indices.** `t_n-1` and `t_i-1` were corrected to `t_{n-1}` and `t_{i-1}`.

14. **Global patching formulas.** Each local backward equation now terminates at the value of the next decoupling field at the grid point. The pieces agree at grid boundaries, so the concatenated process satisfies one global FBSDE.

## Structural global theorem and characteristic equation

15. **Lines 251–360 — unjustified positivity of a ratio.** The source claimed the characteristic ratio `\widehat Y` was positive without assumptions implying a sign. Positivity is not needed; the corrected argument only requires that the denominator process not vanish and that the ratio remain bounded.

16. **Lines 251–360 — variational equations.** Malformed brackets, wrong integration variables, omitted coefficients, and inconsistent difference-quotient notation were repaired. The local terminal map is denoted consistently by `h`, not by an unrelated global symbol `g`.

17. **Characteristic process.** The ratio and its BSDE are derived from the variational system with all coefficient arguments defined. Completion of the square is performed on the correct quadratic terms.

18. **Around line 319 — malformed absolute-value expression.** The unbalanced absolute-value/norm expression was repaired and its dimensions matched.

19. **Around line 335 — undefined process and wrong differential.** The undefined `\widetilde Y` was replaced by the intended variational process, and the integration variable was corrected.

20. **Terminal and exponential notation.** The terminal `\Gamma` index and malformed expression `M_s^{\theta\widehat Y)}` were corrected. The proof now uses localization and a valid stochastic exponential/Girsanov argument.

21. **Nonsmooth local terminal maps.** Differentiability is used first for smooth approximations; the Lipschitz conclusion is then passed to the limit. The original proof implicitly differentiated a merely Lipschitz function.

## Comparison and variational estimates

22. **Comparison theorem — initial condition.** The two systems are stated to have the same initial state before a comparison of their backward components is claimed.

23. **Around line 386 — wrong terminal condition in the auxiliary linear FBSDE.** The source used `\lambda\Delta X_T`; the linear auxiliary system requires `\lambda X_T`.

24. **Comparison proof.** The transformed scalar BSDE and martingale argument were rewritten so every drift and stochastic term is present and the sign of the terminal contribution yields the stated order.

25. **Variational estimate.** Malformed ratio equations, structural identities, and coefficient evaluations were corrected. The estimate now follows from localization, Girsanov, and the bounded characteristic process.

## Monotonicity method and continuation

26. **Monotonicity uniqueness proof.** The stochastic term in Itô’s product formula was malformed. It now has the correct pairings between `\Delta X`, `\Delta Y`, `\Delta Z`, and the coefficient differences. Terminal monotonicity and drift coercivity then imply that all differences vanish.

27. **Reference linear FBSDE — transformation signs.** The correct change of variables is
   \[
   \bar Y=Y-X,
   \qquad
   \bar Z=2Z-\sigma^0,
   \qquad
   Z=\frac{\bar Z+\sigma^0}{2},
   \]
   and the forward diffusion becomes `(\sigma^0-\bar Z)/2`. The signs in the source did not invert the transformation correctly.

28. **Continuation interpolation.** The interpolated coefficient is now
   \[
   f^\alpha=\alpha f+(1-\alpha)x,
   \]
   matching the reference equation. The continuation increment is `\delta(f-X)`, not `\delta(f+X)`, and the terminal increment is retained.

29. **Around line 748 — wrong quantity partitioned.** The source partitioned the time horizon `T`, but the continuation argument advances the homotopy parameter `\alpha\in[0,1]`. The corrected proof chooses `N` so that
   \[
   (N-1)\delta_0<1\le N\delta_0
   \]
   and iterates solvability in `\alpha`.

30. **Continuation contraction proof.** The algebra now uses the monotonicity inequalities with the correct signs and obtains a contraction uniform in the current continuation parameter.

31. **Chapter-wide prose corrections.** “Contract mapping” became “contraction mapping”; capitalization of “backward” and “Brownian” was normalized; missing articles and verbs were supplied; punctuation, display introductions, and singular/plural agreement were repaired. Every literal instance appears in the Chapter 6 patch.

## Package contents

- `Chapter_4_corrected.tex`, `Chapter_5_corrected.tex`, `Chapter_6_corrected.tex`: corrected chapter fragments.
- `Probability_notes_Chapters_4_6_master.tex`: standalone build master.
- `Probability_notes_Chapters_4_6_corrected.pdf`: final 24-page PDF.
- `original/`: byte-for-byte preserved uploaded sources.
- `diffs/`: unified patches showing every literal edit.
- `logs/`: original and corrected compiler/static-analysis logs.
- `qa/rendered_corrected/`: rasterized pages used for visual inspection.
- `qa/contact_sheets/`: contact sheets used for whole-document inspection.
- `MANIFEST.txt` and `SHA256SUMS.txt`: package inventory and checksums.
