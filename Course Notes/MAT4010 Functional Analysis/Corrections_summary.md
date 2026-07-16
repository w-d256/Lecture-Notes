# MAT4010 handwritten-note review: correction ledger

This ledger records every substantive mathematical, logical, notational, grammatical, or compilation-related repair made in the corrected LaTeX manuscript.  The rendered source pages were authoritative, and the source PDF and canonical preamble are preserved byte-for-byte.

## Global and compilation corrections

### G.01 -- source PDF pp. 1--187: Rendered pages treated as the mathematical source

**Category:** Source integrity

**Issue.** The PDF text layer garbles quantifiers, subscripts, arrows, interval endpoints, and many handwritten words.

**Correction.** Every statement and formula was reconstructed from the rendered page images; extracted text was used only to locate material.

**Reason.** Literal use of the extracted text would create false symbols and invalid mathematics.

**Implemented in:** `project-wide`.

### G.02 -- source PDF pp. 1--187: Exact preservation of supplied inputs

**Category:** Source integrity

**Issue.** The review required corrections without silently changing the original manuscript or the reusable preamble.

**Correction.** The source PDF was copied byte-for-byte to source/original-notes.pdf.  The canonical preamble was copied byte-for-byte to preamble/notes-preamble-original.sty and notes-preamble.sty.

**Reason.** This preserves an auditable baseline and keeps source preservation separate from editorial repair.

**Implemented in:** `source/original-notes.pdf; preamble/notes-preamble-original.sty; notes-preamble.sty`.

### G.03 -- source PDF pp. 1--187: Complete page inventory

**Category:** Editorial structure

**Issue.** Decorative, blank, and continuation pages could be mistaken for missing content.

**Correction.** The page ledger accounts for all 187 pages.  Page 1 is a decorative cover; pages 136--137 and 180 are blank grid pages; page 173 is a near-blank continuation page containing only a proof marker.

**Reason.** A complete ledger prevents accidental omission or invented content.

**Implemented in:** `page-ledger.csv`.

### G.04 -- source PDF pp. 2--187: Screenshots retypeset and non-content omitted

**Category:** Transcription

**Issue.** Many definitions and theorem statements appear as embedded textbook screenshots on grid paper.

**Correction.** Mathematical statements were retypeset as editable LaTeX; the grid background and app-interface decoration were omitted.

**Reason.** The result is searchable, style-consistent, accessible, and independent of raster screenshots.

**Implemented in:** `chapters/*.tex`.

### G.05 -- source PDF pp. 1--187: Source order, chapter structure, and traceability

**Category:** Editorial structure

**Issue.** Automatic restructuring could lose the visible five-section organization or obscure the origin of a corrected statement.

**Correction.** The five visible sections became five chapters, the source order was retained, and each block carries a source-page marker.

**Reason.** This preserves the pedagogical sequence while making every transcription auditable.

**Implemented in:** `notes.tex; chapters/*.tex`.

### G.06 -- source PDF pp. 2--187: Notation and scalar conventions normalized

**Category:** Notation

**Issue.** The handwriting alternates among ambiguous symbols for kernels, ranges, closures, quotients, dual pairings, weak convergence, adjoints, and complex inner products.

**Correction.** Standard LaTeX notation was used consistently; domains and codomains were stated; the Hilbert-space convention is linearity in the first variable; Banach adjoints were kept distinct from Hilbert adjoints.

**Reason.** Several identities change signs or conjugates when these conventions are mixed.

**Implemented in:** `notes.tex; chapters/*.tex`.

### G.07 -- source PDF pp. 2--187: Grammar and proof prose repaired

**Category:** Grammar and logic

**Issue.** The source contains sentence fragments, misspellings, missing articles, and compressed transitions such as "similarly" or "contradiction" without the intervening argument.

**Correction.** Spelling, punctuation, capitalization, singular/plural agreement, theorem names, and proof transitions were normalized; omitted nontrivial implications were written out.

**Reason.** A mathematically checkable proof needs the logical bridge, not only its last line.

**Implemented in:** `chapters/*.tex`.

### G.08 -- source PDF pp. project-wide: Compilation-safe source with unchanged canonical preamble

**Category:** Compilation

**Issue.** A literal transcription would contain Unicode lookalikes, malformed delimiters, undefined ad hoc notation, and incompatible theorem numbering.

**Correction.** All symbols use standard LaTeX commands; manuscript-specific macros and unnumbered source-labelled theorem environments live in notes.tex; the supplied preamble is unchanged, with only a local pgfplots compatibility setting in the master.

**Reason.** This avoids compilation failures, duplicate counters, missing glyphs, and silent changes to the reusable preamble.

**Implemented in:** `notes.tex; notes-preamble.sty; chapters/*.tex`.

## Chapter 1 -- Metric Spaces

### C1.01 -- source PDF pp. 2: Completion of a discrete metric space

**Category:** Incomplete proof

**Issue.** The source answered only that the completion is X itself.

**Correction.** The proof now observes that a Cauchy sequence in the discrete metric is eventually constant, so every Cauchy sequence already converges in X.

**Reason.** The conclusion follows from completeness, not merely from the name of the space.

**Implemented in:** `chapters/chapter-1-metric-spaces.tex`.

## Chapter 2 -- Normed Spaces and Banach Spaces

### C2.01 -- source PDF pp. 3--4: Hamel-basis existence and cardinality

**Category:** Proof repair

**Issue.** The exchange argument was compressed and the infinite-cardinality comparison used an informal enumeration.

**Correction.** Zorn's lemma gives a basis containing a prescribed independent family; finite supports and Cantor--Bernstein give equality of the cardinalities of two Hamel bases.

**Reason.** The cardinality claim requires injections in both directions and a valid treatment of finite supports.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.02 -- source PDF pp. 4: Additive functions on the real line

**Category:** Scalar-field and cardinality correction

**Issue.** The source treated solutions of f(x+y)=f(x)+f(y) informally as real-linear maps and did not justify the cardinality.

**Correction.** They are identified as Q-linear functionals on R viewed as a Q-vector space; arbitrary values on a Hamel basis determine them, giving cardinality 2^c.

**Reason.** Additivity gives Q-linearity, not R-linearity, unless continuity or another regularity condition is added.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.03 -- source PDF pp. 5--6: Equivalent norms and equality of topologies

**Category:** Proof repair

**Issue.** The unit-ball argument mixed the two norms and omitted the scaling step needed away from the unit sphere.

