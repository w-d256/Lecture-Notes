# LaTeX note review - Notes on Measure Theory

## Scope

The uploaded item is a 107-page handwritten PDF rather than editable LaTeX source. The original PDF is preserved unchanged. The reviewed edition therefore consists of page-referenced corrected statements and replacement arguments, organized under the original Chapter 0 (Preliminaries), Chapter 1 (Measures), and Chapter 2 (Integration) structure.

The review checked mathematical validity, missing hypotheses, proof completeness, notation, grammar, and LaTeX compilation risks. Repeated mechanical issues are grouped below; every substantive mathematical correction found in the review is recorded separately in the chapter files and compiled PDF.

## Global grammatical, notational, and compilation corrections

1. Standardized the names and capitalization of sigma-algebra, Borel, Lebesgue, Caratheodory, Fubini--Tonelli, Egoroff, Lusin, Scheffe, and related terminology.
2. Replaced ambiguous handwritten membership and containment marks with explicit $\in$, $\subseteq$, complements, and set difference; standardized inverse-image and section notation.
3. Kept premeasures, outer measures, completions, and saturated measures distinct as $\mu_0$, $\mu^*$, $\overline\mu$, and $\widetilde\mu$ instead of recycling one undecorated symbol.
4. Added the finiteness, sigma-finiteness, completeness, nonnegativity, almost-everywhere finiteness, and integrability assumptions at the exact steps where they are used.
5. Replaced sentence fragments such as “similar,” “trivial,” and “by the same argument” whenever a disjointification, measurable-hull, monotone-class, approximation, or limiting step was nontrivial.
6. Corrected recurring grammar: missing articles, mismatched singular/plural verbs, incomplete proof sentences, inconsistent theorem labels, and punctuation around displayed mathematics.
7. Replaced invalid uncountable-additivity arguments by countable constructions and removed subtraction involving $\infty$.
8. Because there was no original `.tex` source, no baseline source compilation was possible. A new portable master and three corrected LaTeX chapter files were created and compiled under strict error handling.

## Substantive correction count

- Chapter 0: 7 corrections.
- Chapter 1: 32 corrections.
- Chapter 2: 34 corrections.
- Total: 73 substantive corrections.

# Preliminaries: corrected statements and proofs

## Maximal principles and well-ordering

### Correction 0.1 -- PDF pp. 2--3: Hausdorff maximal principle and Zorn's lemma

The two principles are equivalent, but both handwritten directions omit the step that makes the chosen object maximal. From the Hausdorff maximal principle, take a maximal chain $C$ in the poset and let $u$ be an upper bound of $C$. If $u<y$, then $C\cup\{y\}$ is a strictly larger chain, so $u$ is maximal. Conversely, order the set of chains by inclusion. The union of any chain of chains is again a chain and is an upper bound, so Zorn's lemma produces a maximal chain.

### Correction 0.2 -- PDF pp. 2--3: well-ordering theorem

Partial well-orderings must be ordered by **initial-segment extension**, not merely by inclusion plus agreement of the two orders. Thus $(A,\preccurlyeq_A)\leq(B,\preccurlyeq_B)$ means that $A$ is an initial segment of $B$ and the orders agree on $A$. The union of a chain of such extensions is then well-defined and well-ordered. Zorn's lemma gives a maximal partial well-ordering; if its underlying set were not all of $X$, one could adjoin a new point as the largest element, contradicting maximality.

### Correction 0.3 -- PDF p. 4: transfinite induction

If $A\subseteq X$ has the property that $I_x:=\{y:y<x\}\subseteq A$ implies $x\in A$, assume $A\neq X$ and choose the least $x_0\in X\setminus A$. Minimality gives $I_{x_0}\subseteq A$, so the induction hypothesis forces $x_0\in A$, a contradiction. The original proof stopped after writing that the predecessors lie in $A$ and did not invoke the hypothesis.

### Correction 0.4 -- PDF p. 4: union of initial segments

For $J=\bigcup_{x\in A}I_x$, the correct conclusion is that either $J=X$ or $J=I_y$ for the least $y\in X\setminus J$. The proof must first note that $J$ is downward closed. If $z<y$, minimality of $y$ gives $z\in J$; if $z\in J$ and $y\leq z$, downward closure would put $y$ in $J$, a contradiction. The handwritten use of $\inf(A\setminus J)$ does not establish that the set is nonempty and is not the right object in general.

### Correction 0.5 -- PDF pp. 4--5: comparison of well-orders

Order partial order-isomorphisms between initial segments by extension. The union of a chain is again an order-isomorphism between initial segments, so Zorn's lemma applies. At a maximal map, the domain and range cannot both be proper: adjoining the least omitted element on each side would extend the map. Hence one well-order is isomorphic to the other or to an initial segment of the other. The chain-upper-bound verification is missing from the notes.

### Correction 0.6 -- PDF p. 5: the first uncountable well-order and countable subsets

