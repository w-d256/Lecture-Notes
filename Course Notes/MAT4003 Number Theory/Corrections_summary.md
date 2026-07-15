# MAT4003 Corrected Transcription - Corrections Summary

This ledger records every substantive mathematical, structural, or compilation-related correction made while transcribing the 109-page source PDF. Routine repeated spelling, punctuation, and notation repairs are grouped at the end.

### Correction G.01 - all pages: Global notation - conflicting conventions for natural numbers

**Category:** Global notation

**Issue:** The source alternates between using natural numbers for positive integers and for nonnegative integers.

**Correction:** The manuscript fixes $\mathbb N=\{1,2,\ldots\}$ and $\mathbb N_0=\{0,1,2,\ldots\}$, then adjusts induction statements and index ranges accordingly.

**Reason:** A proof may fail at its base case or include an unintended zero if the convention changes silently.

**Implemented in:** `notes.tex; mat4003-preamble.sty; all chapter files`.

### Correction G.02 - source PDF pp. 56, 57, 97: Global numbering - duplicate and mistyped labels

**Category:** Global numbering

**Issue:** The source uses Corollary 4.12 on p. 56 and then another result labelled Theorem 4.12 on p. 57; the Pell-equation definition on p. 97 is labelled Definition 6.1 although it begins Chapter 7.

**Correction:** The second 4.12 is labelled Theorem 4.12A, and the Pell definition is labelled Definition 7.1. Other visible source numbers are retained.