**Correction.** Both implications are proved using neighbourhoods of zero, inclusions of balls, and homogeneity to obtain constants c,C>0.

**Reason.** Topological equivalence is a local statement at zero; homogeneity converts it into global two-sided norm estimates.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.04 -- source PDF pp. 6: Separable spaces and finite-dimensional exhaustion

**Category:** Construction repair

**Issue.** The selected indices and dimensions were not well defined when dense vectors were linearly dependent.

**Correction.** A linearly independent subsequence is extracted from a countable dense set and X_n is defined as its first n spans; the union is dense, with dim X_n=n.

**Reason.** Repeated or dependent dense vectors cannot be used to assert exact dimension.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.05 -- source PDF pp. 7--8: Distance to compact sets versus nearest-point selection

**Category:** False continuity claim

**Issue.** The source tried to prove continuity of an arbitrarily chosen nearest-point map.

**Correction.** The distance function d_K(x)=inf_{z in K}||x-z|| is proved 1-Lipschitz and the infimum is attained for compact K; a counterexample shows a nearest-point selection need not be continuous.

**Reason.** Continuity of the scalar distance function does not imply continuity or uniqueness of an argmin.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.06 -- source PDF pp. 9--10: Supremum norms and uniform limits

**Category:** Proof completion

**Issue.** The norm axioms and continuity of a uniform limit were dismissed or argued only pointwise.

**Correction.** The supremum norm is justified using compactness or boundedness as appropriate, and the epsilon/3 proof of uniform-limit continuity is supplied.

**Reason.** Pointwise convergence alone does not preserve continuity.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.07 -- source PDF pp. 13--14: Closed subspaces, isomorphic images, and closed range

**Category:** Missing hypotheses

**Issue.** The source moved between completeness, closedness, and inverse estimates without naming the induced spaces or norms.

**Correction.** Closed subspaces of Banach spaces are characterized correctly; a bounded bijection with bounded inverse transfers completeness; a lower bound ||Ax||>=c||x|| gives injectivity and closed range when the domain is Banach.

**Reason.** Closedness of the image follows by pulling a Cauchy sequence back through the lower bound, which needs completeness of the domain.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.08 -- source PDF pp. 15: Neumann series and openness of the invertible group

**Category:** Proof completion

**Issue.** The source cited numerical analysis and used inversion estimates without deriving them.

**Correction.** The geometric series sum (I-A)^{-1}=sum A^n is proved for ||A||<1, then factored around an invertible operator to obtain the perturbation estimate and continuity of inversion.

**Reason.** Surjectivity and the inverse norm bound come from convergence of the operator series, not from injectivity alone.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.09 -- source PDF pp. 16: Schauder separability and power-small operators

**Category:** Proof repair

**Issue.** The rational-span density estimate was incomplete, and the proof for I-A used a power series without controlling convergence when only ||A^p||<1.

**Correction.** Rational finite combinations of a Schauder basis are shown dense; for ||A^p||<1, I-A is factored using I-A^p and a finite geometric sum.

**Reason.** The ordinary Neumann series need not converge from ||A^p||<1 unless the factorization is used.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.10 -- source PDF pp. 17: Absolute convergence characterizes Banach spaces

**Category:** Proof completion

**Issue.** The converse from convergent absolutely summable series to completeness was compressed into an unjustified subsequence statement.

**Correction.** A Cauchy sequence is thinned so successive differences have summable norms; the resulting telescoping series converges and the full Cauchy sequence has the same limit.

**Reason.** Convergence of one arbitrary subsequence does not by itself imply convergence of the original sequence without the Cauchy property.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.11 -- source PDF pp. 18: Seminorm quotient

**Category:** Well-definedness and positivity

**Issue.** The source asserted a quotient norm without checking independence of representatives.

**Correction.** The null space N={x:p(x)=0} is shown to be a subspace, |p(x)-p(y)|<=p(x-y) gives representative independence, and positive definiteness is proved on X/N.

**Reason.** A formula on cosets is not a norm until these points are verified.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.12 -- source PDF pp. 19--21: Finite-dimensional structure and inequivalent norms

**Category:** Proof and example repair

**Issue.** The lower bound for linear combinations, completeness, and norm equivalence were compressed; the proposed infinite-dimensional counterexample did not give a valid pair of norms on all vectors.

**Correction.** Compactness of the coefficient sphere yields the lower bound; coefficient convergence proves completeness; all finite-dimensional norms are compared to an l1 coordinate norm; a weighted Hamel-coordinate norm gives genuinely inequivalent norms in infinite dimension.

**Reason.** The finite-dimensional conclusions depend on compactness, while an infinite-dimensional counterexample must define finite values on every vector.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.13 -- source PDF pp. 22: Closed and bounded is not compact in infinite dimension

**Category:** False example

**Issue.** The source described the standard basis {e_n} in l2 as compact while simultaneously noting that it has no convergent subsequence.

**Correction.** The set is stated correctly as closed and bounded but not compact, since ||e_n-e_m||=sqrt(2) for n!=m.

**Reason.** Sequential compactness would require a convergent subsequence.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.14 -- source PDF pp. 23--24: Riesz lemma and compact unit balls

**Category:** Endpoint and proof correction

**Issue.** The source suggested the constant 1 could always replace a number theta<1 and used an imprecise inductive contradiction.

**Correction.** Riesz's lemma is stated with 0<theta<1; the endpoint is discussed separately and shown unavailable in general.  The compact-unit-ball theorem uses a separated sequence produced by the lemma.

**Reason.** Because 0 lies in the subspace, distances from a unit vector are at most 1, so a strict bound greater than 1 is impossible.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.15 -- source PDF pp. 25: Completeness of C(K;Y) and B(X;Y)

**Category:** Proof completion

**Issue.** The pointwise limit of a uniformly Cauchy sequence was introduced before continuity and uniform convergence were justified.

**Correction.** Pointwise limits are defined using completeness of Y, the Cauchy estimate is passed to the limit to obtain uniform convergence, and the uniform-limit theorem gives continuity.

**Reason.** Pointwise completeness alone does not produce a limit in the supremum-norm function space.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.16 -- source PDF pp. 26: Best approximation in finite-dimensional subspaces

**Category:** Example and uniqueness correction

**Issue.** The source invoked compactness of the whole ambient space and used an incorrect l1 counterexample.

