# Corrections for Chapters 2, 3, and 4

## Scope

This correction log accompanies the corrected LaTeX reconstruction of the 100-page handwritten continuation of *Notes on Measure Theory*.

- **Source PDF:** `Notes on Measure Theory.pdf`
- **Source SHA-256:** `1c5ba7aa8541df4072a6f56a77e5d96dd851cb52c13076f6f314e9d60d7709cd`
- **Chapter 2 source pages:** 1–29
- **Chapter 3 source pages:** 30–74
- **Chapter 4 source pages:** 75–100
- **Corrected chapter files:**
  - `chapters/chapter-2-differentiation.tex`
  - `chapters/chapter-3-signed-measures.tex`
  - `chapters/chapter-4-lp-spaces.tex`

The entries below record substantive mathematical repairs. Repeated grammatical, typographical, and notation changes are grouped first. A source-page reference means the page number within the supplied 100-page PDF.

---

## Global grammatical, notational, and LaTeX corrections

### G.01 — terminology and capitalization

**Category:** Grammar and notation

**Issue:** The handwritten notes used inconsistent capitalization and several misspellings for standard names and terms.

**Correction:** Standardized such terms as *sigma-algebra*, *Lebesgue*, *Lebesgue–Stieltjes*, *Hardy–Littlewood*, *Radon–Nikodym*, *Fubini–Tonelli*, *Egoroff*, *Vitali*, *Hölder*, *Minkowski*, *Banach–Zarecki*, and *bounded variation*.

**Reason:** Consistent mathematical terminology improves readability and prevents accidental ambiguity between ordinary words and named results.

**Implemented in:** all three chapter files.

### G.02 — set, function, and measure notation

**Category:** Notation

**Issue:** Several handwritten symbols were ambiguous, including `\in` versus `\subseteq`, complements, inverse images, restrictions, sections, and open versus half-open interval endpoints.

**Correction:** Replaced ambiguous marks by explicit LaTeX notation, consistently used `\1_E` for indicator functions, `\restr` for restrictions, `|\nu|` for total variation, and distinct symbols for positive, negative, singular, and absolutely continuous parts.

**Reason:** These distinctions affect the meaning of statements and are especially important in signed-measure and differentiation arguments.

**Implemented in:** all three chapter files.

### G.03 — hypotheses stated where used

**Category:** Mathematical and expository

**Issue:** Finiteness, sigma-finiteness, regularity, continuity, local integrability, and almost-everywhere qualifications were often implicit or omitted.

**Correction:** Added each hypothesis to the theorem or proof step where it is needed. Endpoint cases such as `p=1`, `p=\infty`, finite versus sigma-finite measures, and centered versus uncentered averages were separated explicitly.

**Reason:** Several source arguments are false or incomplete without these assumptions.

**Implemented in:** all three chapter files.

### G.04 — invalid extended-value arithmetic removed

**Category:** Mathematical

**Issue:** Some arguments implicitly subtracted infinite quantities or used a conclusion that would require evaluating `\infty-\infty`.

**Correction:** Replaced those steps by monotone arguments, finite restrictions, Jordan decompositions, or nonnegative difference quotients before applying Fatou or monotone convergence.

**Reason:** `\infty-\infty` is undefined, so such calculations cannot justify a measure or integral identity.

**Implemented in:** Chapters 2 and 3.

### G.05 — proof fragments expanded

**Category:** Grammar and proof completeness

**Issue:** Phrases such as “trivial,” “similar,” “by the same argument,” and “by approximation” sometimes concealed a real covering, disjointification, compactness, monotone-class, or limiting argument.

**Correction:** Supplied the omitted construction whenever it was logically substantive. Routine algebraic repetitions remain concise.

**Reason:** The corrected notes are intended to stand alone as a rigorous manuscript.

**Implemented in:** all three chapter files.

### G.06 — complex-valued conventions

**Category:** Mathematical notation

**Issue:** Pairings and equality cases were occasionally written as though all functions and measures were real-valued.

**Correction:** Used conjugate pairings `\int f\overline g`, separated magnitude proportionality from phase alignment, and defined complex-measure integration through the real and imaginary parts before deriving the polar representation.

**Reason:** Real-valued equality criteria do not automatically remain correct over `\mathbb C`.

**Implemented in:** Chapters 3 and 4.

### G.07 — theorem organization and cross-references

**Category:** LaTeX and exposition

**Issue:** The source numbering continues from earlier material and several references used inconsistent labels such as “Thm above,” “Ex,” or an incorrect chapter number.

**Correction:** Preserved the chapter sequence while replacing unstable prose references with nearby theorem names or logically self-contained arguments.

**Reason:** The modular chapter files must remain readable and compilable without depending on handwritten page placement.

**Implemented in:** all three chapter files.

### G.08 — preamble compatibility

**Category:** Compilation

**Issue:** The supplied style file contained an obsolete driver option and an unmatched `\makeatletter` state.

**Correction:** The compilation-safe copy removes the conflicting `hypertex=true` setting, closes the package with `\makeatother`, and ends with `\endinput`. The exact uploaded preamble remains preserved separately.

