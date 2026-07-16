# Functional Analysis handwritten-note review: correction ledger

This ledger records every substantive mathematical, logical, notational, grammatical, or compilation-related repair made in the corrected LaTeX manuscript. The rendered source pages were authoritative, and the source PDF and canonical preamble are preserved byte-for-byte.

## Global and compilation corrections

### G.01 -- source PDF pp. 1--95: Rendered pages, not extracted text, were treated as authoritative

**Category:** Source integrity

**Issue.** The PDF text layer and automatic extraction garble quantifiers, subscripts, arrows, interval endpoints, and several theorem statements.

**Correction.** Every formula and statement was reconstructed from the rendered page images; extraction was used only for navigation.

**Reason.** Copying the extracted text would have introduced false symbols and broken mathematics.

**Implemented in:** `project-wide`.

### G.02 -- source PDF pp. 1--95: Exact preservation of the supplied inputs

**Category:** Source integrity

**Issue.** The task required a corrected transcription without silently altering the handwritten source or the supplied reusable preamble.

**Correction.** The source PDF was copied byte-for-byte to `source/original-notes.pdf`; the canonical preamble was copied byte-for-byte to `preamble/notes-preamble-original.sty` and to the working `notes-preamble.sty`.

**Reason.** This preserves an auditable baseline and separates source preservation from manuscript corrections.

**Implemented in:** `source/original-notes.pdf; preamble/notes-preamble-original.sty; notes-preamble.sty`.

### G.03 -- source PDF pp. 1--95: Chapter order, the missing Chapter 3, and blank pages

**Category:** Editorial structure

**Issue.** A normal automatic chapter sequence would invent a Chapter 3, while blank pages 16, 58, 60, and 93 could be mistaken for missing content.

**Correction.** The master explicitly advances the chapter counter from 2 to 4, and the page ledger accounts for every page while omitting the four blank pages from the mathematical text.

**Reason.** The corrected edition must preserve the visible source organization rather than silently renumbering or fabricating content.

**Implemented in:** `notes.tex; Page_ledger.csv`.

### G.04 -- source-wide: Notation and scalar conventions

**Category:** Notation

**Issue.** The handwriting alternates among ambiguous symbols for domains, ranges, kernels, closures, dual pairings, weak convergence, adjoints, and complex inner products.

**Correction.** Standard LaTeX notation was adopted consistently, and each complex-space proof states or respects the chosen linearity convention.

**Reason.** These distinctions affect signs, conjugates, and the truth of adjoint identities.

**Implemented in:** `notes.tex; chapters/*.tex`.

### G.05 -- source-wide: Grammar, theorem names, and proof prose

**Category:** Grammar and logic

**Issue.** The source contains fragments, missing articles, spelling errors, and compressed transitions such as “similarly” or “contradiction” without the logical bridge.

**Correction.** Sentences, punctuation, capitalization, theorem names, and agreement were repaired; omitted nontrivial implications were written out.

**Reason.** Readable prose is part of a checkable proof, especially where the omitted step contains a limiting or compactness argument.

**Implemented in:** `chapters/*.tex`.

### G.06 -- source-wide: Compilation-safe mathematical source

**Category:** Compilation

**Issue.** A literal transcription would contain Unicode lookalikes, malformed braces, undefined ad hoc commands, and chapter files with incompatible wrappers.

**Correction.** All symbols use standard LaTeX commands; project macros and source-labelled theorem environments live in the master; chapter files contain no document wrappers or package loading.

**Reason.** The modular project now builds reproducibly through one master file.

**Implemented in:** `notes.tex; chapters/*.tex`.

### G.07 -- canonical preamble: Preamble compatibility without modifying the canonical file

**Category:** Compilation

**Issue.** The reusable preamble sets `pgfplots` compatibility to `newest`, which emits a notification under the installed TeX distribution.

**Correction.** The preamble itself was left byte-identical; the master locally sets `\pgfplotsset{compat=1.18}` after loading it.

**Reason.** This removes the build notification without changing the user-supplied package.

**Implemented in:** `notes.tex`.

### G.08 -- final Chapter 8 transition: Accidental marker-only page removed

**Category:** Layout

**Issue.** A zero-height source-page marker placed after the final Chapter 8 box was pushed onto an otherwise blank page.

**Correction.** The duplicate terminal marker was omitted because page 90 was already marked immediately above, and the closing definition was phrased more compactly.

**Reason.** The mathematical content and source accounting remain intact while the accidental blank continuation page disappears.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

## Chapter 1 -- Review of the Great Theorems

### C1.01 -- source PDF p. 1: Hahn--Banach one-step extension and Zorn argument

**Category:** Mathematical proof

**Issue.** The source stated the maximal-extension idea but did not justify the interval of admissible values for the new vector or the chain upper bound.

**Correction.** The admissible lower and upper bounds for the extension value are derived from sublinearity, and the union of a chain is shown to be a well-defined dominated extension.

**Reason.** Both facts are required before Zorn’s lemma yields an extension to all of the space.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.02 -- source PDF p. 2: Uniqueness of norm-preserving Hahn--Banach extensions

**Category:** False equivalence

**Issue.** The source asserted an “if and only if” between strict convexity of the dual and uniqueness of every norm-preserving extension.

**Correction.** Only the valid sufficient direction is stated: strict convexity of the dual forces two norm-preserving extensions to coincide after averaging. The unsupported converse is explicitly not claimed.

**Reason.** The one-line averaging argument proves sufficiency but not the converse without a substantially stronger unique-extension hypothesis.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.03 -- source PDF p. 3: Norming functionals and separation of points

**Category:** Mathematical completeness

**Issue.** The source used a functional with `f(x)=||x||` without constructing it and compressed point separation into a slogan.