Uniqueness follows from comparison: an isomorphism from one candidate onto a proper initial segment of the other would make an uncountable set countable, because every proper initial segment is countable. For a countable subset $A$ of the first uncountable well-order, $J=\bigcup_{x\in A}I_x$ is countable, so $J\neq\Omega$ and therefore $J=I_y$ for some $y$. Then every $x\in A$ satisfies $x\leq y$, so $y$ is an upper bound. The handwritten argument reverses the countability contradiction and does not justify the last implication.

## Unordered nonnegative sums

### Correction 0.7 -- PDF p. 6: unordered sums

For $f:X\to[0,\infty]$, define $\sum_{x\in X}f(x)$ as the supremum of all finite partial sums. If $A=\{x:f(x)>0\}$ is uncountable, then $A=\bigcup_{n\geq1}\{x:f(x)\geq1/n\}$ forces at least one level set to be infinite; finite subsets of arbitrarily large cardinality then make the unordered sum infinite. If $A$ is countable, enumerate it and compare every finite partial sum with a sufficiently long initial partial sum of the series. Both inequalities are needed; the notes state only one comparison.
# Measures: corrected statements and proofs

## Sigma-algebras and generated structures

### Correction 1.1 -- PDF p. 8: algebra versus sigma-algebra

Because an algebra is already closed under complements, closure under countable intersections is equivalent to closure under countable unions by De Morgan's laws. The remark should state this equivalence rather than presenting the intersection condition without explanation.

### Correction 1.2 -- PDF p. 9: generators of the Borel sigma-algebra

Showing that open, closed, or half-open intervals are Borel gives only one inclusion. For the reverse inclusion, express every open set as a countable union of intervals from the chosen family, or first express each open interval in the generated sigma-algebra. The same two-inclusion argument is required for rays and closed intervals.

### Correction 1.3 -- PDF pp. 9--10: product sigma-algebra generators

For a countable index set, a measurable rectangle is the countable intersection of its coordinate cylinders, while each coordinate cylinder is itself a rectangle with all other coordinates equal to the whole factor. For coordinate subgenerators $\mathcal E_\alpha$, define
$$
\mathcal C_\alpha=\{B\subseteq X_\alpha:\pi_\alpha^{-1}(B)\text{ belongs to the generated sigma-algebra}\}.
$$
Then $\mathcal C_\alpha$ is a sigma-algebra containing $\mathcal E_\alpha$. The handwritten proof compares sets living in different spaces and omits these inclusions.

### Correction 1.4 -- PDF p. 10: Borel sigma-algebra of a finite product

Continuity of the coordinate projections gives $\bigotimes_{j=1}^n\mathcal B(X_j)\subseteq\mathcal B(\prod_jX_j)$. If every $X_j$ is separable metric, choose a countable base $\mathcal U_j$ in each factor. The finite products $U_1\times\cdots\times U_n$ form a countable base for the product topology, so every open set is a countable union of measurable rectangles. The notes mention balls in the factors but never form the product base.

### Correction 1.5 -- PDF p. 11: elementary families

The proof that finite disjoint unions of elementary sets form an algebra is circular as written. First prove closure under finite intersections by distributing over the finitely many pieces. Then expand complements using the finite disjoint decompositions of elementary complements. Finally obtain unions from complements and intersections, or refine $A\cup B$ into $A\setminus B$, $A\cap B$, and $B\setminus A$.

### Correction 1.6 -- PDF p. 12: cardinality of an infinite sigma-algebra

An infinite sigma-algebra does contain countably many pairwise disjoint nonempty sets, but this needs a construction. If it has infinitely many atoms, choose countably many; otherwise recursively split an infinite non-atomic remainder and retain one nonempty piece at each stage. For disjoint $E_n$, the map
$$
S\subseteq\mathbb N\longmapsto\bigcup_{n\in S}E_n
$$
is injective, so the sigma-algebra has cardinality at least $2^{\aleph_0}$. The handwritten cardinality sentence does not define this injection.

## Basic measure theory, completion, and saturation

### Correction 1.7 -- PDF pp. 13--14: continuity from above

If $E_n\downarrow E$, the identity $\mu(E_n)\downarrow\mu(E)$ requires $\mu(E_1)<\infty$ (or finiteness of some later $E_n$). Set $F_n=E_1\setminus E_n\uparrow E_1\setminus E$, apply continuity from below, and subtract from the finite number $\mu(E_1)$. Subtracting from $\infty$ is not legitimate.

### Correction 1.8 -- PDF p. 14: completion of a measure

The completion proof must establish four points that are omitted in the notes. Write
$$
\overline{\mathcal M}=\{A\cup N:A\in\mathcal M,\ N\subseteq Z\in\mathcal M,\ \mu(Z)=0\}.
$$
This is a sigma-algebra; $\overline\mu(A\cup N)=\mu(A)$ is well-defined because two measurable representatives differ only by a measurable null set; the formula is countably additive; and every subset of a null set belongs to $\overline{\mathcal M}$. Uniqueness then follows from agreement on the measurable representative and its null remainder.

### Correction 1.9 -- PDF p. 15: measure of a limsup