**Reason:** These are minimal compatibility repairs required for a stable modern PDF build; they do not alter the mathematical content.

**Implemented in:** `statnotes-preamble.sty`; the unchanged source is `notes-preamble-original.sty`.

---

# Chapter 2 — Differentiation, bounded variation, and absolute continuity

## C2.01 — source PDF pp. 1–2: covering selection in the maximal inequality

**Category:** Mathematical — incomplete covering argument

**Issue:** The proof attempted to choose a “largest” interval repeatedly from an arbitrary family and then applied the selection directly to the entire maximal-function level set. A largest interval need not exist in an infinite family, and the level set need not have a finite subcover.

**Correction:** For each compact set `K` contained in the open level set, choose finitely many witnessing intervals. Apply the finite three-times covering lemma to obtain disjoint intervals `I_j` with

```math
K\subseteq\bigcup_j 3I_j.
```

Use their disjointness to estimate the sum of the integrals, then pass from compact `K` to the whole open level set by inner regularity.

**Reason:** The finite reduction makes the greedy selection valid and supplies the compactness step needed to prove the weak `(1,1)` estimate.

**Implemented in:** `chapters/chapter-2-differentiation.tex`, subsection “Maximal functions and the differentiation theorem.”

## C2.02 — source PDF pp. 3–5: Lebesgue differentiation theorem

**Category:** Mathematical — limiting and exceptional-set argument

**Issue:** The approximation proof used several bad sets with inconsistent thresholds and indices, then passed from control for one continuous approximant to the desired pointwise statement without a complete limiting argument.

**Correction:** Introduced the oscillation functional

```math
Df(x)=\limsup_{r\downarrow0}\frac1{2r}\int_{x-r}^{x+r}|f(y)-f(x)|\,dy.
```

For `g\in C_c(\mathbb R)`, uniform continuity gives `Dg=0`. The estimate

```math
Df\leq M(f-g)+|f-g|+Dg
```

combined with the Hardy–Littlewood and Markov inequalities controls every level set `{Df>2\alpha}`. Density of `C_c` in `L^1` then forces `Df=0` almost everywhere.

**Reason:** This is a complete approximation argument and avoids an unproved diagonal passage between the approximants and the original function.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.03 — source PDF pp. 3–5: one-sided averages and indefinite integrals

**Category:** Mathematical — omitted implication

**Issue:** The source invoked the symmetric differentiation theorem to conclude that

```math
\frac1h\int_x^{x+h}f(t)\,dt\to f(x)
```

without explaining why the one-sided family is covered by the stated theorem.

**Correction:** Added the comparison between one-sided and centered intervals and then applied it to

```math
F(x)=\int_{-\infty}^x f(t)\,dt.
```

The proof now treats both signs of `h` and concludes `F'=f` almost everywhere.

**Reason:** The one-sided differentiation formula is not literally the same displayed limit as the centered theorem and requires a short comparison argument.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.04 — source PDF pp. 6–7: Vitali covering theorem

**Category:** Mathematical — invalid selection and missing tail estimate

**Issue:** The construction used an interval of maximal remaining length even when only a supremum was available. It did not fully prove that an uncovered point meets a later selected interval or that the containing interval lies in a five-times enlargement.

**Correction:** At stage `n`, choose an interval whose length exceeds half the supremum of the eligible lengths. Since the selected intervals are disjoint in a finite-measure open set, their lengths tend to zero. For an uncovered point, choose a sufficiently short Vitali interval and its first later intersection `I_N`; then show

```math
I\subseteq 5I_N.
```

Finally use

```math
m^*\!\left(E\setminus\bigcup_k I_k\right)
 \leq 5\sum_{k>n}|I_k|\to0.
```

**Reason:** Each of these steps is needed to justify the countable disjoint cover up to a null set.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.05 — source PDF p. 8: Dini-derivative level-set estimate

**Category:** Mathematical — strict threshold error

**Issue:** The proof used the same number `\alpha` both in the strict condition `\overline Df>\alpha` and in the interval slope inequality, without separating the limsup threshold from the selected finite difference.

**Correction:** Fixed `0<\beta<\alpha`. The Vitali intervals satisfy

```math
f(d)-f(c)>\beta(d-c),
```

which yields the estimate with `1/\beta`; then let `\beta\uparrow\alpha`.

**Reason:** A smaller auxiliary threshold is the robust way to extract a strict finite-difference inequality from a strict limsup inequality.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.06 — source PDF p. 9: differentiability of monotone functions

**Category:** Mathematical — incomplete exceptional-set proof

**Issue:** The source identified rational upper and lower slope bounds but did not correctly combine the Vitali covering with the preceding level-set estimate, nor did it finish the countable exceptional-set reduction.

**Correction:** For rational `0<\beta<\alpha`, defined

```math
E_{\alpha,\beta}
 =\{\overline Df>\alpha>\beta>\underline Df\}.
```

Used low-slope Vitali intervals inside an open enlargement, applied the upper-Dini estimate to each selected interval, and obtained

