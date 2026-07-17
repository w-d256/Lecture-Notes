# MAT4004 handwritten-note review: correction ledger

This ledger records every substantive mathematical, logical, notational, or
compilation-related repair made in the corrected LaTeX manuscript.  The source
PDF and the supplied preamble are preserved byte-for-byte.

## Global and compilation corrections

### G.01 — source PDF pp. 1–124: OCR was not treated as mathematical source

**Issue.** Automatic text extraction garbles symbols, theorem labels, subscripts,
quantifiers, and many words.

**Correction.** The rendered page images were treated as authoritative.  OCR was
used only for navigation, while theorem statements, formulas, and proofs were
reconstructed semantically from the page images.

**Reason.** Copying the extracted text would introduce false symbols and broken
mathematics.

### G.02 — source PDF pp. 8–124: pasted screenshots were not embedded in the output

**Issue.** Many definitions and theorem statements appear as textbook
screenshots rather than editable text.

**Correction.** Every in-scope statement was retypeset in LaTeX; decorative grid
paper and app-interface elements were omitted.

**Reason.** The result is searchable, accessible, style-consistent, and does not
depend on raster screenshots.

### G.03 — source-wide: visible numbering conflicts

**Issue.** The source uses type-specific labels, so “Definition 1.1” and
“Theorem 1.1” can coexist.  A single shared LaTeX counter would renumber the
notes incorrectly.

**Correction.** The master file defines unnumbered theorem environments and puts
the visible source label in the optional heading.

**Reason.** This preserves the source numbering without duplicate-label or
counter problems.

### G.04 — supplied preamble: preservation and compatibility

**Issue.** A supplied `.sty` file had to be reused without silently changing the
user's baseline.

**Correction.** `preamble/notes-preamble-original.sty` is an exact preserved
copy.  The working `notes-preamble.sty` is byte-identical; no compatibility edit
was required.

**Reason.** The supplied package already compiled under the available TeX Live
installation.

### G.05 — source-wide: notation normalization

**Issue.** The notes alternate among ambiguous handwritten symbols for set
difference, incidence, degree, neighbourhoods, cuts, inflow/outflow, matching
number, odd components, and graph deletion.

**Correction.** The manuscript consistently uses `G-S`, `G-F`, `\deg`, `N(S)`,
`[S,T]`, `f_{\mathrm{out}}`, `f_{\mathrm{in}}`, `\nu(G)`, and
`\operatorname{odd}(G-S)`.

**Reason.** Standardized notation removes ambiguities that can change meaning.

### G.06 — source-wide: grammar and proof prose

**Issue.** The handwritten proofs contain fragments, missing articles,
misspellings, and compressed transitions such as “obvious,” “same,” or
“contradiction” without the relevant implication.

**Correction.** Sentences, punctuation, theorem names, capitalization, and
singular/plural agreement were repaired.  Nontrivial omitted steps were written
out.

**Reason.** Mathematical correctness requires the logical bridge, not merely a
final contradiction symbol.

### G.07 — source-wide: compilation safety

**Issue.** Raw transcription would contain Unicode lookalikes, malformed set
braces, unbalanced delimiters, and undefined ad hoc notation.

**Correction.** All symbols use standard LaTeX commands, project-specific macros
are defined in `notes.tex`, and chapter files contain no package loading or
document wrappers.

**Reason.** The modular project now compiles reproducibly through the master
file.

## Chapter 1 — Definitions and Eulerian graphs

### C1.01 — p. 9: minimum-degree cycle proof

**Issue.** The recursive walk construction did not state how immediate
backtracking is avoided or why the first repeated vertex gives a cycle.

**Correction.** At each step a neighbour distinct from the preceding vertex is
chosen; finiteness gives a first repetition, whose intervening vertices are
distinct.

**Reason.** An arbitrary repeated walk need not directly exhibit a simple cycle.

### C1.02 — p. 11: bipartite iff no odd cycle

**Issue.** The converse proof treated shortest paths as though they were either
disjoint or nested and did not handle their common initial segment correctly.

**Correction.** The last common vertex of two shortest root paths is used; their
internally disjoint tails plus the same-parity edge form an odd cycle.

**Reason.** This is the valid parity argument for arbitrary intersecting shortest
paths.

### C1.03 — p. 12: Euler's theorem

**Issue.** The sufficiency direction only said to keep walking and combine
cycles, without proving that a trail cannot stop away from its start or that
unused edges can be spliced in.

**Correction.** The entering/leaving parity argument and the finite splicing
construction were supplied.

