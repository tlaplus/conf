+++
title = "YannickWelsch"
hidden = true
weight = 200
+++

### Using TLA+ for fun and profit in the development of Elasticsearch

#### Yannick Welsch
##### Elastic

Elasticsearch is a distributed search and analytics engine based on Apache Lucene. Initially
released in 2010, it has quickly become the most popular enterprise search engine, and
is commonly used for log analytics, full-text search, operational and security intelligence,
business analytics, and metrics use cases. Built as a distributed system since its inception,
Elasticsearch effortlessly scales to clusters of hundreds of servers. As part of a larger
resiliency effort, Elasticsearch’s core cluster coordination and data replication algorithms
have undergone major overhauls in recent years. The use of formal methods, with in
particular TLA + , PlusCal and the TLC model checker, has extensively contributed to
the goal of creating a much safer and resilient system. This presentation will provide an
overview on the various uses of TLA + during the development of Elasticsearch:

* We refined and validated an informal specification of the data replication algorithm
that has been powering Elasticsearch since version 6, released in November 2017, by
creating a TLA + specification during the implementation effort. This algorithm, based
on the primary-backup approach, enables high-throughput sharded data ingestion
pipelines and has served as fundational work to build newer features such as cross-
datacenter replication.

* We studied two bugs in a highly concurrent component that handles deletion tomb-
stones and out-of-order writes under various optimizations. The implementation was
mapped onto a PlusCal spec, which, with the use of the TLC model checker, led
us to discover an additional unknown bug in the implementation, which we only
later observed in the wild. The bug fixes were first prototyped using the PlusCal
specification.

* We designed a new cluster coordination subsystem and validated it with TLA + before
starting off our implementation efforts. This new cluster coordination subsystem
is powering all Elasticsearch clusters since version 7, released in April 2019. The
TLA + specification is modeling the core safety bits of the consensus algorithm with
dynamic reconfiguration. The implementation of this core safety module has a direct
one-to-one mapping with the TLA + specification.

* Our chaos-monkey style test infrastructure discovered a bug in the cluster state
storage layer that was related to the atomic persistence of state. This only surfaced
through randomized testing after running for months on our CI infrastructure. The
implementation was mapped onto a TLA + model to rule out other such bugs. The
TLC model checker was able to find this bug within seconds.

All Elasticsearch TLA + specifications are open-source and publicly available on our Github
repository, just as the actual system that is modeled.
