---
title: "Theorems"
---

# Theorems

Some of the information on this page may be repeated elsewhere.

Theorem 4.1. No mechanism using one neighbor preferences, multiple ranked prefences, or multiple unranked preferences can satisfy both the right to delegate and capped power for any cap less than the number of agents n.

Proof: The paper notes that this property can be clearly observed with two agents, as a cap of less than two will not allow either of them to delegate to the other. This can be generalized by noting that for any cap m, a profile can be constructed where m voters voted for each of (n-1)/m candidates, thereby not allowing the remaining voter from delegating without exceeding the cap.

Theorem 5.1. Any tally algorithm which must delegate each agent’s vote to its highest ranked neighbor through which a delegation path exists, only allows simple paths, and guarantees that the vote will eventually reach a voter, cannot satisfy 1-path explainability.

!(google_votes_ambiguity.png)

Theorem 5.2. No deterministic mechanism with multiple unranked preferences can simultaneously satisfy the right to delegate, single-path explainability, and no arbitrary decisions.

Proof: The following delegation graph requires the algorithm to make an arbitrary decision.

!(fluid_mechanics_arbitrary.png)