```math
m^*(E_{\alpha,\beta})
 \leq \frac\beta\alpha m^*(E_{\alpha,\beta}).
```

The finite outer measure and `\beta/\alpha<1` force this measure to be zero. A countable union over rational pairs and infinite-derivative level sets completes the proof.

**Reason:** The corrected argument establishes almost-everywhere differentiability rather than merely identifying a candidate exceptional set.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.07 — source PDF p. 10: integrability of the derivative of an increasing function

**Category:** Mathematical — unsafe subtraction and limiting argument

**Issue:** The handwritten proof manipulated translated integrals in a way that could conceal subtraction of extended values and did not clearly identify a nonnegative sequence to which Fatou applies.

**Correction:** Extended the function constantly past the right endpoint and used nonnegative forward divided differences

```math
D_hf(x)=\frac{f(x+h)-f(x)}h\geq0.
```

Fatou’s lemma gives

```math
\int_a^b f'\leq\liminf_{h\downarrow0}\int_a^bD_hf
 \leq f(b)-f(a).
```

**Reason:** The revised proof never subtracts two infinite quantities and uses Fatou exactly under its nonnegative hypothesis.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.08 — source PDF pp. 11–13: Jordan decomposition and the derivative of a BV function

**Category:** Mathematical — incomplete equivalence

**Issue:** Only the easy direction of the bounded-variation characterization was adequately justified. The canonical increasing components and the sharp derivative estimate were not derived cleanly.

**Correction:** Introduced the variation function

```math
V_f(x)=\operatorname{TV}(f;[a,x])
```

and defined

```math
g=\frac{V_f+f-f(a)}2,
\qquad
h=\frac{V_f-f+f(a)}2.
```

Both are increasing and `f=f(a)+g-h`. Applying the monotone differentiation theorem to the canonical decomposition gives

```math
\int_a^b|f'|\leq\operatorname{TV}(f;[a,b]).
```

**Reason:** This proves both directions and identifies the correct quantitative relation between derivative and total variation.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.09 — source PDF pp. 13–17: oscillatory examples and the BV derivative criterion

**Category:** Mathematical — incorrect or incomplete examples

**Issue:** The source did not rigorously establish the variation behavior of the oscillatory examples and did not obtain the correct general threshold for

```math
x^\alpha\sin(x^{-\beta}).
```

The proof of the `C^1` criterion also used endpoint bounds rather than a valid integral representation on compact subintervals.

**Correction:** Proved that the oscillatory function belongs to BV near zero exactly when `\alpha>\beta`. For `\alpha\leq\beta`, successive extrema yield partition sums dominating

```math
\sum_n n^{-\alpha/\beta},
```

which diverges. For `f\in C([a,b])\cap C^1((a,b))`, proved

```math
f\in\operatorname{BV}([a,b])
 \Longleftrightarrow f'\in L^1(a,b)
```

using the fundamental theorem on compact subintervals and continuity at the endpoints.

**Reason:** The corrected threshold and proof distinguish integrability of the derivative from merely bounded pointwise oscillation.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.10 — source PDF pp. 18–19: absolute continuity implies bounded variation

**Category:** Mathematical — misuse of the defining `\delta`

**Issue:** The source used one small-total-length estimate to control an arbitrary partition, although an arbitrary partition may have total interval length much larger than `\delta`. It then asserted that the variation function is absolutely continuous without a complete refinement argument.

**Correction:** Grouped each partition into finitely many subfamilies, each having total length below `\delta`, to obtain a uniform variation bound. To prove `V_f` is absolutely continuous, refined nearly maximizing partitions inside each of a disjoint family of intervals and combined the refinements before applying the absolute-continuity estimate for `f`.

**Reason:** The definition of absolute continuity controls only collections whose total length is small; grouping and refinement are essential.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.11 — source PDF pp. 20–21: divided differences and uniform integrability

**Category:** Mathematical — circular and incomplete equivalence

**Issue:** The forward direction did not justify the estimate for arbitrary measurable sets, while the reverse direction passed from local averages to the original function without establishing the required uniform convergence. Parts of the source argument risked using the fundamental theorem before it had been proved.

**Correction:** Decomposed an absolutely continuous function into increasing absolutely continuous components. For each component, used Tonelli and translated disjoint intervals to prove uniform integrability of its divided differences. Conversely, applied uniform integrability to the identity

```math
\int_u^vD_hf=A_hf(v)-A_hf(u)
```

and used uniform convergence `A_hf\to f`, which follows from uniform continuity of the constant extension.

**Reason:** This proves the equivalence directly from the definition of absolute continuity and does not presuppose the fundamental theorem of calculus.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.12 — source PDF p. 21: local-to-global absolute continuity for increasing functions

**Category:** Mathematical — incomplete endpoint argument

**Issue:** The source split intervals near zero but did not clearly control intervals crossing the split point or justify the sum of the increments on the initial segment.

**Correction:** Chose `\eta` so that `f(\eta)-f(0)` is small, split every test interval at `\eta`, used monotonicity to bound all increments in `[0,\eta]` by the single increment `f(\eta)-f(0)`, and applied absolute continuity on `[\eta,1]` to the remaining pieces.