The inequality
$$
\mu(\limsup E_n)\geq\limsup\mu(E_n)
$$
is false without a finiteness hypothesis. It is valid, for example, when $\mu(\bigcup_nE_n)<\infty$, because the decreasing tail unions then satisfy continuity from above. That hypothesis must be stated at the point where the theorem is used.

### Correction 1.10 -- PDF p. 16: sigma-finite implies semifinite

From a sigma-finite cover $X=\bigcup_nA_n$ with $\mu(A_n)<\infty$, first replace it by the increasing finite-measure exhaustion $X_n=\bigcup_{k\leq n}A_k$. If $\mu(E)=\infty$, then $\mu(E\cap X_n)\uparrow\infty$, so some $E\cap X_n$ has finite measure exceeding any prescribed constant. A single set $E\cap A_n$ need not have large measure, contrary to the handwritten argument.

### Correction 1.11 -- PDF p. 16: arbitrarily large finite subsets under semifiniteness

Semifiniteness does not justify choosing measurable singletons. Let
$$
S=\sup\{\mu(F):F\subseteq E,\ \mu(F)<\infty\}.
$$
If $S<\infty$, choose $F_n\subseteq E$ with finite measure approaching $S$. Their union has finite measure $S$; the remainder still has infinite measure and hence contains a positive finite-measure set, contradicting maximality of $S$. Therefore $S=\infty$, giving a finite-measure subset larger than any prescribed $C$.

### Correction 1.12 -- PDF pp. 16--17: the semifinite part of a measure

For
$$
\mu_0(E)=\sup\{\mu(F):F\subseteq E,\ \mu(F)<\infty\},
$$
countable additivity on disjoint $E_n$ needs both directions. Finite-measure $F_n\subseteq E_n$ give the lower bound after taking finite unions; any finite-measure $F\subseteq\bigcup_nE_n$ decomposes into $F\cap E_n$ for the upper bound. A valid $\{0,\infty\}$-valued residual measure is $\nu(E)=0$ when $E$ is sigma-finite for $\mu$ and $\nu(E)=\infty$ otherwise. The case table in the notes does not by itself define an additive measure.

### Correction 1.13 -- PDF pp. 18--19: saturation construction

The symbols for the original domain, locally measurable domain, original measure, and saturated measure must remain distinct. To prove countable additivity of the saturated measure, separate the case in which every term lies in the original domain from the case in which one term has value $\infty$; if the union had finite original measure, local measurability would force every summand into the original domain. In the semifinite version, reduce estimates to finite-measure measurable subsets before taking suprema. Several handwritten equalities use these facts before they are proved.

### Correction 1.14 -- PDF p. 19: the saturation example

A finite set such as $\{x,y\}$ is countable and therefore belongs to the countable/co-countable sigma-algebra, so it cannot distinguish the two extensions. Choose instead a subset $E\subseteq X_2$ such that both $E$ and $X_2\setminus E$ are uncountable. Then $E$ is locally measurable but not in the original sigma-algebra; the extension that assigns $\infty$ outside the original domain gives $\widetilde\mu(E)=\infty$, whereas the semifinite extension gives $\underline\mu(E)=0$.

## Outer measures and extension

### Correction 1.15 -- PDF p. 20: induced outer measure

For countable subadditivity, choose for each $A_i$ a countable elementary cover whose cost is at most $\mu^*(A_i)+\varepsilon2^{-i}$, combine all covers, and let $\varepsilon\downarrow0$. One cannot write the cost of a union when the preliminary set function is defined only on the elementary family, and an arbitrary cover does not justify exchanging a sum with separate infima.

### Correction 1.16 -- PDF p. 21: Caratheodory's theorem

Before iterating the measurable-splitting identity, disjointify the sets:
$$
C_1=A_1,\qquad C_n=A_n\setminus\bigcup_{k<n}A_k.
$$
The terms $E\cap A_n$ can overlap and therefore cannot be summed as in the handwritten display. Passing to the limit with the disjoint $C_n$ proves countable additivity on measurable sets. Completeness follows because every outer-null set satisfies the Caratheodory criterion and every subset of it is outer-null.

### Correction 1.17 -- PDF p. 22: extension of a premeasure

To prove $\mu^*|_{\mathcal A}=\mu_0$, disjointify a countable algebra cover of $A\in\mathcal A$ inside $A$ and use countable additivity of the premeasure. To prove that $A$ is Caratheodory measurable, split each covering set $B_j$ into $B_j\cap A$ and $B_j\cap A^c$, use finite additivity on each pair, and then take infima. The displayed inequality in the notes has no justification without this refinement.

### Correction 1.18 -- PDF p. 23: uniqueness of the extension

Any other extension $\nu$ satisfies $\nu(E)\leq\mu^*(E)$ by testing every algebra cover. Equality for sets of finite $\mu^*$-measure requires a disjointified near-minimizing cover so that the union has the same value under both measures. Under sigma-finiteness, first replace the covering sets by a disjoint finite-measure partition $F_n$ and then sum the equalities on $E\cap F_n$. The notes sum over a cover that need not be disjoint.