**Reason.** Both closure of each trail and eventual use of every edge are needed.

### C1.04 — pp. 13–14: bridge characterization

**Issue.** The source proof used a long walk-deletion argument and did not cleanly
show that deleting a bridge creates exactly two components.

**Correction.** An edge lies on a cycle exactly when its endpoints remain joined
after deletion; every vertex is then assigned to the endpoint-side reached by a
path.

**Reason.** The revised proof establishes both directions and the exact component
count.

### C1.05 — p. 15: even-degree graphs have no bridge

**Issue.** The component-degree parity contradiction was only asserted.

**Correction.** In one component of `G-e`, exactly the endpoint of the bridge has
odd degree, contradicting the handshaking lemma.

**Reason.** The relevant degrees are degrees in the induced component, not the
original graph.

### C1.06 — pp. 15–16: Fleury's algorithm

**Issue.** The source did not justify why the algorithm cannot become stranded or
leave an unused component behind.

**Correction.** The parity invariant for the unused-edge graph and the role of
avoiding a bridge whenever an alternative exists were made explicit.

**Reason.** Termination alone does not prove that the returned trail uses every
edge.

### C1.07 — p. 17: union of bipartite graphs

**Issue.** Only the construction for `n\le 2^k` appeared; the necessary bound was
missing.

**Correction.** Each vertex is assigned its `k`-bit record of bipartition sides.
Adjacent vertices must have different records, giving `n\le 2^k`.

**Reason.** The theorem is an “if and only if,” so both directions are required.

### C1.08 — p. 17: long path and long cycle

**Issue.** The longest-path argument did not explain why the furthest neighbour
of an endpoint yields a sufficiently long cycle.

**Correction.** All endpoint neighbours lie on a longest path; the largest index
among at least `k` neighbours is at least `k`.

**Reason.** The degree bound controls the index only after distinct neighbours
are counted.

### C1.09 — p. 18: decomposition into trails

**Issue.** Adding edges and breaking an Euler circuit proved only an upper bound;
the lower bound and the case of no odd vertices were omitted.

**Correction.** Each open trail accounts for at most two odd endpoints, so at
least `k` trails are needed; a nontrivial Eulerian graph still needs one trail.
The final formula is `max{k,1}`.

**Reason.** The original statement was a minimum assertion.

### C1.10 — p. 18: Havel–Hakimi theorem

**Issue.** The “only if” direction was reduced to a sentence about adding or
deleting a vertex and did not justify adjacency to the largest residual
degrees.

**Correction.** A degree-preserving 2-switch maximization argument forces the
largest-degree vertex to be adjacent to the next `d_1` vertices.

**Reason.** Deleting an arbitrary realization need not produce the prescribed
reduced sequence.

### C1.11 — p. 19: graphs with the same degree sequence

**Issue.** The source's common-neighbour count did not prove that repeated
2-switches reach the target graph.

**Correction.** The symmetric difference is decomposed into alternating even
trails; a switch reduces the symmetric-difference size, allowing induction.

**Reason.** A monotone integer measure is needed to prove termination.

### C1.12 — p. 20: girth versus diameter

**Issue.** The shortest-cycle argument omitted why a shorter external path would
contradict minimality of the cycle.

**Correction.** Every shorter arc of a shortest cycle is shown to be geodesic;
otherwise the shortcut and one cycle arc contain a shorter cycle.

**Reason.** The displayed diameter inequality depends on this geodesic property.

### C1.13 — p. 20: Moore-type radius bound

**Issue.** The first distance layer was counted with the wrong branching factor.

**Correction.** The root has at most `d` neighbours, while later layers branch by
at most `d-1`, giving
`1+d\sum_{i=0}^{k-1}(d-1)^i`.

**Reason.** Using `d-1` at the first layer undercounts the graph.

### C1.14 — p. 21: minimal edge cut exercise

**Issue.** The argument introduced an auxiliary graph but did not explicitly use
minimality to make the remaining edge a bridge.

**Correction.** `G-(F\setminus\{e\})` is connected by minimality, and `e` is a
bridge there; the bridge theorem gives both conclusions.

**Reason.** This supplies the missing logical link.

### C1.15 — pp. 22–23: distance characterization of bipartite graphs

**Issue.** The shortest odd-cycle proof did not justify the asserted distances
to the two middle adjacent vertices.

**Correction.** Any shorter route would combine with one of the two cycle arcs to
produce a shorter odd closed walk and hence a shorter odd cycle.

