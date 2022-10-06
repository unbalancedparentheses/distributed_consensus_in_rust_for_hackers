# Replicated state machines

most algorithms are described in terms of replicated state-machines, explain them here

https://decentralizedthoughts.github.io/2019-10-15-consensus-for-state-machine-replication/
schneider paper
(maybe) lampson paper

## Definitions

## From primary/backup to CFT consensus
these posts show how to go from primary backup to fault tolerant consensus
we may want to follow a similar route, for example introducing the lock-commit as an intermediate step before the more sophisticated algorithms (raft, pbft, etc)
https://decentralizedthoughts.github.io/2020-09-13-synchronous-consensus-omission-faults/
https://decentralizedthoughts.github.io/2020-11-29-the-lock-commit-paradigm/
https://decentralizedthoughts.github.io/2020-11-30-the-lock-commit-paradigm-multi-shot-and-mixed-faults/

this maybe a bit redundant with two phase commit, though. perhaps we can do this instead of 2pc earlier
also they are more difficult than streamlet, introduced later
perhaps it's best to just rewrite the previous primary/backup implementation as a state machine instead of introducing the more complex algorithms

[CODE SAMPLES HERE]

## Conclusions
## References
