# LaTeX Note Review — Reflected SDEs, PDE Characterizations, and Reflected BSDEs

This report records the mathematical, grammatical, notational, and compilation corrections applied to the four uploaded chapter fragments. The original uploads are preserved byte-for-byte under `originals/`; all edited files have separate `_corrected.tex` names. Original line ranges below refer to those preserved uploads. Repeated mechanical edits—punctuation, spacing, delimiter normalization, and terminology—are grouped once; the unified patches in `diffs/` record every literal source change.

## Scope

The review covered:

- mathematical correctness of definitions, theorem statements, estimates, and proofs;
- missing assumptions, edge cases, type inconsistencies, and sign errors;
- grammar, mathematical prose, terminology, punctuation, and notation;
- LaTeX syntax, portability, theorem environments, hyperlinks, and page layout;
- clean compilation, log inspection, static source checking, PDF rendering, and all-page visual inspection.

## Build and quality-assurance result

- Corrected master: `Corrected_notes_master.tex`
- Engine: pdfLaTeX through `latexmk`
- Final PDF: `Corrected_notes.pdf`
- Final page count: **28 US Letter pages**
- Fatal LaTeX errors: **0**
- Undefined control sequences: **0**
- Undefined references or citations: **0**
- Multiply defined labels: **0**
- LaTeX or package warnings: **0**
- Missing-character warnings: **0**
- Overfull or underfull boxes: **0**
- LaCheck findings: **0**
- Raw `$$...$$` displays in corrected sources: **0**
- Tabs, trailing whitespace, and unresolved `TODO`/`FIXME`/`XXX` markers: **0**
- Rendered-page inspection: **all 28 pages checked at 200 dpi**; no clipping, overlap, missing glyphs, malformed delimiters, blank content pages, broken theorem boundaries, or equations outside the text block.
- Stable build: the clean final compilation and the subsequent no-change compilation both produced 28 pages.

The uploaded chapters were fragments rather than standalone documents. A minimum compatibility master reconstructed for the baseline produced a 47-page PDF and exposed three overfull equations, with excesses of approximately 21.80 pt, 6.90 pt, and 26.42 pt. The corrected standalone master eliminates all three layout defects.

## Project-wide corrections

1. **Portable master document.** Added a self-contained `book` master with the necessary encoding, font, geometry, AMS, theorem, list, bold-math, microtype, and hyperlink packages. The master defines all theorem environments and common macros, inputs the corrected chapters in order, and no longer relies on an unidentified external preamble.

2. **Originals preserved.** The four uploads were copied without modification to `originals/`. Corrected copies use portable filenames without spaces or parenthesized duplicate suffixes.

3. **Display-math repair.** Replaced every raw `$$...$$` display with `equation`, `align`, `aligned`, or `\[...\]`. This gives AMS-compatible spacing, numbering, and error diagnostics.

4. **Malformed LaTeX repaired.** Corrected unmatched delimiters, missing braces, invalid or undefined commands, incorrect integral endpoints, stray alignment tokens, malformed accents, and formulas that compiled only because TeX interpreted them in an unintended way.

5. **Notation standardized conservatively.** Standardized probability and expectation to `\mathbb P` and `\mathbb E`, differentials to `\mathrm d`, indicators to `\mathbf 1`, transposes to `{}^\top`, Euclidean spaces to `\mathbb R^d`, domains and codomains of maps, boundary notation, norms, positive parts, and finite-variation integrals.

6. **Symbol collisions removed.** Separated the one-dimensional regulator map, multidimensional correction map, finite-variation process, obstacle, and Lipschitz constant so that a single letter no longer denotes incompatible mathematical objects.

7. **Object types repaired.** Rewrote expressions so vectors, matrices, set-valued reflection fields, measures, paths, and scalar regulators are used in type-compatible ways. In particular, products with reflection directions and covariance matrices now have explicit dimensions and meanings.

8. **Terminology standardized.** Standardized “Skorokhod,” “reflected SDE,” “reflection,” “Brownian motion,” “Wiener process,” “Itô,” “Feynman--Kac,” “Snell envelope,” “càdlàg,” “well posed/well-posed,” “submartingale problem,” and “viscosity solution.”