**Correction.** A minimizing sequence is restricted to a bounded closed subset of the finite-dimensional subspace; strict convexity gives uniqueness.  In l1^2, x=(1,0) and Y=span{(1,1)} have all t in [0,1] as minimizers.

**Reason.** Only the finite-dimensional approximating set is compact, and the counterexample must exhibit two genuine minimizers.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.17 -- source PDF pp. 27: Compact subsets have empty interior in infinite dimension

**Category:** Proof repair

**Issue.** The rescaling argument around an interior ball did not clearly produce a compact closed unit ball.

**Correction.** An affine homeomorphism carries a closed ball inside the compact set to the closed unit ball; this contradicts the finite-dimensional characterization.

**Reason.** Compactness is preserved under continuous affine images, which is the needed bridge.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.18 -- source PDF pp. 29--33: Bounded linear maps and operator spaces

**Category:** Proof and notation repair

**Issue.** Several proofs mixed injectivity, lower bounds, operator norms, finite-dimensional boundedness, and continuity; the c0 functional norm argument ignored nonattainment.

**Correction.** The lower-bound criterion, exact c0 functional norm, operator-norm axioms, completeness of B(V,W), finite-dimensional boundedness, discontinuous Hamel functional, and continuity/boundedness equivalence are each proved with the necessary estimates.

**Reason.** These statements are related but logically distinct; nonattainment of a supremum cannot be replaced by a maximizing vector.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.19 -- source PDF pp. 34--35: Definition and criteria for compact operators

**Category:** Circular definition and proof repair

**Issue.** The source defined a compact operator as already bounded and used compactness/relative compactness interchangeably.

**Correction.** Compactness is defined for a linear map by relative compactness of bounded images, and boundedness is then proved.  The sequential criterion and finite-rank implications are established carefully.

**Reason.** Boundedness should be a consequence for linear compact maps, not an assumption hidden in the definition.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.20 -- source PDF pp. 36: Unbounded inverse counterexample

**Category:** Codomain correction

**Issue.** The source referred to an inverse without making the diagonal map surjective onto the stated codomain.

**Correction.** The map T:l1->Ran(T), T(x_n)=(x_n/n), is used with the inherited l1 norm; it is a bounded bijection onto its range, while T^{-1} is unbounded.

**Reason.** An inverse exists only after the codomain is restricted to the actual range.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.21 -- source PDF pp. 37--38: Extension from a dense subspace and composition norms

**Category:** Proof completion

**Issue.** The extension proof assumed limits were well defined and the norm identity was immediate.

**Correction.** Cauchyness, independence of approximating sequences, linearity, boundedness, uniqueness, and equality of norms are proved; the composition estimate is derived directly.

**Reason.** Completeness of the codomain is essential for the defining limits.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.22 -- source PDF pp. 39--42: Subspaces, quotient norms, and quotient completeness

**Category:** Proof repair

**Issue.** Connectedness and closure arguments were abbreviated, and the quotient completeness proof used representatives without a summable-error construction.

**Correction.** Open subspaces are shown to be the whole space; closures of subspaces are subspaces; the quotient seminorm is a norm exactly for closed U; completeness is proved by choosing near-minimal representatives and corrections with summable errors.

**Reason.** Arbitrary representatives need not form a Cauchy sequence even when their cosets do.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

### C2.23 -- source PDF pp. 43--45: Dual spaces and codimension-one kernels

**Category:** Definition and proof cleanup

**Issue.** The source blurred algebraic and continuous duals and compressed the codimension-one decomposition.

**Correction.** The two dual notions are separated, the continuous dual is shown Banach, and a nonzero functional gives the unique decomposition X=span{x0}\oplus Ker f; proportionality of functionals with the same kernel is proved.

**Reason.** Continuity changes the space under discussion, while the codimension-one statement is algebraic.

**Implemented in:** `chapters/chapter-2-normed-banach-spaces.tex`.

## Chapter 3 -- Fundamental Theorems for Banach Spaces

### C3.01 -- source PDF pp. 46--47: Closed kernels of linear functionals

**Category:** False equivalence

**Issue.** The source treated a proper kernel as equivalent to boundedness.

**Correction.** For a nonzero linear functional, boundedness, continuity, and closedness of the kernel are proved equivalent; properness is only the algebraic consequence of nonzeroness.

**Reason.** Every nonzero functional has a proper kernel, including discontinuous ones.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.02 -- source PDF pp. 47--48: Discontinuous functionals on infinite-dimensional spaces

**Category:** Construction repair

**Issue.** The source assigned values on an ill-specified subset of a basis and did not prove unboundedness.

**Correction.** Choose distinct normalized Hamel basis vectors e_n and define phi(e_n)=n, extending linearly to the whole Hamel basis; then ||e_n||=1 but |phi(e_n)|=n.

**Reason.** A linear functional is discontinuous precisely when it is unbounded on the unit ball.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.03 -- source PDF pp. 49: One-dimensional Hahn--Banach extension

**Category:** Inequality repair

**Issue.** The admissible constant was derived with inconsistent signs and variables.

**Correction.** The exact interval sup_m(f(m)-p(m-x0)) <= alpha <= inf_m(p(m+x0)-f(m)) is derived and shown nonempty by sublinearity.

**Reason.** The Zorn extension step works only after both signs and endpoint order are correct.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.04 -- source PDF pp. 50--56: Real and complex Hahn--Banach theorems

**Category:** Proof completion and scalar correction

**Issue.** The Zorn proof omitted compatibility on chains, and the complex case mixed real and complex linearity.

**Correction.** Chain unions are verified, maximality is contradicted using the one-dimensional interval, and the complex extension is reconstructed from a real extension by F(x)=U(x)-iU(ix), with a phase-rotation norm argument.

**Reason.** Complex linearity and equality of norms do not follow from a real extension without the reconstruction formula.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.05 -- source PDF pp. 56--57: Norm-preserving extensions and norming functionals

**Category:** Proof completion

**Issue.** The source used a norming functional and the dual norm formula before constructing them.

**Correction.** Hahn--Banach extends the functional alpha x -> alpha||x|| on span{x}; this gives ||f||=1, f(x)=||x|| and hence ||x||=sup_{||f||<=1}|f(x)|.

**Reason.** The normalization and the reverse inequality both require an explicit construction.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.06 -- source PDF pp. 58--59: Taylor--Foguel unique-extension criterion

**Category:** Logical repair