### Correction 1.19 -- PDF pp. 25--26: measurable hulls

If $A_n\supseteq E$ are measurable approximants, replace them by $B_n=\bigcap_{k\leq n}A_k$ before applying continuity from above. In the sigma-finite case, a countable union of $G_\delta$ sets need not be $G_\delta$. Use doubly indexed approximants $B_{n,k}$, set $C_k=\bigcup_nB_{n,k}$, and then take $C=\bigcap_kC_k$; the error outside $E$ is bounded by a summable double series.

### Correction 1.20 -- PDF p. 27: finite total mass and inner measure

For finite $\mu_0(X)$, the equality $\mu^*(E)=\mu_*(E)$ implies measurability only after introducing a measurable hull $B\supseteq E$ with $\mu^*(B)=\mu^*(E)$. Comparing complements inside the finite space shows $\mu^*(B\setminus E)=0$, and then $E=B\setminus(B\setminus E)$ is measurable. Direct subtraction involving an unproved measurable difference is not valid.

### Correction 1.21 -- PDF pp. 27--28: the outer measure regenerated from its measurable sets

Always $\mu^*(E)\leq\mu^+(E)$, since every measurable cover is also an outer-measure cover. Equality holds exactly when $E$ has a measurable hull $B\supseteq E$ with $\mu^*(B)=\mu^*(E)$; obtain such a hull by intersecting nested near-minimizing measurable covers. For the two-point example, the values $0,2,3,4$ on $\varnothing,\{0\},\{1\},X$ give measurable sets only $\varnothing$ and $X$, so $\mu^+$ equals $4$ on every nonempty set.

### Correction 1.22 -- PDF p. 29: saturation of the induced measure

If a locally measurable set $E$ has finite outer measure, place it inside a measurable hull $B$ of the same finite measure; then $E=E\cap B$ is measurable. If $E$ were not measurable in the infinite case, a strict failure of the Caratheodory equality would occur on a test set of finite outer measure. Replacing that test set by a finite measurable hull and using local measurability of $E$ and $E^c$ gives a contradiction. The handwritten proof switches from $B$ to $B_0$ without preserving these inequalities.

### Correction 1.23 -- PDF pp. 30--32: completion versus saturation

An element of the completion must be written with an identified measurable null container, not merely as an arbitrary union $E\cup F$. In the sigma-finite case, Caratheodory-measurable sets are exactly the completion: use a measurable hull with null difference and then a measurable null cover. In general, every finite Caratheodory-measurable set is in the completion, and the full Caratheodory domain is the saturation of that completion. All appeals to measurable hulls require finite outer measure to be stated first.

## Lebesgue--Stieltjes and Lebesgue measure

### Correction 1.24 -- PDF p. 33: a measure on traces of a nonmeasurable set

If $\mu^*(E)=\mu(X)<\infty$, then for every measurable $A$,
$$
\mu^*(E)\leq\mu^*(E\cap A)+\mu^*(E\cap A^c)\leq\mu(A)+\mu(A^c)=\mu(X),
$$
so $\mu^*(E\cap A)=\mu(A)$. This proves well-definedness of $\nu(A\cap E)=\mu(A)$. For countable additivity, disjointify measurable representatives without changing their traces on $E$; the representatives cannot simply be assumed disjoint.

### Correction 1.25 -- PDF pp. 34--35: Lebesgue--Stieltjes premeasure

Well-definedness follows by refining two finite interval decompositions at all endpoints and using telescoping increments of $F$. For countable additivity on a bounded half-open interval, shrink its left endpoint, enlarge the covering intervals slightly using right continuity, take a finite subcover of the resulting compact interval, and let the error tend to zero. Infinite endpoints must be handled afterward by monotone limits; expressions such as $F(a+\delta)-F(a)$ are meaningless when $a=-\infty$.

### Correction 1.26 -- PDF pp. 37--39: open covers and regularity

For the open-interval covering formula, subadditivity gives one inequality, while the reverse inequality comes from enlarging a near-minimizing half-open cover by amounts with summable measure error. For inner regularity of bounded $E$, choose an open $U\supseteq\overline E\setminus E$ and set $K=\overline E\setminus U$; then $K\subseteq E$ and $\mu(E\setminus K)<\varepsilon$. The formula $\mu(K)=\mu(E)-\mu(U)$ in the notes is false because $U$ need not lie in $E$.

### Correction 1.27 -- PDF p. 39: $G_\delta$ and $F_\sigma$ descriptions

For an unbounded measurable set, overlapping truncations do not automatically preserve the required descriptive class. Work on a disjoint finite-measure exhaustion, choose open supersets with summable excess on each piece, and intersect the resulting global open sets. Apply the result to the complement to obtain the $F_\sigma$ form. This yields $E=G\setminus N=F\cup N'$ with null remainders.

### Correction 1.28 -- PDF p. 39: translation and dilation invariance

Define the translated or dilated measure first on Borel sets, verify its values on half-open intervals, and use uniqueness of the sigma-finite extension. Then show that null sets map to null sets and pass to the Lebesgue completion. The phrase ``the measures agree on the algebra'' is not enough unless uniqueness and completion are explicitly invoked.