9. **Grammar and mathematical prose.** Repaired sentence fragments, run-on sentences, missing articles, subject--verb disagreement, singular/plural disagreement, ambiguous pronouns, capitalization, spelling, and punctuation after displayed formulas. Informal phrases such as “obvious,” “easy,” and “one can see” were replaced by the missing argument when the omission concealed a real step.

10. **Proof organization.** Reorganized compressed arguments into construction, well-definedness, estimate, convergence, identification, and uniqueness steps. This is especially important in the weak-existence, Snell-envelope, penalization, and viscosity sections.

11. **Long-display layout.** Reflowed long stochastic estimates, stopping-time formulas, and obstacle-PDE expressions with `aligned` or multiline displays. Short optional chapter titles prevent long running heads from entering the margin.

12. **Hyperref title-page repair.** Temporarily disabled page anchors around `\maketitle`, then re-enabled them before the table of contents. This removes duplicate-destination warnings in the standalone book.

13. **Mechanical source cleanup.** Removed raw tab characters, trailing whitespace, inconsistent blank-line spacing, spaces before punctuation, inconsistent abbreviation spacing, and obsolete source artifacts.

# Chapter 1 — The Skorokhod Problem and One-Dimensional Reflected SDEs

## Definitions and explicit Skorokhod map (original lines 1–92)

1. **Standard title and state-space language.** Replaced “Skorokhod’s Problem” by the standard “Skorokhod problem,” replaced “positive half-line” by “nonnegative half-line,” and removed informal wording such as “glitching.”

2. **Complete definition.** Stated the reflected path, regulator, nonnegativity, monotonicity, initial normalization, and support condition in one logically complete definition. The regulator is now explicitly a continuous scalar path and the Stieltjes integral is well typed.

3. **Explicit formula and sign.** Corrected the regulator to
   \[
     \ell(t)=\sup_{0\le s\le t}[-f(s)]^+
             =-\min_{0\le s\le t}(f(s)\wedge0),
     \qquad g=f+\ell.
   \]
   The original later used the incompatible sign convention `l=f-g`; the correct relation is `\ell=g-f`.

4. **Existence proof supplied.** Verified continuity, monotonicity, nonnegativity, and the support of `\mathrm d\ell`. The original formula was asserted without proving that the regulator increases only on the boundary.

5. **Uniqueness proof repaired.** Supplied the missing symmetric argument: every admissible regulator dominates the running negative part, while any strict excess contradicts the support condition at its first increase. This proves both regulator and reflected-path uniqueness.

6. **Extension outside the normalized domain.** Clarified that the explicit map may be evaluated for any continuous path, but when `f(0)<0` its initial correction is positive and it no longer solves the normalized problem with `\ell(0)=0`.

7. **Lipschitz estimates.** Corrected the path and regulator estimates to
   \[
     \|\Lambda f-\Lambda h\|_T\le \|f-h\|_T,
     \qquad
     \|\Gamma f-\Gamma h\|_T\le 2\|f-h\|_T.
   \]
   The original argument changed minimizer variables mid-proof and mixed incompatible signs.

8. **Growth and modulus estimates.** Reproved the finite-horizon growth and continuity-modulus bounds using the running-supremum formula. The corrected proof no longer assumes that a minimizer is unique or differentiable.

## Reflected SDEs and estimates (original lines 98–195)

9. **Strong-solution definition.** Added a filtered probability space, adaptedness, Brownian dimension, coefficient domains, finite-variation support, and the relation between the unconstrained input and its Skorokhod reflection.

10. **Existence argument made valid.** The original invoked ordinary “standard SDE theory,” although the Skorokhod map makes the coefficient equation path-dependent. The corrected proof uses a local Picard contraction for the nonanticipative map and then concatenates the solution across finitely many subintervals.

11. **Moment hypotheses added.** Added the necessary `L^2` or `L^p` integrability of the initial condition before asserting moment estimates. The original estimates were not meaningful without these assumptions.

12. **A priori estimates consolidated.** Replaced duplicated and partly contradictory estimates by valid finite-horizon bounds for `\mathbb E\sup |X|^p`, the regulator, solution stability, and increments. Each use of BDG, Hölder, Young, and Gronwall now has compatible exponents and endpoints.