**Issue.** The converse direction in the source used an unsupported affine-combination argument.

**Correction.** The theorem is stated with the required global unique norm-preserving extension property and proved via the common-kernel quotient and distance formula; strict convexity of X* gives the forward direction by averaging.

**Reason.** A local one-line averaging argument proves only one direction unless the global hypothesis is made precise.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.07 -- source PDF pp. 60: Separation from a closed subspace

**Category:** Proof repair

**Issue.** The source attempted to define a functional on a Hamel enlargement without establishing the distance estimate.

**Correction.** For x0 not in Y, the functional on Y+span{x0} taking y+alpha x0 to alpha d(x0,Y) is shown bounded with norm one and then extended by Hahn--Banach.

**Reason.** Closedness is needed to make the distance positive and the functional bounded.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.08 -- source PDF pp. 61--62: Separable dual implies separable space

**Category:** Proof completion

**Issue.** The source normalized a dense sequence informally and left the contradiction incomplete.

**Correction.** A dense sequence in the dual unit sphere is paired with almost norming unit vectors; if their closed span were proper, a norm-one annihilator would contradict dual density.

**Reason.** The selected vectors must be tied quantitatively to the approximating functionals.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.09 -- source PDF pp. 63--65: Minkowski functionals and geometric separation

**Category:** Missing hypotheses and proof repair

**Issue.** The gauge was used without clearly ensuring absorbency or distinguishing strict from non-strict sublevel sets.

**Correction.** For an open convex absorbing set containing zero, p_C is proved sublinear and C={x:p_C(x)<1}; Hahn--Banach then separates a point and, by translating, two disjoint open convex sets.

**Reason.** Without absorbency the gauge may be infinite, and openness requires a strict sublevel set.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.10 -- source PDF pp. 65: Strict separation of closed and compact convex sets

**Category:** Hypothesis and gap correction

**Issue.** The source did not identify which set needed compactness or justify a positive separation margin.

**Correction.** For closed convex A and compact convex K with empty intersection, A-K is closed away from zero; a small open ball is separated from A-K to obtain a uniform positive gap.

**Reason.** Weak separation is insufficient for the stated strict inequalities.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.11 -- source PDF pp. 66: Larger-norm extensions over strict closed subspaces

**Category:** Proof repair

**Issue.** The source varied a coefficient without proving that some choice increases the norm.

**Correction.** A point outside the subspace is used to define a family of algebraic extensions; a uniform bound for all coefficients would be contradicted by sending the coefficient to infinity, so one extension has larger norm and is then extended to X.

**Reason.** The conclusion is existential and needs a quantitative contradiction.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.12 -- source PDF pp. 67: Continuity of sublinear functionals

**Category:** Proof completion

**Issue.** Only one side of the difference estimate was written.

**Correction.** Subadditivity gives p(x)-p(y)<=p(x-y) and p(y)-p(x)<=p(y-x); continuity at zero then implies continuity everywhere.

**Reason.** Both inequalities are needed to control the absolute difference.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.13 -- source PDF pp. 68--69: Kernel exercises and separation of an open ball

**Category:** Proof and hypothesis repair

**Issue.** The source compressed the kernel-subspace dichotomy, the uniqueness criterion in the extension step, and used an unjustified separation theorem for a ball.

**Correction.** The algebraic decomposition is written explicitly; uniqueness is tied to equality of the extension interval endpoints; for 0 not in B(f0,r), a norming functional satisfies Re phi(f)>=||f0||-|phi(f-f0)|>||f0||-r>0.

**Reason.** The direct norming-functional proof supplies the claimed strict positivity without invoking a theorem under mismatched hypotheses.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.14 -- source PDF pp. 70--71: Supporting functionals and hyperplanes

**Category:** Proof completion

**Issue.** The negative-scalar case in the one-dimensional domination argument and the hyperplane converse were incomplete.

**Correction.** Sublinearity is used to show alpha p(x0)<=p(alpha x0) for all real alpha; Hahn--Banach supplies a support functional.  Every codimension-one subspace is then represented as the kernel of a nonzero functional.

**Reason.** The sign change is essential for real linearity, and the hyperplane statement needs a well-defined quotient coordinate.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.15 -- source PDF pp. 72: Riesz--Stieltjes representation

**Category:** Normalization and formulation

**Issue.** The shorthand C([a,b])*=BV([a,b]) ignored that adding a constant to the integrator does not change the functional.

**Correction.** The theorem is stated as representation by a normalized bounded-variation function (or equivalently a finite signed/complex measure), with total variation equal to the operator norm.

**Reason.** Without normalization the representing BV function is not unique.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.16 -- source PDF pp. 73--77: Adjoints, annihilators, and reflexivity

**Category:** Closure and convention repair

**Issue.** The source interchanged ranges with closures, mixed annihilators in primal and dual spaces, and abbreviated the canonical-embedding argument.

**Correction.** The Banach adjoint norm equality is proved; (Ran T)^perp=Ker T*, closure(Ran T)=preann(Ker T*), and weak-* closure formulas are stated correctly; the canonical embedding is shown isometric and reflexivity implications are separated.

**Reason.** For a general bounded operator, Ran T need not be closed, and primal/dual annihilators live in different spaces.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.17 -- source PDF pp. 78--82: Baire, Cantor intersections, and countable Hamel bases

**Category:** False statements and proof repair

**Issue.** Nowhere-dense/dense formulations were conflated, open balls were nested without retaining their limit, and the no-countable-basis proof omitted closedness of finite-dimensional spans.

**Correction.** Baire is proved with nested closed balls; Cantor's theorem uses closed sets with diameters tending to zero; the closed-set form is derived; finite-dimensional spans are closed and cannot all have interior unless one equals X; completeness is characterized by the intersection theorem.

**Reason.** Closedness and diameter control are what keep the limiting point in every set.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.18 -- source PDF pp. 83--84: Continuous nowhere differentiable functions

**Category:** Baire-set proof repair

**Issue.** The source sets were not clearly closed and the empty-interior construction lacked endpoint and slope control.

**Correction.** Closed sets F_n of functions with a bounded local difference quotient are defined; uniform convergence and compactness prove closedness; polynomial approximation followed by a close piecewise-linear perturbation with steep slopes proves empty interior.

**Reason.** Baire applies only after both closedness and nowhere density are established.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.19 -- source PDF pp. 85--88: Uniform boundedness, pointwise limits, and polynomial incompleteness