**Correction.** Hahn--Banach is applied to the one-dimensional span of `x`, producing a norm-one functional; applying it to `x-y` separates distinct points.

**Reason.** This supplies the exact normalization and proves the separating property of the dual.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.04 -- source PDF pp. 3--4: Minkowski functional hypotheses and sublevel characterization

**Category:** Missing hypotheses

**Issue.** The gauge was introduced for an open convex set without clearly requiring `0` in the set and absorbency, and the proof mixed strict and non-strict sublevel sets.

**Correction.** The set is assumed open, convex, absorbing, and containing `0`; the proof establishes sublinearity, positive homogeneity, and `C={x:p_C(x)<1}`.

**Reason.** Without absorbency the gauge may be infinite, and the open-set conclusion requires a strict inequality.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.05 -- source PDF p. 5: Geometric separation theorems

**Category:** Mathematical precision

**Issue.** The handwritten inequalities did not consistently distinguish weak separation from strict separation or state which set must be open/compact.

**Correction.** The point-versus-open-set result is derived from the gauge; the two-set theorem states strict separation when one set is open and positive-gap separation when one set is closed and the other compact.

**Reason.** The hypotheses determine whether a separating hyperplane merely orders the sets or separates them by a positive margin.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.06 -- source PDF pp. 6--7: Baire category definitions, conclusion, and proof

**Category:** False statement and proof

**Issue.** “Nowhere dense” was identified only with empty interior, and the open-dense formulation was written as an intersection equal to `X`. The proof used open balls whose limits need not remain inside them.

**Correction.** Nowhere dense means `int(cl A)=empty`; a countable intersection of open dense sets is dense, not generally all of `X`; the proof uses nested closed balls with radii tending to zero.

**Reason.** These are the correct equivalent forms, and closed balls are needed to retain the limiting point.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.07 -- source PDF pp. 7--8: Uniform boundedness estimate

**Category:** Invalid translated-ball estimate

**Issue.** The source bounded operators on a ball centered at `x_0` and then treated that as a bound on a ball centered at the origin without subtracting values correctly.

**Correction.** For small `h`, both `x_0+h` and `x_0-h` lie in the Baire ball, so `2T_i h=T_i(x_0+h)-T_i(x_0-h)` gives a uniform origin-centered bound and hence a norm bound.

**Reason.** The translation step is the essential bridge from pointwise boundedness on an interior set to uniform operator norms.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.08 -- source PDF p. 8: Pointwise limits and weak boundedness

**Category:** Mathematical completeness

**Issue.** The pointwise-limit theorem omitted the uniform boundedness step, and weak boundedness of a set was asserted without a valid Banach-space family.

**Correction.** Uniform boundedness is applied to the approximating operators; for weak boundedness, the canonical evaluations `Jx` are viewed as operators on the Banach space `X*`, yielding `||Jx||=||x||`.

**Reason.** These arguments justify continuity of the limit and convert pointwise functional bounds into a norm bound.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.09 -- source PDF pp. 9--10: Open mapping and bounded inverse theorems

**Category:** Incomplete proof

**Issue.** The source’s iterative approximation did not fully control the residual or establish an origin-centered ball inside the image.

**Correction.** Baire first yields interior of the closure of `T(B_X)`; symmetry gives a ball at zero, and a geometrically decaying lifting sequence produces an exact preimage. The bounded inverse theorem then follows from continuity at zero.

**Reason.** Density of the image is not enough; the convergent correction series is what turns approximation into surjectivity on a ball.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.10 -- source PDF pp. 10--11: Boundary-value example and equivalent norms

**Category:** Missing hypothesis

**Issue.** The differential-operator example used the bounded inverse theorem before proving the boundary-value map was bijective, and the norm-equivalence proof was compressed.

**Correction.** The a priori estimate is stated conditionally on bijectivity; equivalence of two complete norms is proved by applying the closed graph theorem to the identity in both directions.

**Reason.** The bounded inverse theorem requires a bounded bijection, and completeness alone does not identify the two topologies.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.11 -- source PDF pp. 12--14: Closed graph theorem and everywhere-defined symmetric maps

**Category:** Proof repair and scalar convention

**Issue.** The source conflated a closed graph with boundedness, then gave a circular linearity proof for a symmetric map and ignored conjugation in complex spaces.

**Correction.** The graph norm proves the closed graph theorem. For an everywhere-defined symmetric map, additivity and homogeneity are obtained by testing against arbitrary vectors; closedness follows from the inner-product identity, with the linearity convention stated.

**Reason.** Closed operators can be unbounded on proper domains, and the complex case changes where conjugates occur.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

### C1.12 -- source PDF p. 15: Adjoints, compactness, closed ranges, and surjectivity

**Category:** Incorrect range identities

**Issue.** The source interchanged a range with its closure, omitted closed-range hypotheses, and stated surjectivity criteria without the required lower bound on the adjoint.

**Correction.** Schauder compactness is stated correctly; annihilator identities use closures where necessary; the closed range theorem gives equivalence of closed ranges, and surjectivity is characterized by injectivity plus a uniform lower bound for the adjoint.

**Reason.** For a general bounded operator, `Ran(T)` need not be closed, so replacing closure by equality changes the theorem.

**Implemented in:** `chapters/chapter-1-great-theorems.tex`.

## Chapter 2 -- Weak Convergence and Weak Topology

### C2.01 -- source PDF pp. 17--18: Topologies generated by maps

**Category:** Definition repair

**Issue.** The source mixed the notions of a base, a subbase, and the coarsest topology making coordinate maps continuous.

**Correction.** Bases and subbases are defined separately, and the initial topology is written as the topology generated by inverse images of open sets, with its universal mapping property proved.