13. **Support condition on finite horizons.** Stated the reflection condition on every interval `[0,t]`, rather than through a single improper integral to infinity.

## Markov property (original lines 197–233)

14. **Independence argument corrected.** A restarted solution is not justified by saying a deterministic object is “independent of `X_s`.” The proof now uses the independence of future Brownian increments from `\mathcal F_s`, the nonanticipativity of the Skorokhod map, and pathwise uniqueness.

15. **Flow property stated properly.** Identified the restarted pathwise solution and derived the conditional-expectation formula from the flow. The proof now works for arbitrary bounded measurable test functions after the standard monotone-class extension.

16. **Transition family versus semigroup.** Time-dependent coefficients produce a two-parameter transition family; a one-parameter semigroup is claimed only in the time-homogeneous case.

## Boundary local time and Brownian example (original lines 235–327)

17. **Local-time convention fixed.** The original mixed right local time and symmetric local time. The corrected text defines the convention, writes the matching Tanaka formula and occupation-density formula, and tracks the factor of two.

18. **Regulator/local-time identity.** Under boundary nondegeneracy, proved that the regulator equals one half of the right local time and equals the symmetric local time at zero. The equality is now derived from Tanaka’s formula and the boundary support rather than asserted under inconsistent conventions.

19. **Boundary occupation reasoning.** Corrected the argument involving the singleton `{0}` and the occupation-time formula. The proof now distinguishes Lebesgue time spent at the boundary from local time accumulated there.

20. **Simultaneous-in-time statement.** Established the identity at rational times and then used continuity to obtain one almost-sure event on which it holds for every time, rather than silently changing exceptional sets with `t`.

21. **Lévy/Skorokhod sign correction.** For Brownian input `B`, corrected the regulator identity to
   \[
     \Lambda B=\Gamma B-B,
   \]
   not `B-\Gamma B`. The corresponding distributional identities were changed consistently.

22. **Spelling and exposition.** Corrected “conlcude” and other spelling errors, repaired articles and punctuation, and separated formulas from explanatory prose.

# Chapter 2 — Multidimensional Reflected Stochastic Differential Equations

## Half-space and domain geometry (original lines 1–138)

1. **Half-space problem retyped.** Defined the state space, normal vector, vector reflected path, scalar regulator, and boundary support on every finite horizon. The explicit solution now correctly reflects only the last coordinate.

2. **Dimension error.** Replaced the assertion `D\in\mathbb R^n` by the type-correct `D\subset\mathbb R^d`.

3. **Half-space signs.** Corrected the multidimensional regulator and reflected coordinate to the same sign convention as Chapter 1.

4. **Normal directions.** Defined the exterior-sphere normal set with an inward orientation and fixed the geometry in the surrounding prose.

5. **Missing domain hypothesis.** The original implicitly treated the uniform exterior-sphere condition as sufficient for deterministic Skorokhod uniqueness in a general nonconvex domain. Added the standard local non-tangency/cone-type condition and stated explicitly where it is needed. Exterior spheres alone do not justify the claimed uniqueness theorem.

6. **Smooth-domain regime.** Presented the nearest safe `C^2` normal-reflection theorem separately, rather than blending smooth-boundary facts with the more general nonsmooth-domain setup.

7. **Penalization sign.** Corrected the penalty drift to point inward:
   \[
     -\frac{1}{2\varepsilon}\nabla p(x),
   \]
   where `p` grows outside the domain. The original plus sign pushed trajectories farther away from the domain.

## General reflection field and Skorokhod problem (original lines 141–328)

8. **Set-valued reflection field.** The original declared a set-valued field but then wrote it as a single vector `v(g(s))`. The corrected definition uses a finite-variation correction and a measurable unit direction selected from the admissible cone at the current boundary point.

9. **Finite-variation formulation.** Defined the total-variation measure, the Radon--Nikodym direction, boundary support, and state constraint. This makes the correction meaningful even when several reflection directions are available.

10. **Notation collision removed.** Used `\mathcal K(x)` for the reflection cone, `\mathcal R(f)` for the correction component of the Skorokhod map, and `K` for a finite-variation process. The original reused one symbol for all three.

