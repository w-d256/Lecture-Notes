# Mathematical, grammatical, and LaTeX review

Line references below refer to the original uploaded chapter files. The original uploads were not overwritten. Repeated punctuation, spacing, delimiter, and notation repairs are grouped; every substantive mathematical or compilation correction is listed separately.

## Project-wide corrections

1. **Portable project structure.** The uploads were chapter fragments rather than standalone documents. I created `Corrected_notes_master.tex`, defined the theorem environments and the differential macro `\dd`, and input the four corrected chapters in order. This makes the source tree compile without relying on an unidentified external preamble.
2. **Notation.** I standardized `\colon` in maps, `\dd` for differentials, `\widetilde{\cdot}` for comparison objects, `\mathcal L` for operator spaces, `\otimes` for tensor products, and consistent first-/second-level rough-path notation `(X,\mathbb X)`.
3. **Typography.** I standardized Hölder, Fréchet, Riemann--Stieltjes, Arzelà--Ascoli, Itô, Stratonovich, Itô--Lyons, Doob--Meyer, and Burkholder--Davis--Gundy; repaired sentence fragments, missing articles, run-on sentences, display punctuation, and malformed quotation marks.
4. **Types and contractions.** Products such as `Y'_s\mathbb X_{s,t}`, brackets, traces, and quadratic covariations were rewritten with explicit operator/tensor types or contractions so that each formula has a well-defined codomain.
5. **Proof presentation.** Compressed symbolic arguments were divided into construction, well-definedness, estimate, convergence, and uniqueness steps. Vague claims such as “easy,” “straightforward,” and “the same argument” were retained only where the omitted step is genuinely routine.
6. **Compilation repairs.** Malformed `\left...\right` pairs, missing braces, missing integral endpoints, stray alignment symbols, invalid math accents, and undefined commands were repaired. Long equations were rebroken to remain inside the text block.

## Chapter 1 — Rough Paths and Rough Integrals

