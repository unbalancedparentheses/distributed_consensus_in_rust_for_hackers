# Living with failure

## fallacies of distributed computing
- original ones from deutsch,
  - emphasis in unreliable networks
  - there's some concrete examples and data in data-intensive book, eg. about failures in cloud environments
  - see also Bailis/Kingsbury article

## other problems
- pitfall: a remote call is just like a funcion call.
  - see "A Note on Distributed Computing", Waldo
- unreliable clocks
- nodes die / expect failures
- (maybe) end to end system design

## Conclusions

for theory, connect with models chapter for a more formal treatment, required for consensus algorithms
for practice: let it crash philosophy from erlang and related papers

## References

TODO: review these references, incorporate what's useful, remove the rest

- The Trouble with Distributed Systems - Designing Data-Intensive Applications chapter 8
- Distributed Systems Intoroduction and Overview - Database Internals chapter 8
- [Fallacies of distributed computing](https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing)
- [Distribunomicon - Learn you some Erlang for great good](https://learnyousomeerlang.com/distribunomicon)
- [The network is reliable](https://queue.acm.org/detail.cfm?id=2655736)
- [Making reliable distributed systems in the presence of software errors](https://erlang.org/download/armstrong_thesis_2003.pdf)
- [Recovery Oriented Computing (ROC): Motivation, Definition, Techniques, and Case Studies](https://www2.eecs.berkeley.edu/Pubs/TechRpts/2002/CSD-02-1175.pdf)
- [Crash-Only Software](https://research.cs.wisc.edu/areas/os/ReadingGroup/os-old/Papers/HotOSIX/Candea-CrashOnlySoftware.pdf)
- [A Note on Distributed Computing](https://scholar.harvard.edu/files/waldo/files/waldo-94.pdf)
