---
title: "SQLSynthGen"
---

## Implementation at UCLH using sqlsynthgen

*SQLSYNTHGEN* (SSG), a portmanteau of 'SQL Synthetic Generator', is a [software tool](https://github.com/alan-turing-institute/sqlsynthgen) designed by a team ([May Yong](https://www.turing.ac.uk/people/researchers/may-yong), [Ian Stenson](https://www.turing.ac.uk/people/research-engineering/iain-stenson), and [Markus Hauru](https://www.turing.ac.uk/people/researchers/markus-hauru)) working under Professor [Carsten Maple](https://www.turing.ac.uk/people/researchers/carsten-maple) at the Alan Turing Institute.

SSG creates synthetic replicas of relational (SQL) databases. By default, whilst it reliably replicates the *structure* of the database, it will only populate that structure with random data using another tool called [Mimesis](https://mimesis.name/en/master/index.html).

> Fake data refers to data that is not useful or sensitive, but is used to occupy a space where real data is typically located.

We believe that there are two key features of SSG that crucial to our work.

1.  The decision making is transparent. A single file written in human readable code is used to configure the tool, and document where a user decides to improve the fidelity of the synthetic data by learning from the source data.

2.  Statistical Disclosure Control decisions are part of the workflow using an approach called [differential privacy](https://en.wikipedia.org/wiki/Differential_privacy) which provably defends against re-identification attacks.[^5]