**Category:** Proof and example repair

**Issue.** The source UBP estimate omitted the symmetric x0+h and x0-h argument, and the polynomial example used coefficient functionals that are not continuous in the stated supremum norm.

**Correction.** The uniform boundedness principle is proved with a Baire ball and subtraction; Banach--Steinhaus follows; incompleteness of polynomials is shown by Taylor polynomials of e^x converging uniformly to a nonpolynomial; the two UBP applications are then justified.

**Reason.** A contradiction to UBP requires a family of genuinely bounded functionals on the full normed space.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.20 -- source PDF pp. 89--90: Pólya theorem for quadrature formulas

**Category:** Missing hypothesis and proof repair

**Issue.** The norm identity ||L_n||=sum|w_j^{(n)}| was used without ensuring a continuous function could realize all signs at the nodes.

**Correction.** The nodes are required to be distinct; a piecewise-linear sign interpolant attains the norm, and Weierstrass approximation plus uniform boundedness proves the equivalence.

**Reason.** Repeated nodes can cancel and invalidate the absolute-weight formula.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.21 -- source PDF pp. 91--92: Norm of the Lagrange interpolation operator

**Category:** Proof completion

**Issue.** Only the upper bound was immediate; the lower-bound test function was not fully constructed.

**Correction.** A continuous piecewise-linear function is chosen with prescribed signs at the interpolation nodes at a point maximizing the Lebesgue function, yielding equality in the operator norm formula.

**Reason.** The supremum is exact only after a continuous sign pattern is realized at all nodes.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.22 -- source PDF pp. 93--94: Fourier partial sums and Dirichlet kernels

**Category:** Normalization and divergence repair

**Issue.** Constants in the convolution formula and the lower bound for the Dirichlet-kernel L1 norm were inconsistent.

**Correction.** The Fourier partial-sum operator is written with the correct 1/(2pi) factor, its norm is identified with the normalized L1 norm of D_n, and a harmonic-series lower bound proves unboundedness; UBP then gives a continuous function with divergent partial sums.

**Reason.** The conclusion depends on the exact operator norm and a genuine divergent lower bound.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.23 -- source PDF pp. 95--97: Separately continuous bilinear maps and positive quadrature weights

**Category:** Proof and counterexample repair

**Issue.** Separate boundedness was used as though it immediately gave a joint estimate, and the non-Banach counterexample was not cleanly normalized.

**Correction.** Uniform boundedness applied to x->B(x,y) yields ||B(x,y)||<=C||x||||y||; a bilinear form on c00 shows completeness is essential; the positive-weight consequence is proved using a polynomial positive on the compact interval.

**Reason.** Joint continuity requires a uniform bound over one family of separately bounded operators.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.24 -- source PDF pp. 98--100: Basic weak convergence and total-set testing

**Category:** Proof and scalar repair

**Issue.** The source used a norming functional without phases and omitted the uniform boundedness needed to extend convergence from a total subset.

**Correction.** Weak limits are unique, weakly convergent sequences are norm bounded by UBP, the norm is weakly lower semicontinuous using a complex-safe norming functional, and convergence on a total set is extended using a uniform norm bound.

**Reason.** Density alone cannot control the approximation errors unless the sequence is uniformly bounded.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.25 -- source PDF pp. 101: Weak convergence in l^p and Radon--Riesz

**Category:** Proof and complex-scalar repair

**Issue.** Coordinate convergence was treated as sufficient without a boundedness hypothesis, and the uniformly convex argument used an order relation unavailable over C.

**Correction.** For 1<p<infinity, boundedness plus coordinatewise convergence is shown equivalent to weak convergence; the Radon--Riesz proof uses a phase-adjusted norming functional and its real part.

**Reason.** Complex scalar values are not ordered, and coordinate convergence alone can coexist with unbounded norms.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.26 -- source PDF pp. 102: Weak convergence under compact and bilinear maps

**Category:** Proof completion

**Issue.** The compact-operator argument did not rule out a bad subsequence, and the bilinear limit estimate mixed weak and norm convergence.

**Correction.** Boundedness of weakly convergent sequences plus compactness gives a norm-convergent subsubsequence whose weak limit forces the norm limit; the bilinear estimate separates the norm-convergent and weakly convergent variables.

**Reason.** Compactness proves norm convergence only after the uniqueness of the weak limit is used.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.27 -- source PDF pp. 103--105: Weak/weak-star topologies and operator convergence

**Category:** Definition and UBP repair

**Issue.** The source conflated norm, strong, weak, and weak-* convergence and did not prove boundedness of strong operator limits.

**Correction.** The topologies and sequence notions are defined separately; UBP supplies a uniform operator bound; convergence on a total set plus this bound gives strong operator convergence; weak-* convergence of functionals is treated as the scalar-valued case.

**Reason.** Pointwise convergence does not by itself imply a bounded limit operator without completeness of the domain.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.28 -- source PDF pp. 106--107: Reflexivity results and the closed canonical image

**Category:** Scope and proof transparency

**Issue.** The source listed Milman--Pettis and Eberlein--Smulian with sketches too short to establish the deep conclusions.

**Correction.** The theorems are recorded in correct form with an explicit note that the handwritten sketches are not complete proofs; the elementary equivalence "J(X) closed in X** iff X Banach" is proved fully.

**Reason.** Deep results should not be presented as proved by an argument that omits their central compactness machinery.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.29 -- source PDF pp. 108--110: Lp weak convergence, weak lower semicontinuity, and weak-* subsequences

**Category:** False DCT step and proof completion

**Issue.** The source invoked dominated convergence without a common pointwise dominator and gave only a fragmentary oscillating example.

**Correction.** For 1<p<infinity, boundedness plus a.e. convergence is proved weakly using Egorov and Holder; an alternating-cell sequence converges weakly to 1/2 but not strongly; weak lower semicontinuity and closed-span membership are proved by separation; the separable weak-* subsequence result uses a diagonal argument and bounded extension.

**Reason.** Uniform Lp boundedness is not a pointwise dominating function, and the example needs an exact weak-limit calculation.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.30 -- source PDF pp. 111: Toeplitz limit theorem

**Category:** Proof completion

**Issue.** Only the conditions of the matrix theorem were displayed.

**Correction.** The regularity criterion is stated with the row-sum, fixed-column, and uniform l1-row conditions, and the standard split into a finite head and small tail is supplied.