1. **Hölder norms and strict inclusions (original lines 3–30).** The chapter used the Hölder seminorm as though it were a complete norm and stated strictness of `\mathcal C^\beta\subset\mathcal C^\alpha` without edge cases. I distinguished the seminorm from `|X_0|+\|X\|_\alpha` and stated strictness only when `T>0` and the target space is nontrivial. On a degenerate interval or zero space, the spaces coincide.
2. **Lower semicontinuity (lines 33–35).** I corrected the spelling and rewrote the argument as a pointwise limit followed by a supremum, yielding `\|X\|_\alpha\le\liminf_n\|X^n\|_\alpha`. The original presentation blurred an ordinary limit with a liminf.
3. **Hölder interpolation (lines 38–76).** I corrected the exponents and supplied the standard estimate that interpolates the uniform norm and the `\beta`-Hölder seminorm. The original derivation did not consistently track the power `1-\alpha/\beta`.
4. **Compact embedding (lines 79–95).** The original lemma was false for arbitrary Banach-valued paths: boundedness and equicontinuity do not imply pointwise relative compactness in an infinite-dimensional Banach space. I changed the theorem to finite-dimensional `V` and added the more general valid alternative requiring pointwise relative compactness.
5. **Two-parameter maps and rough-path types (lines 97–161).** I specified the tensor-product norm, the simplex on which second-level increments live, and the codomains in Chen’s relation. This prevents treating a tensor as a scalar or using a rough-path level in the wrong space.
6. **Rough-path metric (around original line 156).** The original full norm repeated or omitted terms. I restored the first-level Hölder seminorm and second-level `2\alpha`-Hölder seminorm, with the initial point handled separately.
7. **Additive perturbations (lines 165–180).** An arbitrary two-index map cannot simply be added to a rough path while preserving Chen’s relation. I required the perturbation to be an additive increment, for example `F_{s,t}=F_t-F_s`, and verified Chen’s relation.
8. **Interpolation of rough paths (lines 184–227).** I added the needed range `1/3<\alpha<\beta\le1/2`, corrected the second-level interpolation inequality (the original repeated the first-level bound), and replaced the incomplete convergence argument by uniform convergence plus equicontinuity/interpolation on both levels.
9. **Weakly geometric and geometric rough paths (lines 231–268).** I derived the symmetric second-level identity correctly and qualified the approximation inclusions by finite dimensionality. In a general Banach space, smooth canonical lifts can depend on tensor-product and approximation properties, so the unqualified inclusion was too broad.
10. **Sewing lemma—existence (lines 275–349).** I supplied a complete dyadic construction and showed that the approximants are Cauchy with the correct geometric-series constant.
11. **Sewing lemma—arbitrary partitions (same location).** The original proof effectively handled only dyadic refinement. I added the comparison with arbitrary partitions and proved convergence of every Riemann sum as the mesh tends to zero.
12. **Sewing lemma—uniqueness (same location).** I added the standard argument that two additive maps satisfying the higher-order error estimate must coincide. The original theorem asserted uniqueness without proving it.
13. **Sewing typo (around original line 345).** I repaired the malformed factor `|t-s \|\pi|` to the correct product of interval length and a power of the mesh.
14. **Young integral (lines 353–379).** I typed the integrand as operator-valued, parenthesized the Riemann sums, and derived the sewing defect `-(Y_u-Y_s)X_{u,t}`. This makes the product and its target space unambiguous.
15. **Stability of Young integration (lines 390–419).** The original difference decomposition evaluated one coefficient at the wrong time and lost a factor of `|t-s|^\alpha`. I corrected the decomposition and the local estimate before taking Hölder seminorms.
16. **Young integration by parts (lines 422–445).** I stated the formula for a continuous bilinear map `B:V\times W\to U`, rather than relying on an untyped scalar product, and proved that the cross-increment remainder has order `\alpha+\beta>1`.
17. **Young chain rule (lines 448–459).** I added `\gamma\in(0,1]`, required `\alpha(1+\gamma)>1`, and used local Hölder bounds for `Df` on the compact image of the path. Global boundedness of the derivative is not needed.
18. **Associativity of Young integration (lines 465–485).** I supplied compatible operator-valued domains and used composition in the local model. The original notation allowed products whose domains and codomains did not match.
19. **Controlled-path definition and norm (lines 491–513).** I defined the Gubinelli derivative and remainder on the correct spaces and stated a complete norm including initial data. The original used a seminorm as if it were a Banach norm.
20. **Nonuniqueness of the Gubinelli derivative (around line 516).** I changed “any continuous `Y'`” to an `\alpha`-Hölder derivative. Mere continuity does not ensure the proposed remainder is `2\alpha`-Hölder.
21. **Products of controlled paths (lines 519–533).** I rewrote the result through an arbitrary continuous bilinear map and displayed all three remainder terms. This resolves the original untyped multiplication.
22. **Rough integral construction (lines 539–568).** I corrected the Chen-relation calculation, the contraction of `Y'_s` with `\mathbb X_{s,t}`, and the exact sewing defect. Several signs, subscripts, and delimiters in the original prevented the displayed proof from being valid.
23. **Rough integral as a controlled path (lines 572–582).** I promoted the informal observation to a proposition and gave the explicit `2\alpha`-remainder bound. This is needed later in the RDE fixed-point argument.
24. **Stability of controlled paths and rough integrals (lines 584–664).** I repaired malformed delimiters and inconsistent variables, defined a mixed controlled-path seminorm, and recomputed the difference sewing defect term by term. The original formula did not consistently compare the two drivers and two remainders.
25. **Final rough-integral stability corollary (lines 667–705).** I corrected a driver-space typo (`\mathscr D_X` versus `\mathscr D_{\widetilde X}`), included all initial-value and driver-distance terms, and derived the integral estimate from the controlled remainder identity.

## Chapter 2 — Properties of Rough Integration