11. **Strong and weak solutions.** Rewrote both definitions so the filtration, Brownian property, adaptedness, law of the initial state, and reflection equation are specified without circularly assuming the conclusion.

12. **Nonanticipativity.** Derived nonanticipativity from uniqueness of solutions to restricted path problems. Continuity of a map by itself does not imply that its value up to time `t` depends only on the input up to time `t`.

## Weak existence and approximation (original lines 141–328)

13. **Invalid proof replaced.** The original weak-existence argument was not repairable by local edits. It mixed deterministic and stochastic events, misused Doob’s inequality for small increments, malformed the Skorokhod-representation tuple, and attempted to pass stochastic integrals to the limit while both integrands and Brownian motions changed.

14. **Euler approximation made explicit.** Defined the piecewise-frozen approximation, its unconstrained input, and its reflected output on one probability space.

15. **Tightness estimate.** Used fourth-moment BDG estimates and a Kolmogorov/Aldous-type argument, together with continuity of the Skorokhod map and variation control. This replaces the incorrect claim that Doob’s inequality alone gives the required short-time modulus.

16. **Limit identification.** Passed to a subsequence in law, identified the limit through the martingale problem and quadratic-covariation relations, and then invoked Brownian representation on an enlarged space. This avoids the false assertion that copied Brownian motions automatically remain Brownian in every enlarged/generated filtration.

17. **Skorokhod-map identity.** Corrected the false identity `\Gamma\eta_n=\xi_n\circ\phi_n` to the actual reflected-map relation for the copied variables.

18. **No false stochastic-integral `L^2` limit.** Removed the unjustified `L^2` convergence of integrals against changing Brownian motions. The martingale/bracket characterization is stable under weak convergence and is the appropriate identification tool.

19. **Subsequence language repaired.** Removed the nonsensical phrase “a subsequence of `k`” and specified subsequences of the approximation index.

## Continuous dependence (original lines 332–418)

20. **Coefficient-variable typo.** Corrected inconsistent state variables in the coefficient convergence assumptions.

21. **Hypotheses strengthened.** Stated local-uniform coefficient convergence, uniform growth/Lipschitz control, convergence of initial laws, and the relevant uniqueness assumptions before claiming convergence of solutions.

22. **Weak convergence conclusion.** Derived convergence in distribution from tightness plus uniqueness in law of every limit point.

23. **Common-noise convergence.** For solutions driven by the same Brownian motion, replaced an unsupported direct argument by the standard pathwise-uniqueness/Gyöngy--Krylov route to convergence in probability.

24. **Grammar and terminology.** Standardized “reflection field,” “bounded variation,” “pathwise uniqueness,” “weak existence,” and “continuous dependence,” and repaired run-ons and missing punctuation throughout.

# Chapter 3 — PDE and Submartingale Characterizations

## Generator and transition family (original lines 1–58)

1. **Well-posedness requirement.** Weak existence alone does not select a unique transition law. Added uniqueness in law/well-posedness before defining `P_t\varphi(x)=\mathbb E_x\varphi(X_t)`.

2. **Generator typed correctly.** Defined the covariance `c=\sigma\sigma^\top`, the second-order operator, and the oblique derivative `\partial_\gamma\varphi` with compatible dimensions.

3. **Generator claim weakened to a valid statement.** The original implicitly identified the full generator domain/core. The corrected proposition only identifies a natural core candidate on which the pointwise derivative at zero equals `\mathcal A\varphi`.

4. **Semigroup caveat.** Added that a pointwise derivative at zero does not establish the Feller property, strong continuity, the full domain, or the core property required by Hille--Yosida theory.

5. **Time-inhomogeneous terminology.** Replaced “semigroup” by “transition family” when coefficients depend on time.

## Backward equation and Feynman--Kac (original lines 60–161)

6. **Conditioning notation repaired.** Avoided conditioning on the zero-probability event `X_t=x`; the representation is expressed under the law of a process started from `(t,x)`.

7. **Assumptions made explicit.** Stated regularity and integrability sufficient for applying Itô’s formula, optional stopping, and dominated convergence.

8. **False process claim removed.** A classical PDE solution is a deterministic function, not itself a Markov process. The corrected text relates the deterministic solution to the reflected Markov family.

