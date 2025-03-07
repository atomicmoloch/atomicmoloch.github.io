---
title: "Modeling Liquid Democracy Mechanisms"
---
[Brubach, Ballarin, and Nazeer][bbn] model delegation in liquid democracy with directed graphs.

A *preference graph* is a graph of delegation preferences. A directed edge between agent *u* and agent *v* indicates that *u* would rather delegate their vote to *v* than vote directly.

A *delegation graph* is the graph of the actual delegations. In other words, a directec edge between agent *u* and agent *v* means that agent *v* has actually been delegated agent *u*'s vote.

In certain liquid democracy mechanisms, such as LiquidFeedback, the preference graph *is* the delegation graph. In others, a *tally algorithm* is used to resolve a preference graph into a delegation graph.

Here are definitions for some terminology used by Brubach, Ballarin, and Nazeer, with definitions which may not be obviously apparent.

**Ground truth:** When operating under the assumption that, in a choice of options, there is one 'correct' option and one or more 'incorrect' options, the ground truth is the correct option.

**Neighbor:** An agent's neighbor on a delegation graph; e.g. the agent who that agent immediately delegates their vote to.

**One-neighbor preferences (ONP):** Agents may choose only one other agent to delegate their vote to; in other words, each node on the delegation graph has at most one neighbor.  In the preference graph, edges are unweighted.

**Multiple ranked preferences (MRP):** Agents provide a ranked list of other agents they are willing to delegate to. In the preference graph, the outgoing edges of each vertex are ranked. In the preference graph, edges are weighted.

**Multiple unranked preferences (MUP):** Agents provide an unranked list of other agents they are willing to delegate to. In the preference graph, edges are unweighted.


[bbn]: https://arxiv.org/pdf/2206.05339
