# Introduction to Consensus

data-intensive ch. 8, 9
db internals ch. 8
https://decentralizedthoughts.github.io/2019-06-27-defining-consensus/

- definition
- relation to consistency: consensus can be a way to implement linearizability in a system
- different types of consensus based on their fault tolerance

## Atomic broadcast
- definition
- it's the same problem as consensus but looked from a different angle

this relation is well covered in db internals book and in the tendermint thesis

## Safety and liveness properties
here or somewhere else, explain how it maps to other classification of properties, eg.: agreement, integrity, validity, termination
termination = fault-tolerance


## streamlet
https://decentralizedthoughts.github.io/2020-05-14-streamlet/
https://eprint.iacr.org/2020/088
http://elaineshi.com/docs/blockchain-book.pdf chapter 7

this is a "textbook" protocol, good for pedagogical value so it's an obvious candidate to introduce some topics
NOTE: this is a blockchain protocol and it's permissioned, so it kind of jumps ahead in the topics as currently organized in the book. nevertheless it seems like a better approach to start with this as the first consensus example before moving into classical stuff like paxos or raft.

[CODE SAMPLES HERE]

## Conclusions
## References
