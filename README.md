<!-- solve-problem:c6c47954-0c53-46b2-94f7-30f43f4ae1ff -->
# Near-linear exact Euclidean minimum-weight perfect matching

A [Tangle Solve problem](https://solve.tangle.tools/problems/c6c47954-0c53-46b2-94f7-30f43f4ae1ff).

## What is the problem?

Given an even number n of points in the plane (say, with integer or rational coordinates, so that squared Euclidean distances are exactly representable), compute a **minimum-weight perfect matching** — a perfect matching M minimizing Σ_{(p,q)∈M} |pq| — in **near-linear time**, i.e., O(n log^O(1) n), using **exact arithmetic** so the output is provably the true optimum.

The formal model: points have rational coordinates; distances compared via exact squared-distance comparisons (integers of O(log n + C) bits, where C is the input coordinate bit-length). "Near-linear" means n·polylog(n). The question: does an exact algorithm with this running time exist, or is there a lower bound separating exact from approximate? The census formulation leaves the arithmetic model somewhat open — an acceptable solution must pin it down (e.g., unit-cost exact rational arithmetic, or bit-complexity accounting).

Standard equivalent formulation: min-cost matching in the complete geometric graph, whose weight matrix is implicitly the Euclidean metric. Do not confuse with bipartite geometric assignment (min-cost matching between two n-point sets), which is a closely related but distinct problem.

## Why does it matter?

Exact geometric matching underlies exact solutions to geometric assignment, vehicle/robot pairing, and preprocessing in TSP heuristics with exactness guarantees; it is also the canonical test case for whether geometry lets us beat general graph matching bounds. General-graph min-cost perfect matching takes ~O(n^3) (with near-linear-in-m work per augmentation); geometric structure is known to help (Varadarajan's near-linear-in-n·polylog algorithms for the *approximate* variant), and settling the exact case would clarify the fundamental power of geometry in combinatorial optimization.

## What's already known?

- General graphs: exact min-weight perfect matching is solvable in polynomial time (Edmonds' blossom algorithm); recent combinatorial implementations (e.g., Gabow's work) achieve ~Õ(nm + n² log n), which on dense graphs is ~n³. No near-linear exact algorithm even for explicit dense graphs is known or expected there.
- Geometry helps structurally: the Euclidean MST, nearest-neighbor structure, and the fact that long matching edges are "isolated" (sparsity properties of optimal geometric matchings) give near-linear-size candidate graph constructions (verify exact bounds in Varadarajan 1998).
- Varadarajan (1998): divide-and-conquer giving O(n^{3/2} polylog n) (verify exact exponent) for exact min-cost perfect matching in the plane — the best-known exact bound in this line. The gap to near-linear remains open.
- Approximation: near-linear PTAS/FPTAS-style schemes for geometric matching exist (e.g., via well-separated pair decompositions, following Varadarajan–Agarwal lines of work); these do not address exactness.
- TOPP Problem 6 (Kaneko et al.'s open-problem list in discrete/computational geometry) lists near-linear exact planar matching among its challenges.

## What would count as solving it?

1. **Upper bound (positive):** a randomized or deterministic algorithm computing an exact min-weight perfect matching of n planar rational points in O(n log^k n) time under a stated exact-arithmetic model, with a correctness proof.
2. **Lower bound (negative):** a proof that exact Euclidean matching requires ω(n polylog n) time in a reasonable model (e.g., a reduction showing Ω(n^{1+ε}) comparisons are needed, or a fine-grained reduction from a conjectured-hard problem).
3. **Intermediate:** shaving Varadarajan's exponent (e.g., O(n polylog n) for fixed dimension or integer-bounded coordinates) would be significant partial progress.

A referee would demand: exactness (not approximation), stated arithmetic model, and full worst-case analysis.

## How to start

1. Read Varadarajan (1998) carefully — understand the divide-and-conquer scheme, where the n^{3/2} (verify) bottleneck arises (recursive geometric separator-based decomposition and recombination of boundary matchings), and whether the bottleneck is combinatorial or arithmetic.
2. Study sparsity lemmas for optimal geometric matchings (edge-length vs. neighborhood density arguments, as in Euclidean MST-style proofs) to build a near-linear-size exact candidate graph; the obstacle is that such sparsification is provably safe for MST but lossy for matching.
3. Consider the bipartite/assignment variant, where geometry-plus-matching literature (Agarwal, Varadarajan, and later work on geometric matching) is richer; techniques may transfer.
4. Alternatively, attempt a lower bound: show instances where distinguishing two optimal matchings requires many distance comparisons.

## Key references

- K. Varadarajan (1998), "A divide and conquer algorithm for min-cost perfect matching in the plane," *ICALP 1998*. Gives a divide-and-conquer exact algorithm for planar min-cost perfect matching running in roughly O(n^{3/2} polylog n) time — the key exact upper bound to beat. (Link via Springer LNCS 1443; verify.)
- A. Kaneko, M. Kano, and colleagues, "Open Problems on Discrete and Computational Geometry" (TOPP), Problem 6. Lists efficient exact geometric matching as an open challenge. (Verify exact citation and problem numbering.)
- Edmonds (1965), "Maximum matching and a polyhedron with 0,1-vertices," *J. Res. NBS*. Foundational blossom algorithm establishing polynomial-time exact matching on general graphs — the baseline that geometry must beat.
- Well-separated pair decomposition literature (Callahan–Kosaraju 1995) and geometric matching approximation papers building on it — the toolkit for near-linear geometric sparsification. (Verify which specific papers treat matching approximation.)

## Warnings

- Exactness is the whole problem: any near-linear approximation scheme is known/straightforward by prior work and does not count.
- The arithmetic model matters. Squared distances between rational points are exact integers; but if you allow adversarial real inputs, "exact" comparisons may cost Ω(bit-length) each — state the model up front.
- Don't conflate perfect matching on 2n points with bipartite assignment between two n-point sets; results differ.
- The candidate-graph (sparsification) approach has a known pitfall: safe sparsification lemmas for MST do not obviously extend to perfect matching, since optimum matchings can use edges excluded by nearest-neighbor-type structures. Verify any claimed sparsity lemma before building on it.
- Exact exponents attributed to Varadarajan's paper here should be checked against the original; secondary summaries disagree.

---
*`ALGO-000159` · unverified*

## Acceptance guidance

1. **Upper bound (positive):** a randomized or deterministic algorithm computing an exact min-weight perfect matching of n planar rational points in O(n log^k n) time under a stated exact-arithmetic model, with a correctness proof.
2. **Lower bound (negative):** a proof that exact Euclidean matching requires ω(n polylog n) time in a reasonable model (e.g., a reduction showing Ω(n^{1+ε}) comparisons are needed, or a fine-grained reduction from a conjectured-hard problem).
3. **Intermediate:** shaving Varadarajan's exponent (e.g., O(n polylog n) for fixed dimension or integer-bounded coordinates) would be significant partial progress.

A referee would demand: exactness (not approximation), stated arithmetic model, and full worst-case analysis.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/c6c47954-0c53-46b2-94f7-30f43f4ae1ff?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000159.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000159)
