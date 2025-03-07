---
title: "Modeling Liquid Democracy Mechanisms"
---
[Brubach, Ballarin, and Nazeer][bbn] model liquid democracy as…


**Ground truth:** When operating under the assumption that, in a choice of options, there is one 'correct' option and one or more 'incorrect' options, the ground truth is the correct option.

**Neighbor:** An agent's neighbor on a delegation graph; e.g. the agent who that agent immediately delegates their vote to.

**One-neighbor preferences (ONP):** Agents may choose only one other agent to delegate their vote to; in other words, each node on the delegation graph has at most one neighbor.  In the preference graph, edges are unweighted.

**Multiple ranked preferences (MRP):** Agents provide a ranked list of other agents they are willing to delegate to. In the preference graph, the outgoing edges of each vertex are ranked. In the preference graph, edges are weighted.

**Multiple unranked preferences (MUP):** Agents provide an unranked list of other agents they are willing to delegate to. In the preference graph, edges are unweighted.


[bbn]: https://arxiv.org/pdf/2206.05339