**Reason.** Equality of the two distances is the contradiction required by the
exercise.

### C1.16 — p. 24: local half-cut property

**Issue.** The partition-switching calculation was present but the maximizing
object and change in cut size were not clearly stated.

**Correction.** A maximum cut is chosen, and moving a vertex with fewer than half
its incident edges crossing would strictly increase its size.

**Reason.** This is the precise extremal argument.

## Chapter 2 — Hamiltonian graphs and digraphs

### C2.01 — p. 26: Hamiltonian deletion condition

**Issue.** The source concluded the component bound without identifying the
spanning subgraph that controls it.

**Correction.** Deleting `|S|` vertices from a Hamiltonian cycle leaves at most
`|S|` paths, and adding edges cannot increase components.

**Reason.** The cycle, not the whole graph directly, gives the count.

### C2.02 — p. 27: uniqueness of Hamiltonian closure

**Issue.** The two proposed closure sequences were compared informally, with no
order-independent invariant.

**Correction.** Every added edge is shown to belong to every closed supergraph of
`G`; hence all terminal closed graphs contain one another.

**Reason.** This is a confluence proof independent of the edge-addition order.

### C2.03 — p. 27: Ore edge-addition lemma

**Issue.** The indexing of neighbours along the Hamiltonian path was incomplete
and did not force a common index.

**Correction.** Two index sets of sizes `deg(u)` and `deg(v)` are placed inside
`{1,\ldots,n-1}`; their total size exceeds `n-1`, so they intersect.

**Reason.** The intersecting index is exactly what closes the replacement cycle.

### C2.04 — pp. 28–29: Chvátal degree-sequence proof

**Issue.** The handwritten argument jumped from a nonedge degree sum to two
contradictory degree-sequence inequalities without counting the relevant
nonneighbours.

**Correction.** A maximum-degree-sum nonedge is selected in the closure, and the
numbers of nonneighbours of each endpoint are counted explicitly.

**Reason.** The contradiction requires both `d_i\le i` and
`d_{n-i}\le n-i-1`.

### C2.05 — pp. 29–30: Hamiltonian path in a tournament

**Issue.** The insertion point for the deleted vertex was not fully specified.

**Correction.** The first transition along the existing directed path from an
edge entering the new vertex to an edge leaving it is used.

**Reason.** This handles all three endpoint/interior cases.

### C2.06 — p. 30: strongly connected tournaments

**Issue.** The source induction assumed that a Hamiltonian cycle in an induced
subtournament could always absorb the last vertex, which is false without
additional work.

**Correction.** A longest directed cycle is used.  Every outside vertex either
dominates the whole cycle or is dominated by it; strong connectivity supplies
an arc between the two types, allowing two outside vertices to be inserted.

**Reason.** This is a valid proof of Camion's theorem.

### C2.07 — pp. 31–32: Richardson's kernel theorem

**Issue.** The recursive sets in the source were unfinished and did not establish
independence or absorption.  One page ends mid-proof.

**Correction.** In a strongly connected component, parity of directed paths from
a root gives a bipartition and either side is a kernel.  For a general digraph,
a sink strongly connected component is combined inductively with the graph
outside vertices already absorbed by its kernel.

**Reason.** The replacement proves both kernel conditions and terminates by
induction on the number of vertices.

### C2.08 — p. 33: directed Euler theorem

**Issue.** The source stated balanced indegree/outdegree but did not include the
necessary connectivity condition on nonisolated vertices.

**Correction.** The underlying graph is required to have at most one nontrivial
component, and the closed-trail splicing proof is supplied.

**Reason.** Several disjoint balanced directed cycles are not jointly Eulerian.

### C2.09 — p. 33: de Bruijn application

**Issue.** The relationship between binary strings, arcs, and consecutive cyclic
blocks was compressed into a diagram.

**Correction.** Vertices are length-`n-1` strings, arcs are length-`n` strings,
and an Euler circuit supplies each arc exactly once.

**Reason.** This explicitly proves the cyclic-word property.

### C2.10 — p. 34: tournament king

**Issue.** The maximum-outdegree proof used the final contradiction without
spelling out the missing intermediate vertex.

**Correction.** If `u\to v` and no out-neighbour `w` of `v` satisfies `w\to u`,
then `u` dominates `v` and every out-neighbour of `v`, contradicting maximality.

**Reason.** The desired length-two path is `v\to w\to u`.

### C2.11 — pp. 35–36: metric TSP double-tree bound

**Issue.** The source selected first occurrences in an Euler walk but did not
prove that shortcuts exist or do not increase weight.