**Reason.** The continuity criterion is valid only for the correctly generated topology.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.02 -- source PDF pp. 19--20: Weak topology: Hausdorffness, neighbourhoods, and finite dimensions

**Category:** Proof completion

**Issue.** The source separated points informally and asserted finite-dimensional equivalence without a complete coordinate argument.

**Correction.** A Hahn--Banach functional separates distinct points; basic weak neighbourhoods are finite intersections of inverse images; a basis and coordinate functionals show weak and norm convergence coincide in finite dimensions.

**Reason.** These facts identify the topology and prevent reliance on an unstated norm equivalence.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.03 -- source PDF p. 20: Boundedness and norm lower semicontinuity of weakly convergent sequences

**Category:** Proof repair

**Issue.** The source invoked Hahn--Banach and uniform boundedness in a way that did not specify the Banach space on which the operators act.

**Correction.** The sequence is identified with canonical evaluation operators on `X*`; uniform boundedness gives norm boundedness, and norming functionals yield `||x|| <= liminf ||x_n||`.

**Reason.** The canonical embedding supplies the correct operator family and the exact lower-semicontinuity inequality.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.04 -- source PDF pp. 20--21: Weak closure of the unit sphere

**Category:** Missing dimensional qualification

**Issue.** The source suggested the weak closure of the unit sphere is always the closed unit ball.

**Correction.** The statement is restricted to infinite-dimensional normed spaces; a finite set of functionals has a nonzero common kernel, allowing a unit-sphere perturbation inside every weak neighbourhood.

**Reason.** In finite dimensions weak and norm topologies agree, so the sphere is already closed and the claim fails.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.05 -- source PDF pp. 21--22: Compact operators and Mazur convex-tail theorem

**Category:** Proof repair

**Issue.** The weak-to-strong compactness implication and the convex-combination theorem were stated with missing subsequence and separation steps.

**Correction.** Every subsequence of `Tx_n` has a norm-convergent subsubsequence whose weak limit must be `Tx`; Mazur’s theorem is proved by separating `x` from the norm-closed convex tail if approximation fails.

**Reason.** Compactness alone does not identify the limit, and the convex-tail conclusion requires Hahn--Banach separation.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.06 -- source PDF pp. 22--24: Convex closures, weak lower semicontinuity, and weakly continuous operators

**Category:** Mathematical precision

**Issue.** The source used weak closure and strong closure interchangeably and treated weak continuity of a linear map as automatic.

**Correction.** For convex sets, norm closure equals weak closure by separation; norm-lower-semicontinuous convex functions are weakly lower semicontinuous through closed sublevel sets; a linear map is weak-to-weak continuous exactly when it is norm bounded.

**Reason.** Convexity is essential to the closure theorem, and unbounded linear maps are not weakly continuous.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.07 -- source PDF pp. 24--26: Weak-star dual and closed hyperplanes

**Category:** Proof completion

**Issue.** The source asserted that every weak-star continuous functional is an evaluation and that every weak-star closed hyperplane has evaluation form without proving finite dependence.

**Correction.** A finite-functional-dependence lemma factors a continuous functional through finitely many coordinates; linearity then reduces it to one evaluation. The kernel description gives the hyperplane theorem.

**Reason.** Initial-topology continuity controls only finitely many coordinates locally; this is the key missing step.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.08 -- source PDF pp. 26--27: Banach--Alaoglu theorem

**Category:** Proof repair

**Issue.** The product-space proof did not establish that the embedded dual ball is closed in the compact product.

**Correction.** The dual ball is embedded by evaluations into a product of compact scalar discs; linearity and the norm bound are expressed by closed coordinate equations, so the image is closed and compact.

**Reason.** Tychonoff gives compactness only for the ambient product; closedness of the image is indispensable.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.09 -- source PDF pp. 28--30: Goldstine and Kakutani reflexivity criteria

**Category:** Proof repair

**Issue.** The source’s separation arguments omitted the correct weak-star neighbourhood and the canonical embedding step.

**Correction.** Goldstine is proved by finite-dimensional separation of coordinates; Kakutani identifies reflexivity with weak compactness of the closed unit ball through continuity of the canonical embedding and Goldstine density.

**Reason.** These steps connect weak compactness in `X` with weak-star compactness in `X**`.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.10 -- source PDF p. 30: Eberlein--Smulian theorem

**Category:** Scope and proof honesty

**Issue.** The source presented a short sketch as though it proved the equivalence of weak compactness and weak sequential compactness.

**Correction.** The theorem is stated and its consequences are used, but the note explicitly identifies it as a deep result rather than claiming the source sketch is a complete proof.

**Reason.** The missing argument is substantial and cannot be replaced by metrizability in general.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.11 -- source PDF pp. 30--32: Separability and metrizability of weak/weak-star balls

**Category:** Hypothesis repair

**Issue.** Several metrizability claims lacked the correct separability assumption or confused separability of `X` with separability of `X*`.

**Correction.** The dual ball is weak-star metrizable when `X` is separable; the primal ball is weakly metrizable when `X*` is separable; the converse characterizations are stated with the appropriate spaces and metrics.

**Reason.** The countable family needed to define the metric lives in different spaces in the weak and weak-star settings.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.12 -- source PDF p. 33: Weak-star sequential compactness and Radon--Riesz

**Category:** Proof completion

**Issue.** The source passed from compactness to sequential compactness without metrizability and compressed the uniformly convex argument.

**Correction.** For separable predual spaces, Banach--Alaoglu plus metrizability gives weak-star sequential compactness. The Radon--Riesz proof uses midpoint uniform convexity and lower semicontinuity of the norm.

**Reason.** Compactness is not sequential compactness in an arbitrary topology, and the norm-convergence conclusion needs the quantitative convexity step.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