9. **Transition-density existence separated.** Removed the implication that every reflected diffusion automatically has a smooth transition density. Density and regularity statements are now conditional on additional hypotheses.

10. **Feynman--Kac signs and variables.** Corrected the signs of discount/source terms, repaired malformed syntax, and matched every integration variable to its differential.

## Hitting times and annulus example (original lines 163–222)

11. **Mean hitting-time theorem.** Specified the stopped reflected process, boundary decomposition, domain of the PDE, and regularity of the candidate solution. The corrected proof assumes the function extends `C^2` to a neighborhood of the closure when applying Itô’s formula up to the stopping time.

12. **Boundary conditions.** Distinguished absorbing and reflecting boundary portions and applied Dirichlet and oblique-Neumann conditions to the correct sets.

13. **Annulus coefficient.** Restored the missing factor `R^d` in the `d\ge3` radial solution:
    \[
      U(\rho)=\frac{r^2-\rho^2}{d}
      +\frac{2R^d}{d(d-2)}\bigl(r^{2-d}-\rho^{2-d}\bigr).
    \]
    Without `R^d`, the Neumann condition at the outer boundary fails.

14. **Boundary restriction and notation.** Replaced `u|_K` by a restriction to the appropriate boundary, fixed the misspelling “ansantz,” and corrected radial coefficients.

15. **One-dimensional case.** Added the omitted `d=1` formula rather than leaving a dimension gap between logarithmic and power-law cases.

## Submartingale problem and time change (original lines 224–331)

16. **Open domain.** Replaced the example `G=[0,\infty)` by the open domain `G=(0,\infty)`.

17. **Confinement statement.** Required the coordinate process to remain in the closure for all times on one probability-one event, not merely at each fixed time with a potentially changing exceptional set.

18. **Submartingale representation.** Restored the initial term, imposed `L_{t_0}=0`, fixed the boundary support, and corrected the lower limit of the quadratic-variation integral.

19. **Boundary holding relation.** Stated the relation between elapsed boundary time and the local-time/holding-rate term with compatible measures and dimensions.

20. **Operator typo.** Corrected `\rho(x)f(x)+Jf` to the intended time-space operator `\rho\,\partial_t f+Jf`.

21. **Localization interval.** Repaired inconsistent stopping intervals and indices in the localization argument.

22. **Time-change theorem restricted.** The original formula mixed time-dependent coefficients with a one-parameter additive time change. The corrected theorem is stated in the time-homogeneous setting and uses
    \[
      A_s=s+\int_{t_0}^s\rho(\bar X_r)\,\dd\bar L_r,
      \qquad
      \tau_t=\inf\{s\ge t_0:A_s>t\}.
    \]

23. **Strong Markov wording.** Distinguished the coordinate process from the time-space process and stated the Markov conclusion for the correct object.

24. **Cross-check with SDE formulation.** Explained that equivalence of the reflected SDE and submartingale problem requires suitable geometric and well-posedness assumptions; it is not automatic in nonsmooth domains.

# Chapter 4 — Reflected Backward Stochastic Differential Equations

## Definitions and basic estimates (original lines 1–307)

1. **Probability-space setup.** Added the augmented Brownian filtration, Brownian dimension, and the scalar nature of the RBSDE.

2. **Solution spaces.** Defined `\mathbb S^2`, `\mathbb H^2`, and `\mathbb A^2`, including continuity, adaptedness/predictability, monotonicity, normalization, and square integrability.

3. **Data assumptions.** Stated square-integrability of the terminal value, progressive measurability and Lipschitz continuity of the driver, integrability of `f(\cdot,0,0)`, obstacle continuity/integrability, and terminal compatibility `S_T\le\xi`.

4. **Notation collision.** Renamed the Lipschitz constant to `\lambda` while reserving `S` for the obstacle and `K` for the regulator.

5. **RBSDE definition.** Standardized the backward equation, obstacle inequality, and Skorokhod minimality condition with consistent signs.

6. **First-contact theorem.** Corrected the contact stopping time, terminal reward, and assertion that the regulator is constant before first contact. The pathwise regulator representation is now derived from the BSDE rather than stated without justification.

7. **Comparison with an ordinary BSDE.** The original incorrectly added `K_t` to a driver as if `K` were absolutely continuous. Replaced this with a finite-variation comparison/integrating-factor argument.

