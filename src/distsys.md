# Distributed consensus in Rust for Hackers

## 1. A tour de force in distributed systems
data-intensive ch. 8
db internals ch. 8

### sequential, concurrent, parallel, distributed
#### sequential computing
[CODE SAMPLE]

#### concurrent computing
[CODE SAMPLE]

side notes:
- problems that arise in concurrent programming (deadlocks, race conditions, code complexity, difficulty to test)
- briefly describe concurrent programming models

#### async programming

[CODE SAMPLE]

#### parallel computing
[CODE SAMPLE]

#### distributed computing
[CODE SAMPLE]

reasons to distribute: performance (speed, scalability of resources, cost-efficiency), reliability

When your program is a local text editor, your users don't expect it to continue running if their laptop runs out of battery or the hard drive crashes. As a programmer, you can safely ignore those scenarios. But if your program is a web application, it's not acceptable to go offline if there's a faulty hard drive in some datacenter or a power outage in in North Virginia. Web applications need to serve thousands or millions of users so it's not cost-effective to run them on a single host; you need multiple servers and with more components the probability of faulty hardware increases. What's more, as you'll see in the next section, networks are even less reliable than computers: messages get lost or duplicated, hosts become unreachable. The bottom line is that in distributed setups you need to assume things are going to break, even in unexpected ways, and design systems that continue working even in the presence of errors.

### Conclusions
### References

## Replication and Consistency
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
https://decentralizedthoughts.github.io/2019-11-01-primary-backup/
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

### Modeling distributed systems

- review: [Consensus in the Presence of Partial Synchrony](https://groups.csail.mit.edu/tds/papers/Lynch/jacm88.pdf)  (defines failure and synchrony models, is used by modern BFT)
- [Unreliable Failure Detectors for Reliable Distributed Systems](https://www.cs.utexas.edu/~lorenzo/corsi/cs380d/papers/p225-chandra.pdf)

- https://decentralizedthoughts.github.io/2021-10-29-consensus-cheat-sheet/

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

show practical examples of each synchrony model

##### FLP impossibility
how it can be worked around in practice
randomization, failure detectors (see chandra paper), partial synchrony
provide examples and trade-offs

#### Mapping to the real world
data-intensive apps has a good section about this

models help not only to understand the terms in which algorithms are stated and where they are applicable, but also to reason about and make trade-off analysis in real systems

### Atomic broadcast
- definition
- it's the same problem as consensus but looked from a different angle

this relation is well covered in db internals book and in the tendermint thesis

### Safety and liveness properties
here or somewhere else, explain how it maps to other classification of properties, eg.: agreement, integrity, validity, termination
termination = fault-tolerance

## Replicated State-machines
most algorithms are described in terms of replicated state-machines, explain them here

https://decentralizedthoughts.github.io/2019-10-15-consensus-for-state-machine-replication/
schneider paper
(maybe) lampson paper

[CODE SAMPLES HERE]

#### From primary/backup to CFT consensus
these posts show how to go from primary backup to fault tolerant consensus
we may want to follow a similar route, for example introducing the lock-commit as an intermediate step before the more sophisticated algorithms (raft, pbft, etc)
this maybe a bit redundant with two phase commit, though. perhaps we can do this instead of 2pc earlier

https://decentralizedthoughts.github.io/2020-09-13-synchronous-consensus-omission-faults/
https://decentralizedthoughts.github.io/2020-11-29-the-lock-commit-paradigm/
https://decentralizedthoughts.github.io/2020-11-30-the-lock-commit-paradigm-multi-shot-and-mixed-faults/

### Conclusions
### References

## 4. Crash fault-tolerant (CFT) consensus
explain raft in detail, the rest briefly

http://thesecretlivesofdata.com/raft/ -> would be good to have more like this for other algorithms
https://github.com/ongardie/raft.tla/blob/master/raft.tla
raft paper
paxos made live https://www.cs.utexas.edu/users/lorenzo/corsi/cs380d/papers/paper2-1.pdf (chubby. covers issues when going to production)


- paxos
- (maybe) Viewstamped Replication
- zab
- chubby
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

### streamlet
https://decentralizedthoughts.github.io/2020-05-14-streamlet/
review the paper
this is a "textbook" protocol, good for pedagogical value so it's an obvious candidate to introduce some topics
TODO: the question is whether it makes sense to bring it up here, after going through raft and introducing BFT. most likely it's easier to do it earlier.

### Tendermint
### Diem
previously Libra, based on hotstuff
(need to make differences with tendermint explicit, and if they are not big enough probably not worth getting into the details here, perhaps just mentioning it)

### Algorand?
Byzantine Agreement, Made Trivial

### DAGs
https://decentralizedthoughts.github.io/2022-06-28-DAG-meets-BFT/
https://www.paradigm.xyz/2022/07/experiment-narwhal-bullshark-cosmos-stack
[Bullshark: DAG BFT Protocols Made Practical](https://arxiv.org/pdf/2201.05677.pdf)

### Conclusions
### References

## Appendix: summary of consensus algorithms
make a table with each algorithm: synchrony and failure models it assumes, adversary threshold, performance, code complexity