### C2.13 -- source PDF p. 34: Milman--Pettis reflexivity theorem

**Category:** Complex-case and topology repair

**Issue.** The source used real inequalities in a possibly complex setting and treated weak-star density as sequence density.

**Correction.** The proof uses real parts of dual pairings and the weak-star density supplied by Goldstine, allowing nets when the topology is not metrizable.

**Reason.** Complex separation is formulated with real parts, and density in a general compact space need not be sequential.

**Implemented in:** `chapters/chapter-2-weak-convergence.tex`.

## Chapter 4 -- Lebesgue Spaces

### C4.01 -- source PDF p. 35: Uniform convexity and reflexivity of Lp

**Category:** Hypothesis and inequality repair

**Issue.** The source quoted Clarkson inequalities without separating the ranges `1<p<=2` and `2<=p<infinity`, then jumped directly to reflexivity.

**Correction.** The correct Clarkson inequality is used in each exponent range, uniform convexity is deduced, and Milman--Pettis gives reflexivity.

**Reason.** The two formulas have different exponents and directions; using the wrong one invalidates the modulus estimate.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

### C4.02 -- source PDF pp. 35--37: Duality of Lp and the endpoint L1 dual

**Category:** Missing hypotheses

**Issue.** The conjugate exponent and isometric norm computation were incomplete, and the endpoint theorem was stated without a measure-space qualification.

**Correction.** For `1<p<infinity`, Hölder and the equality case identify `(L^p)*` with `L^{p\prime}` isometrically. For `p=1`, the `L^infinity` representation is stated under the standard sigma-finite/Lebesgue setting used in the notes.

**Reason.** The endpoint representation can depend on the measure space, while the reflexive-range proof requires the correct conjugate exponent.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

### C4.03 -- source PDF pp. 37--38: Nonreflexivity remarks for L1 and L-infinity

**Category:** False unrestricted claim

**Issue.** The source said these spaces are never reflexive.

**Correction.** The remarks now exclude finite-dimensional measure-algebra cases and explain the standard infinite-dimensional setting in which nonreflexivity holds.

**Reason.** Finite atomic measure spaces can make `L^1` and `L^infinity` finite-dimensional and therefore reflexive.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

### C4.04 -- source PDF p. 39: Separability and dense smooth classes

**Category:** Scope repair

**Issue.** The source blurred separability of `L^p` for finite `p`, nonseparability of `L^infinity`, and density of compactly supported functions.

**Correction.** The statements are separated: `L^p` is separable for `p<infinity` under the present Lebesgue hypotheses; `L^infinity` is not; `C_c` and `C_c^infinity` are dense in finite-`p` spaces.

**Reason.** The endpoint behaves differently, and smooth density requires the usual regularity of Lebesgue measure.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

### C4.05 -- source PDF pp. 39--40: Young convolution inequality and mollifier approximation

**Category:** Proof repair

**Issue.** The source omitted the exponent relation and several integrability/limit justifications.

**Correction.** Young’s inequality is stated with `1+1/r=1/p+1/q`; differentiation of convolution is justified; a standard approximate identity is used to prove convergence in `L^p` and uniformly on compact sets where appropriate.

**Reason.** Convolution estimates depend on the exact exponent balance, and derivative/limit interchange needs an integrable dominating bound.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

### C4.06 -- source PDF p. 40: Vanishing weak gradient

**Category:** Missing connectedness qualification

**Issue.** The source concluded that a function with zero weak gradient is globally constant on an arbitrary open set.

**Correction.** The conclusion is stated componentwise, and global constancy is asserted only when the domain is connected.

**Reason.** Different connected components may carry different constants while all weak derivatives still vanish.

**Implemented in:** `chapters/chapter-4-lp-spaces.tex`.

## Chapter 5 -- Hilbert Spaces

### C5.01 -- source PDF pp. 41--42: Orthogonal complements and direct sums

**Category:** Mathematical precision

**Issue.** The source compressed the closure of `M^perp`, the identity `M^{perp perp}=closure(M)`, and the direct-sum theorem.

**Correction.** Each orthogonal complement is shown closed; the double-complement identity is proved; a closed subspace yields the unique decomposition `H=M directsum M^perp`.

**Reason.** Closure is essential unless the original subspace is already closed.

**Implemented in:** `chapters/chapter-5-hilbert-spaces.tex`.

### C5.02 -- source PDF pp. 42--43: Projection theorem and minimizing sequence

**Category:** Proof repair

**Issue.** The minimizing-sequence proof did not fully derive Cauchyness from the parallelogram law or pass to the limit inside the closed convex set.

**Correction.** The midpoint estimate makes the sequence Cauchy; completeness and closedness give the minimizer; strict convexity of the norm gives uniqueness.

**Reason.** These are the precise steps that turn an infimum into an attained unique minimum.

**Implemented in:** `chapters/chapter-5-hilbert-spaces.tex`.

### C5.03 -- source PDF pp. 43--44: Variational characterization and nonexpansiveness

**Category:** Proof completion

**Issue.** The source mixed the convex-set inequality with the subspace orthogonality condition and then asserted a Lipschitz bound without the monotonicity calculation.

**Correction.** Directional perturbations give `Re <x-Px,v-Px> <=0`; for subspaces this becomes orthogonality. Combining the two inequalities for different points proves metric projection is nonexpansive.

**Reason.** The convex and linear cases have different characterizations, and nonexpansiveness is not automatic from existence.

**Implemented in:** `chapters/chapter-5-hilbert-spaces.tex`.

### C5.04 -- source PDF p. 44: Linearity of projections and Riesz representation

**Category:** False generality