8. **A priori estimate absorption.** The original Young-inequality step left an unabsorbed term proportional to `\varepsilon K_T^2`. The corrected estimate chooses constants in an order that genuinely absorbs all solution terms into the left side.

9. **Malformed integral endpoints.** Repaired occurrences such as `\int_2^T`, missing lower limits, and mismatched time variables.

10. **Stability notation.** Defined `\Delta f` on the correct pair of solutions and used consistent norms for `\Delta Y`, `\Delta Z`, and `\Delta K`.

11. **Reflection cross term.** Controlled the finite-variation cross term by using that `\mathrm dK^i` is supported on `{Y^i=S^i}`. The original sign argument was incomplete.

12. **Correct norm for regulators.** Used the uniform/supremum norm for the difference of two increasing regulators. Total variation of `K^1-K^2` cannot be replaced by its terminal absolute value without further monotonicity.

13. **Comparison theorem.** Replaced the original contradiction at time zero—which did not exclude a later crossing—by an Itô--Tanaka estimate for the positive part and a Gronwall argument.

## Essential suprema and Snell envelopes (original lines 308–586)

14. **Essential-supremum construction.** Replaced the circular Zorn-style argument and expectations of possibly nonintegrable variables. The corrected proof applies the bounded strictly increasing transform `\psi(x)=\arctan x+\pi/2` to select a countable cofinal family.

15. **Directed-family sequence.** For an upward-directed family, constructed a monotone maximizing sequence whose pointwise supremum is the essential supremum.

16. **Terminal reward compatibility.** Defined the reward to equal the obstacle before `T` and `\xi` at `T`, avoiding a false continuity claim when `S_T<\xi`.

17. **Stopping-time DPP algebra.** Corrected uses of `\tau\wedge t'` and `\tau\vee t'`, so pasted stopping times lie in the intended admissible set.

18. **Measurable pasting.** Supplied the event on which each stopping rule is chosen and verified that the pasted variable is a stopping time.

19. **Maximal inequality.** Used Doob’s `L^2` maximal inequality for the martingale part; the original invoked BDG in a setting where the displayed object was not the relevant stochastic integral.

20. **Obstacle indices.** Corrected mismatched obstacle and terminal indices in the stopping-time dynamic programming formula.

21. **Snell-envelope proof.** Reorganized the proof into value-family construction, càdlàg/continuous modification under the stated obstacle assumptions, supermartingale decomposition, first-contact optimality, and Skorokhod minimality.

22. **Doob--Meyer/minimality.** Identified the increasing process and proved that it increases only on the contact set. The original jumped from a supermartingale statement to minimality without the necessary support argument.

## Picard iteration and penalization (original lines 587–812)

23. **Picard stochastic integrand.** In iteration `n`, the stochastic integral must use the new unknown `Z^n`, not `Z^{n-1}`. This was corrected throughout.

24. **Global contraction.** Replaced informal local-interval patching by a contraction in a weighted `\mathbb H^2`/`\mathbb S^2` norm. The contraction constant is made smaller than one by choosing the exponential weight.

25. **Penalization theorem added.** The original section launched into a proof without a precise statement. Added a theorem specifying the penalized BSDE, monotonicity, convergence spaces, and limiting reflected solution.

26. **Monotone stability.** Weak `L^2` convergence does not preserve pathwise monotonicity of `K`. Replaced that claim with the standard monotone-stability argument and strong convergence of the relevant components.

27. **Exact minimality argument.** Used `S^n=Y^n\wedge S` and the penalized identity to pass to the limit. This replaces a partition argument that assumed the desired contact property before proving it.

28. **Identification of the limit.** Passed the driver and martingale terms in the correct norms and then recovered `K` from the equation, rather than declaring convergence of all three processes simultaneously.

## Markovian RBSDE and obstacle PDE (original lines 813–997)

29. **Forward SDE typo and dimensions.** Corrected `\mathrm dB_S` to the integration variable `\mathrm dB_r`, specified state/Brownian dimensions, and repaired coefficient domains.

30. **Classical verification sign.** Corrected the regulator formula to
    \[
      K_t=-\int H u(r,X_r)\,\dd r
    \]
    on the contact region under the chosen PDE sign convention. The original formula had the opposite sign.

