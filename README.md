# Distributed Consensus in Rust for Hackers

## 1. A tour de force in distributed systems
data-intensive ch. 8
db internals ch. 8

### sequential, concurrent, parallel and distributed computing

[CODE SAMPLES HERE]

### fallacies of distributed computing
- original ones from deutsch,
  - emphasis in unreliable networks
- unreliable clocks
- nodes die / expect failures
- local/remote execution waldo note on distributed computing
- (maybe) end to end system design

https://en.wikipedia.org/wiki/Fallacies_of_distributed_computing
learn erlang ch. 26
soft arch ch 9

### Modeling distributed systems

(this is easier to introduce next to failures, but it may be too theoretic for the first chapter. alternatively, it could be moved to the consensus intro chapter, closer to where it's used)

#### failure models
pick one of:
crash-stop / crash-recovery / byzantine (data-intensive)
crash / omission / byzantine (db internals)
https://alvaro-videla.com/2013/12/failure-modes-in-distributed-systems.html
http://cs.boisestate.edu/~amit/teaching/555/handouts/fault-tolerance-handout.pdf

note: omissions includes network paritions as used in CAP

#### synchrony models
synchronous, asynchronous, partially synchronous
https://decentralizedthoughts.github.io/2019-06-01-2019-5-31-models/

##### FLP impossibility
how it can be worked around in practice

#### Mapping to the real world
data-intensive apps has a good section about this

models help not only to understand the terms in which algorithms are stated and where they are applicable, but also to reason about and make trade-off analysis in real systems

### Conclusions
### References

## 2. Replication and Consistency
http://book.mixu.net/distsys/replication.html
db internals ch 11, 13
data-intensive ch 9

touch briefly, just the necessary to move to the consensus problem in next chapter
show how to go from single node, to single leader, to fault tolerance and the options and trade-off of different methods

### Replication
this is covered in data-intesive apps book

- definition
- can serve two purposes: performance and reliability (relate to failures as described in first chapter)
- touch briefly on types of replication, and give examples of implementations of each: leader/followers, multi-leader, leaderless (e.g dynamo)
- having redundancy introduces the problem of keeping replicas consistent with each other

#### primary/backup replication
simplest form of replication
explained in distsys fun and profit
can be used as example of weak consistency to intrduce the next section?

[CODE SAMPLES HERE]

### Consistency
this is covered in database internals book
- definition
- consistency models: linearizability, sequential, causal, eventual (mention strong eventual/crdts here)
- add a diagram with stronger->weaker and a tree of models/submodels and systems that implement it

#### cap (and its problems)
summarize conjecture
explain problems of the theorem
give precise meaning to terms: partition compared with failures from ch 1; consistency compared with models from previous section.
(maybe) minor side note about relation between FLP and CAP
explain what's its actual value in tradeoff analysis for system design

#### distributed transactions/2-phase commit 

https://www.the-paper-trail.org/post/2008-11-27-consensus-protocols-two-phase-commit/


[CODE SAMPLES HERE]

2PC can be thought of a solution to consensus, but it's not an interesting one because it's not fault tolerant (cannot tolerate crashes of the coordinator)
(it can also be used to solve a different problem than consensus, i.e.  saving different things in different nodes vs replicating the same value in consensus, see eg spanner that uses both 2pc and paxos.)
for fault tolerance we need more sophisticated consensus protocols, introduced next chapter

### Conclusions
### References

## 3. Introduction to Consensus
data-intensive ch. 8, 9
db internals ch. 8
https://decentralizedthoughts.github.io/2019-06-27-defining-consensus/

- definition
- relation to consistency: consensus can be a way to implement linearizability in a system
- different types of consensus based on their fault tolerance

### Atomic broadcast
- definition
- it's the same problem as consensus but looked from a different angle

this relation is well covered in db internals book and in the tendermint thesis

### Safety and liveness properties
here or somewhere else, explain how it maps to other classification of properties, eg.: agreement, integrity, validity, termination
termination = fault-tolerance

### State-machine replication
(maybe better in replication chapter?)
most algorithms are described in terms of replicated state-machines, explain them here

https://decentralizedthoughts.github.io/2019-10-15-consensus-for-state-machine-replication/
schneider paper
(maybe) lampson paper

[CODE SAMPLES HERE]

### Conclusions
### References

## 4. Crash fault-tolerant (CFT) consensus
explain raft in detail, the rest briefly

http://thesecretlivesofdata.com/raft/ -> would be good to have more like this for other algorithms
https://github.com/ongardie/raft.tla/blob/master/raft.tla
raft paper

- paxos
- (maybe) Viewstamped Replication
- zab
- (maybe) chubby
- raft
  - leader election
  - log replication

### Conclusions
### References

## 5. Byzantine fault-tolerant (BFT) consensus
sources:
real-world crypto ch. 12
https://pontem.network/posts/aptosbft-all-you-need-to-know-about-the-bft-consensus-in-aptos

### The Byzantine generals problem
### Practical Byzantine fault-tolerance PBFT
### Bitcoin and permissionless consensus
before bitcoin BFT was a theoretical problem and the solutions impractical, but a permissionless network required to assume arbitrary/malicious nodes.
### Proof of authority, proof of work, proof of stake

### Conclusions
### References

## 6. Proof of Stake consensus protocols
real-world crypto ch. 12

### Tendermint
### Diem
previously Libra, based on hotstuff
(need to make differences with tendermint explicit, and if they are not big enough probably not worth getting into the details here, perhaps just mentioning it)

### Algorand?
Byzantine Agreement, Made Trivial

### DAGs
https://decentralizedthoughts.github.io/2022-06-28-DAG-meets-BFT/
https://www.paradigm.xyz/2022/07/experiment-narwhal-bullshark-cosmos-stack

### Conclusions
### References

## Appendix: summary of consensus algorithms
make a table with each algorithm: synchrony and failure models it assumes, adversary threshold, performance, code complexity

## Appendix: TLA?

# Notes/TODO

- review: [Consensus in the Presence of Partial Synchrony](https://groups.csail.mit.edu/tds/papers/Lynch/jacm88.pdf)  (defines failure and synchrony models, is used by modern BFT)
- [the tendermint thesis](https://knowen-production.s3.amazonaws.com/uploads/attachment/file/1814/Buchman_Ethan_201606_Msater%2Bthesis.pdf) does a long introduction and comparison to other protocols, can be used as guide for this
- the [raft thesis](https://www.web.stanford.edu/~ouster/cgi-bin/papers/OngaroPhD.pdf) is similar
- [Unreliable Failure Detectors for Reliable Distributed Systems](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)

# references

- https://pontem.network/posts/aptosbft-all-you-need-to-know-about-the-bft-consensus-in-aptos
- https://dl.acm.org/doi/10.1145/3293611.3331591
- [Bullshark: DAG BFT Protocols Made Practical](https://arxiv.org/pdf/2201.05677.pdf)