**Reason:** Unique labels are needed for reliable cross-references without renumbering the rest of the manuscript.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex; chapters/chapter-7-diophantine-equations.tex`.

### Correction G.03 - source PDF pp. 1, 5: Source accounting - non-content pages

**Category:** Source accounting

**Issue:** Page 1 is a cover and page 5 is blank. Neither contains mathematical content.

**Correction:** Both pages are recorded explicitly in Page_ledger.csv and are not represented as mathematical sections.

**Reason:** The source inventory must account for every page without inventing content.

**Implemented in:** `Page_ledger.csv; Validation_report.txt`.

### Correction G.04 - source PDF p. 12: Transcription decision - extended Euclidean example

**Category:** Transcription decision

**Issue:** The handwriting in the example is visually ambiguous in the extracted text, which reads as 121 in places.

**Correction:** The rendered page and the displayed arithmetic identify the example as $\gcd(123,45)=3=45\cdot11-123\cdot4$.

**Reason:** The alternative reading is arithmetically false, whereas the chosen reading matches every Euclidean step on the page.

**Implemented in:** `chapters/chapter-1-divisibility-and-primes.tex`.

### Correction G.05 - package-wide: Compilation setup - no LaTeX preamble was supplied

**Category:** Compilation setup

**Issue:** The uploaded materials contain the scanned notes and the review skill, but no original .tex or .sty preamble.

**Correction:** The source PDF and skill are preserved byte-for-byte; a new, self-contained working package mat4003-preamble.sty was created. A README in preamble/ records that no original preamble existed.

**Reason:** It would be inaccurate to claim an original preamble was preserved or baseline-compiled.

**Implemented in:** `mat4003-preamble.sty; preamble/README_no_original_preamble.txt; Validation_report.txt`.

### Correction C1.01 - source PDF p. 7: Mathematical - division algorithm existence set

**Category:** Mathematical

**Issue:** The handwritten proof takes the quotient parameter from the natural numbers. For negative dividends this can make the set of nonnegative remainders empty.

**Correction:** The set is defined with $q\in\mathbb Z$, and nonemptiness is proved by choosing $q$ sufficiently negative.

**Reason:** The well-ordering argument can begin only after the set is known to be nonempty for every integer dividend.

**Implemented in:** `chapters/chapter-1-divisibility-and-primes.tex`.

### Correction C1.02 - source PDF pp. 8-9: Mathematical - Bezout remainder bound

**Category:** Mathematical

**Issue:** The proof divides $a$ by the least positive linear combination $d$ but uses an inconsistent remainder bound.

**Correction:** It now writes $a=dq+r$ with $0\le r<d$, observes that $r$ is another integer linear combination, and forces $r=0$ by minimality; the same is done for $b$.

**Reason:** The contradiction requires comparison with the least positive element $d$, not with $a$.

**Implemented in:** `chapters/chapter-1-divisibility-and-primes.tex`.

### Correction C1.03 - source PDF p. 11: Mathematical - Euclidean-step lemma

**Category:** Mathematical

**Issue:** The source proof introduces unrelated gcd and Bezout variables and does not cleanly establish both divisibilities.

**Correction:** The proof is replaced by the exact statement that an integer divides both $a,b$ if and only if it divides both $a,b-aq=r$.

**Reason:** Equality of the common-divisor sets immediately gives equality of the gcds and avoids circular reasoning.

**Implemented in:** `chapters/chapter-1-divisibility-and-primes.tex`.

### Correction C1.04 - source PDF pp. 13-14: Mathematical - induction and uniqueness details

**Category:** Mathematical

**Issue:** The product version of Euclid's lemma and the uniqueness part of the fundamental theorem of arithmetic are only sketched.

**Correction:** The product lemma is stated as an induction on the number of factors, and the uniqueness proof explicitly matches a prime factor, reorders, cancels, and invokes the smallest-counterexample argument.

**Reason:** The original fragments omit the precise induction step and the reason cancellation yields a smaller counterexample.

**Implemented in:** `chapters/chapter-1-divisibility-and-primes.tex`.

### Correction C2.01 - source PDF p. 19: Mathematical - linear congruence solution count

**Category:** Mathematical

**Issue:** The source conflates the set of values $ax-mk$ with multiples of the gcd and does not justify the number of incongruent solutions.

**Correction:** The congruence is converted to $ax-my=b$; all solutions are $x=x_0+t(m/d)$, and $t=0,\ldots,d-1$ are shown to be exactly the $d$ classes modulo $m$.

**Reason:** Solvability and the class count are distinct claims and both require proof.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.02 - source PDF pp. 20-22: Mathematical - Chinese remainder uniqueness and theorem order

**Category:** Mathematical

**Issue:** The CRT uniqueness argument and the proof of Fermat's little theorem are presented out of dependency order; Fermat is called a direct corollary before Euler's theorem is proved.

**Correction:** A product-divisibility lemma proves CRT uniqueness, Euler's theorem is proved first, and Fermat's theorem is then derived as its prime-modulus case.

**Reason:** The revised order removes a forward dependency and makes the uniqueness modulus explicit.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.03 - source PDF pp. 23-24: Mathematical - Wilson theorem edge cases

**Category:** Mathematical

**Issue:** The inverse-pairing proof does not separate $p=2$, and the converse proof compresses the repeated-factor composite case.

**Correction:** The prime $2$ is handled directly. In the converse, $n=4$ is isolated; for $n=a^2$, $a\ge3$, the distinct factors $a$ and $2a$ in $(n-1)!$ show $a^2\mid(n-1)!$.

**Reason:** Without these cases the pairing or factor argument can double-count or use a factor outside the factorial.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.04 - source PDF p. 24: Mathematical - square root of -1 modulo a prime

**Category:** Mathematical

**Issue:** The sufficiency argument is compressed to an informal pairing statement.

**Correction:** For $p\equiv1\pmod4$, residues are paired by $u\leftrightarrow-u^{-1}$; absence of a fixed point would force $(p-1)!\equiv1\pmod p$, contradicting Wilson.

**Reason:** The fixed points of this involution are exactly the solutions of $u^2\equiv-1$.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.05 - source PDF pp. 26-27: Algorithmic - Miller-Rabin decision rule

**Category:** Algorithmic

**Issue:** The handwritten wording effectively treats a first occurrence of $1$ that is not followed by $-1$ as the failure condition. The correct condition concerns a $1$ not preceded by $-1$ in the squaring chain.

**Correction:** The algorithm is rewritten in standard bounded form: test $a^d$, square at most $s-1$ times, accept the base on $-1$, and reject on an early $1$ or on failure to reach $-1$. A gcd check is included.

**Reason:** Reversing 'preceded' and 'followed' changes the algorithm and can misclassify composites.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.06 - source PDF pp. 27-30: Mathematical - Rabin one-quarter bound

**Category:** Mathematical

**Issue:** The source proof contains unsupported permutation, order, and counting assertions and does not close all factorization cases.

**Correction:** The liar count is computed exactly in the cyclic unit groups of the prime-power factors and combined by CRT. Separate bounds cover at least three prime factors, two factors including the equal 2-adic exceptional case, and prime powers.

**Reason:** The probability claim requires a valid count for every odd composite, not only a generic case.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C2.07 - source PDF pp. 31-32: Mathematical - Hensel hypotheses and lift alternatives

**Category:** Mathematical

**Issue:** The source uses the lifting formula without consistently stating that $p$ is prime and $k\ge1$, and the singular case is abbreviated.

**Correction:** The simple-root theorem states all hypotheses and solves one linear congruence for the unique $t\pmod p$. The singular-root theorem proves that either all $p$ lifts work or none do according to $f(a)\pmod{p^{k+1}}$.

**Reason:** The derivative is invertible only under the prime/simple-root hypothesis, while the singular case has a different dichotomy.

**Implemented in:** `chapters/chapter-2-congruences.tex`.

### Correction C3.01 - source PDF p. 34: Mathematical - divisor parametrization for sigma_k

**Category:** Mathematical

**Issue:** The divisor decomposition in the source is written with ambiguous repeated divisor symbols.

**Correction:** For coprime $m,n$, each divisor of $mn$ is uniquely written $d_1d_2$ with $d_1\mid m$ and $d_2\mid n$, producing a genuine bijection and the product of two sums.

**Reason:** Multiplicativity depends on uniqueness of this decomposition.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.02 - source PDF p. 36: Mathematical - Gauss totient-sum partition

**Category:** Mathematical

**Issue:** The source's sets are indexed inconsistently by $d$ and $n/d$, obscuring the cardinality being counted.

**Correction:** The sets $S_d=\{x:1\le x\le n,\gcd(x,n)=d\}$ are used, and $x=dy$ gives a bijection with reduced residue classes modulo $n/d$.

**Reason:** The corrected indexing makes the partition disjoint and yields $|S_d|=\varphi(n/d)$.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.03 - source PDF p. 37: Mathematical - converse for even perfect numbers

**Category:** Mathematical

**Issue:** The handwritten converse jumps from the divisor-sum equation to the Mersenne form without fully excluding an extra odd factor.

**Correction:** Writing $n=2^kn_1$ gives $n_1=(2^{k+1}-1)n_2$. If $n_2>1$, the three distinct divisors $1,n_2,n_1$ contradict the required value of $\sigma(n_1)$; hence $n_2=1$ and the remaining odd factor is prime.

**Reason:** The extra-factor exclusion is the essential step in the Euclid-Euler converse.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.04 - source PDF pp. 40-41: Mathematical - inverse of a multiplicative function

**Category:** Mathematical

**Issue:** The source's double-sum proof double-counts terms and does not establish multiplicativity cleanly.

**Correction:** The inverse is defined recursively on prime powers to obtain a multiplicative candidate; convolution with the original function is then $I$ on every integer, and uniqueness identifies the candidate with $f^{-1}$.

**Reason:** This avoids the defective decomposition and uses the already-proved convolution theorem correctly.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.05 - source PDF pp. 45-47: Mathematical - infinite products and rearrangement

**Category:** Mathematical

**Issue:** The Euler-product and Dirichlet-series arguments rely on limiting and rearranging infinite sums without explicitly controlling the omitted terms.

**Correction:** Finite Euler products are compared with the zeta series by a tail bounded by $\sum_{n>N}n^{-\Re(s)}$. For Dirichlet series, absolute convergence of the double series is stated before regrouping by $ab=n$.

**Reason:** Conditional rearrangement is not valid in general; the absolute estimates are what justify both operations.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.06 - source PDF p. 48: Mathematical - probability language and squarefree error term

**Category:** Mathematical

**Issue:** A 'randomly selected positive integer' is not a uniform probability model, and the source does not control the floor errors with absolute values.

**Correction:** The claim is stated as natural density. The count is $Q(N)=N\sum_{d\le\sqrt N}\mu(d)/d^2+O(\sqrt N)$, and division by $N$ gives $1/\zeta(2)$.

**Reason:** Natural density is the precise limiting model, and the explicit error proves the limit.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C3.07 - source PDF pp. 49-50: Mathematical - domain and asymptotic for coprime pairs

**Category:** Mathematical

**Issue:** The source places pairs in $\mathbb R^2$ even though gcd is defined for integers, and its final error estimate is incomplete.

**Correction:** The set is corrected to integer lattice pairs $1\le a,b\le N$. Mobius inversion gives $A(N)=\sum_{d\le N}\mu(d)\lfloor N/d\rfloor^2$ and an $O((\log N)/N)$ normalized error.

**Reason:** The original domain is undefined, and the limit needs a summable quantitative bound.

**Implemented in:** `chapters/chapter-3-arithmetic-functions.tex`.

### Correction C4.01 - source PDF p. 54: Mathematical - Lagrange root bound factorization

**Category:** Mathematical

**Issue:** The source writes $f(x)=(x-x_0)g(x)$ from a modular root without specifying the coefficient field.

**Correction:** Polynomial division is performed in $\mathbb F_p[x]$, after which every root of $f$ is $x_0$ or a root of the degree-$n-1$ polynomial $g$.

**Reason:** An integer polynomial need not be divisible by $x-x_0$ in $\mathbb Z[x]$ merely because $x_0$ is a root modulo $p$.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.02 - source PDF pp. 55-56: Mathematical - exact root and order counts

**Category:** Mathematical

**Issue:** The source's degree-count proof and the passage from roots of $x^d-1$ to elements of exact order $d$ omit some set-counting details.

**Correction:** The complement factor is given its exact degree, yielding at least and at most $d$ roots. The counts $N_d$ are then compared with Gauss's identity $\sum_{d\mid p-1}\varphi(d)=p-1$ to rule out a missing order.

**Reason:** Both inequalities and the final nonzero argument are needed to prove existence of primitive roots modulo every prime.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.03 - source PDF p. 57: Mathematical - lifting from p to p^2

**Category:** Mathematical

**Issue:** The source proof is compressed around the two possible orders and the binomial expansion of $(g+p)^{p-1}$.

**Correction:** The order modulo $p^2$ is shown to be either $p-1$ or $p(p-1)$. If $g^{p-1}\equiv1\pmod{p^2}$, the first-order binomial term proves $(g+p)^{p-1}\not\equiv1$, so $g+p$ has full order.

**Reason:** This establishes the promised alternative without assuming the conclusion.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.04 - source PDF p. 58: Mathematical - lifting primitive roots to all p-powers

**Category:** Mathematical

**Issue:** The handwritten induction asserts that certain powers form a permutation and uses unsupported divisibility conclusions.

**Correction:** A valuation lemma proves $v_p(u^p-1)=v_p(u-1)+1$. Applied to $u=g^{p-1}$, it shows the order gains exactly one factor of $p$ at each lift.

**Reason:** The valuation identifies the exact obstruction and makes the induction rigorous.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.05 - source PDF p. 60: Mathematical - necessity in the classification of primitive-root moduli

**Category:** Mathematical

**Issue:** The phrase 'combining the theorems above' does not exclude all other moduli; in particular, a direct application to factors $4$ and $p^k$ would not cover every higher power of $2$.

**Correction:** Writing $m=2^\alpha n$, multiple odd prime-power factors are excluded by coprime decomposition. For $\alpha\ge3$, every unit already has exponent $\varphi(m)/2$; the case $4p^k$ is excluded separately.

**Reason:** The classification requires both construction for the listed forms and a complete necessity argument.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.06 - source PDF p. 61: Mathematical - power congruence criterion and count

**Category:** Mathematical

**Issue:** The index proof does not explicitly justify that a solution $x$ is a unit or why the number of index solutions equals the number of residue solutions.

**Correction:** Since $x^k$ is congruent to the unit $a$, $x$ is a unit. The problem becomes $kb\equiv\ell\pmod{\varphi(m)}$, which has exactly $d$ index classes and hence exactly $d$ unit classes under the primitive-root bijection.

**Reason:** The discrete logarithm is defined only on units, and the counting correspondence must be one-to-one.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C4.07 - source PDF pp. 64-65: Mathematical - RSA decryption for nonunits

**Category:** Mathematical

**Issue:** The source applies Euler's theorem directly to the message, which is invalid when the message shares a factor with $n=pq$.

**Correction:** Decryption is proved separately modulo $p$ and modulo $q$: a message is either zero or a unit in each field. CRT then gives $M^{ed}\equiv M\pmod n$ for every message representative.

**Reason:** Textbook RSA correctness does not require $\gcd(M,n)=1$, but the proof must handle the zero cases locally.

**Implemented in:** `chapters/chapter-4-primitive-roots.tex`.

### Correction C5.01 - source PDF p. 68: Mathematical - parity formula in Gauss's lemma

**Category:** Mathematical

**Issue:** The source's floor-sum calculation is difficult to follow and mixes least residues with their absolute representatives.

**Correction:** The residues are written $ka=pq_k+r_k$; those above $p/2$ are reflected, and comparison of the two sums modulo $2$ gives $n\equiv\sum q_k$.

**Reason:** Separating the least residues from the reflected permutation is necessary for the parity count.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.02 - source PDF p. 70: Mathematical - lattice line in quadratic reciprocity

**Category:** Mathematical

**Issue:** The geometry uses the line with the coefficients interchanged in one formulation.

**Correction:** The line is written $qy=px$, so the two floor sums count the lattice points on its two sides in the stated rectangle.

**Reason:** The first floor sum represents $y<px/q$; therefore the boundary equation must be $qy=px$.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.03 - source PDF p. 72: Mathematical - missing oddness hypothesis for powers of 2

**Category:** Mathematical

**Issue:** The statement says $x^2\equiv a\pmod{2^k}$ is solvable exactly when $a\equiv1\pmod8$ for arbitrary $a$. This is false for even squares, which may be $0$ or $4$ modulo $8$.

**Correction:** The theorem now assumes $a$ is odd. The induction compares the two candidate lifts $x_0$ and $x_0+2^{k-1}$ modulo $2^{k+1}$.

**Reason:** The criterion $a\equiv1\pmod8$ characterizes odd unit squares, not all residues.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.04 - source PDF pp. 74-75: Mathematical - Jacobi supplementary and reciprocity exponents

**Category:** Mathematical

**Issue:** The source multiplies prime-level formulas but does not clearly account for repeated prime factors or combine the parity exponents.

**Correction:** The two parity identities are stated as Lemma 5.13 and used to combine all prime-factor contributions, including multiplicities.

**Reason:** Jacobi symbols use prime powers in the denominator, so the exponent bookkeeping cannot assume distinct factors.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.05 - source PDF pp. 78-79: Mathematical - circular Carmichael argument

**Category:** Mathematical

**Issue:** The proof of the Euler-witness lemma invokes squarefreeness as a 'conclusion below' before establishing it and does not prove the divisibilities $q_i-1\mid n-1$.

**Correction:** Assuming every base is a liar first implies the Carmichael congruence. A CRT-selected unit of primitive order modulo $p^2$ proves squarefreeness; CRT-selected primitive roots modulo each $q_i$ then prove $q_i-1\mid n-1$.

**Reason:** The reordered proof removes the circular dependency and supplies the order argument used later.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.06 - source PDF p. 79: Mathematical - CRT choice must remain a unit modulo n

**Category:** Mathematical

**Issue:** Choosing only a primitive root modulo $p^2$ does not by itself describe the residues at the other prime-power factors.

**Correction:** The chosen integer is required to be primitive modulo $p^2$ and congruent to $1$ at every other prime-power factor, so it is a unit modulo all of $n$.

**Reason:** The universal Carmichael congruence applies only to units.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C5.07 - source PDF pp. 78-79: Mathematical - liar bound via a homomorphism

**Category:** Mathematical

**Issue:** The source's multiplication-map argument does not establish closure, image size, or the exact relation between liars and the map.

**Correction:** The map $\Psi(b)=(b/n)b^{-(n-1)/2}$ on the unit group is a homomorphism. Euler liars are exactly its kernel, and the witness lemma makes the map nontrivial, so the kernel has index at least two.

**Reason:** The kernel theorem gives the half bound with no unproved counting assumptions.

**Implemented in:** `chapters/chapter-5-quadratic-residues.tex`.

### Correction C6.01 - source PDF p. 80: Mathematical - Euclidean induction termination

**Category:** Mathematical

**Issue:** The rational continued-fraction proof assumes a nonzero remainder and omits the exact-division case.

**Correction:** If the remainder is zero, the expansion is the one-term fraction $[a_0]$; otherwise induction continues with the smaller positive denominator.

**Reason:** Without the base branch the construction does not cover integers.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.02 - source PDF p. 81: Mathematical - finite representation edge cases

**Category:** Mathematical

**Issue:** The source says every rational has exactly two finite representations and exactly one ends in an entry greater than $1$, without treating one-term integer expansions such as $0$ or $1$.

**Correction:** The two-representation rule is stated for nonintegral rationals. Integers are recorded separately as $[a_0]=[a_0-1;1]$, with the one-term expansion taken as canonical.

**Reason:** The unqualified terminal-entry claim has small but genuine integer exceptions.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.03 - source PDF pp. 81-82: Mathematical - uniqueness of finite expansions

**Category:** Mathematical

**Issue:** The backward-induction proof in the source does not cleanly establish simultaneous termination or exclude the terminal-one ambiguity.

**Correction:** After requiring final entries greater than $1$, equality determines the integer part and then the reciprocal tail at every step; the tails terminate together.

**Reason:** The floor-and-tail recursion is the invariant that makes uniqueness rigorous.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.04 - source PDF pp. 84-85: Mathematical - convergence and irrationality

**Category:** Mathematical

**Issue:** The source invokes monotone convergence and a rational contradiction without explicitly proving that denominators grow unbounded or giving the lower bound for a nonzero rational numerator.

**Correction:** The recurrences give unbounded positive $q_k$; adjacent convergents differ by $1/(q_kq_{k+1})$. If the limit were $p/q$, then $|pq_k-qp_k|\ge1$ contradicts the adjacent upper bound.

**Reason:** Both the common limit and the irrationality conclusion depend on these quantitative estimates.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.05 - source PDF p. 87: Mathematical - best-approximation theorem

**Category:** Mathematical

**Issue:** The source's sign argument uses coefficients introduced without a complete justification and leaves cases unresolved.

**Correction:** The unimodular pair $(p_k,q_k),(p_{k+1},q_{k+1})$ uniquely expresses $(a,b)$. The bound $b<q_{k+1}$ forces opposite coefficient signs, while consecutive approximation errors also have opposite signs, giving the desired absolute-value inequality.

**Reason:** The theorem is stronger than a distance comparison and needs the determinant and sign structure explicitly.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.06 - source PDF p. 88: Mathematical - Legendre's convergent criterion

**Category:** Mathematical

**Issue:** The contradiction in the handwritten proof skips the distinct-reduced-fraction lower bound and the final inequality comparison.

**Correction:** A denominator interval $q_k\le b<q_{k+1}$ is chosen, Theorem 6.12 gives an error bound, and $|a/b-p_k/q_k|\ge1/(bq_k)$ contradicts the sum of the two strict approximation bounds.

**Reason:** The determinant lower bound is what forces the rational approximation to be a convergent.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.07 - source PDF pp. 89-90: Mathematical - both directions in the quadratic-irrational characterization

**Category:** Mathematical

**Issue:** The source proves the quadratic formula direction but not fully the converse, and the periodic-tail proof only shows 'rational or quadratic.'

**Correction:** For the converse, $(c\alpha-a)^2=d$ supplies an integer quadratic equation and nonsquare $d$ proves irrationality. For a periodic fraction, Theorem 6.9 rules out the rational alternative after the linear-fractional transformation.

**Reason:** An if-and-only-if statement and a quadratic-irrational conclusion both require explicit exclusion of rational values.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.08 - source PDF pp. 91-93: Mathematical - Lagrange periodicity proof

**Category:** Mathematical

**Issue:** The source asserts boundedness of the standard-form parameters after several unproved sign and integrality steps.

**Correction:** The initial form is obtained by scaling the radicand by a square so that $Q_0\mid D-P_0^2$. The conjugated finite-tail formula shows $x_k^*<0$ eventually, which yields $Q_k>0$, $|P_k|<\sqrt D$, and finitely many pairs $(P_k,Q_k)$.

**Reason:** Repetition follows only after the integer recurrence and finite-state bound have both been established.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C6.09 - source PDF pp. 94-95: Mathematical - reduced iff purely periodic

**Category:** Mathematical

**Issue:** The source does not rigorously propagate a repeated complete quotient backward, and its converse does not locate the conjugate root precisely.

**Correction:** A reduced quotient is shown to have the unique reduced predecessor determined by $a=\lfloor-1/y^*\rfloor$, so repetition reaches the initial quotient. Conversely the period polynomial has opposite signs at $-1$ and $0$, placing the conjugate in $(-1,0)$.

**Reason:** Eventual periodicity alone is weaker than pure periodicity, and reducedness requires the exact conjugate interval.

**Implemented in:** `chapters/chapter-6-continued-fractions.tex`.

### Correction C7.01 - source PDF p. 97: Numbering - chapter mismatch

**Category:** Numbering

**Issue:** The Pell-equation definition is labelled Definition 6.1 on the first page of Chapter 7.

**Correction:** It is labelled Definition 7.1 in the corrected manuscript.

**Reason:** The original label conflicts with the continued-fraction chapter and breaks chapter-local numbering.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.02 - source PDF pp. 97-98: Mathematical - strict inequality in the approximation lemma

**Category:** Mathematical

**Issue:** The lemma allows $\alpha=0$ but immediately uses $x_0^2>\delta y_0^2$.

**Correction:** The proof observes that $\alpha=0$ would make $\sqrt\delta=x_0/y_0$ rational; hence $\alpha>0$ and the strict inequality is valid.

**Reason:** The displayed estimate divides by the positive difference and needs strict positivity.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.03 - source PDF p. 98: Mathematical - negative right-hand side in Pell approximation

**Category:** Mathematical

**Issue:** The source says the $n<0$ case follows directly but does not connect the reciprocal approximation to the convergents of $\sqrt d$.

**Correction:** The equation is rewritten as an approximation to $1/\sqrt d$, the fraction is reduced if necessary, Legendre's criterion is applied, and the leading-zero continued fraction shows that nonzero convergents are reciprocals.

**Reason:** The reciprocal step is essential and is not a formal consequence of the positive case alone.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.04 - source PDF pp. 99-100: Mathematical - locating all Pell solutions

**Category:** Mathematical

**Issue:** The source relies on the periodic $Q_i$ sequence without proving the exact occurrences of $Q_i=1$ or excluding $Q_i=-1$.

**Correction:** Reducedness gives $Q_i=1$ exactly at multiples of the least period and makes $Q_i=-1$ impossible. Combined with $p_k^2-dq_k^2=(-1)^{k+1}Q_{k+1}$, this yields all positive and negative Pell solutions with the correct parity of the period.

**Reason:** The sign and completeness claims depend on both facts about $Q_i$.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.05 - source PDF p. 101: Mathematical - fundamental solution generates all solutions

**Category:** Mathematical

**Issue:** The minimality proof in the source introduces coefficients without a complete inequality showing that a smaller solution results.

**Correction:** For any solution $\eta$, choose $n$ with $\varepsilon^n\le\eta<\varepsilon^{n+1}$ and set $\delta=\eta\varepsilon^{-n}$. Norm one gives integer coefficients; monotonicity of $z+z^{-1}$ on $[1,\infty)$ makes any positive irrational coefficient produce a solution with smaller $x$.

**Reason:** This closes the minimality contradiction and forces $\delta=1$.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.06 - source PDF p. 102: Mathematical - missing nonzero hypothesis in an infinitude application

**Category:** Mathematical

**Issue:** The statement 'if $x^2-dy^2=n$ has a solution, then it has infinitely many' is false for $n=0$ when the only stated solution may be $(0,0)$.

**Correction:** The application now assumes a nonzero integer solution before multiplying by the infinitely many norm-one Pell units.

**Reason:** Multiplying the zero solution never creates distinct solutions.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.07 - source PDF p. 103: Mathematical - Pythagorean parametrization

**Category:** Mathematical

**Issue:** The squarefree-factor argument in the source is compressed and obscures why two factors are coprime squares.

**Correction:** The proof factors $(z+x)/2$ and $(z-x)/2$, proves they are coprime, and concludes each is a square. The converse explicitly uses coprimality and opposite parity to obtain primitiveness.

**Reason:** Coprime product-is-a-square is the key step and must be applied to the correct integer factors.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.08 - source PDF p. 105: Mathematical - infinite-descent divisibility chains

**Category:** Mathematical

**Issue:** The two descent examples jump from congruences to divisibility of every variable without displaying the intermediate reductions.

**Correction:** For the system, $z^2+w^2\equiv0\pmod7$ first gives $7\mid z,w$, then the exact sum gives $7\mid x,y$. For $x^3+2y^3=4z^3$, successive reductions modulo $2$ show $2\mid x,y,z$ and recover the same equation after division.

**Reason:** A valid descent must construct an actual smaller solution of the identical system or equation.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.09 - source PDF p. 106: Mathematical - Fermat exponent four statement and descent

**Category:** Mathematical

**Issue:** The source theorem means 'no nontrivial solution,' but an unqualified 'no nonzero integer solution' would be false when one of $x,y$ is zero. The descent also omits the parity reason for choosing the even parameter and several coprime-square steps.

**Correction:** The statement now defines nontrivial as $xyz\ne0$ and proves the stronger positive equation. In the parametrization, $r$ cannot be even because then $x^2\equiv3\pmod4$; the remaining coprime factors are successively shown to be squares, producing a smaller hypotenuse.

**Reason:** The corrected wording excludes only the intended solutions, and the completed descent supplies the strict decrease.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C7.10 - source PDF p. 107: Mathematical - local obstruction for y^2=x^3+7

**Category:** Mathematical

**Issue:** After showing $x$ is odd, the source uses $x+2\equiv3\pmod4$ without deriving it.

**Correction:** The case $x\equiv3\pmod4$ makes the right side $2\pmod4$, so $x\equiv1\pmod4$ and $x+2\equiv3\pmod4$. A prime $p\equiv3\pmod4$ then divides $x+2$ to odd order and would make $-1$ a square modulo $p$.

**Reason:** The missing congruence is what guarantees the required prime factor.

**Implemented in:** `chapters/chapter-7-diophantine-equations.tex`.

### Correction C8.01 - source PDF p. 108: Mathematical - omitted proofs for roots of unity and Mobius sums

**Category:** Mathematical

**Issue:** The final chapter lists the root and sum statements without proofs.

**Correction:** Distinct powers of a primitive root are counted, the exact-order condition is proved by the order formula, and the sum over exact orders is inverted to obtain $f(n)=\mu(n)$.

**Reason:** These are substantive results rather than definitions and need arguments to form complete notes.

**Implemented in:** `chapters/chapter-8-roots-of-unity.tex`.

### Correction C8.02 - source PDF p. 109: Mathematical - cyclotomic integrality and explicit formula

**Category:** Mathematical

**Issue:** The source states $\Phi_n\in\mathbb Z[x]$ and the Mobius product formula with no derivation.

**Correction:** Induction in the factorization $x^n-1=\prod_{d\mid n}\Phi_d(x)$ proves integrality using monic polynomial division. Multiplicative Mobius inversion in $\mathbb C(x)^\times$ gives the explicit product.

**Reason:** The negative exponents in the formal product and the integer-coefficient conclusion both require justification.

**Implemented in:** `chapters/chapter-8-roots-of-unity.tex`.

## Grouped grammatical, notational, and LaTeX repairs

- Standardized names and capitalization, including Bezout/Bézout, Euclidean, Diophantine, Carmichael, Hensel, Möbius, Riemann, Dirichlet, Lagrange, Jacobi, Pythagorean, Miller--Rabin, Solovay--Strassen, and Chinese remainder theorem.
- Replaced sentence fragments and OCR-like shorthand with complete mathematical prose; expanded `WLOG`, `s.t.`, and unsupported “trivial/similar” transitions where an argument was required.
- Standardized `\gcd`, `\operatorname{lcm}`, order, index, floor functions, congruence notation, interval endpoints, residue-class terminology, and domains/codomains.
- Corrected repeated spelling errors such as “Arimetic,” “Primitire,” “Nonliear,” “remaindar,” and “congruenas,” while preserving the mathematical voice and source order.
- Replaced Unicode/OCR lookalikes by LaTeX commands and balanced every delimiter, exponent, subscript, product, and summation bound against the rendered page.
- Added punctuation around displays and consistent theorem, definition, corollary, lemma, remark, and application headings.
- Created a compilation-safe preamble because no original preamble was provided; loaded only declared packages, added stable theorem environments and macros, corrected page-anchor/fancy-header warnings, and removed every temporary or unresolved marker.

**Substantive entries:** 58.