**Reason:** This gives a direct proof from the definition and correctly handles intervals that cross the endpoint neighborhood.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.13 — source PDF pp. 25–26: fundamental theorem of calculus

**Category:** Mathematical — circular proof

**Issue:** The handwritten proof inferred the integral representation from uniform integrability of divided differences without fully justifying convergence of their integrals; other steps used consequences equivalent to the theorem itself.

**Correction:** Used the absolutely continuous Jordan decomposition `f=g-h`. The monotone theorem supplies `g',h'\in L^1`. Divided differences converge almost everywhere and form uniformly integrable families, so the Vitali convergence theorem gives

```math
\int_a^x g'=g(x)-g(a),
\qquad
\int_a^x h'=h(x)-h(a).
```

Subtracting proves the representation. The converse follows from absolute continuity of the Lebesgue integral.

**Reason:** Every convergence step now rests on a previously established theorem rather than on the desired conclusion.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.14 — source PDF pp. 22–23 and 27–29: null-set property and the Banach–Zarecki converse

**Category:** Mathematical — completed converse

**Issue:** The source correctly aimed to show that absolutely continuous functions map null sets to null sets, but the converse criterion for increasing continuous functions was not supplied by a complete argument.

**Correction:** Proved Lusin’s property `(N)` by covering the null set with disjoint intervals whose total length is small, and proved measurability of images by decomposing a measurable set into an `F_\sigma` part and a null remainder. For the increasing converse, introduced the Lebesgue–Stieltjes measure `\mu_f`; property `(N)` implies `\mu_f\ll m`, so Radon–Nikodym gives

```math
f(x)-f(a)=\int_a^x u(t)\,dt,
```

and hence absolute continuity.

**Reason:** The converse requires a measure-theoretic argument; property `(N)` alone cannot simply be substituted into the definition.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.15 — source PDF p. 28: equality between variation and the integral of `|f'|`

**Category:** Mathematical — missing converse

**Issue:** The source proved the easy inequality but did not fully justify why equality forces absolute continuity.

**Correction:** At points of differentiability, used

```math
V_f'(x)\geq|f'(x)|.
```

Equality of the endpoint quantities forces

```math
\int_a^bV_f'=V_f(b)-V_f(a).
```

The monotone characterization then makes `V_f` absolutely continuous; its canonical Jordan components, and therefore `f`, are absolutely continuous.

**Reason:** Equality in an integral inequality does not by itself imply absolute continuity until the variation function is shown to attain equality in the monotone derivative bound.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.16 — source PDF p. 27: concentration criterion for singular increasing functions

**Category:** Mathematical — intervals assigned to the wrong part of the estimate

**Issue:** The source interchanged the short selected intervals and their complementary intervals when estimating derivative mass and total increase.

**Correction:** Used Vitali intervals around points where the derivative is zero to capture almost all of that set while carrying very little increase. The complementary intervals then carry almost all of the total increase but have arbitrarily small total length. Conversely, absolute continuity of the integral of `u'` controls the selected union, while the monotone derivative estimate controls the complementary intervals.

**Reason:** The two interval families play different roles; reversing them destroys the estimate proving `u'=0` almost everywhere.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

## C2.17 — source PDF pp. 27–29: Lebesgue decomposition of a BV function

**Category:** Mathematical — uniqueness and normalization

**Issue:** The source stated the decomposition into absolutely continuous and singular parts but treated uniqueness as literal equality without accounting for additive constants.

**Correction:** Defined

```math
g(x)=\int_a^x f'(t)\,dt,
\qquad s=f-g.
```

Then `g` is absolutely continuous and `s` is singular. Two decompositions differ by a function that is both absolutely continuous and singular, hence constant. Imposing `g(a)=0` gives uniqueness.

**Reason:** Derivatives determine functions only up to an additive constant.

**Implemented in:** `chapters/chapter-2-differentiation.tex`.

---

# Chapter 3 — Signed measures, Radon–Nikodym theory, and differentiation of measures

## C3.01 — source PDF p. 30: continuity for signed measures

**Category:** Mathematical — missing finiteness hypothesis

**Issue:** Continuity from above was stated as though it held for every decreasing sequence of sets.

**Correction:** Added the hypothesis that `\nu(E_1)` is finite and proved the result by applying continuity from below to `E_1\setminus E_n` and subtracting only from this finite number.

**Reason:** Without finiteness, subtraction can be undefined and continuity from above can fail for signed measures.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.02 — source PDF pp. 31–32: positive-subset lemma and Hahn decomposition

**Category:** Mathematical — invalid recursive argument

**Issue:** The source changed signs in a way that could reverse the standing hypothesis and used a sequence of negative subsets without proving that the thresholds tend to infinity or that the residual set is positive.

**Correction:** Removed pairwise disjoint negative subsets `A_k` at successively minimal thresholds `-1/n_k`. Proved `n_k\to\infty`, that the total removed measure is finite from below, that the residual set has positive measure, and that any negative subset of the residual set would contradict the minimality of a later threshold. Used this lemma to complete the Hahn decomposition.

