### bird-out
Here birds burn-out, and so do we

# Bird-oriented task tracker
If you ever dreamed to learn to fly and scale Agile teams to infinity, this is the right place.

## Behind the curtain
_microservices talk to each other; people talk to frontends; frontends fail with TypeErrors; birds scream_

### Task creation and completion
![img](https://mermaid.ink/svg/pako:eNqFVE1vozAQ_SsjpEqJlFZpq1w4VCJNdw9ttlLhshKXCUyIFWyzxqSbbfrfdwwJ-YDuckDgee_Z857tDy_RKXm-V9KvilRCM4GZQRkr4KdAY0UiClQW5oAlzFFhRqapXl2dAYJUCtXlzQJHnNGGcl2QCXq5bXnaFQi_O4EQM-zWgtDVgsquICSzEQl1MVHkMBGW668x0xeHmYo8FyrrmeZHM4_CfMuDZbzvU2lLkNPSgl7yOn1YGq0sqbQENARaCmspPaANJRZMtsDB7Xg8grv2Nb65HzaQjujch0dDyCOWGziC5nD98MDt-4DcvDbiDx2L7Mq1KzP59fmS45aZ9Elyw8cfNt2Bo4gnKEuRKbDapRR0INMXH96FXaUG32vFm8Kwx84K2c9gN31Q1KBhYFCtQSiQurRAvwtSpdjQiSHs57lGT2-8n2rfjMhWtXHf8no7-_BM2xISVLAgeHocwVsYjIBs0nBr7ct47iYTTuaek7md_DueWcBmalnk1LHzfDkOOHv72RsXn5A2mH6ts2gu4pFo1i0v7YW5iArc7tPBrSTe0508LxNqNY8RLUSWEafEGrqy5f8yck0fQjoxmrPa3yMOtnvlxHfcyqA-opHBZE1m2EL5-DpUcPBtx9t7cHrih72qJ6fGicfKG3mSjESR8m334TixZ1ckKfZ8_kxpiVVuYy9WnwytipTpT6mw2ni-NRWNPI5Oh1uVHP4bzP7CbAY__wLDt5cL)

### Scaling/HA considerations
#### Saga services
Saga's only state is pending requests, so it can be scaled easily, it seems.

Saga services can communicate with others syncrhonuously to keep impl complexity low.

Alternative is to make all communication asynchronuous in actor-like manner, by maintaining user requests and internal communication queues. That would allow to apply batching and multiplexing. Price is maintenance and development complexity.

#### Task services
Task service can store state in external scalable database. I guess something like Master and Read Replicas would do fine here.

If task services store state themselves, then during scaling state can be partitioned by UserId in Cassandra-like fashion. Though state replication would be hard to implement manually. Specifically, order of task mutation would be hard to guarantee.

#### There's more, but I'm tired, SRY :)

### Fun fact
If you ever scream "AGILE IS HIP" in a big empty room with a guitar in it, you may hear strange echo: Giles, Giles and Fripp...