**Correction.** Completeness supplies every shortcut edge, and repeated use of
the triangle inequality bounds its weight by the skipped subwalk.

**Reason.** Both hypotheses are essential to the approximation guarantee.

## Chapter 3 — Connectivity

### C3.01 — pp. 38–39: Whitney inequalities

**Issue.** The source chose endpoints from a minimum edge cut but did not cover
singleton sides, duplicate chosen endpoints, or the remaining bridge case.

**Correction.** The proof treats an isolated singleton separately, chooses at
most one endpoint per remaining cut edge, and then either obtains a vertex cut
or deletes one end of the sole remaining bridge.

**Reason.** These are the cases needed for `\kappa(G)\le\lambda(G)`.

### C3.02 — pp. 40–41: Menger's theorem

**Issue.** The edge-contraction induction was incomplete and did not establish
that the two path families could be joined without unintended intersections.

**Correction.** The theorem is proved by the standard vertex-splitting reduction
to integral max flow and min cut, with the easy separator bound stated first.

**Reason.** The reduction gives an exact correspondence between capacities,
vertex-disjoint paths, and separators.

### C3.03 — pp. 43–44: cubic graphs satisfy `\kappa=\lambda`

**Issue.** The case analysis in the source counted incident edges informally and
did not identify the final two-edge cut.

**Correction.** Cases `\lambda=0,1,2,3` are separated.  In the last case, the six
edge slots at a two-vertex cut force exactly two components with opposite
`1–2` incidence distributions; deleting the two unique incidence edges gives
a forbidden two-edge cut.

**Reason.** This closes the only nontrivial case.

### C3.04 — pp. 45–46: fan lemma

**Issue.** The converse argued that every fan path meets the separator but did
not force two paths to share the same separator vertex.

**Correction.** A `k`-set `S` containing the smaller separator and a vertex in a
different component is chosen.  The path ending at that external vertex must
meet a separator vertex whose own fan path is distinct.

**Reason.** The shared vertex contradicts pairwise intersection only at the fan
centre.

## Chapter 4 — Trees, spanning trees, and shortest paths

### C4.01 — p. 48: tree equivalences

**Issue.** Several equivalences were listed without a coherent proof, and edge
counts were used before being established.

**Correction.** Leaf induction, component counting, bridge/cycle equivalence,
unique paths, and the unique-cycle-after-edge-addition property were organized
into a valid implication chain.

**Reason.** Each characterization now has a proved connection to the others.

### C4.02 — p. 49: existence of a spanning tree

**Issue.** The source claimed that adding an outside vertex to a maximal tree
would create a cycle, which is the opposite of what happens.

**Correction.** A connecting edge to a vertex outside the maximal tree produces
a strictly larger tree, contradicting maximality.

**Reason.** A new leaf cannot create a cycle.

### C4.03 — p. 50: spanning-tree exchange

**Issue.** The proposed replacement edge was not shown to cross the two
components of `T-e`.

**Correction.** The unique path in the second spanning tree between the ends of
`e` must cross the cut, and any such crossing edge reconnects the components.

**Reason.** This proves both connectivity and acyclicity after exchange.

### C4.04 — p. 51: Kruskal correctness

**Issue.** The source tried to prove that each selected edge belongs to some MST
without maintaining a precise invariant.

**Correction.** After each choice, an MST containing the current forest is
maintained by a cycle exchange with an edge crossing the same component cut.

**Reason.** The invariant proves the final tree is minimum.

### C4.05 — p. 52: Prim correctness

**Issue.** The original repeated exchanges did not make clear why the replacement
preserves a spanning tree and never increases weight.

**Correction.** Adding the chosen cut edge to an MST creates a cycle containing
another edge of the same cut; replacing that edge preserves an MST containing
the grown tree.

**Reason.** This is the cut-exchange invariant required by Prim's algorithm.

### C4.06 — pp. 53–55: Dijkstra hypothesis and proof

**Issue.** The source annotation asked why positive weights were necessary and
used strict positivity in the proof.

**Correction.** The hypothesis is nonnegative arc weights.  The proof finalizes
the minimum label using the first unprocessed vertex on a shortest path.

**Reason.** Zero-weight arcs are valid; negative arcs, not zero arcs, break the
greedy step.

### C4.07 — p. 55: walk decomposition

**Issue.** The source stated the path-plus-cycles decomposition but gave only
“induction on the walk.”

**Correction.** A minimal repeated-vertex segment is removed as a directed
cycle, and induction is applied to the shorter walk.