### Correction 1.29 -- PDF p. 41: positive-measure sets contain nonmeasurable subsets

Use a Vitali equivalence relation and **countably many rational translates**. A measurable subset of a Vitali selector must have measure zero because its distinct rational translates are disjoint and lie in a bounded interval. If every intersection of a positive-measure set with the countably many translates were measurable, all would be null and their union could not cover the set. The notes incorrectly suggest that measurability of one intersection forces measurability of all and flirt with uncountable additivity.

### Correction 1.30 -- PDF p. 42: density in an interval

Assume $m(E\cap I)\leq\alpha m(I)$ for every interval and some $\alpha<1$. Choose a bounded positive-measure part of $E$ and an open interval cover with total length below $m(E)/\alpha$. Then
$$
m(E)\leq\sum_jm(E\cap I_j)\leq\alpha\sum_jm(I_j)<m(E),
$$
a contradiction. The handwritten estimate reverses one of these inequalities.

### Correction 1.31 -- PDF p. 43: Steinhaus theorem

The shifted-set argument is invalid because $(E+h)\cap I$ need not remain in the same interval as $E\cap I$. A proof that uses only material already established is: choose compact $K\subseteq E$ with $m(K)>0$ and open $U\supseteq K$ with $m(U)<2m(K)$. For sufficiently small $h$, compactness gives $K+h\subseteq U$. Since $K$ and $K+h$ cannot be disjoint inside $U$, $h\in E-E$; hence $E-E$ contains a neighborhood of $0$.

### Correction 1.32 -- PDF p. 44: a Borel set of intermediate density in every interval

The instruction to ``replace intervals with Cantor-type sets'' is not a proof. Enumerate the rational subintervals of $[0,1]$. Recursively place two pairwise disjoint compact nowhere-dense sets of positive measure inside each interval while avoiding all earlier choices. Put all first sets into $A$ and reserve all second sets for $A^c$. Then every nonempty interval contains positive measure from both $A$ and its complement, and $A$ is $F_\sigma$, hence Borel.
# Integration: corrected statements and proofs

## Measurable functions

### Correction 2.1 -- PDF pp. 45--47: generated measurability and algebraic operations

For a generated target sigma-algebra, the class $\{B:f^{-1}(B)\in\mathcal M\}$ is a sigma-algebra on the **target**. Continuity proves that inverse images of open sets are open; the passage to all Borel sets then uses generation. For sums and products of complex measurable functions, first show $(f,g):X\to\mathbb C^2$ is measurable and compose with continuous addition or multiplication. The notes blur these distinct steps and alternate between incompatible codomains.

### Correction 2.2 -- PDF p. 49: dyadic simple approximation

A correct increasing approximation for $f\geq0$ is
$$
\phi_n=\sum_{k=0}^{n2^n-1}k2^{-n}\mathbf1_{\{k2^{-n}\leq f<(k+1)2^{-n}\}}
+n\mathbf1_{\{f\geq n\}}.
$$
Then $0\leq\phi_n\leq f$, $\phi_n\uparrow f$, and $f-\phi_n<2^{-n}$ on $\{f<n\}$. The upper index and terminal level set in the handwritten formula are malformed, so monotonicity is not verifiable as written.

### Correction 2.3 -- PDF pp. 49--50: completeness and measurable representatives

On a complete space, if $f=g$ almost everywhere and $f$ is measurable, split every inverse image of $g$ into its part off the measurable null set and a subset of that null set. Conversely, incompleteness is witnessed by $g=\mathbf1_E$ for a nonmeasurable subset $E$ of a measurable null set. For the completion, choose simple completed-measurable approximants, replace each by an original-measurable simple function off a measurable null set, take one countable union of exceptional sets, and define the limit there separately. The notes use the final null set before constructing it.

### Correction 2.4 -- PDF p. 51: arithmetic on the extended real line

Products with the convention $0(\pm\infty)=0$ and sums in which the two indeterminate pairs are assigned a fixed value must be treated as piecewise Borel maps on $\overline{\mathbb R}^2$. Partition into the measurable regions where both values are finite, where a sign determines $\pm\infty$, and where the special convention applies. The handwritten inverse-image formulas omit cases and do not establish measurability.

### Correction 2.5 -- PDF p. 51: set on which a sequence converges

The proof is circular because it multiplies by the indicator of the very convergence set whose measurability is at issue. For real-valued $f_n$, the finite-limit set is
$$
\{\limsup f_n=\liminf f_n\}\cap\{\limsup f_n<\infty\}\cap\{\liminf f_n>-\infty\}.
$$
For complex-valued functions, use the measurable Cauchy criterion with rational tolerances. Either description makes the set measurable without assuming the conclusion.

### Correction 2.6 -- PDF p. 52: reconstruction from an increasing family $E_a$

