---
title: "Modeling Liquid Democracy Mechanisms"
---
[Brubach, Ballarin, and Nazeer][bbn] model delegation in liquid democracy with directed graphs.

A *preference graph* is a graph of delegation preferences. A directed edge between agent *u* and agent *v* indicates that *u* would rather delegate their vote to *v* than vote directly.

A *delegation graph* is the graph of the actual delegations. In other words, a directed edge between agent *u* and agent *v* means that agent *v* has actually been delegated agent *u*'s vote.

In certain liquid democracy mechanisms, such as [LiquidFeedback](/mechanisms#liquidfeedback), the preference graph *is* the delegation graph. In others, a *tally algorithm* is used to resolve a preference graph into a delegation graph.

# Types of delegation input
In this model, a mechanism has three options (listed below) for how voters
indicate how their votes on a particular issue are to be delegated.
These options are listed in order of least expressive to most expressive.

**One-neighbor preferences (ONP):** Agents may choose only one other agent to delegate their vote to; in other words, each node on the delegation graph has at most one neighbor.  In the preference graph, edges are unweighted.

**Multiple unranked preferences (MUP):** Agents provide an unranked list of other agents they are willing to delegate to. In the preference graph, edges are unweighted.

**Multiple ranked preferences (MRP):** Agents provide a ranked list of other agents they are willing to delegate to. In the preference graph, the outgoing edges of each vertex are ranked. In the preference graph, edges are weighted.

# Cycles
When voters can delegate both their voting power and that of others, there
arises the possibility of **delegation cycles**, in which a voter receives
voting power that they previously delegated.
A cycle presents a pathological case that a liquid democracy mechanism must
handle specially,
as a cycle breaks the rule that all votes must eventually end up as yes votes
or no votes.
Under this model, mechanisms handle cycles in one of three ways:

**Assume Away Cycles (AAC)**: Consciously designing the mechanism around the
assumption
cycles will never occur, and as a result not designing the mechanism to
handle them.

**Discard cycles (DC)**: Ignoring all votes locked up in a cycle, effectively
treating them as abstentions.

**Break cycles (BC)**: Transforming the delegation graph in such a way that the
cycle is broken using some predefined algorithm.

# Definitions
This model defines certain terms to describe the functioning of a liquid
democracy mechanism and its inputs:

**Ground truth:** When operating under the assumption that, in a choice of options, there is one 'correct' option and one or more 'incorrect' options, the ground truth is the correct option.

**Neighbor:** An agent's neighbor on a delegation graph; e.g. the agent who that agent immediately delegates their vote to.



[bbn]: https://arxiv.org/pdf/2206.05339