**Issue.** The source risked treating projection onto every closed convex set as linear and abbreviated the representation proof.

**Correction.** Linearity is asserted only for orthogonal projection onto a closed linear subspace. Riesz representation is proved by projecting onto the kernel and normalizing the orthogonal vector.

**Reason.** Metric projections onto general convex sets are nonlinear.

**Implemented in:** `chapters/chapter-5-hilbert-spaces.tex`.

### C5.05 -- source PDF pp. 45--46: Orthogonal series, Hilbert sums, and orthonormal bases

**Category:** Proof completion

**Issue.** The source stated convergence and Parseval formulas without proving the Cauchy criterion or completeness of the basis expansion.

**Correction.** Orthogonality gives the norm-square sum and Cauchy criterion; mutually orthogonal projections are summed; Bessel, Parseval, Fourier expansion, and the separable Gram--Schmidt construction are derived.

**Reason.** The coefficient identities alone do not prove that the series converges to the original vector.

**Implemented in:** `chapters/chapter-5-hilbert-spaces.tex`.

## Chapter 6 -- Spectral Theory

### C6.01 -- source PDF pp. 47--48: Resolvent of a closed unbounded operator

**Category:** Definition and boundedness

**Issue.** The source defined the resolvent as though every operator were bounded and did not explain why a bijective shifted operator has a bounded inverse.

**Correction.** For a closed densely defined operator, `lambda` is resolvent precisely when `T-lambda I` is bijective from its domain onto the space and its inverse is bounded; boundedness follows from the closed graph theorem.

**Reason.** Domain information is part of the operator, and algebraic bijectivity alone does not visibly provide a bounded inverse until closedness is used.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.02 -- source PDF p. 48: Resolvent openness, identity, and compactness of the spectrum

**Category:** Sign and proof repair

**Issue.** The source used an inconsistent sign in the resolvent identity and compressed the Neumann-series argument.

**Correction.** With `R(lambda,T)=(T-lambda I)^{-1}`, the identity is written with the corresponding sign; the Neumann series proves openness, and the large-`lambda` expansion plus nonemptiness gives compact spectrum for bounded operators.

**Reason.** Changing from `(lambda I-T)^{-1}` to `(T-lambda I)^{-1}` reverses the standard sign.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.03 -- source PDF pp. 48--50: Polynomial spectral mapping and spectral-radius formula

**Category:** Proof completion

**Issue.** The source factorization did not justify both inclusions, and the radius proof omitted the analytic boundedness contradiction.

**Correction.** Polynomial factorization proves both spectral-mapping inclusions. The spectral-radius formula combines the easy norm bound with a resolvent/Cauchy-estimate argument for the reverse inequality.

**Reason.** One inclusion alone does not give equality, and submultiplicativity by itself gives only an upper bound.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.04 -- source PDF pp. 50--51: Compactness criteria and finite-rank approximation

**Category:** Hypothesis repair

**Issue.** Several statements alternated among compact, precompact, and totally bounded without specifying the ambient completeness, and the closure of finite-rank maps was stated too broadly.

**Correction.** Sequential compactness and total boundedness are related with completeness stated explicitly; finite-rank maps are compact, compact maps form an operator-norm closed subspace when the codomain is Banach, and the identity is compact only in finite dimensions.

**Reason.** A totally bounded set need not be compact in an incomplete space, and operator-norm limits require the codomain limit to exist.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.05 -- source PDF pp. 51--52: Separable range and compact extension from a dense subspace

**Category:** Missing Banach hypotheses

**Issue.** The source extended a compact operator from a dense domain without ensuring limits exist in the codomain.

**Correction.** A bounded map on a dense subspace extends to the completion; compactness is preserved when the domain and codomain are Banach. The range of a compact map is shown separable via compact images of balls.

**Reason.** The extension is defined by limits, so codomain completeness is essential.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.06 -- source PDF p. 52: Schauder theorem

**Category:** Incomplete proof

**Issue.** The source asserted compactness of the adjoint from compactness of the original map without a complete finite-net construction.

**Correction.** A finite net for the compact image is used to map the adjoint unit ball into a totally bounded finite-coordinate set, proving compactness; the converse follows by applying the result twice and the canonical embeddings.

**Reason.** Boundedness of the adjoint family alone is not compactness.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.07 -- source PDF pp. 53--54: Spectrum of a compact operator

**Category:** Proof repair

**Issue.** The source mixed point spectrum and full spectrum and did not justify countability, finite-dimensional eigenspaces, or the unique accumulation point.

**Correction.** For nonzero spectral values, Fredholm theory yields eigenvectors; separated normalized eigenvectors rule out infinite-dimensional eigenspaces and nonzero accumulation; a countable-annulus argument gives countability.

**Reason.** Compactness constrains nonzero spectral values but does not remove zero from the spectrum in infinite dimensions.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.08 -- source PDF pp. 54--55: Closed range, stabilization, and Riesz decomposition

**Category:** Proof completion

**Issue.** The kernel/range chains were manipulated without proving when they stabilize or why the sum is direct.

**Correction.** For nonzero `lambda`, `T-lambda I` has closed range; compactness rules out indefinitely growing kernels or shrinking ranges; stabilization gives `X=Ker(T-lambda I)^n directsum Ran(T-lambda I)^n`.

**Reason.** The decomposition depends on both closedness and eventual stabilization, not merely formal inclusions.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.09 -- source PDF pp. 56--57: Fredholm alternative and solvability conditions

**Category:** Logical repair

**Issue.** The source’s alternatives did not distinguish injectivity from surjectivity and omitted the annihilator condition for an inhomogeneous equation.

**Correction.** For `I-T` with compact `T`, injectivity and surjectivity are equivalent; the homogeneous solution spaces are finite-dimensional; `f` is solvable exactly when it annihilates `Ker(I-T*)`.

