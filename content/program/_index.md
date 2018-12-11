+++
title = "Program"
weight = 200
+++

```tla

Schedule(t) == ...

Talks == UNION { {"case studies","success stories"},
                 {"TLC",  "Toolbox", "TLAPS", "SANY"},
                 {"teaching", "courses"} }

\A talk \in Talks : Schedule(talk)

```
