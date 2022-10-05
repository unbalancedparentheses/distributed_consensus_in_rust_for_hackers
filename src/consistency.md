# Consistency

this is covered in database internals book
- definition
- consistency models: linearizability, sequential, causal, eventual (mention strong eventual/crdts here)
- add a diagram with stronger->weaker and a tree of models/submodels and systems that implement it

## cap (and its problems)
summarize conjecture
explain problems of the theorem
give precise meaning to terms: partition compared with failures from ch 1; consistency compared with models from previous section.
(maybe) minor side note about relation between FLP and CAP
explain what's its actual value in tradeoff analysis for system design

## distributed transactions/2-phase commit

TODO: see basic consensus implementations from next chapters, may not be the best idea to introduce this here

https://www.the-paper-trail.org/post/2008-11-27-consensus-protocols-two-phase-commit/

[CODE SAMPLES HERE]

2PC can be thought of a solution to consensus, but it's not an interesting one because it's not fault tolerant (cannot tolerate crashes of the coordinator)
(it can also be used to solve a different problem than consensus, i.e.  saving different things in different nodes vs replicating the same value in consensus, see eg spanner that uses both 2pc and paxos.)
for fault tolerance we need more sophisticated consensus protocols, introduced next chapter



## Conclusions
## References