**Reason.** The inhomogeneous equation is controlled by the cokernel, represented by the adjoint kernel.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.10 -- source PDF pp. 15, 57: Banach adjoint versus Hilbert adjoint; biorthogonal lemma

**Category:** Notation and scalar convention

**Issue.** The source used the same star notation with incompatible scalar conventions and stated biorthogonal vectors without a proof.

**Correction.** The Banach adjoint is defined by composition, while the Hilbert adjoint uses the stated inner-product convention; finite independent functionals are separated inductively to obtain biorthogonal vectors.

**Reason.** In complex spaces, conjugate linearity changes formulas, and the lemma is needed in the Fredholm dimension argument.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

### C6.11 -- source PDF p. 59: Arzelà--Ascoli and continuous-kernel integral operators

**Category:** Proof completion

**Issue.** The source invoked Ascoli without checking equiboundedness and equicontinuity of the image of the unit ball.

**Correction.** The continuous kernel gives a uniform bound and a common modulus of continuity; Arzelà--Ascoli then yields relative compactness.

**Reason.** Pointwise boundedness alone is not enough for compactness in `C(K)`.

**Implemented in:** `chapters/chapter-6-spectral-theory.tex`.

## Chapter 7 -- Operator Semigroups and Hille--Yosida

### C7.01 -- source PDF pp. 61--63: Generator domain, invariance, differentiation, and closedness

**Category:** Proof completion

**Issue.** The source listed generator properties but left domain density, invariance, and closedness only partially justified.

**Correction.** Averaged orbit vectors approximate arbitrary vectors and lie in the generator domain; semigroup commutation gives invariance and differentiation; an integral identity proves the graph is closed.

**Reason.** These properties are foundational and cannot be inferred from the formal derivative notation alone.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.02 -- source PDF pp. 63--64: Laplace-transform resolvent and notation

**Category:** Convention repair

**Issue.** The chapter’s formula conflicted with the preceding chapter’s `(T-lambda I)^{-1}` convention and obscured the sign in the Laplace integral.

**Correction.** For generators, the standard notation `R(lambda,A)=(lambda I-A)^{-1}` is declared locally; the Bochner integral `int_0^infinity e^{-lambda t}T(t) dt` is shown to be the inverse.

**Reason.** The local convention prevents a hidden sign error in every Hille--Yosida formula.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.03 -- source PDF pp. 64--65: Contraction Hille--Yosida theorem and Yosida approximants

**Category:** Proof repair

**Issue.** The source did not clearly separate necessity from sufficiency or establish the uniform bounds for the approximating generators.

**Correction.** Necessity follows from the Laplace resolvent; sufficiency uses bounded Yosida approximants `A_lambda=lambda A(lambda I-A)^{-1}`, their contraction semigroups, and strong convergence on a dense core.

**Reason.** A formal exponential of an unbounded operator is not defined without the approximation argument.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.04 -- source PDF pp. 66--67: Abstract Cauchy problem, core density, and Euler approximation

**Category:** Proof completion

**Issue.** Uniqueness of the evolution equation, the claim that `D(A^2)` is a core, and the Euler formula were stated with missing estimates.

**Correction.** A resolvent regularization proves uniqueness; `lambda R(lambda,A)x` approximates `x` in the graph norm; the Yosida semigroups yield the Euler limit `(I-tA/n)^{-n}`.

**Reason.** These statements require graph-norm and strong-convergence control, not only formal differentiation.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.05 -- source PDF pp. 68--70: Exponentially bounded semigroups and Hille--Yosida--Phillips

**Category:** Hypothesis and estimate repair

**Issue.** The source gave a first-resolvent estimate where higher powers are required and did not state the growth bound uniformly.

**Correction.** Uniform boundedness on compact time intervals leads to `||T(t)||<=Me^{omega t}`; the Laplace formula gives all power estimates, and the Hille--Yosida--Phillips theorem is stated with the necessary `M/(Re lambda-omega)^n` bound.

**Reason.** For `M>1`, a one-power estimate alone is not the full generation criterion.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.06 -- source PDF pp. 71--72: Translation semigroup and its generator

**Category:** Domain repair

**Issue.** The source identified the generator with differentiation without specifying the function space or the exact differentiability domain.

**Correction.** The translation semigroup is placed on a strongly continuous state space, and its generator is the derivative on the functions whose derivative belongs to that space, with the difference quotient proved.

**Reason.** The same translation formula is not strongly continuous on every possible sup-norm function space.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.07 -- source PDF pp. 72--73: Positive self-adjoint operator example

**Category:** Sign error

**Issue.** The source said a positive self-adjoint operator `A` itself generates a contraction semigroup.

**Correction.** The generator is corrected to `-A`, since the spectrum of `-A` lies in the left half-plane and `e^{-tA}` is contractive.

**Reason.** With generator `A`, positive spectrum would produce exponential growth rather than contraction.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.08 -- source PDF pp. 73--74: Dissipative/accretive operators and Lumer--Phillips

**Category:** Definition and proof repair

**Issue.** The source used a Hilbert-space inner-product test in a general Banach space and did not make the range condition precise.

**Correction.** Dissipativity is formulated through a norming functional from the duality map; Lumer--Phillips states dissipativity plus `Ran(lambda I-A)=X` for some positive `lambda`, with closedness and maximality proved.

**Reason.** A Banach space has no canonical inner product, and dissipativity alone does not guarantee generation.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.09 -- source PDF pp. 74--75: Adjoint dissipativity and invariant cores

**Category:** Missing hypotheses

**Issue.** The source concluded generation from dissipativity of `A` and `A*` without checking density/closedness, and used “core” without the graph norm.