**Reason:** The positivity of the residual carrier is the central missing step in the source proof.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.03 — source PDF p. 32: Hahn and Jordan uniqueness

**Category:** Mathematical — carriers not distinguished

**Issue:** Positive, negative, and null carriers were conflated, and the uniqueness of the Jordan parts was asserted without clearly invoking the null symmetric differences of two Hahn decompositions.

**Correction:** Proved that `P\cap N'` and `P'\cap N` are simultaneously positive and negative and therefore null. Defined

```math
\nu^+(E)=\nu(E\cap P),
\qquad
\nu^-(E)=-\nu(E\cap N),
```

and derived uniqueness and mutual singularity from the carrier decomposition.

**Reason:** The Jordan measures are unique even though the Hahn carriers themselves are unique only modulo null sets.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.04 — source PDF pp. 33–35: null sets, total variation, and extremal formulas

**Category:** Mathematical — incomplete total-variation arguments

**Issue:** The source moved between `\nu`, `\nu^+`, `\nu^-`, and `|\nu|` without always identifying the relevant Hahn carrier. Some supremum formulas were stated without proving both inequalities.

**Correction:** Proved that a set is `\nu`-null exactly when its total variation is zero, established

```math
\left|\int f\,d\nu\right|\leq\int|f|\,d|\nu|,
```

and obtained equality in the extremal formula by taking the sign function `\1_P-\1_N` on a Hahn decomposition. The partition formula for total variation was also proved in both directions.

**Reason:** The sign choice and the Hahn carriers are necessary for the reverse inequalities.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.05 — source PDF pp. 37–38: finite Lebesgue–Radon–Nikodym theorem

**Category:** Mathematical — maximal-density proof incomplete

**Issue:** The source considered minorizing densities but did not fully prove closure under maxima, attainment of the supremum, or singularity of the residual measure.

**Correction:** Defined the class of nonnegative `g` satisfying

```math
\int_Eg\,d\mu\leq\nu(E)
```

for every measurable `E`, proved it is closed under pointwise maxima, chose successive maxima with integrals approaching the supremum, and used monotone convergence to obtain a maximal density `f`. A comparison lemma shows that a nonsingular residual would dominate `\varepsilon\mu` on a positive-measure set, allowing `f` to be increased and contradicting maximality.

**Reason:** This supplies the key argument that the residual measure is singular.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.06 — source PDF p. 38: sigma-finite Radon–Nikodym theorem

**Category:** Mathematical — patching on overlapping sets

**Issue:** The source passed from finite to sigma-finite measures without first producing a disjoint partition on which both the reference measure and the total variation of the signed measure are finite.

**Correction:** Chose a countable measurable partition `(X_n)` with

```math
\mu(X_n)<\infty,
\qquad
|\nu|(X_n)<\infty,
```

applied the finite theorem on each piece, and patched the local densities and singular parts along the disjoint partition.

**Reason:** Disjointness prevents double counting and makes the global density well defined almost everywhere.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.07 — source PDF p. 44: extended Radon–Nikodym theorem

**Category:** Mathematical — arbitrary positive measures

**Issue:** The source used an extended density but did not separate the sigma-finite region from the region on which the measure must be infinite, leaving ambiguous expressions involving infinite values.

**Correction:** Maximized the reference-measure size of a set `S` on which `\nu` is sigma-finite. Used an ordinary density `f_0` on `S` and defined `f=+\infty` off `S`. If a set has positive `\mu`-measure outside `S`, its `\nu`-measure must be infinite; otherwise `S` could be enlarged. Signed measures are handled on disjoint Jordan carriers.

**Reason:** The case distinction avoids conventions such as `0\cdot\infty` and proves the identity for every measurable set.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.08 — source PDF p. 45: decomposable measures

**Category:** Mathematical — uncountable additivity error

**Issue:** The source effectively summed over an uncountable family by countable additivity and did not allow null decomposition pieces, which are needed when a sigma-finite cover is disjointified.

**Correction:** Defined decomposability using the unordered nonnegative sum. For a finite-measure set `E`, first proved that only countably many pieces satisfy `\mu(E\cap F)>0`. The remaining part is measurable and `\mu`-null, hence `|\nu|`-null. Countable additivity and the integral decomposition can then be used legitimately.

**Reason:** Countable additivity cannot be applied directly to an arbitrary uncountable family.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.09 — source PDF pp. 39–42 and 46–47: Radon–Nikodym chain and product rules

**Category:** Mathematical — missing hypotheses and incomplete verification

**Issue:** The source stated chain and product identities without consistently specifying that the intermediate measures are positive and sigma-finite, and it attempted to verify the product formula at singletons.

**Correction:** Stated the sigma-finite hypotheses explicitly. Proved the chain rule by substituting one Radon–Nikodym representation into the other and invoking uniqueness. Proved the product rule by checking the proposed density on measurable rectangles, using uniqueness of product measures, and then uniqueness of the derivative.

**Reason:** Singleton calculations do not determine a product measure in general, whereas rectangles form the correct generating class.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.10 — source PDF pp. 43–44: failures without sigma-finiteness

