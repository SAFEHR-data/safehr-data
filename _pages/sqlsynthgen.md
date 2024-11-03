---
layout: archive
---

## Implementation at UCLH using sqlsynthgen

*SQLSYNTHGEN* (SSG), a portmanteau of 'SQL Synthetic Generator', is a [[software tool]{.underline}](https://github.com/alan-turing-institute/sqlsynthgen) designed by a team ([[May Yong]{.underline}](https://www.turing.ac.uk/people/researchers/may-yong), [[Ian Stenson]{.underline}](https://www.turing.ac.uk/people/research-engineering/iain-stenson), and [[Markus Hauru]{.underline}](https://www.turing.ac.uk/people/researchers/markus-hauru)) working under Professor [[Carsten Maple]{.underline}](https://www.turing.ac.uk/people/researchers/carsten-maple) at the Alan Turing Institute.

SSG creates synthetic replicas of relational (SQL) databases. By default, whilst it reliably replicates the *structure* of the database, it will only populate that structure with random data using another tool called [[Mimesis]{.underline}](https://mimesis.name/en/master/index.html).

> Fake data refers to data that is not useful or sensitive, but is used to occupy a space where real data is typically located.

We believe that there are two key features of SSG that crucial to our work.

1.  The decision making is transparent. A single file written in human readable code is used to configure the tool, and document where a user decides to improve the fidelity of the synthetic data by learning from the source data.

2.  Statistical Disclosure Control decisions are part of the workflow using an approach called [[differential privacy]{.underline}](https://en.wikipedia.org/wiki/Differential_privacy) which provably defends against re-identification attacks.[^5]

We use the worked example from the [[tutorial]{.underline}](https://sqlsynthgen.readthedocs.io/en/latest/introduction.html) for SSG to provide a brief overview. In this example, the task is to create a synthetic copy of a [[database]{.underline}](https://www.kaggle.com/competitions/airbnb-recruiting-new-user-bookings/overview) containing AirBnB bookings. This contains four linked tables: a table of users (containing gender, age etc.), a table of booking destinations (called 'countries' and containing distance, language etc.), and table of web sessions (where the user interacted with the website containing ). There is also a summary table that groups users by age, gender and country destination. The idea is to predict the country that a user is likely to visit.

![](media/image1.png){width="6.925in" height="5.599169947506562in"}

Synthetic data generation proceeds as follows. The notes below summarise the documentation, demonstrate some of the basic commands, and highlight the generated data. The code snippets are commented but we skip some steps to improve readability. You will need to follow the actual documentation if you wish to test this properly.

### Complete independence from the source data

The first step creates and then runs a little application that only mimics the structure of the source data. From the documentation, these two commands

\# create the application to mimic the source data\
sqlsynthgen make-tables\
\# run the application to mimic the source data\
sqlsynthgen create-tables

> This creates an [[ssg.py]{.underline}](https://ssg.py) file that contains one generator class (not to be confused with Python generator functions) per source database table. By default, without any user configuration, the data produced by these generators fulfills the schema of the original data: the data types are correct and the foreign key and uniqueness constraints are respected.

The means that a source table, the original real data, that looks like this \...

  ---------------- ------------------------- -------------- ----------------------------- --------------
  **age_bucket**   **country_destination**   **gender**     **population_in_thousands**   **year**

  100+             AU                        male           1                             2015
  ---------------- ------------------------- -------------- ----------------------------- --------------

\... is recreated synthetically so that it looks like this.

  ---------------- ------------------------- -------------- ----------------------------- --------------
  **age_bucket**   **country_destination**   **gender**     **population_in_thousands**   **year**

  8k\$X-en         vQjTJ=p\*                 1m\>?l\]"}     485                           534
  ---------------- ------------------------- -------------- ----------------------------- --------------

The *structure* is correct but the *contents are nonsense*.

### Informed independence

At this stage, we use our own 'expert' knowledge to improve the quality of the table above. For example, rather than the nonsense strings for country and gender, we can randomly sample from actual country codes, and gender categories. The data are structurally more accurate because we are using a list of valid countries, but because we are picking *randomly* then we have learned nothing about the data.

  ---------------- ------------------------- -------------- ----------------------------- --------------
  **age_bucket**   **country_destination**   **gender**     **population_in_thousands**   **year**

  8k\$X-en         UK                        female         485                           534
  ---------------- ------------------------- -------------- ----------------------------- --------------

In a similar manner, we may want to enforce some logical constraints. Imagine there was a table of hospital admissions that contained both the date of admission, and the date of birth. It would make no sense for the date of birth to be after the date of admission. SSG allows the user to specify this logic in a transparent manner.

  ----------------------- ----------------------- -----------------------
  **name**                **date_of_birth**       **date_of_admission**

  TK53EDBJ                1974-10-21              2021-02-14

  BY13UILQ                2016-12-29              [1985-10-04]{.mark}
  ----------------------- ----------------------- -----------------------

  ----------------------- ----------------------- -----------------------
  **name**                **date_of_birth**       **date_of_admission**

  TK53EDBJ                1974-10-21              2021-02-14

  BY13UILQ                [1962-11-01]{.mark}     1985-10-04
  ----------------------- ----------------------- -----------------------

### Utilisation of Aggregate Data with Privacy Techniques

The final step is to use qualities of the data itself to help improve the fidelity of the synthetic data generation. Using the same table above, it might be desirable to simulate data so the ages were similar to the source. For example, we can calculate the mean and the standard deviation of people's age from the source data. These aggregate values and *only* these aggregate values are passed to the synthetic data generating step. The random age values that are manufactured and inserted into the synthetic data are now constrained to have the same mean and standard deviation.

![](media/image2.png){width="6.925in" height="4.62711176727909in"}

A histogram of real age values from which the mean and the standard deviation are calculated

![](media/image3.png){width="6.925in" height="4.62711176727909in"}

A histogram of synthetic age values built using only the mean and the standard deviation of the real values

Where there is a risk of releasing private information from these aggregate statistics, we can take the additional step of adding additional random noise during the synthetic data generation. For example, if all patients have the *same* age, then the standard deviation would be zero, and the mean reveal the real age. Here the SSG tool uses differential privacy to identify that these aggregate statistics themselves might leak data, and insert additional noise (here so the standard deviation is not zero) to guarantee against re-identification.

[^1]:  Data are often organised as a set of linked tables. There might be a table of patients describing age, gender, and ethnicity. This would be linked to a table of COVID tests describing the date of the test and the result, and another table of hospital admissions. Any analysis will need to navigate these tables and assemble the information so that we can ask which patients had tests, and who needed hospital admission following a positive test result.

[^2]:  We would always check these tables for small numbers; perhaps originally the highest age category was greater than 100 years, but there is only one person in that age band. This would present a re-identification risk if the local newspaper had reported people who had recently celebrated their 100th birthday, so we broaden the highest age band to greater than 80 years which now contains tens of individuals.

[^3]:  Arenas, D. et al. Design choices for productive, secure, data-intensive research at scale in the cloud. Preprint at [[https://doi.org/10.48550/arXiv.1908.08737]{.underline}](https://doi.org/10.48550/arXiv.1908.08737) (2019).

[^4]:  In 2006, Cynthia Dwork, Frank McSherry, Kobbi Nissim, and Adam D. Smith introduced a privacy safeguard called ε-differential privacy. They aimed to turn big sets of confidential data into statistics without breaching the privacy of the people who supplied the data.

    Their idea for ε-differential privacy was basically this: If your data isn\'t included in the database, you can\'t have your privacy breached. So, they aimed to make sure that everyone\'s privacy was about as safe as if their data had been left out. This means that the statistical analysis shouldn\'t overly rely on any one person\'s data.

    They also noted that how much each person contributes to the statistical results depends on how many people\'s data is included. For instance, if it\'s just one person\'s data, then they contribute 100%. But if 100 people\'s data is included, each only contributes 1%.

    The real breakthrough of differential privacy lies in its idea that the fewer people\'s data you have, the more \'noise\' (random data) you need to add to the results to keep privacy levels high. This is why they called their 2006 paper, \"Calibrating noise to sensitivity in private data analysis.\" Simply put, it means adjusting the balance between the amount of confidential data used and the randomness added to keep things private.

[^5]:
