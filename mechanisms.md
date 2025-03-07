---
title: "Existing Mechanisms"
---

# Existing Mechanisms

The paper starts by analyzing the properties of the two liquid democracy mechanisms that have been put into real world use in any substantive capacity: Google Votes and LiquidFeedback. It then covers two further mechanisms that have been proposed in papers: [GreedyCap][kahng] and a [fluid mechanics model][golz].

## Google Votes

**Background:** Google Votes was used internally by Google between 2012 and 2015 to vote to make inconsequential community decisions, such as those regarding meals, snacks, and internal project logos. Information is primary available through a [Google Techtalk][google] from 2014, which does not fully explain the algorithm used by the central delegation mechanism.  In particular, it is ambiguous how the mechanism chooses among multiple possible delegation paths in the case of delegation cycles.

**Mechanism:** The mechanism functions by conducting a breadth-first search, starting at each agent who directly voted. Then, duplicate votes are removed by taking the highest ranked path between a delegating agent and a voter.

**Cycle resolution:** According to the Google Techtalk, cycles are not allowed, but the mechanism for breaking cycles is never explained. Brubach, Ballarin, and Nazeer theorize that it may either break cycles by choosing the shortest path to a voter (breadth-first), or by removing the last edge in a cycle (depth-first). Either way, the place that the vote ends up is determined by the position of the initial delegator in the cycle, and a vote delegated to an agent may end up at a different place than the personal vote which that agent delegates.

**Tractability:** Lack of documentation prevents the exact running time from being known, except that enumerating all paths between agents and voters is lower bounded by the number of paths ($n^2$). Brubach et al note that polynomial-time algorithms can be devised for each of their theorized resolution steps.

**Single-path explainability:** No. The Google Votes mechanism guarentees single-path explainability for each voter's individual vote, but cannot do so for all votes delegated to a voter, as proven in [Theorem 5.1](theorems).

**Right to Delegate:** Yes. No agent will be compelled to vote if they would rather delegate.

**Right to Top Rank:** Yes. The algorithm guarentees that every agent's top ranked neighbor preference is honored.

**Limits on power**: None.

## LiquidFeedback

**Background:** [Liquidfeedback][liquidfeedback] is a free software package which implements a simple liquid democracy mechanism. It was most notably used by the German Pirate Party to make party decisions, making this one of the few attempts to use liquid democracy in an actual political situation. LiquidFeedback was also briefly used by the district governments of Friesland and Rotenburg in northern Germany, albeit only as a glorified suggestion box without any direct power and with almost no adoption by the citizen body.

**Mechanism:** Agents can either vote directly, or specify a single agent to delegate all of their votes to. Each voter has a number of votes equivalent to the number of nodes discoverable from a breadth-first search on the reversed delegation graph, starting from that voter.

**Cycle resolution:** There is no attempt to resolve cycles; should a cycle exist, all votes contained within it will be wasted.

**Tractability**: The tally algorithm runs in O(n) time.

**Single-path explainability:** Yes.

**Right to Delegate:** Yes.

**Limits on power:** None.

## Breadth-first

**Background:** Breadth-first delegation was introduced in the paper [Incentivising Participation in Liquid Democracy with Breadth-First Delegation][kotsialou].

**Mechanism:** Taking as input a directed delegation graph (multiple ranked preferences), each agent's vote is delegated to the voting agent that is closest to them. Should there be a tie, the vote is delegated to the higher ranked voter. Thus, the ranked preferences are only used in ties. Brubach et al seem to take issue with this, since it punishes multi-level delegations and goes against their conception of liquid democracy as a system of 'experts at selecting experts', and is insufficiently differentiated from proxy voting.

**Cycle resolution:** As long as there exists a path from an agent to a voter, cycles are broken by choosing the shortest path to a voter.

**Tractability:** The mechanism runs in O(n+m) time.

**Right to Delegate:** Yes.

**Right to Top Rank:** No.

**Limits on power:** No direct mechanisms to limit power, but the authors who posited the system theorize that it may limit concentrated power in practice.


## GreedyCap

**Background:** GreedyCap was introduced in the paper [Liquid Democracy: An Algorithmic Perspective][kahng]. This paper begins with the model of an election in which there is one objectively 'correct' option and one 'incorrect' option, and attempts to create a liquid democracy mechanism which will have an as-good or better chance of picking the correct option than a direct democracy. The paper's model assumes that each agent has a 'competency level' which is the probability that that agent would vote for the correct option if they voted themselves. Furthermore, the paper assumes that each agent may only delegate their votes to strictly more competent neighbors. In these circumstances, GreedyCap will outperform direct voting, in the sense of being always at least as likely, and sometiems more likely, to make the 'correct' decision.

**Mechanism:** Taking as input an unweighted, directed delegation graph (one neighbor preferences) and a cap C, A greedy algorithm chooses the agent v with the most delegated votes (incoming edges), and up to C - 1 agents who delegated their votes to v. Agent v votes with the votes of all the chosen nodes and then all chosen nodes, including v, are removed from the graph. These steps are repeated until no nodes exist on the graph.

**Cycle resolution:** Under the supposition that agents will only delegate to agents with strictly higher competency levels, cycles are impossible, and the mechanism does not concern itself with them.

**Tractability:** The greedy algorithm runs in O(n log n) time.

**Single-path explainability:** Yes.

**Right to Delegate:** No. As proven in [Theorem 4.1](theorems), no mechanism using one neighbor preference and capped power can satisfy the right to delegate for any cap less than the number of voters.

**Limits on power:** An individuals' votes are capped at C.

## Fluid Mechanics

**Background:** The 'fluid mechanics approach' was introduced in the paper [The Fluid Mechanics of Liquid Democracy][golz]. It attempts to minimize the maximum power of any voter through modeling votes as liquid and a delegation graph as connected vessels, therby adapting the principles of confluent flow (and the natural 'leveling' which results) to a liquid democracy context.

**Mechanism:** Taking as input an unweighted, directed delegation (multiple unranked preferences), each agent is treated as being a source of one vote and all agents who voate are treated as sinks. The algorithm finds a flow graph - a subset of the delegation graph such that each node has at most one outgoing edge - that minimizes the number of votes which each sink receives, while maximizing the number of votes which have a path to a sink. Each voter votes with a number of votes equal to the number of nodes which have a path to that voter in the flow graph.

**Cycle resolution:** If there is no path from an agent to a sink (such as in a closed delegation cycle with no voters), the vote goes wasted. Otherwise, cycles will be broken as the mechanism will find a flow path from the voter to a sink according to the normal operating principles outlined already.

**Tractability:** Finding the optimal flow graph is NP-hard.

**Single-path explainability:** Yes.

**Right to Delegate:** Yes.

**Limits on power:** The number of votes delegated to each voter is minimized.

**Logically predictable:** No. As proven in [Theorem 5.2](theorems), a deterministic mechanism with multiple unranked preferences, single-path explainability, and which always maintains the right to delegate, must make arbitrary decisions. This is easily seen with n = 3, where one agent has includes the other two agents, who are voters, in their delegation preferences. Then the mechanism must arbitrarily choose which voter to give that agent's vote to. This could be solved, perhaps, by using a ranking which is only used in such tiebreaking situations, as the breadth-first mechanism does.

[kahng]: https://cdn.aaai.org/ojs/11468/11468-13-14996-1-2-20201228.pdf
[golz]: https://arxiv.org/pdf/1808.01906
[google]: https://www.youtube.com/watch?v=F4lkCECSBFw
[liquidfeedback]: https://liquidfeedback.com/en/
[kotsialou]: https://arxiv.org/pdf/1811.03710