**Category:** Mathematical — examples and decomposition claims

**Issue:** The source’s counting-measure examples did not cleanly separate absolute continuity from the existence of a Radon–Nikodym density or a Lebesgue decomposition.

**Correction:** On `\mathbb N`, used a weighted finite measure to show that `\nu\ll\mu` need not imply a global epsilon–delta estimate when `\nu` is not finite. On an uncountable interval, showed that Lebesgue measure is absolutely continuous with respect to counting measure but has no counting-measure density, because any density must vanish at every singleton.

**Reason:** These examples isolate exactly which finiteness and sigma-finiteness assumptions are indispensable.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.11 — source PDF pp. 46–49: complex integration, variation, and polar decomposition

**Category:** Mathematical — incomplete complex-measure theory

**Issue:** Integration with respect to a complex measure was called “obvious,” and the source used the formula `|\nu|=|f|\mu` before proving it. The partition and simple-function descriptions of variation were not connected rigorously.

**Correction:** Defined complex integration through `\Re\nu` and `\Im\nu`. With

```math
\mu=|\Re\nu|+|\Im\nu|,
\qquad \nu=f\mu,
```

proved `|\nu|\leq|f|\mu` from partitions and the reverse inequality by approximating the phase `\overline f/|f|` with simple functions. Only then defined the unimodular polar factor `h=f/|f|`. The equivalent partition and simple-test-function formulas were proved explicitly.

**Reason:** The polar decomposition depends on, rather than proves automatically, the total-variation identity.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.12 — source PDF pp. 50–54: maximal theorem and differentiation in `\mathbb R^n`

**Category:** Mathematical — finite-cover and approximation gaps

**Issue:** The source chose largest balls from an arbitrary cover and passed directly from the selected family to the whole level set. The differentiation proof did not completely control the approximation error.

**Correction:** Proved the finite three-times ball lemma, applied it to a finite subcover of a compact subset of `{Mf>\alpha}`, and used inner regularity. For differentiation, approximated by `C_c` functions and used

```math
\limsup_{r\downarrow0}|A_rf-f|
 \leq M(f-g)+|f-g|.
```

The maximal and Markov inequalities then make the bad set arbitrarily small.

**Reason:** This is the Euclidean analogue of the corrected one-dimensional proof and avoids an unjustified infinite greedy selection.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.13 — source PDF p. 55: differentiation of singular regular measures

**Category:** Mathematical — singular part not localized correctly

**Issue:** The source attempted to control the singular measure globally and used an open set without first reducing to a finite measure or preserving the relevant carrier estimate.

**Correction:** Restricted the variation to a compact ball, selected a compact subset `K` of a null carrier leaving arbitrarily small residual variation, and applied the maximal estimate to that residual finite measure. Outside `K`, sufficiently small balls avoid `K`, so the density of the singular part is zero almost everywhere. Nicely shrinking sets are then dominated by the centered-ball estimate.

**Reason:** Finiteness and regularity are needed before the maximal inequality can be applied to the singular residual.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.14 — source PDF p. 58: right-continuous modification of a monotone function

**Category:** Mathematical — derivative comparison incomplete

**Issue:** The source introduced a point-mass measure for the jumps but did not justify the local finiteness and limiting estimate needed to conclude that the correction has derivative zero almost everywhere.

**Correction:** Proved directly that the jump set is countable. At a point outside the jump set where both derivatives exist, the difference `H=G-F` vanishes at the point and on a dense set. Taking a sequence of continuity points approaching the point forces `H'=0`.

**Reason:** The direct dense-sequence argument is shorter and avoids constructing a measure whose role was not fully justified.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.15 — source PDF pp. 59–61: right continuity of the variation function

**Category:** Mathematical — missing near-maximizing partition argument

**Issue:** The source estimated the variation jump using symbols that were not tied to a fixed nearly maximizing partition, so the passage to zero was not established.

**Correction:** Fixed a partition on `[x,x+1]` whose variation sum is within `\varepsilon` of the total variation. For small `h`, removed the first partition point and used right continuity of `F` to prove

```math
0\leq V(x,x+h)\leq\varepsilon+|F(x+h)-F(x)|.
```

Letting `h\downarrow0` and then `\varepsilon\downarrow0` gives right continuity of `T_F`.

**Reason:** Total variation is a supremum, so a near-maximizer must be fixed before it can be compared at neighboring endpoints.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.16 — source PDF pp. 62–64 and 67: Lebesgue–Stieltjes correspondence and variation measure

**Category:** Mathematical — measure and variation conflated

**Issue:** The source decomposed a complex measure into positive pieces but did not prove that the variation of the resulting measure is the Stieltjes measure generated by the variation function.

**Correction:** Established the bijection

```math
F\in\operatorname{NBV}(\mathbb R)
 \longleftrightarrow \mu_F
```

using half-open intervals. On every finite partition, identified the variation sum of `F` with the corresponding partition sum for `\mu_F`, then used the partition characterization of complex total variation to obtain

```math
|\mu_F|=\mu_{T_F}.
```