31. **Obstacle complementarity.** Standardized the obstacle problem and its equivalent minimum/maximum form so the inequalities, contact condition, and regulator monotonicity agree.

32. **Decoupling field.** Defined `u(t,x)=Y_t^{t,x}` on the correct time-space domain and justified determinism through the Markov flow and uniqueness, not by an unsupported measurability assertion.

33. **Malformed Tanaka calculation removed.** Replaced the unmatched bracket, undefined `h`, and invalid local-time manipulation with a valid Lewy--Stampacchia-type bound for the regulator density under the stated smoothness assumptions.

34. **Time modulus.** Corrected the zero expression `(t_2-t_2)^{1/4}` to `(t_2-t_1)^{1/4}` and restored missing interval-length factors in the driver and regulator estimates.

35. **Viscosity test directions.** Corrected the signs and local-maximum/local-minimum directions in the subsolution and supersolution tests.

36. **Driver arguments.** Replaced incorrect occurrences of the value process where the gradient/diffusion term `z=\sigma^\top\nabla\varphi` is required.

37. **Localized contradiction proof.** Replaced the vague appeal to “strict comparison” with a localized stopping time, a short-horizon BSDE estimate/Girsanov argument, and the resulting contradiction to the touching condition.

38. **Obstacle active/inactive cases.** Treated the contact case separately from the continuation case, so the viscosity proof does not divide by or infer signs from a quantity that may vanish at the obstacle.

39. **Spelling and terminology.** Corrected “Snell Envelop,” “holf,” “firt,” and related typographical errors; standardized RBSDE, obstacle problem, penalization, Picard iteration, and viscosity-solution prose.

# Highest-priority mathematical corrections

1. The one-dimensional regulator has the sign `\ell=g-f`, and the Brownian example has `\Lambda B=\Gamma B-B`.
2. Ordinary SDE theory cannot be invoked without accounting for the path-dependent Skorokhod map; the corrected proof uses a nonanticipative fixed point.
3. The multidimensional penalty drift must point inward, and deterministic Skorokhod uniqueness requires more than an exterior-sphere condition in a general nonconvex domain.
4. The original weak-existence proof for reflected SDEs mishandled tightness, copied Brownian motions, and stochastic-integral limits; it is replaced by a martingale-problem identification.
5. Weak existence alone does not define a unique transition semigroup or PDE representation; uniqueness in law/well-posedness is now explicit.
6. The annulus mean-hitting-time solution was missing the factor `R^d`.
7. The submartingale formulation now has the correct initial term, bracket interval, boundary support, and time-change clock.
8. A finite-variation reflection process cannot be inserted into a BSDE driver as though it were a density.
9. The essential-supremum and Snell-envelope arguments are no longer circular.
10. Picard iteration uses the new `Z^n`; penalization uses monotone stability rather than claiming weak convergence preserves monotonicity.
11. The obstacle-PDE sign, regulator density, time modulus, and viscosity test directions are consistent with the RBSDE convention.

# Package contents

- `Corrected_notes_master.tex` — portable standalone master.
- `Chapter_1_corrected.tex` — reviewed one-dimensional reflected-SDE chapter.
- `Chapter_2_corrected.tex` — reviewed multidimensional reflected-SDE chapter.
- `Chapter_3_corrected.tex` — reviewed PDE/submartingale chapter.
- `Chapter_4_corrected.tex` — reviewed reflected-BSDE chapter.
- `Corrected_notes.pdf` — compiled corrected notes.
- `Corrections_summary.md` — this complete review log.
- `README.md` — package and build instructions.
- `Validation_report.txt` — concise clean-build, source-check, and visual-QA record.
- `compile_and_validate.sh` — reproducible strict compile/log-scan helper.
- `originals/` — untouched uploaded sources.
- `diffs/` — unified patches recording every literal source edit.
- `SHA256SUMS.txt` — checksums for package integrity.

The corrected notes retain the original chapter sequence and pedagogical topics. Where a proof was mathematically invalid rather than merely abbreviated, it was replaced by the nearest standard valid statement and a coherent proof or proof outline under explicit hypotheses.