For $A_x=\{a:x\in E_a\}$, define
$$
f(x)=\inf A_x=\sup\{a:x\notin E_a\}.
$$
The assumptions that $\bigcup_aE_a=X$ and $\bigcap_aE_a=\varnothing$ make this a finite real number. Then $x\in E_a$ implies $f(x)\leq a$, while $x\notin E_a$ implies $f(x)\geq a$. Moreover
$$
\{f<a\}=\bigcup_{q\in\mathbb Q,\ q<a}E_q.
$$
The handwritten definition uses a supremum of the upward-closed set $A_x$, which is generally $+\infty$.

### Correction 2.7 -- PDF p. 53: Cantor function construction

For $g(x)=f(x)+x$, strict increase comes from the $x$ term, not merely from monotonicity of the Cantor function. A continuous bijection from compact $[0,1]$ to Hausdorff $[0,2]$ is a homeomorphism; a continuous bijection is not automatically open in arbitrary spaces. On every complementary interval of the Cantor set, $f$ is constant, so $g$ preserves its length; therefore $m(g(C))=2-1=1$. A nonmeasurable subset of $g(C)$ pulls back to a Lebesgue-measurable but non-Borel subset of the null Cantor set.

## The integral and convergence theorems

### Correction 2.8 -- PDF p. 57: sigma-finite support of an integrable nonnegative function

If $\int f<\infty$, then $\{f=\infty\}$ is null and
$$
\{f>0\}=\bigcup_{n\geq1}\{f\geq1/n\},\qquad
\mu\{f\geq1/n\}\leq n\int f.
$$
The handwritten sets of the form $\{n\leq f\leq n+1\}$ miss all sufficiently small positive values and do not prove sigma-finiteness of the support.

### Correction 2.9 -- PDF p. 62: dominated convergence for complex functions

The phrase ``without loss of generality the functions are real'' needs a reduction. Apply the real dominated convergence theorem to real and imaginary parts, each dominated by the same integrable function, or apply Fatou's lemma to $g\pm\operatorname{Re}f_n$ and $g\pm\operatorname{Im}f_n$. Only then combine the two limits.

### Correction 2.10 -- PDF pp. 63--65: Riemann versus Lebesgue integration

The upper step function uses interval suprema and the lower step function interval infima, but pointwise limits need not exist for an arbitrary sequence of unrelated partitions. Choose nested refinements whose mesh tends to zero, so upper functions decrease and lower functions increase, or use limsup and liminf. Equality of their integrals then follows from the Riemann criterion, and the equality set is exactly the continuity set up to endpoints.

### Correction 2.11 -- PDF p. 66: uniform convergence on an infinite-measure space

The proposed counterexample is not in $L^1(\mathbb R)$, so it does not satisfy the exercise hypotheses. A valid example for failure of integral convergence is
$$
f_n=\frac1n\mathbf1_{[0,n]},
$$
which converges uniformly to $0$ while every integral equals $1$. A valid example in which the uniform limit is not integrable is $f_n=f\mathbf1_{[-n,n]}$ for $f(x)=(1+|x|)^{-1}$.

### Correction 2.12 -- PDF p. 67: Scheffe's lemma

For nonnegative $f_n,f$ with almost-everywhere convergence and convergent integrals, use
$$
\|f_n-f\|_1=\int f_n+\int f-2\int(f_n\wedge f).
$$
Since $f_n\wedge f\to f$ and is dominated by $f$, dominated convergence gives the result. If convergence is only in measure, apply this argument to an almost-everywhere convergent subsubsequence of every subsequence. The handwritten converse invokes a dominating function that is never specified.

### Correction 2.13 -- PDF pp. 67--68: simple-function sandwiches on the completion

An arbitrary monotone simple approximation need not converge uniformly, and $2g-\phi_n$ is not simple when $g$ is not simple. For bounded $g$, use dyadic lower and upper original-measurable simple functions with pointwise gap at most $2^{-n}$ off one measurable null set, and use the global bound on the null set. Conversely, choose a subsequence with summable integrals of $\psi_n-\phi_n$; then the gap tends to zero almost everywhere and the squeezed function is measurable for the completion.

### Correction 2.14 -- PDF p. 69: the dense-singularity example

For $f(x)=x^{-1/2}\mathbf1_{(0,1)}(x)$, $\int f=2$, not $1$, so $\int g=2\sum_n2^{-n}=2$. To show that no null-set modification becomes continuous, it is not enough to point to isolated singular points that could be altered. Every interval contains a rational shift $r_n$ and a positive-measure subinterval on which $2^{-n}f(\,\cdot-r_n)$ exceeds any prescribed bound; thus $g$ is essentially unbounded on every interval, a property unchanged by null modifications.

### Correction 2.15 -- PDF p. 70: continuity of an indefinite integral

A lower simple approximation alone does not give an upper bound on the integral over a short interval. Use absolute continuity of the Lebesgue integral: for every $\varepsilon>0$ there is $\delta>0$ such that $m(A)<\delta$ implies $\int_A|f|<\varepsilon$. Then
$$
|F(x+h)-F(x)|\leq\int_{[x,x+h]}|f|
$$
for $|h|<\delta$. If one keeps the simple-function proof, the omitted $L^1$ error term and finite-measure support must be included.