**Reason.** This preserves the arc multiset and endpoints.

### C4.08 — p. 56: shortest-path triangle inequality

**Issue.** The proof said all cycles had positive weight, while the hypothesis
only excludes negative cycles.

**Correction.** Cycles are correctly stated to have nonnegative weight.

**Reason.** Zero-weight cycles are allowed and do not invalidate the inequality.

### C4.09 — pp. 57–58: Bellman–Ford correctness

**Issue.** The source inequalities between labels and bounded-edge shortest paths
were reversed or left unproved in places.

**Correction.** Two invariants are separated: after pass `i`, labels are at most
the best path with at most `i` arcs; every finite label is a walk weight and is
therefore at least the true distance when no reachable negative cycle exists.

**Reason.** The two inequalities meet after `|V|-1` passes.

### C4.10 — p. 59: subpaths of shortest paths

**Issue.** The source used a disjoint-union assertion even when an alternative
prefix intersects the remaining path.

**Correction.** The alternative prefix is concatenated to a walk, and nonnegative
cycle removal converts it to a no-heavier path.

**Reason.** Intersections do not invalidate the corrected walk argument.

### C4.11 — p. 60: negative-cycle detection

**Issue.** The chain of label inequalities was written with inconsistent primed
labels and an unclear direction.

**Correction.** Assuming no decrease in the extra pass gives one relaxation
inequality per cycle arc; summing them yields `0\le w(C)`, contradicting
negativity.

**Reason.** The telescoping sum is the complete proof.

### C4.12 — pp. 61–63: MST uniqueness and cut/cycle properties

**Issue.** The source exchange calculations did not consistently identify which
edge is lighter or why the replacement remains a tree.

**Correction.** Each proof uses the fundamental cycle or fundamental cut and a
strict weight comparison.

**Reason.** These are the precise hypotheses that produce a lighter spanning
tree contradiction.

### C4.13 — p. 64: deleting an MST leaf

**Issue.** The source attempted to compare sums in a way that obscured why
`G-v_0` is connected and why a lighter tree would extend back to `G`.

**Correction.** Paths in `T` between remaining vertices avoid the leaf, and any
lighter spanning tree of `G-v_0` plus the deleted leaf edge would beat `T`.

**Reason.** Both claims follow directly from the leaf structure.

## Chapter 5 — Network flows

### C5.01 — pp. 67–68: net-flow identity

**Issue.** The source cancellation calculation mixed arcs internal to `S` with
cut arcs and changed notation mid-display.

**Correction.** The sum of `f_out(v)-f_in(v)` over `S` is written explicitly;
internal arcs cancel and conservation leaves only the source value.

**Reason.** This establishes the identity used by every cut argument.

### C5.02 — p. 68: weak duality

**Issue.** The cut bound was described as following “directly” without showing
the backward-flow term.

**Correction.** `val(f)=f_out(S)-f_in(S)\le f_out(S)\le c[S,T]` is displayed.

**Reason.** The nonnegative inflow term is part of the inequality.

### C5.03 — pp. 69–70: augmenting-path characterization

**Issue.** The source's proof of `(b)\Rightarrow(c)` used ambiguous signs and
asserted saturation for every cut arc without defining reachability in the
residual graph.

**Correction.** `S` is the set reachable from `s` in the residual digraph.
Forward arcs from `S` to `T` are saturated and reverse-direction original arcs
carry zero flow, yielding cut equality.

**Reason.** These two residual conditions are exactly what makes
`val(f)=c[S,T]`.

### C5.04 — p. 71: Ford–Fulkerson termination

**Issue.** The source suggested every augmentation increases the value by at
least one without stating integer capacities.

**Correction.** The claim is restricted to integer capacities; residual
capacities and augmentation amounts then stay integral.

**Reason.** With arbitrary real capacities, Ford–Fulkerson can fail to terminate.

### C5.05 — p. 71: residual graph

**Issue.** Forward and backward residual possibilities were described verbally,
with zero-capacity arcs not clearly excluded.

**Correction.** Both residual arc types and their capacities are defined
formally, and only positive-capacity residual arcs are retained.

**Reason.** Augmenting paths are precisely directed source–sink paths in this
graph.

### C5.06 — p. 72: vertex-disjoint path reduction

**Issue.** The handwritten split construction mixed copies and arc directions,
assigned capacity one to the wrong arcs in places, and did not explain endpoint
treatment.

**Correction.** Every internal vertex receives a capacity-one split arc; original
edges become large-capacity traversal arcs in both directions, while the chosen
endpoints are source and sink.