1. **Integration against a rough integral (original lines 7–23).** I added the operator domains required for `K\,\dd Z`, defined the right-hand side as the rough integral of the controlled product, and corrected the local expansion used in the Riemann-sum proof.
2. **Canonical lift of a rough integral (lines 52–80).** The original confused the new rough path `\mathbf Z` with `\mathbb X` and used inconsistent second-level symbols. I defined `\mathbb Z_{s,t}=\int_s^t Z_{s,r}\otimes\dd Z_r`, verified Chen’s relation, and proved compatibility of integration against `Z` with integration against the original driver.
3. **Bracket definition (lines 85–115).** I standardized `\mathbf X=(X,\mathbb X)` and defined `[\mathbf X]_{s,t}=X_{s,t}^{\otimes2}-2\operatorname{Sym}\mathbb X_{s,t}` as a `2\alpha`-Hölder symmetric tensor increment.
4. **Bracket of a rough integral (lines 116–138).** I restored the correct tensor contraction in `\int (K\otimes K)\,\dd[\mathbf X]` and justified the identity from the second-order local expansion.
5. **Rough Itô formula (lines 148–186).** I replaced the invalid “without loss of generality, assume globally bounded derivatives” step by a local boundedness hypothesis on a neighborhood of the compact collection of line segments traversed by `X`. I also corrected the symmetric-second-level cancellation and the bracket term.
6. **Itô formula for controlled dynamics (lines 189–229).** The original proof applied the rough Itô formula to an undefined rough path `\mathbf Y`, treated `Y'_{s,t}` as a second level, and wrote an incorrect bracket for `Y`. I replaced it by a direct second-order expansion of the controlled equation, identified the rough, drift, and bracket contributions, and checked the `3\alpha` error.
7. **Composition of controlled paths (lines 236–278).** I corrected the derivative to `D\varphi(Y)Y'` and wrote the exact Taylor remainder. Stray punctuation and inconsistent derivative notation were removed.
8. **Local versus global derivative bounds (around lines 284–286).** I removed another false “no loss of generality” assertion about globally bounded derivatives. Only bounds on the compact range and connecting segments are used.
9. **Hölder composition stability (lines 289–323).** I corrected “Holder,” supplied the averaged-derivative representation, and tracked the initial-value and Hölder-distance terms correctly.
10. **Stability of controlled composition (lines 325–400).** I repaired `\bar X`, `R^{\bar Y}`, `R^{\widetilde Y_t}`, and other inconsistent symbols; restored a missing plus sign; and used an exact Taylor representation before estimating. The original displayed remainder difference contained terms that were literally zero or compared the wrong path.
11. **Fubini theorem (lines 401–439).** I corrected “Fubuni” and stated measurable Bochner-integrability assumptions in the Banach controlled-path space. Pointwise measurability alone is insufficient to interchange a parameter integral with rough integration.
12. **Singular Hölder paths (lines 443–461).** I rewrote the weighted seminorm equivalence with the supremum over `0<s<t\le T` and supplied both directions directly. This avoids undefined powers at `s=0` when the singular exponent is negative.
13. **Improper Young integral—hypotheses (lines 463–518).** I added the sharp conditions `\eta\le\alpha`, `\eta+\alpha>0`, and `\eta\ne0`. The lower condition ensures summability near zero, while `\eta=0` is the logarithmic borderline excluded by the stated Hölder target.
14. **Improper Young integral—driver and output (same location).** I changed `\dd\mathbf X` to `\dd X`, corrected the dyadic exponents, and proved the output belongs to `\mathcal C^{\alpha+(\eta\wedge0)}`. The original mixed Young and rough drivers and did not justify the endpoint behavior.
15. **Singular controlled paths (lines 521–546).** I restored `\alpha\in(1/3,1/2]`, used `[\varepsilon,T]` rather than `[\varepsilon,1]`, and placed all weighted suprema over `0<s<t\le T`. The original formula could evaluate a negative power at zero.
16. **Improper rough integral—parameter range (lines 547–633).** I corrected the hypotheses to `-\alpha<\eta\le2\alpha` and `\eta\ne0`, matching the convergence of the first- and second-level contributions.
17. **Improper rough integral—dyadic proof (same location).** I corrected the dyadic intervals, the controlled relation (which uses `X`, not `\mathbb X`), and the growth of `Y'`. I handled separately `\eta<\alpha`, `\eta=\alpha` (logarithmic growth), and `\eta>\alpha`; the original omitted the borderline case and used incorrect exponents.
18. **Improper rough integral—controlled output (same location).** I proved both the weighted increment bound and the weighted remainder bound, hence the claimed singular controlled-path class. The original conclusion was asserted before both estimates were established.
19. **Undefined natural-number command (original lines 492, 502, 579, 592, and 619).** Five uses of `\N` caused undefined-control-sequence errors in the baseline build. I replaced them by ordinary quantified integers or explicitly written index sets.
20. **True roughness definition (lines 643–667).** I specified the dual vector used to test the driver and corrected the quantifiers over dense times. This resolves ambiguity between vectors in the state space and linear functionals.
21. **Uniqueness of the Gubinelli derivative (lines 668–701).** I applied true roughness to the scalarized controlled expansion and made the density/continuity step explicit.
22. **Doob--Meyer principle (lines 702–733).** The original subtraction had the wrong sign. I corrected the identity to `(Y_s-\widetilde Y_s)X_{s,t}=-(Z_s-\widetilde Z_s)(t-s)+O(|t-s|^{2\alpha})`, then used true roughness and continuity to identify both coefficients.
23. **Quantitative roughness (lines 734–787).** I defined the oscillation scale and quantified roughness constant consistently, replacing an undefined or changing constant.
24. **Quantitative derivative recovery (same location).** The original proof used `\operatorname{osc}(X,\varepsilon)` where it needed the controlled path and ignored that `R^Y_{s,t}` was defined only for `s\le t`. I added the backward-increment comparison term `\|Y'\|_\alpha\|X\|_\alpha\varepsilon^{2\alpha}` and obtained a valid two-sided estimate.
25. **Norris lemma (lines 788–810).** I made the Hölder ranges and norms consistent, replaced an undefined `M` by the stated control quantity, and expanded the interpolation/optimization argument enough to explain the exponent rather than merely asserting the estimate.