**Reason.** Each condition controls a different error term in Ax-x.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.31 -- source PDF pp. 112--116: Open mapping, inverse bounds, equivalent norms, and stable surjectivity

**Category:** Proof repair and hypotheses

**Issue.** The source moved from density of T(B) to actual surjectivity without the corrective series, applied bounded inverse before bijectivity, and compressed the perturbation argument.

**Correction.** Baire gives a ball in the closure and a convergent correction series puts a smaller ball inside T(B); the bounded inverse theorem is derived; the boundary-value estimate is made conditional on bijectivity; complete norm equivalence and stability of surjectivity are proved with the appropriate iterative series.

**Reason.** Density is not equality, and bounded inverse requires a bounded bijection between Banach spaces.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.32 -- source PDF pp. 117--120: Closed graph theorem and differentiation

**Category:** Proof and domain repair

**Issue.** The source conflated closedness of an operator with boundedness and did not distinguish an everywhere-defined map from a proper-domain closed operator.

**Correction.** The product Banach norm and graph-norm proof of the closed graph theorem are given; the sequential criterion is stated; closedness from a closed domain is supplied only under Banach hypotheses; differentiation C^1->C is used as a closed but unbounded proper-domain example.

**Reason.** Closed operators may be unbounded when their domain is not all of the Banach space.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

### C3.33 -- source PDF pp. 121--124: Inverses, compact-domain maps, termwise differentiation, and graph extensions

**Category:** Hypothesis and proof repair

**Issue.** Several exercises omitted compactness/continuity hypotheses or treated a closed linear relation as automatically single-valued.

**Correction.** Graphs are transposed to prove inverse closedness; images and preimages of compact sets are handled by sequences; the compact-domain result is restated for a compact metric domain and a bijective closed-graph map; a bounded inverse gives closed range; termwise differentiation follows from closedness; a closed relation is a graph exactly when it contains no nonzero vertical vector.

**Reason.** Single-valuedness, compactness, and completeness are the hypotheses that make the conclusions valid.

**Implemented in:** `chapters/chapter-3-fundamental-theorems.tex`.

## Chapter 4 -- Hilbert Spaces

### C4.01 -- source PDF pp. 125--127: Inner-product axioms, Cauchy--Schwarz, and polarization

**Category:** Convention and proof completion

**Issue.** The complex linearity convention was unstated and several geometric identities were recorded without proof or with real-only formulas.

**Correction.** The inner product is declared linear in the first variable; Cauchy--Schwarz, equality cases, Pythagoras, triangle inequality, the parallelogram identity, real and complex polarization formulas, and continuity are proved consistently.

**Reason.** Conjugates and signs depend on the chosen convention.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.02 -- source PDF pp. 128: Operator norm and origin-fixing isometries

**Category:** Proof and scalar-scope correction

**Issue.** The source inferred linearity of an isometry from norm preservation without distinguishing real and complex spaces.

**Correction.** The inner-product operator norm formula is proved; an origin-fixing isometry between real inner-product spaces is shown linear via polarization, while complex conjugation is recorded as a counterexample to complex linearity.

**Reason.** Distance preservation alone gives real affine structure, not complex linearity.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.03 -- source PDF pp. 129: Mazur--Ulam theorem

**Category:** Generality correction

**Issue.** The source gave a special strict-convexity midpoint argument as though it were the full theorem.

**Correction.** The full statement -- every surjective isometry between real normed spaces is affine -- is recorded, and the strict-convexity argument is labelled as a special elementary proof.

**Reason.** Mazur--Ulam does not require strict convexity.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.04 -- source PDF pp. 130: Vanishing quadratic form

**Category:** Field correction

**Issue.** The source did not clearly state that the conclusion T=0 from <Tx,x>=0 is complex-specific.

**Correction.** The complex proof uses x+iy and polarization of the associated sesquilinear form; a real skew-symmetric rotation is given as a counterexample.

**Reason.** Over real spaces, a nonzero skew-symmetric operator has zero quadratic form.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.05 -- source PDF pp. 131--132: Projection theorem for closed convex sets

**Category:** Proof completion

**Issue.** The minimizing sequence was asserted Cauchy without a complete parallelogram estimate and the limit was not explicitly kept inside the set.

**Correction.** The midpoint estimate yields Cauchyness; Hilbert completeness and closedness give a minimizer; strict convexity gives uniqueness.

**Reason.** An infimum becomes an attained unique minimum only after all three steps.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.06 -- source PDF pp. 132--134: Orthogonal and metric projections

**Category:** Linearity and inequality repair

**Issue.** The source mixed the subspace orthogonality condition with the convex-set variational inequality and risked treating every metric projection as linear.

**Correction.** For closed subspaces, x-P_Mx is orthogonal to M and P_M is linear with ||P_M||<=1; for closed convex sets, Re<x-P_Cx,z-P_Cx><=0 and the projection is nonexpansive; linearity is asserted only for subspaces.

**Reason.** Convex projections are generally nonlinear, and their characterization is an inequality rather than equality.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.07 -- source PDF pp. 135: Resolvent of a projection and nested convex projections

**Category:** Proof repair

**Issue.** The algebra for (lambda I-P)^{-1} and the convergence of nested projections were incomplete.

**Correction.** The inverse formula is checked on range P and kernel P; the nested-projection result uses the variational inequalities to prove Cauchyness and identify the limit as the projection onto the closed union span.

**Reason.** The direct-sum decomposition and monotonicity estimate are the missing mechanisms.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.08 -- source PDF pp. 136--137: Blank-page accounting

**Category:** Source integrity

**Issue.** Two blank grid pages could be mistaken for omitted notes.

**Correction.** They are recorded explicitly in the source-page ledger and omitted from the typeset mathematical text.

**Reason.** No mathematical content should be invented to fill blank pages.

**Implemented in:** `page-ledger.csv; chapters/chapter-4-hilbert-spaces.tex`.

### C4.09 -- source PDF pp. 138--140: Orthogonal complements, double complements, and projection kernels

**Category:** Closure and proof completion

**Issue.** The source compressed closedness of M^perp, the closure in M^{perp perp}, direct-sum uniqueness, and range/kernel identities.

**Correction.** M^perp is proved closed, M^{perp perp}=closure(M), H=M directsum M^perp for closed M, Ran P_M=M, Ker P_M=M^perp, and P_{M^perp}=I-P_M.

