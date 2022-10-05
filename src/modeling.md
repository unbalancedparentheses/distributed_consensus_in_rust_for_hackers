# Modeling distributed systems


- review: [Consensus in the Presence of Partial Synchrony](https://groups.csail.mit.edu/tds/papers/Lynch/jacm88.pdf)  (defines failure and synchrony models, is used by modern BFT)
- [Unreliable Failure Detectors for Reliable Distributed Systems](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)

- https://decentralizedthoughts.github.io/2021-10-29-consensus-cheat-sheet/

## failure models
pick one of:
crash-stop / crash-recovery / byzantine (data-intensive)
crash / omission / byzantine (db internals)
https://alvaro-videla.com/2013/12/failure-modes-in-distributed-systems.html
http://cs.boisestate.edu/~amit/teaching/555/handouts/fault-tolerance-handout.pdf

note: omissions includes network paritions as used in CAP

## synchrony models
synchronous, asynchronous, partially synchronous
https://decentralizedthoughts.github.io/2019-06-01-2019-5-31-models/

show practical examples of each synchrony model

### FLP impossibility
how it can be worked around in practice
randomization, failure detectors (see chandra paper), partial synchrony
provide examples and trade-offs

## Mapping to the real world
data-intensive apps has a good section about this

models help not only to understand the terms in which algorithms are stated and where they are applicable, but also to reason about and make trade-off analysis in real systems