**Reason:** The equality of these positive measures is not automatic from the real and imaginary Jordan decompositions.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.17 — source PDF pp. 63–65: absolute continuity of NBV functions

**Category:** Mathematical — definition equivalent to the conclusion

**Issue:** The source’s global absolute-continuity condition was stated in a way that already resembled the desired measure-theoretic characterization and did not clearly specify locality on the real line.

**Correction:** Defined an NBV function to be absolutely continuous when it is absolutely continuous on every compact interval. Proved

```math
F\text{ locally absolutely continuous}
 \Longleftrightarrow \mu_F\ll m,
```

and then recovered `d\mu_F=F'\,dm` and the compact-interval fundamental theorem.

**Reason:** Local absolute continuity is the natural notion for a function on all of `\mathbb R` and matches local finiteness of the associated measure.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

## C3.18 — source PDF p. 70: change of variables for an increasing map

**Category:** Mathematical — pushforward and endpoint issues

**Issue:** The source computed generalized inverses on intervals but did not formulate the result as a pushforward identity, and the failure in the merely right-continuous case was not explained structurally.

**Correction:** For continuous increasing `G:[a,b]\to[c,d]`, proved that the pushforward of `\mu_G` under `G` is Lebesgue measure by checking half-open intervals and applying a monotone-class argument. Therefore

```math
\int_c^d f(y)\,dy
 =\int_a^b f(G(x))\,d\mu_G(x).
```

A discontinuous step function shows the failure without continuity because its Stieltjes measure has atoms.

**Reason:** The pushforward formulation makes the measure identity and the role of continuity precise.

**Implemented in:** `chapters/chapter-3-signed-measures.tex`.

---

# Chapter 4 — `L^p` spaces

## C4.01 — source PDF p. 76: finite-measure embeddings and the endpoint `q=\infty`

**Category:** Mathematical — omitted endpoint

**Issue:** The source applied Hölder with the exponent `q/p` even when `q=\infty`, where that calculation is not meaningful.

**Correction:** Treated finite `q` by Hölder and handled the endpoint separately using

```math
\int_X|f|^p\leq\|f\|_\infty^p\mu(X).
```

The unified conclusion is

```math
\|f\|_p\leq\mu(X)^{1/p-1/q}\|f\|_q.
```

**Reason:** Endpoint cases require their own argument rather than formal substitution of infinity into finite exponents.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.02 — source PDF p. 77: dual formula for `\|f\|_p`

**Category:** Mathematical — endpoint and complex phase

**Issue:** The norming function was written only for `1<p<\infty` and without a fully correct complex-valued convention.

**Correction:** For `1<p<\infty`, used

```math
h=\frac{f|f|^{p-2}}{\|f\|_p^{p-1}},
```

and for `p=1` used the measurable phase `h=f/|f|` on `{f\neq0}`. Pairings are written as `\int f\overline h`.

**Reason:** The endpoint `p=1` has conjugate exponent infinity, and complex norming functions must cancel the phase of `f`.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.03 — source PDF pp. 83 and 86: equality in Hölder and Minkowski

**Category:** Mathematical — real equality criterion used for complex functions

**Issue:** The source recorded proportionality of absolute values but did not separately require alignment of complex phases. The Minkowski equality proof used a norming function without completing the equality analysis.

**Correction:** Equality in Hölder is stated as the conjunction of

```math
|f|^p=c|g|^{p'}
```

and constant phase of `f\overline g`. Equality in Minkowski for `1<p<\infty` is equivalent to nonnegative proportionality `af=bg` almost everywhere. The `L^1` equality case is stated as `f\overline g\geq0` almost everywhere.

**Reason:** Magnitude proportionality alone is insufficient over the complex field.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.04 — source PDF p. 84: the `L^\infty` dual norm formula

**Category:** Mathematical — zero norm and finite-support selection

**Issue:** The source divided by the measure of a near-extremal set without first ensuring that the set has finite positive measure and did not separate the case `\|f\|_\infty=0`.

**Correction:** Treated the zero case immediately. For positive norm, sigma-finiteness supplies a finite positive-measure subset `F` of `{|f|>M-\varepsilon}`. The normalized phase indicator on `F` has `L^1` norm one and yields a pairing larger than `M-\varepsilon`.

**Reason:** A near-extremal level set may have infinite measure, and normalization by zero or infinity is invalid.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.05 — source PDF p. 80: natural map from `L^{p'}` into `(L^p)^*`

**Category:** Mathematical — injectivity at `p=1`

**Issue:** The source claimed injectivity for arbitrary measure spaces. At `p=1`, nonzero `L^\infty` functions supported on parts of the space that contain no nonzero integrable test functions may not be detected without an additional measure-theoretic hypothesis.

**Correction:** Added sigma-finiteness in the endpoint case `p=1`, retained the isometric injection for `1<p<\infty`, and used the corrected dual norm formula to prove equality of operator and function norms.

**Reason:** Sigma-finiteness supplies positive finite-measure test subsets and prevents the pairing from missing a nonzero essential value.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.06 — source PDF pp. 79 and 91: completeness for `p\geq1` and for `0<p<1`