**Reason.** The closure cannot be dropped when M is not closed.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.10 -- source PDF pp. 141: Riesz representation theorem

**Category:** Complex conjugation correction

**Issue.** With inner products linear in the first variable, the source chose the representative with the wrong scalar conjugation.

**Correction.** After choosing a unit vector u orthogonal to Ker phi, the representative is h=overline{phi(u)}u, so phi(x)=<x,h> and ||phi||=||h||.

**Reason.** Using phi(u)u instead gives the conjugate scalar under the stated convention.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.11 -- source PDF pp. 142: Bounded sesquilinear forms

**Category:** Convention and proof repair

**Issue.** Riesz representation was applied directly to a conjugate-linear variable.

**Correction.** For fixed x, the linear functional y -> overline{b(x,y)} is represented by Sx; the resulting operator is shown linear, bounded, unique, and norm preserving.

**Reason.** Riesz applies to linear, not conjugate-linear, functionals under the chosen convention.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.12 -- source PDF pp. 143: Strict convexity and the Hilbert unit ball

**Category:** Example repair

**Issue.** The infinite-dimensional counterexample coordinates were unclear and the equality case was not fully justified.

**Correction.** The Hilbert ball is proved strictly convex by the equality case of Cauchy--Schwarz; a precise l-infinity example supplies distinct unit vectors whose midpoint still has norm one.

**Reason.** A counterexample must satisfy all three norm equalities exactly.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.13 -- source PDF pp. 144: Extension of operators from Hilbert subspaces

**Category:** Norm and zero-space correction

**Issue.** The source wrote ||P_U||=1 without treating U={0} and did not separate the Hahn--Banach extension from the projection step.

**Correction.** First extend S from U to closure(U) or use the supplied extension to a Banach codomain, then compose with P_U; use ||P_U||<=1 and restriction for the reverse norm inequality.

**Reason.** The orthogonal projection has norm zero on the zero subspace and norm one only when U is nonzero.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.14 -- source PDF pp. 145: Equality in the triangle inequality for functionals

**Category:** Scope and example correction

**Issue.** The source jumped from equality of norms to equality of representatives and cited an unspecified non-uniformly-convex space.

**Correction.** Riesz representatives reduce the Hilbert-space equality case to strict convexity; l1^2 gives a concrete Banach-space counterexample where equality holds for nonproportional functionals.

**Reason.** The Hilbert conclusion uses strict convexity and need not hold in arbitrary Banach spaces.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.15 -- source PDF pp. 146--150: Orthogonal series, Bessel, maximal families, and Parseval

**Category:** Proof completion

**Issue.** Unordered sums and coefficient identities were stated without a complete Cauchy criterion or proof that the series converges to the vector.

**Correction.** Finite orthogonal sums give the square-norm identity; square summability is shown equivalent to convergence; Bessel's inequality, the closed-span formula, maximality, Fourier expansion, and Parseval are derived.

**Reason.** Coefficient formulas alone do not identify the norm limit without totality or maximality.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

### C4.16 -- source PDF pp. 151--155: Totality, separability, Hilbert dimension, and Fourier projections

**Category:** Proof and conjugation repair

**Issue.** The source compressed countability of orthonormal families, classification by basis cardinality, and coefficient formulas under the chosen inner-product convention.

**Correction.** Totality is characterized by zero orthogonal complement; separable Hilbert spaces get countable bases by Gram--Schmidt; arbitrary Hilbert spaces are classified by orthonormal-basis cardinality using countable supports; projections and functional representatives use the correct conjugated coefficients.

**Reason.** The cardinality comparison and complex coefficients require more than the finite-dimensional argument.

**Implemented in:** `chapters/chapter-4-hilbert-spaces.tex`.

## Chapter 5 -- Spectral Theory on Normed Spaces

### C5.01 -- source PDF pp. 156--157: Resolvent definition for closed operators

**Category:** Definition and convention repair

**Issue.** The source used a nonstandard "regular" condition involving injectivity and a bounded inverse on a dense range.

**Correction.** The standard resolvent requires T-lambda I to be bijective onto X with bounded inverse.  The source convention is retained in a remark and proved equivalent for closed operators by extending the bounded inverse from the dense range and using closedness.

**Reason.** The standard spectrum is the complement of true invertibility on the whole Banach space.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.02 -- source PDF pp. 157: Spectrum of a diagonal operator

**Category:** Range-density and classification repair

**Issue.** The source jumped from eigenvalues to the full interval spectrum and did not separate point, continuous, and residual cases.

**Correction.** For Te_n=lambda_n e_n with dense values in [0,1], injectivity, dense range, surjectivity failure, and boundedness of the inverse are checked pointwise to identify the point and continuous spectra.

**Reason.** Closure of the eigenvalue set alone does not classify why each non-eigenvalue lies in the spectrum.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.03 -- source PDF pp. 158--162: Resolvent calculus, spectral mapping, and spectral radius

**Category:** Proof completion

**Issue.** The source compressed the local resolvent expansion, signs in the resolvent identity, polynomial spectral mapping, nonemptiness of the spectrum, and the radius formula.

**Correction.** Neumann factorization proves openness and analyticity; the resolvent identity is derived algebraically; polynomial factors prove spectral mapping; Liouville gives nonempty compact spectrum; the Cauchy--Hadamard argument yields r(T)=lim ||T^n||^{1/n}.

**Reason.** Each conclusion depends on an exact factorization and the correct sign convention for R_lambda=(T-lambda I)^{-1}.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.04 -- source PDF pp. 163--165: Compact operators and norm limits

**Category:** Definition and proof repair

**Issue.** Compactness was mixed with boundedness and the norm-limit proof divided by an uncontrolled sequence bound.

**Correction.** Compact linear maps are defined by relatively compact bounded images and then shown bounded; finite rank and composition properties are proved; for T_n->T, a diagonal subsequence argument uses M=max(1,sup||x_n||) to avoid division by zero.

**Reason.** The diagonal proof needs a uniform finite normalization even when the original bound is zero.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.05 -- source PDF pp. 164: Compact operators send weak convergence to norm convergence

**Category:** Proof completion

**Issue.** The source showed only that a convergent image subsequence has the correct limit.

**Correction.** Every subsequence is shown to have a further subsequence converging in norm to Tx; the subsequence principle then forces the whole sequence Tx_n to converge to Tx.

