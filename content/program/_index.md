+++
title = "Program"
weight = 200
+++

```tla

Schedule(t) == ...

Keynote == {"Dharmak Shukla - Cosmos DB"}

Talks == UNION { {"case studies","success stories"},
                 {"TLC",  "Toolbox", "TLAPS", "SANY"},
                 {"teaching", "courses"} }

\A talk \in (Talks \cup Keynote) : Schedule(talk)

```