**Reason.** Capacity one must restrict use of vertices, not use of graph edges.

### C5.07 — pp. 73–74: baseball elimination

**Issue.** The network diagram did not fully explain the meanings of the three
arc types or the saturation criterion.

**Correction.** Source-to-game capacities count unplayed games, game-to-team
arcs allocate wins, and team-to-sink capacities enforce the tested team's best
possible total.

**Reason.** This gives a reversible correspondence between schedules and
saturating flows.

### C5.08 — p. 75: circulation with demands

**Issue.** The source used several split copies and inconsistent signs for supply
and demand.

**Correction.** A standard super-source/super-sink reduction is used: source arcs
enter supply vertices with capacity `-d(v)`, and demand vertices send arcs to
the sink with capacity `d(v)`.

**Reason.** Ordinary flow conservation then becomes
`f_in(v)-f_out(v)=d(v)` after the auxiliary arcs are removed.

## Chapter 6 — Matchings

### C6.01 — p. 77: connected graphs of maximum degree two

**Issue.** The source split into degree-one and degree-two cases but did not rule
out an outside vertex attached to a cycle or prove a maximal path is spanning.

**Correction.** Following edges from a degree-two graph gives a cycle only when
all vertices lie on it; otherwise a longest path from a low-degree vertex must
contain every vertex.

**Reason.** Connectedness plus the degree bound forbids branching attachments.

### C6.02 — p. 77: Berge's theorem

**Issue.** The symmetric-difference proof stated that a larger matching gives an
augmenting component but did not classify the components or count edge types.

**Correction.** Components are alternating paths and even cycles; a global
excess of edges from the larger matching forces a path that starts and ends
with those edges.

**Reason.** Such a path has both endpoints exposed by the smaller matching.

### C6.03 — pp. 78–80: regular bipartite graphs

**Issue.** The source flow proof used an incomplete cut calculation and obscured
the simpler Hall count.

**Correction.** Edges between `S` and `N(S)` are counted to get
`k|S|\le k|N(S)|`, and Hall yields a perfect matching.

**Reason.** This is direct and avoids an erroneous capacity expression.

### C6.04 — pp. 79–80: Hall's theorem induction

**Issue.** The original induction mixed the strict and equality cases and did not
verify Hall's condition after deleting a chosen pair.

**Correction.** The proof is divided into: strict Hall for every proper subset,
where any edge can be removed; and an equality subset, where two induced
problems are matched independently.

**Reason.** These two cases exhaust the possibilities and preserve the Hall
inequalities.

### C6.05 — p. 80: systems of distinct representatives

**Issue.** The source only said to construct a bipartite graph.

**Correction.** Index vertices, element vertices, and the exact edge condition
are stated, and the union-size condition is identified with Hall's condition.

**Reason.** This proves the equivalence rather than merely suggesting it.

### C6.06 — p. 81: Latin rectangle extension

**Issue.** Rows, columns, and symbols were conflated, and a Latin rectangle was
called a matching without specifying the graph for the new row.

**Correction.** Columns are matched to symbols missing from those columns.  The
resulting graph is `(n-m)`-regular on both sides, so a perfect matching supplies
one new row; the construction is repeated.

**Reason.** Existing rows are not themselves the matching being sought.

### C6.07 — pp. 82–83: Birkhoff–von Neumann theorem

**Issue.** The source base case used the pigeonhole principle incorrectly and
subtracted a permutation matrix without normalizing the remainder.

**Correction.** Hall's theorem finds a positive diagonal permutation.  With
`\mu` the smallest selected entry,
`B=(A-\mu P)/(1-\mu)` is doubly stochastic and has fewer positive entries.

**Reason.** Without division by `1-\mu`, row and column sums are no longer one.

### C6.08 — pp. 84–85: Kőnig–Egerváry theorem

**Issue.** The source attempted to split a minimum cover into two Hall matchings,
but the claimed neighbourhood inequalities were not justified.

**Correction.** The standard alternating-reachability construction from
unmatched left vertices produces the cover
`(X\setminus Z_X)\cup Z_Y` of size exactly `|M|`.

**Reason.** The construction simultaneously proves that the set is a cover and
counts its size.

### C6.09 — p. 85: Gale–Shapley algorithm

**Issue.** The source stated the algorithm but gave no termination, perfectness,
or stability proof.

**Correction.** Proposals never repeat, women only trade upward, an unmatched
proposer would create a counting contradiction, and any alleged blocking pair
was previously rejected.