### Correction 2.16 -- PDF p. 71: the exponential-series exercise

For $f_n(x)=ae^{-nax}-be^{-nbx}$ with $0<a<b$, the sign changes at
$$
x=\frac{c}{n},\qquad c=\frac{\log(b/a)}{b-a},
$$
not at a constant independent of $n$. Consequently
$$
\int_0^\infty|f_n(x)|\,dx=\frac{2(e^{-ac}-e^{-bc})}{n},
$$
so the series of absolute integrals diverges harmonically, while each signed integral is zero.

## Modes of convergence

### Correction 2.17 -- PDF p. 74: Cauchy in measure

Choose a subsequence $g_j=f_{n_j}$ satisfying
$$
\mu\{|g_{j+1}-g_j|>2^{-j}\}<2^{-j}.
$$
The tail unions have summable measure, so outside a null limsup only finitely many bad increments occur and $g_j(x)$ is Cauchy. The indices and thresholds in the handwritten construction do not imply the displayed pointwise estimate. The full sequence then converges in measure to the same limit by the original Cauchy property.

### Correction 2.18 -- PDF p. 75: Egoroff's theorem

For fixed $k$, the sets
$$
E_{n,k}=\bigcup_{m\geq n}\{|f_m-f|\geq1/k\}
$$
decrease to the empty set. The step $\mu(E_{n,k})\to0$ uses **continuity from above** and the hypothesis $\mu(X)<\infty$, not continuity from below. Choosing one $n_k$ for each $k$ with summable exceptional measures then yields uniform convergence off their union.

### Correction 2.19 -- PDF p. 76: dominated convergence in measure

Fatou's lemma supplies only a lower bound and cannot by itself prove $\int|f_n-f|\to0$. From any subsequence, extract a further subsequence converging almost everywhere; dominated convergence applied to that subsubsequence gives $L^1$ convergence. Since every subsequence has such a subsubsequence, the original nonnegative sequence of $L^1$ distances must tend to zero.

### Correction 2.20 -- PDF p. 81: Lusin's theorem

A finite almost-everywhere finite measurable function on $[a,b]$ need not be integrable, so the proof cannot begin with an $L^1$ approximation by continuous functions. First choose $M$ so that $\{|f|>M\}$ has small measure. The bounded truncation is integrable; approximate it by continuous functions, pass to an almost-everywhere convergent subsequence, apply Egoroff, and finally use inner regularity to choose a compact subset of the good set.

## Product measures and changes of variables

### Correction 2.21 -- PDF pp. 84--85: monotone class and section formula

In the monotone-class proof, for fixed $E$ define the auxiliary class of $F$ for which $E\setminus F$, $F\setminus E$, and $E\cap F$ lie in the monotone class, and verify closure before claiming equality. For the section formula, decreasing limits in the finite case use finiteness of both factor measures; the sigma-finite case must use disjoint finite-measure partitions and then sum the finite-case identities. These hypotheses are only implicit in the notes.

### Correction 2.22 -- PDF pp. 87--88: Fubini--Tonelli for completed products

A product-null measurable set has almost-everywhere null sections directly from the section formula; checking only null rectangles is insufficient. A set in the completion is contained in such a product-null measurable set, and completeness of the factors then makes almost all of its sections measurable and null. For a completed-product-measurable function, first choose an ordinary product-measurable representative $g=f$ almost everywhere, apply Fubini--Tonelli to $g$ in the nonnegative or integrable case, and only afterward identify the integrals. The handwritten proof writes the equality before proving either hypothesis.

### Correction 2.23 -- PDF p. 89: the diagonal with Lebesgue and counting measure