**Category:** Mathematical — convergence construction incomplete

**Issue:** The source defined pointwise sums of successive differences but did not fully prove that the majorant belongs to `L^p`, that the limit is measurable, or that the original Cauchy sequence—not merely the selected subsequence—converges. The `0<p<1` case was treated as though `\|\cdot\|_p` were a norm.

**Correction:** Chose a subsequence with summable successive `L^p` distances and formed the monotone majorants

```math
g_N=|f_{n_1}|+\sum_{k<N}|f_{n_{k+1}}-f_{n_k}|.
```

Minkowski and monotone convergence give `g\in L^p`, so the telescoping series converges almost everywhere. Fatou yields convergence of the subsequence in `L^p`, and the Cauchy property gives convergence of the full sequence. For `0<p<1`, used the complete metric

```math
d(f,g)=\|f-g\|_p^p
```

and the inequality `|\sum u_k|^p\leq\sum|u_k|^p`.

**Reason:** Completeness requires a limit in the actual metric and a final return from the subsequence to the whole sequence.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.07 — source PDF p. 85: failure of interval-step density in `L^\infty`

**Category:** Mathematical — counterexample not justified

**Issue:** The source selected a fat Cantor set but did not clearly prove that every finite interval step function fails to approximate its indicator in essential supremum.

**Correction:** Used a fat Cantor set `C` for which every interval meeting the construction contains positive-measure portions of both `C` and `C^c`. On an interval where a step function is constant, being within less than `1/2` of `\1_C` would require that constant to be simultaneously near `1` and near `0` on positive-measure subsets.

**Reason:** Essential-supremum approximation is defeated by positive-measure oscillation inside every interval of constancy, not merely by topological density.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.08 — source PDF p. 95: small-interval integral limit

**Category:** Mathematical — incorrect parameter range

**Issue:** The source’s necessity calculation and endpoint treatment did not give the exact range of `\lambda`.

**Correction:** For `1\leq p<\infty`, Hölder gives the sufficient condition

```math
\lambda\leq1-\frac1p,
```

including equality because the local `L^p` integral tends to zero. Power-function tests prove necessity. For `p=\infty`, the exact range is `\lambda<1`; the constant function excludes `\lambda\geq1`.

**Reason:** The finite-`p` endpoint and the `p=\infty` endpoint behave differently.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.09 — source PDF pp. 94 and 98: definition of uniform integrability

**Category:** Mathematical — definition insufficient on general spaces

**Issue:** The source used only the small-set condition. On spaces with atoms, that condition may be vacuous and does not imply a uniform `L^1` bound.

**Correction:** Defined uniform integrability by requiring both

```math
\sup_{f\in\mathcal F}\int|f|<\infty
```

and uniform absolute continuity on sufficiently small measurable sets. Explained that on a finite nonatomic Lebesgue-measure set, the first condition follows by partitioning the space into finitely many small pieces.

**Reason:** The explicit uniform bound is necessary for a definition that works on arbitrary measure spaces.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.10 — source PDF pp. 97–99: Vitali convergence on finite and general spaces

**Category:** Mathematical — escape of mass not separated from concentration

**Issue:** The source used uniform integrability alone in settings where mass may escape to infinity and moved between almost-everywhere convergence and convergence in measure without a subsequence argument.

**Correction:** On a finite-measure set, extracted almost-everywhere convergent subsubsequences, used Fatou to transfer the small-set estimate to the limit, and applied Egoroff. On a general measure space, added tightness: a finite-measure set must capture all tails uniformly. The converse from `L^1` convergence treats a tail close to the singleton `{f}` and absorbs finitely many initial terms.

**Reason:** Uniform integrability prevents concentration on small sets, whereas tightness prevents mass from escaping through larger and larger regions.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## C4.11 — source PDF pp. 97–99: `L^p` Vitali and Scheffé–Riesz criteria

**Category:** Mathematical — endpoint and power-difference arguments

**Issue:** The source treated all `p` by the same formal calculation and invoked a generalized dominated-convergence statement without proving the needed uniform-integrability conclusion.

**Correction:** Proved the Scheffé–Riesz criterion directly with Fatou’s lemma applied to

```math
g_n=2^{p-1}(|f_n|^p+|f|^p)-|f_n-f|^p.
```

For the `L^p` Vitali criterion, treated `p=1` separately. For `p>1`, used

```math
\bigl||u|^p-|v|^p\bigr|
 \leq p(|u|+|v|)^{p-1}|u-v|
```

and Hölder to obtain `L^1` convergence of the `p`th powers from `L^p` convergence. The converse applies the general Vitali theorem to `|f_n-f|^p`.

**Reason:** The endpoint `p=1` and the nonlinear map `u\mapsto|u|^p` require distinct arguments.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

---

## Files corresponding to this log

- `measure-theory-notes-part2.tex`
- `chapters/chapter-2-differentiation.tex`
- `chapters/chapter-3-signed-measures.tex`
- `chapters/chapter-4-lp-spaces.tex`
- `statnotes-preamble.sty`
- `notes-preamble-original.sty`
- `measure-theory-notes-part2.pdf`

