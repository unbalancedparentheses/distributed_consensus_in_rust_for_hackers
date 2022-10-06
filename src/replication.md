# Replication

http://book.mixu.net/distsys/replication.html
db internals ch 11, 13
data-intensive ch 9

touch briefly, just the necessary to move to cons problem in next chapter
show how to go from single node, to single leader, to fault tolerance and the options and trade-off of different methods
TODO: see how to best distribute between replication and consistency chapters

## Replication
this is covered in data-intesive apps book

- definition
- can serve two purposes: performance and reliability (relate to failures as described in first chapter)
- touch briefly on types of replication, and give examples of implementations of each: leader/followers, multi-leader, leaderless (e.g dynamo)
- having redundancy introduces the problem of keeping replicas consistent with each other

## primary/backup replication
simplest form of replication
explained in distsys fun and profit
https://decentralizedthoughts.github.io/2019-11-01-primary-backup/
can be used as example of weak consistency to intrduce the next section?

[CODE SAMPLES HERE]

### Conclusions
### References