To show $(m\times\#)(D)=\infty$, consider a countable rectangle cover $D\subseteq\bigcup_nA_n\times B_n$. In any finite-cost cover, every rectangle with infinite $B_n$ must have $m(A_n)=0$, while every finite $B_n$ contributes only finitely many diagonal coordinates. The diagonal coordinates covered by all such rectangles form a null set plus a countable set, not all of $[0,1]$. Thus no finite-cost cover exists. The finite-rectangle argument in the notes does not prove the outer-measure claim.

### Correction 2.24 -- PDF p. 89: unequal iterated sums on $\mathbb N^2$

For $f(m,n)=1$ when $m=n$, $-1$ when $m=n+1$, and $0$ otherwise, summing first in $n$ gives a single uncancelled boundary term and total $1$, whereas summing first in $m$ gives $0$ in every column and total $0$. The handwritten solution concludes that both iterated integrals are zero, contradicting the exercise. Also $\sum_{m,n}|f(m,n)|=\infty$, so Fubini's theorem does not apply.

### Correction 2.25 -- PDF p. 92: a countable counting-measure factor

If $Y$ is countable, every measurable $E\subseteq X\times Y$ has the disjoint decomposition
$$
E=\bigsqcup_{y\in Y}E^y\times\{y\},
$$
so $(\mu\times\#)(E)=\sum_y\mu(E^y)$ directly. Tonelli for nonnegative functions follows by applying monotone convergence to the corresponding countable sum. The handwritten sets defined by section cardinalities are unnecessary and their measurability has not yet been established.

### Correction 2.26 -- PDF p. 93: regularity of Lebesgue measure on $\mathbb R^n$

The sentence ``the proof is similar to the one-dimensional case'' omits the main construction. Approximate open sets by countable unions of rational rectangles with compact closures, use finite subunions for inner approximation, and obtain outer approximation from rectangle covers. Extend to arbitrary measurable sets by finite-measure truncations and completion. This also supplies the compactly supported continuous approximation used immediately afterward.

### Correction 2.27 -- PDF pp. 94--95: translations and invertible linear maps

Defining $m'(E)=m(E+a)$ on all Lebesgue sets before proving that translations preserve the completed sigma-algebra is circular. Work first on Borel sets, use uniqueness from rectangles, prove that null sets map to null sets, and then pass to the completion. For an invertible linear map, decompose it into permutations, diagonal scalings, and shears; verify the Jacobian factor for each and compose. ``Apply Fubini and the one-dimensional case'' omits the shear and determinant bookkeeping.

### Correction 2.28 -- PDF p. 96: nonlinear change of variables

The proof is entirely omitted. A valid statement requires a $C^1$ diffeomorphism between open sets, a nonnegative or integrable function, and $|\det DG|$. A proof reduces locally to maps close to their derivative, covers compact subsets by small cubes, compares image volumes, and then uses monotone convergence and exhaustion. Without the diffeomorphism and absolute determinant, the formula is false.

### Correction 2.29 -- PDF p. 98: an integral kernel on a triangle

Before interchanging the integrals for
$$
g(x)=\int_x^a\frac{f(t)}{t}\,dt,
$$
verify absolute integrability:
$$
\int_0^a\int_x^a\frac{|f(t)|}{t}\,dt\,dx
=\int_0^a\frac{|f(t)|}{t}\int_0^t dx\,dt
=\int_0^a|f(t)|\,dt<\infty.
$$
The handwritten proof applies Fubini directly to the signed kernel and only afterward asserts that $g$ is integrable.

### Correction 2.30 -- PDF pp. 99--100: polar coordinates and surface measure

Define $\sigma(E)=n\,m(\{r\omega:0<r\leq1,\ \omega\in E\})$ and verify countable additivity. Let $m_\Phi$ denote the pushforward of Lebesgue measure under polar coordinates and let $\rho$ be the radial measure with density $r^{n-1}$. On rectangles $(a,b]\times E$,
$$
m_\Phi((a,b]\times E)=\frac{b^n-a^n}{n}\sigma(E)=\rho((a,b])\sigma(E).
$$
Uniqueness then gives $m_\Phi=\rho\times\sigma$. The notes reuse one symbol for both measures and cite sigma-finiteness of the wrong space.

## Absolute continuity and uniform integrability

### Correction 2.31 -- PDF p. 102: converse absolute-continuity criterion

If $m(E)<\infty$ and every measurable $A\subseteq E$ of sufficiently small measure satisfies $\int_A|f|<1$, partition $E$ into finitely many measurable pieces of that size. Summing the finitely many bounds gives $\int_E|f|<\infty$. The one-line handwritten proof says only ``by the lemma'' and never performs the finite partition or the sum.

### Correction 2.32 -- PDF p. 104: Vitali convergence on a finite-measure set

After Egoroff, uniform integrability controls $\int_A|f_n|$, and Fatou controls $\int_A|f|$. On $E\setminus A$, uniform convergence gives
$$
\int_{E\setminus A}|f_n-f|\leq m(E\setminus A)\sup_{E\setminus A}|f_n-f|.
$$
If $m(E\setminus A)=0$, this term is already zero; otherwise choose the uniform tolerance after dividing. The handwritten proof divides without separating the zero-measure case.

### Correction 2.33 -- PDF p. 105: the three uniform-integrability examples

The classifications in the notes are reversed. (a) The family $|f|\leq1$ on $[0,1]$ **is** uniformly integrable. (b) Continuous functions with $\int|f|\leq1$ need not be uniformly integrable; continuous triangular spikes of height $n$ and base $2/n$ are a counterexample. (c) A bound on signed integrals over intervals does not control $\int_A|f|$: the functions $f_n(x)=n^2\sin(2\pi n^2x)$ have interval integrals bounded by $1/\pi$, but on $A_n=[0,1/n]$ their absolute integrals grow like $2n/\pi$ while $m(A_n)\to0$.

### Correction 2.34 -- PDF pp. 105--107: finite versus infinite measure and tightness

On an infinite-measure space, uniform integrability controls small sets but not escape of mass. The sequence $\mathbf1_{[n,n+1]}$ is uniformly integrable and converges pointwise to zero while all integrals equal one; it fails tightness. Vitali convergence on an arbitrary space therefore requires both uniform integrability and a finite-measure set outside which all tail integrals are uniformly small. The final proof must choose one such set that also handles the finitely many initial terms.