**Reason.** Identifying one subsubsequence is insufficient unless all bad subsequences are excluded.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.06 -- source PDF pp. 166--167: Total boundedness, separable range, completion, and Schauder theorem

**Category:** Proof completion

**Issue.** The equivalence between relative compactness and total boundedness and the separability conclusion were abbreviated; compactness of the adjoint was asserted without a finite-net argument.

**Correction.** Separated-sequence and finite-net proofs are supplied; the range is covered by countably many compact images; compact maps extend to completions; a finite-net approximation of the adjoint unit ball proves Schauder's theorem, and the converse uses canonical embeddings.

**Reason.** Pointwise boundedness of the adjoint family is not compactness.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.07 -- source PDF pp. 168: Countability of nonzero eigenvalues

**Category:** Proof repair

**Issue.** The source did not justify linear independence, closed finite spans, or the separated image sequence.

**Correction.** Eigenvectors for distinct eigenvalues are proved independent; Riesz's lemma chooses normalized vectors away from earlier invariant spans; compactness then rules out infinitely many eigenvalues bounded away from zero, and annuli give countability.

**Reason.** The only possible accumulation point is zero, but that conclusion needs a quantitative separation argument.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.08 -- source PDF pp. 169--171: Finite-dimensional generalized eigenspaces and closed ranges

**Category:** Hypothesis and proof repair

**Issue.** The source manipulated kernel/range chains without proving closedness or excluding infinite-dimensional closed subspaces of a compact range.

**Correction.** For lambda!=0, generalized null spaces are finite dimensional, Ran(T-lambda I) is closed, and a compact operator between Banach spaces cannot have a closed infinite-dimensional subspace in its range; all Banach hypotheses are stated.

**Reason.** Open mapping and Riesz's lemma require complete domain/range spaces.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.09 -- source PDF pp. 172--173: Stabilization and the Banach adjoint scalar

**Category:** Proof and conjugation correction

**Issue.** The source gave incomplete stabilization arguments and inserted a complex conjugate into the Banach-space adjoint formula.

**Correction.** Compactness rules out strictly increasing kernels and strictly decreasing ranges for powers of T-lambda I; throughout, (T-lambda I)^*=T^*-lambda I because the Banach adjoint is defined by composition.

**Reason.** Conjugation appears only after Hilbert-space identification by Riesz, not in the Banach adjoint itself.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.10 -- source PDF pp. 174--176: Equal ascent/descent and the Riesz--Schauder decomposition

**Category:** Proof completion

**Issue.** The source asserted stabilization equivalences and the direct-sum decomposition without proving trivial intersection or surjectivity of the sum.

**Correction.** Equal stabilized nullities/ranges are proved, every nonzero spectral value of a compact operator is shown to be an eigenvalue, and X=Ker(A^m) directsum Ran(A^m) is established for A=T-lambda I.

**Reason.** The decomposition needs both closed range and eventual stabilization.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.11 -- source PDF pp. 177: Noncompact examples

**Category:** Proof repair

**Issue.** The source relied only on spectral slogans for multiplication and Volterra-type examples.

**Correction.** Explicit bounded sequences are used to show the diagonal/multiplication example lacks compact image subsequences; incompatibility of range properties supplies the second contradiction.

**Reason.** Noncompactness should be tied to the definition or to a previously proved spectral theorem with all hypotheses checked.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.12 -- source PDF pp. 178--180: Fredholm solvability for A=T-lambda I

**Category:** Proof completion

**Issue.** The source stated the annihilator condition without showing both directions or bounded selection of representatives.

**Correction.** Ran A=preann Ker A* is proved using closed range and Hahn--Banach; a bounded right-inverse estimate on a complement/quotient is established; the blank page 180 is accounted for.

**Reason.** The inhomogeneous equation is controlled by the adjoint kernel, but equality requires closedness of the range.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.13 -- source PDF pp. 181: Solvability of the adjoint equation

**Category:** Invalid theorem reuse

**Issue.** The source tried to obtain a solution in X* by applying the previous theorem to T*, which would move the problem into X*** and required unproved identifications.

**Correction.** A bounded functional is defined directly on Ran(T-lambda I), the bounded representative estimate proves continuity, and Hahn--Banach extends it to X.

**Reason.** The direct construction reaches X* without assuming reflexivity.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.14 -- source PDF pp. 182--183: Injectivity, surjectivity, and biorthogonal vectors

**Category:** Proof completion

**Issue.** The source mixed the equations for T-lambda I and its adjoint and used biorthogonal vectors without construction.

**Correction.** Stabilization yields injectivity iff surjectivity and bounded inverse for I-T with compact T; finite independent functionals are separated inductively to construct vectors x_j with f_i(x_j)=delta_ij.

**Reason.** The dimension argument later in Fredholm theory depends on an actual biorthogonal system.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.15 -- source PDF pp. 184: Equality of nullities and Fredholm index zero

**Category:** Scalar and dimension correction

**Issue.** The source used a conjugated eigenvalue and did not prove equality of kernel dimensions.

**Correction.** For nonzero lambda, lambda is an eigenvalue of T iff it is an eigenvalue of the Banach adjoint T* in the appropriate solvability argument; annihilator dimensions and biorthogonal systems give dim Ker A=dim Ker A* and index zero.

**Reason.** The Banach adjoint carries the same scalar lambda under the composition convention.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.16 -- source PDF pp. 185: Definition of the Fredholm alternative

**Category:** Logical correction

**Issue.** The first alternative was described only by trivial homogeneous kernels, which is not equivalent to solvability for arbitrary operators.

**Correction.** The alternatives are stated as: both B and B* are bijective, or both homogeneous equations have equal positive finite-dimensional solution spaces and the inhomogeneous equation satisfies the orthogonality condition.

**Reason.** Injectivity alone does not imply surjectivity outside the compact-perturbation setting.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.

### C5.17 -- source PDF pp. 186--187: Compact integral operators and adjoint kernels

**Category:** Proof completion and convention repair

**Issue.** The final source pages gave only fragments of Arzela--Ascoli compactness and the adjoint integral equation.

**Correction.** Uniform boundedness and equicontinuity of the kernel operator are proved, Arzela--Ascoli gives compactness, the Hilbert adjoint kernel is written with the correct conjugation, and the Fredholm solvability condition is stated explicitly.

**Reason.** Compactness and the adjoint formula require continuity of the kernel and the declared inner-product convention.

**Implemented in:** `chapters/chapter-5-spectral-theory.tex`.
