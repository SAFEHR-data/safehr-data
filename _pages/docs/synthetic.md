---
permalink: /docs/synthetic
title: "Synthetic Data"
---

The synthetic data we share here is fabricated from health statistics that are already in the public domain, or has been approved for public release by a standard disclosure control procedure for publishing heatlh infomration. Such data are labelled "artificial data" by NHS England. We choose to label it 'publicy-sourced' to make clear that it has never had a direct connection with real patient data.

Our publicly-sourced synthetic data takes the structure of a real dataset and applies publicly-available statistical information. This statistical information is either already in the public domain (e.g., distribution of patient ages), or has been approved for public release using a standard disclosure control procedure for publishing health information. There is no link back to individual patient records; any attempt to reverse-engineer the publicly-sourced synthetic data would only yield the same aggregate statistics on which the publicly-sourced synthetic data is based. Since publicly-sourced synthetic data is entirely generated from dataset structures and statistical information approved for public release, with no direct access to individual personal data, the disclosure risk it carries is the same as that carried by aggregated information that may be openly published for clinical governance,  public health, and freedom of information reporting – i.e., zero. It is not “personal data”.

Please see [SQL Synthetic Generator](synthetic/sqlsynthgen.md) for details of the implementation at UCLH using sqlsynthgen. And to learn more checkout this [Introduction to Synthetic Data](https://www.researchdata.scot/engage-and-learn/data-explainers/intro-to-synthetic-data/) from HDR-UK, and Research Data Scotland.