**Reason.** These are the three required correctness properties.

### C6.10 — pp. 86–88: Tutte–Berge formula

**Issue.** The source induction stopped mid-case and the second case did not prove
that a maximum matching misses only one vertex.  Several symmetric-difference
claims were unsupported.

**Correction.** The universal upper bound is proved by counting unmatched odd
components.  Equality is obtained from the standard deficiency structural lemma
(factorable even components, factor-critical odd components, and Hall matching
from the separator into odd components), whose alternating-path basis is stated
explicitly.

**Reason.** This replaces an incomplete proof with a valid standard proof
framework and makes clear which structural lemma carries the difficult half.

### C6.11 — p. 89: perfect matching versus independence number

**Issue.** The source built a second bipartite graph and began a Hall proof that
was longer than necessary and contained unclear set differences.

**Correction.** A perfect matching bounds an independent set by one endpoint per
matching edge.  Conversely, `\alpha+\tau=|V|` and Kőnig's theorem give a matching
of size `|V|/2`.

**Reason.** The corrected proof is complete and uses already established results.

### C6.12 — pp. 92–93: matching lower bound in a bipartite graph

**Issue.** The source maximal-set argument did not clearly connect the size of a
matching to the number of edges.

**Correction.** A minimum vertex cover has size `\nu(G)` by Kőnig, and its
vertices cover at most `\Delta(G)` edges each, so
`|E|\le\Delta\nu`.

**Reason.** This directly yields `\nu\ge |E|/\Delta`.

### C6.13 — pp. 94–96: perfect matchings in trees

**Issue.** The uniqueness proof selected an arbitrary vertex of the symmetric
difference instead of using its component structure.  The existence induction
risked recursing on the original tree rather than a smaller subtree.

**Correction.** Two perfect matchings would create an alternating cycle, which a
tree cannot contain.  For existence, choose a leaf `x` and its neighbour `y`;
all other components of `T-y` are even and inherit the same odd-component
condition, so induction plus the edge `xy` gives a perfect matching.

**Reason.** Every recursive component is strictly smaller.

### C6.14 — pp. 97–99: Petersen's theorem for cubic graphs

**Issue.** The source used four claims and a long extremal-set argument whose last
“even component” contradiction was not established.

**Correction.** For each odd component of `G-S`, degree parity makes its cut odd;
bridgelessness forces at least three cut edges.  Summing gives
`3\operatorname{odd}(G-S)\le3|S|`, so Tutte's condition holds.

**Reason.** This is a short complete proof with no unsupported maximality step.

## Chapter 7 — Planar graphs

### C7.01 — pp. 101–102: Euler's formula

**Issue.** The induction base and the effect of deleting an edge were compressed
and did not distinguish a bridge from a cycle edge.

**Correction.** Trees provide the base.  A nonbridge cycle edge preserves
connectedness and merges exactly two faces, decreasing both `m` and `f` by one.

**Reason.** Deleting a bridge would not have the same face effect.

### C7.02 — pp. 102–103: planar edge bounds

**Issue.** The source alternated inequality directions and referred to faces as
being “incident with edges” without counting boundary occurrences.

**Correction.** The face-degree identity `\sum_F\deg(F)=2m` is combined with
minimum face lengths three or four and Euler's formula.

**Reason.** Bridges and repeated face-boundary edges must be counted with
multiplicity.

### C7.03 — p. 104: maximal planar equivalences

**Issue.** The source wrote `m=3n-6 \Leftrightarrow 2m=3f` as though this alone
proved every face is a triangle, and omitted simplicity and `n\ge3`.

**Correction.** The theorem is stated for simple planar graphs with `n\ge3`.
Maximality first forces triangular faces; triangular faces give the edge count;
the extremal edge count forbids adding an edge.

**Reason.** The missing hypotheses and implication order are essential.

### C7.04 — p. 105: Kuratowski's theorem

**Issue.** The handwritten “proof” established only that a graph containing a
Kuratowski subdivision is nonplanar, not the difficult converse.

**Correction.** The easy direction is proved and the converse is explicitly
identified as the substantive content of the named theorem rather than being
falsely claimed from closure properties.

**Reason.** Subgraph closure alone cannot prove every nonplanar graph contains
one of the two subdivisions.

### C7.05 — pp. 106–108: Wagner's theorem

**Issue.** The source's contraction case split around one edge was incomplete and
made unsupported degree claims about the contracted vertex.

