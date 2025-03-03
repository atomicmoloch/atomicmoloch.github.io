---
title: "Properties"
---
[Brubach, Ballarin, and Nazeer][bbn] attempt to analyze the fairness, transparency, and accountability of liquid democracy by formalizing a number of desirable properties which are idiosyncratic to a liquid democracy mechanism.
*   Right to Delegate (RTD): Every participant that wants to delegate their vote will always be able to do so. Formally, a mechanism satisfies the *right to delegate* if every agent with delegable preferences has all of the votes assigned to them delegated to one or more of their approved delegates.
*   Right to top rank (RTTR): A mechanism satisfies *right to top rank* if every agent with a top rank delegation path has all of the votes assigned to them delegated along that path.
*   Capped Power (CP): A hard upper bound is placed on the weight or number of votes that can be delegated to a single individual.

## Transparency
Transparency, in a Liquid Democracy context, is primar

Explainability: For the sake of transparency, it is desirable that every voter should know exactly to what ends their vote eventually contributed.
*   𝜓 -path explainability (𝜓-PE): A mechanism satisfies 𝜓-PE if it can provide every agent with a list of at most 𝜓 total vote paths and the fraction of that agent's vote which was delegated to each path. The paper focusses little on general 𝜓-path explainability, focussing primarily on single-path explainability.
*   Local feedback explainability (LFE): A mechanism satisfies LFE if it can provide every agent with the fraction of that agent's vote which was delegated to each neighbor and what percent of the vote delegated to each neighbor supported each outcome.


## Accountability

Positive gain: If there is a single correct outcome (ground truth), the mechanism will find it.

Do no harm: In terms of finding the ground truth, a liquid democracy mechanism will not perform worse than direct democracy.

[bbn]: https://arxiv.org/pdf/2206.05339