## Chapter 3 — Rough Differential Equations

1. **Hölder composition lemma (original lines 7–31).** I replaced the invalid symbol `\vDash`, repaired the two integral expressions, and used the averaged derivative identity to obtain the stated Hölder estimate.
2. **Young fixed-point map (lines 34–88).** The original map omitted the upper integration endpoint, had malformed brackets in both small-time conditions, and contained sentence fragments. I defined `\mathcal M_t(Y)_r` for every `r\le t`, proved invariance and contraction on a complete ball, and explained finite iteration to `[0,T]`.
3. **Regularity upgrade for the Young solution (same location).** I derived `Y_{s,t}=f(Y_s)X_{s,t}+O(|t-s|^{\alpha+\beta})`, which proves `\beta`-Hölder regularity. The original conclusion was asserted without the estimate.
4. **Young stability statement (lines 90–97).** I repaired the missing brace in the bound on `\widetilde X` and standardized the data and norm dependencies.
5. **Young stability proof (lines 99–116).** The original proof stopped after a malformed local inequality and never obtained the proposition. I absorbed the local contraction term, propagated endpoint errors over a finite partition, and used discrete Gronwall to get the global bound.
6. **Composition of controlled paths (lines 122–175).** I retained the valid estimates but rewrote the proof with the exact controlled remainder and consistent `2\alpha` scaling. This removes ambiguous products and redundant nested integrals.
7. **Stability of controlled composition (lines 177–249).** I corrected repeated substitutions of `\bar Y` for `\widetilde Y`, a missing addition sign, and the erroneous term `R^Y-R^Y`. I then subtracted exact Taylor remainders and estimated one factor at a time.
8. **Rough integrals as controlled paths (lines 252–289).** I corrected the local second-order term from an untyped `Y'_s\mathbf X_{s,t}` to `Df(Y_s)Y'_s\mathbb X_{s,t}`, inserted the missing separator between displayed estimates, and derived the `2\alpha` remainder bound.
9. **Stability of rough-integral controlled paths (lines 291–345).** I replaced `\overline{\mathbf X}`, `\bar Y`, and malformed integral superscripts by the intended tilde objects and applied the rough-integral stability theorem to the two controlled integrands.
10. **RDE fixed-point map (lines 355–434).** I defined the integral as a path `r\mapsto\int_0^r`, fixed the incomplete sentence “Since `\mathcal B_t` a closed subset,” and used a single driver in the contraction comparison. The original formula accidentally introduced a different driver inside a same-driver fixed-point argument.
11. **Choice of auxiliary exponent (around original line 364).** I strengthened the choice to `\max\{1/3,2\beta/3\}<\alpha<\beta`. The original arbitrary `\alpha\in(1/3,\beta)` does not guarantee that a `3\alpha` error is regular enough to recover a `2\beta` remainder.
12. **Upgrade to `\mathscr D_X^{2\beta}` (lines 436–443).** I used the full expansion `Y_{s,t}=f(Y_s)X_{s,t}+Df(Y_s)f(Y_s)\mathbb X_{s,t}+O(|t-s|^{3\alpha})`. With `3\alpha>2\beta`, this proves the desired remainder regularity; the original omitted the second-level contribution and made an unjustified inference.
13. **Itô--Lyons stability theorem (lines 452–458).** I repaired the duplicated/malformed common bound, replaced the undefined smoothness index `C_b^s` by `C_b^3`, and stated the rough-path distance consistently.
14. **Local Itô--Lyons estimate (lines 460–501).** I corrected `R^Y-R^{\bar Y}`, malformed interval brackets, and several integral labels. The local estimate now uses the current endpoint error `|Y_s-\widetilde Y_s|`, not the original initial error on every subinterval.
15. **Global Itô--Lyons estimate (lines 503–513).** The original ended with “one can deduce” the global bound. I supplied the endpoint recursion and discrete Gronwall argument, which is necessary because Hölder seminorms on adjacent intervals do not simply add.