**Correction.** The corollary includes dense definition and closedness; a core is defined by graph-norm density; invariance plus resolvent approximation proves the invariant-core theorem.

**Reason.** The generator theorem is about closed densely defined operators, and ordinary norm density is too weak for a core.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.10 -- source PDF pp. 75--76: Gaussian heat semigroup and generator

**Category:** False state-space claim

**Issue.** The source placed the Gaussian heat semigroup on all of `C_b(R^d)`, where strong continuity at zero fails for non-uniformly-continuous functions.

**Correction.** The semigroup is stated on `C_0(R^d)` (and noted to work on `BUC`), and the generator is the closure of the Laplacian on a standard smooth core.

**Reason.** The sup-norm approximate identity converges only for uniformly continuous functions, not arbitrary bounded continuous ones.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

### C7.11 -- source PDF p. 76: Poisson semigroup generator

**Category:** Sign and operator identification

**Issue.** The source’s Fourier calculation blurred the sign and the square of the generator.

**Correction.** The generator is identified as `-(-Delta)^{1/2}`, so its square is `-Delta` on the appropriate domain.

**Reason.** The Fourier multiplier is `-|xi|`; omitting the minus sign changes contraction into growth.

**Implemented in:** `chapters/chapter-7-semigroups.tex`.

## Chapter 8 -- Sobolev Spaces

### C8.01 -- source PDF pp. 77--78: Banach structure and the one-dimensional fundamental theorem

**Category:** Proof completion

**Issue.** The source asserted completeness and the absolutely continuous representation without fully identifying the weak derivative.

**Correction.** The graph map into `L^p x L^p` proves completeness; the weak derivative integrates to an absolutely continuous representative satisfying the fundamental theorem.

**Reason.** A distributional derivative is an equivalence class until a representative is constructed.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.02 -- source PDF pp. 78--79: Zero weak derivative

**Category:** Scope and proof repair

**Issue.** The source concluded constancy from a test-function calculation without addressing the interval/component structure.

**Correction.** A zero weak derivative yields an almost-everywhere constant function on each interval component, using the absolutely continuous representative.

**Reason.** Weak derivatives are local, so disconnected domains permit different constants.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.03 -- source PDF pp. 79, 89: Endpoint dual characterization at p=1

**Category:** False endpoint theorem

**Issue.** The source used an `L^infinity` test-function bound to characterize `W^{1,1}`.

**Correction.** The Sobolev characterization is restricted to `1<p<infinity` (with the separate Lipschitz endpoint); at `p=1`, the analogous bound characterizes a finite Radon-measure derivative, namely `BV`, not necessarily `W^{1,1}`.

**Reason.** The dual of `L^infinity` is larger than `L^1`, so the derivative need not have an `L^1` density.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.04 -- source PDF p. 80: Lipschitz and difference-quotient characterizations

**Category:** Endpoint repair

**Issue.** The source treated all exponents uniformly and blurred `W^{1,infinity}` with finite-`p` difference-quotient compactness.

**Correction.** `W^{1,infinity}` is identified with Lipschitz representatives. The difference-quotient criterion is stated for `1<p<infinity`; the `p=1` endpoint is again identified with `BV` unless uniform integrability is added.

**Reason.** The reflexive compactness argument used for finite `p>1` fails at `p=1`.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.05 -- source PDF pp. 81--83: Extension, mollification, and smooth density

**Category:** Proof repair

**Issue.** The source gave the constructions informally and risked claiming compactly supported smooth density on every open set.

**Correction.** A bounded reflection extension is constructed; convolution commutes with weak derivatives; smooth functions are dense in `W^{1,p}` by local mollification, while `C_c^infinity(Omega)` is reserved for `W_0^{1,p}` or the full space `R^N`.

**Reason.** Boundary traces obstruct compactly supported approximation of arbitrary Sobolev functions.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.06 -- source PDF pp. 83--84: One-dimensional embeddings and compactness

**Category:** Scope repair

**Issue.** The source combined continuous and compact embeddings without separating bounded from unbounded intervals or the exponent endpoints.

**Correction.** On a bounded interval, `W^{1,p}` embeds into continuous functions for `p>1`, and the stated embeddings are compact in the indicated ranges; on unbounded intervals, decay is proved but the embedding is not compact.

**Reason.** Translations on an unbounded interval destroy compactness even when the embedding remains continuous.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.07 -- source PDF p. 85: Product, chain, and integration-by-parts rules

**Category:** Missing hypotheses

**Issue.** The source wrote formal differentiation rules without the boundedness or regularity conditions needed for the products and compositions to remain Sobolev.

**Correction.** The product rule assumes bounded factors as needed; the chain rule assumes a bounded derivative; integration by parts is derived through smooth approximation.

**Reason.** Formal derivatives may exist algebraically while the resulting terms fail to lie in `L^p`.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.08 -- source PDF pp. 86--87: Higher-order spaces and trace-zero characterization

**Category:** Definition repair

**Issue.** The source conflated the closure definition of `W_0^{1,p}` with a trace condition without specifying a bounded interval and continuous representative.

**Correction.** `W^{m,p}` and `W_0^{1,p}` are defined separately; on a bounded interval the trace theorem identifies `W_0^{1,p}` with functions whose continuous representative vanishes at both endpoints.

**Reason.** Trace values are not part of the abstract closure definition on arbitrary domains.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.09 -- source PDF p. 87: Poincare inequality and negative Sobolev representation

**Category:** Missing zero-trace hypothesis

**Issue.** The source stated a Poincare estimate for arbitrary `W^{1,p}` functions, which constants contradict.