**Correction.** Minors of planar graphs are planar.  Conversely, Kuratowski gives
a subdivision, and contracting each subdivided path produces `K_5` or
`K_{3,3}` as a minor.

**Reason.** This is the direct valid deduction of Wagner's theorem from
Kuratowski's theorem.

### C7.06 — p. 109: minor does not imply subdivision

**Issue.** The drawn counterexample was not specified precisely enough to verify
the claimed degrees.

**Correction.** One vertex of `K_5` is split into adjacent degree-three vertices
with its four old neighbours divided two-and-two.  Contracting the split edge
gives a `K_5` minor, but only four vertices have degree at least four.

**Reason.** A `K_5` subdivision needs five branch vertices of degree at least
four.

### C7.07 — p. 109: Petersen graph nonplanarity

**Issue.** The source listed the question without a completed argument.

**Correction.** The Petersen graph has `n=10`, `m=15`, is bridgeless, and has
girth five.  Planarity would give `2m\ge5f`, while Euler gives `f=7`, producing
`30\ge35`.

**Reason.** The face-length contradiction is immediate and complete.

## Chapter 8 — Graph colouring

### C8.01 — pp. 110–111: Five-Colour Theorem

**Issue.** The source did not state the cyclic order of the five neighbours and
only asserted that two Kempe chains cannot intersect.

**Correction.** Neighbours are ordered around the chosen plane vertex.  A
`1–3` Kempe path together with two incident edges forms a separating closed
curve, so a `2–4` path cannot join the alternating neighbours.

**Reason.** Planar separation, not mere colour difference, is the key argument.

### C8.02 — p. 112: greedy colouring

**Issue.** The algorithm appeared without a proof of the `\Delta+1` bound.

**Correction.** At each step at most `\Delta` colours are forbidden by already
coloured neighbours.

**Reason.** This gives the exact available-colour count.

### C8.03 — pp. 112–114: Brooks's theorem

**Issue.** The handwritten induction and recolouring argument was incomplete and
its final two cases did not establish a valid global ordering.

**Correction.** A standard Brooks ordering lemma is stated: two nonadjacent
vertices with a common final neighbour receive one colour, and every other
nonfinal vertex has a later neighbour.  Greedy colouring then uses at most
`\Delta` colours; the block reduction is summarized in the lemma proof.

**Reason.** The ordering is the invariant that makes every greedy step work.

### C8.04 — pp. 115–117: Vizing's theorem

**Issue.** The source fan sequence stopped in unresolved cases and did not prove
that the proposed colour switches preserve a proper edge colouring.

**Correction.** The fan extension lemma is separated from the induction theorem.
Fan rotations move a missing colour, and Kempe interchanges occur only on
maximal two-coloured components, preserving properness.

**Reason.** The lemma is the nontrivial extension step needed to colour the final
edge.

### C8.05 — pp. 118–119: bipartite edge colouring

**Issue.** The source copied the graph and added edges informally but did not
ensure equal part sizes or equal total deficits.

**Correction.** Dummy vertices equalize the two parts; deficient vertices are
joined until a `\Delta`-regular bipartite multigraph is obtained.  Repeated
perfect matchings decompose its edges into `\Delta` colour classes.

**Reason.** Regularity on both sides is required before applying Hall repeatedly.

### C8.06 — pp. 120–121: pairwise-intersecting odd cycles

**Issue.** The source used five colours correctly but did not explain why deleting
one chosen odd cycle removes every odd cycle.

**Correction.** Any odd cycle in the remainder would be disjoint from the chosen
cycle, contrary to the pairwise-intersection hypothesis.

**Reason.** This proves the remainder is bipartite.

### C8.07 — pp. 122–124: chromatic index of complete graphs

**Issue.** The modular colour formulas were difficult to parse, and the lower
bound for odd order was not separated from the degree bound.

**Correction.** For odd `n`, matching size gives the lower bound `n` and the
colour `i+j\pmod n` gives an `n`-edge-colouring.  For even `n`, the standard
round-robin perfect matchings on
`\{\infty\}\cup\mathbb Z_{n-1}` give `n-1` colours.

**Reason.** This handles parity correctly and supplies explicit constructions.

### C8.08 — p. 124: complement chromatic product

**Issue.** The source tuple argument said vaguely that an edge would share a
colour “no matter which graph it lies in.”

**Correction.** Vertices receive the pair of their colours in `G` and
`\overline G`; equal pairs would make them nonadjacent in both complementary
graphs, impossible.

**Reason.** The injective pair-colour map proves
`\chi(G)\chi(\overline G)\ge |V(G)|`.