## Chapter 4 — Connections with Stochastic Calculus

1. **Kolmogorov criterion—statement (original lines 4–16).** I stated the first level as a one-parameter process and the second level as a measurable two-parameter process, separated the almost-sure Chen event, and used `\alpha\in(0,\beta-1/q)`. This avoids treating a pair with different parameter domains as one map and avoids the degenerate `\alpha=0` rough-path notation.
2. **Dyadic decomposition (lines 18–71).** I defined dyadic intervals explicitly, corrected the typo `X_{u_t,u_{i+1}}`, and derived first- and second-level bounds with the right multiplicities. The original notation used point sets as though they were interval families.
3. **Continuous modification (lines 73–103).** I constructed the first-level extension from dyadic limits and then defined the second level through a continuous additive correction, proving independence of approximating sequences, Chen’s relation, and the modification property. This removes a circular appeal to continuity of the object being constructed.
4. **Corrupted Itô superscripts (lines 110–141 and throughout).** Expressions such as `\mathrm{It}\hat t`, `\mathrm I t\hat t`, `\mathrm{It}\hat0`, and plain `Ito` were standardized to a consistently rendered Itô label. These corruptions changed symbols and, in one place, caused invalid accent processing in math mode.
5. **Brownian rough-path moment proof (lines 123–142).** I used Brownian scaling, Burkholder--Davis--Gundy, and Minkowski to obtain the correct first- and second-level moments. For a fixed `\alpha<1/2`, I choose one finite `q` with `\alpha<1/2-1/q`; the original phrase “take `q\to\infty`” was not a valid operation on a single modification.
6. **Stratonovich lift (lines 144–186).** I corrected “Stratonovichenhanced,” the Itô--Stratonovich conversion symbols, and the symmetric-part identity. I then justified geometricity through the weakly geometric identity and finite-dimensional approximation, rather than the incomplete sentence “It follows from that.”
7. **Itô consistency—integrability (lines 190–232).** I made the coefficient spaces explicit and observed that continuous adapted controlled paths are locally square integrable after radial truncation. This supplies the missing condition for the stochastic Itô integral.
8. **Itô consistency—second-level sums (same location).** I rewrote the second-level correction as a martingale-difference sum with explicit contractions, proved its `L^2` norm tends to zero under truncation, and then removed truncation in probability. The original orthogonality formula multiplied vector/tensor objects without specifying an inner product and contained the typo `\pi^n k`.
9. **Simultaneous equality in time (same location).** I proved equality first at fixed times and then for all times by taking continuous versions. The original only stated a terminal-time equality but later used a process identity.
10. **Contracted quadratic covariation (lines 237–312).** For vector/matrix-valued integrands I defined `\operatorname{Ctr}(Y')`, the contraction that replaces the scalar `Y'`. The original formula `Y'_s(t-s)` was dimensionally ambiguous.
11. **Stratonovich consistency (same location).** I decomposed `B_{u,v}^{\otimes2}` through the symmetric Itô second level plus `(v-u)I_d`, showed the martingale and remainder sums vanish, and identified `[Y,B]_t=\int_0^t\operatorname{Ctr}(Y'_u)\,\dd u` before applying Itô--Stratonovich conversion.
12. **RDE/SDE consistency—hypotheses (lines 316–336).** I added the usual conditions on the filtration, an `\mathcal F_0`-measurable initial value with the correct dimension, and the full domain/codomain of `f`. These are needed for the claims of adaptedness and strong solutions.
13. **Adaptedness of the RDE solution (lines 339–354).** Continuity of the global Itô--Lyons map alone does not prove adaptedness. I used its causal restriction: for each `t`, the solution on `[0,t]` is a measurable function only of `y` and the stopped/restricted rough path up to `t`.
14. **Strong uniqueness (same location).** After identifying the rough integral with the Itô or Stratonovich integral, I invoked global Lipschitzness implied by `f\in C_b^3` to justify uniqueness of the strong SDE solution. The original concluded uniqueness without giving the reason.
15. **Invalid math accent (original line 349).** The Unicode/LaTeX rendering of “Itô” inside `\mathrm{...}` produced two `Command \^ invalid in math mode` warnings. I replaced it by a valid math-mode accent construction.

## Baseline compilation findings

Compiling the unmodified chapters through a minimal master produced a 52-page PDF but reported:

- five undefined-control-sequence errors from `\N` in Chapter 2 (original lines 492, 502, 579, 592, and 619);
- two invalid math-accent warnings in Chapter 4 (original line 349);
- five overfull boxes, including excesses of approximately 14.1 pt, 23.8 pt, and 32.9 pt;
- numerous source formulas that compiled only because TeX interpreted malformed notation in an unintended way.

## Final validation

- Final master: `Corrected_notes_master.tex`
- Engine: pdfLaTeX through `latexmk`
- Final PDF: 30 pages, US Letter
- Fatal LaTeX errors: none
- Undefined control sequences: none
- Undefined references or citations: none
- Overfull boxes: none
- Underfull boxes: none
- Package/LaTeX warnings: none
- Missing-character warnings: none
- Text-extraction replacement glyphs: none
- Visual inspection: every one of the 30 rendered pages was checked at 200 dpi; no clipping, overlap, missing glyphs, malformed theorem boundaries, blank content pages, or equations outside the margins were found.