**Correction.** The estimate is stated on `W_0^{1,p}` for finite `p`, with a separate zero-trace `W^{1,infinity}` observation; the dual `W^{-1,p\prime}` representation is written with both zeroth- and first-order coefficient functions.

**Reason.** Subtracting or fixing the constant mode is necessary for Poincare, and the dual acts on both the function and its derivative.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.10 -- source PDF pp. 88--90: Multivariable weak derivatives and Meyers--Serrin

**Category:** Scope repair

**Issue.** The source suggested that `C_c^infinity(Omega)` is dense in all of `W^{1,p}(Omega)` and abbreviated the localization argument.

**Correction.** Weak derivatives and the graph norm are defined componentwise; an exhaustion and partition of unity prove density of `C^infinity(Omega) cap W^{1,p}(Omega)`, with compact support only on `R^N` or in `W_0^{1,p}`.

**Reason.** Functions with nonzero trace cannot be approximated in `W^{1,p}` by compactly supported smooth functions.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.11 -- source PDF pp. 89--90: Distribution/translation criteria and multivariable chain rules

**Category:** Endpoint and regularity repair

**Issue.** The source used the same criterion at `p=1` and stated coordinate-change rules without controlling the map and its inverse.

**Correction.** The equivalence is restricted to `1<p<infinity`, with `p=1` identified as `BV`; products, compositions, and changes of variables include bounded-derivative and bi-Lipschitz hypotheses.

**Reason.** Weak compactness and change-of-variable estimates require these exponent and regularity assumptions.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

### C8.12 -- source PDF p. 90: Higher-order norm and terminal source marker

**Category:** Notation and layout

**Issue.** The source listed several equivalent norms without a stable convention, and the final page marker generated a blank output page.

**Correction.** A concrete sum norm is chosen, equivalence of finite-dimensional combinations is noted, `H^m=W^{m,2}` is identified, and the duplicate marker is removed.

**Reason.** A fixed norm improves compilation and cross-reference consistency; the marker change affects only layout, not content.

**Implemented in:** `chapters/chapter-8-sobolev-spaces.tex`.

## Chapter 9 -- Calculus of Variations and Distributions

### C9.01 -- source PDF p. 91: Coercive quadratic minimization hypotheses and Hilbert reduction

**Category:** Missing hypotheses

**Issue.** The source called the bilinear form coercive but did not separately state boundedness, symmetry, or the real-space setting needed for a quadratic functional.

**Correction.** The theorem assumes a continuous symmetric coercive form on a real Banach space; the induced norm is shown equivalent and complete, turning the space into a Hilbert space.

**Reason.** Coercivity alone does not make the quadratic expression a continuous inner-product norm.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.02 -- source PDF pp. 91--92: Projection formulation, Lipschitz dependence, and variational inequality

**Category:** Proof completion

**Issue.** The source jumped from completing the square to the Euler condition without treating a convex constraint or continuity of the solution map.

**Correction.** The minimizer is the metric projection in the induced Hilbert norm; nonexpansiveness gives Lipschitz dependence; one-sided variations yield the variational inequality and, for subspaces, the variational equation.

**Reason.** A constrained minimizer satisfies an inequality, not an equality in every direction.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.03 -- source PDF p. 92: Lax--Milgram lemma

**Category:** False symmetry restriction

**Issue.** The source tied Lax--Milgram to the preceding symmetric quadratic form.

**Correction.** The theorem is stated for any continuous coercive bilinear/sesquilinear form, not necessarily symmetric, and the associated operator is shown bounded below with closed range and trivial adjoint kernel.

**Reason.** Lax--Milgram is strictly more general than minimization of a symmetric quadratic functional.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.04 -- source PDF p. 92: Stampacchia variational inequality

**Category:** Proof repair

**Issue.** The source stated existence and uniqueness without a complete contraction construction.

**Correction.** A small-step projected fixed-point map is shown contractive using coercivity and boundedness; its fixed point is equivalent to the variational inequality, and the same estimate gives Lipschitz dependence.

**Reason.** Closed convex constraints remove linearity, so a projection/fixed-point argument is required.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.05 -- source PDF pp. 94--95: Test-function topology and weak derivatives

**Category:** Topological precision

**Issue.** The source described convergence in `D(Omega)` as though one norm or one compact set governed the whole space.

**Correction.** The LF topology is stated: eventually common compact support plus uniform convergence of every derivative; weak derivatives are defined by integration by parts against all test functions.

**Reason.** `D(Omega)` is not normable or metrizable by a single global seminorm family in the naive way suggested.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.06 -- source PDF pp. 94--95: Distribution continuity, convergence, and regular distributions

**Category:** Definition repair

**Issue.** The source gave a global order estimate without localizing to compact supports and did not clearly distinguish pointwise distributional convergence from test-function topology.

**Correction.** Continuity is characterized on each compact set by finitely many derivative seminorms; distributional convergence means convergence on every test function; locally integrable functions define regular distributions.

**Reason.** Distribution order and constants may depend on the compact support under consideration.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

### C9.07 -- source PDF p. 95: Dirac delta and distributional derivative sign

**Category:** Proof and sign repair

**Issue.** The source asserted that delta is not regular and identified derivatives without a complete contradiction or the multi-index sign.

**Correction.** Shrinking smooth bump functions contradict absolute continuity of a hypothetical `L^1_loc` density for delta; `D^alpha T(phi)=(-1)^{|alpha|}T(D^alpha phi)` is stated and shown to agree with weak and classical derivatives.

**Reason.** The sign is forced by repeated integration by parts, and point evaluation cannot be represented by an absolutely continuous measure.

**Implemented in:** `chapters/chapter-9-calculus-of-variations.tex`.

## Counts

- Global/editorial/compilation entries: 8
- Chapter-specific substantive entries: 77
- Total detailed entries: 85
