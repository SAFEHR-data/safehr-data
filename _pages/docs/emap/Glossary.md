---
title: Glossary
---

## A


- <a id="a_e">**A & E**</a>

	Accident and Emergency department in a hospital. Also know as [ED](#ed)

- <a id="adt">**ADT**</a>

	Admission, Discharge and Transfer Data.

- <a id="atos">**ATOS**</a>

	Hospital IT Contractor

- <a id="audit">**Audit classes**</a>

	Code used to keep track of hospital data that has been corrected/deleted to allow for a complete trail of changes
    in an item of data to be preserved.

## B

- <a id="boiler">**Boilerplate code**</a>

	In computer programming, boilerplate code or just boilerplate are sections of code that are repeated in multiple places with little to no variation.


## C

- <a id="caboodle">**Caboodle**</a>

	Database used by [EPIC](#epic) for reporting purposes. Updated every 24 hours with the data available
    through live streams. More processing makes data more readable than [Clarity](#clarity), another reporting database.
    Within the UCLH intranet, you can access the [Caboodle Dictionary](https://uclvwlbpraecb01.uclh201.net/Warehouse) to explore the tables.

- <a id="ccu">**CCU**</a>

	Critical Care Unit.

- <a id="chron">**Chronicles**</a>

	The live data store of the running [Epic application](#epic). Live chronicles is the data you interact with when
    using Epic. A second copy of the live data is available through [Shadow-Chronicles](#shadowchron).

- <a id="ci">**Continuous Integration**</a>

	Continuous Integration. The practice of automating the integration of code changes from multiple contributors into a software project.

- <a id="clarity">**Clarity**</a>


	Database used by [EPIC](#epic) the purpose of reporting. Updated every 24 hours. Holds
    data that is otherwise not available through any of the other databases, e.g. [Caboodle](#caboodle).

- <a id="csn">**CSN**</a>

	The Contact Serial Number, assigned to a patient on arrival at the hospital, is related to a particular visit. Within [EPIC}(#epic) many interactons are related to the patient via the CSN. Note though that not every patient is assigned
    a CSN. Information relevant to a patient is available through the CSN or [MRN](#mrn) of a patient.

- <a id="ci">**Continuous integration**</a>

	An automated test pipeline that runs test code automatically when code is committed to a
	repository.

- <a id="criu">**CRIU**</a>

	Clinical Research Informatics Unit.

	A group within the Trust who work on trying to develop the research capability of the hospital.

## D

- <a id="debug">**Debugging**</a>

	Debugging tries to find where and why a particular, possibly unexpected behaviour occurs.

- <a id="docker">**Docker container**</a>

	A [Docker](https://www.docker.com/) container image is a lightweight, standalone, executable package of software that includes everything needed to run an application.

## E

- <a id="eav">**EAV**</a>

	Entity Attribute Value is a representation whereby entities are described with attributes, and these attributes are
    then further described with values. For example, a patient could be the entity with an attribute age, which could
    have the value 56.

- <a id="ed">**ED**</a>

	Emergency Department of a hospital. Also known as [A & E](#a_e).

- <a id="ehrs">**EHRS**</a>

	Electronic Health Record System

- <a id="emap">**EMAP**</a>

	Experimental Medicine Application Platform; collects data from several reporting databases (including [Caboodle](#caboodle) and
    [Clarity](#clarity)) and live data streams. See [Technical Overview](./technical_overview/Technical_overview_of_EMAP.md)

- <a id="epic">**EPIC**</a>

	Epic systems is one of the largest providers of health information technology. Epic is a complete suite of
    applications which can cater to all sections of the hospital and can be customised for a particular institute.

- <a id="etl">**ETL**</a>

	ETL, which stands for extract, transform and load, is a data integration process that combines data from multiple data sources into a single, consistent data store that is loaded into a data warehouse or other target system.

## F

- <a id="flowsheets">**Flowsheets**</a>

	Flowsheets within hospital data refer to data taken as a measurements over a period of time.

- <a id="fk">**Foreign Key**</a>

	A foreign key is a column or group of columns in a [relational database](#db) table that provides a link between data in two tables.
	It acts as a cross-reference between tables because it references the [primary key](#pk) of another table, thereby establishing a link between them.

## G

- <a id="gae">**GAE**</a>

	Generic application environment.

- <a id="get">**getter**</a>

	Term used to refer to computer code used to retrieve types of data e.g. a function getName() would be used to
    retrieve the 'name' piece of data. Counterpart of setter.

## H

- <a id="hic">**HIC**</a>

	Health Informatics Collaborative. The [NIHR](#nihr) HIC is a collaboration between NHS trusts, each of which has a strong relationship with a partner university.

- <a id="hl7">**HL7**</a>

	Health Level 7 International is a set of standards for sharing, intergrating, and exchanging electronic healthcare
	information, e.g. patient or clinical staff information in a hospital. For detailed information see
    [here](https://www.hl7.org/about/index.cfm?ref=nav).

- <a id="hoov">**Hoover**</a>

	Is the component of the [EMAP pipeline](#emap) that collects relevant data from reporting databases including
    [Clarity](#clarity) and [Caboodle](#clarity).

- <a id="hos_num">**Hospital number**</a>

	A unique identifier for an individual within a hospital. Also known as [MRN](#mrn).

- <a id="hsl">**HSL**</a>

	Health Service Laboratories provide the biochemistry and microbiology analysis for the hospital.
	Made up of a number of partners [TDL](#tdl) , [UCLH](#uclh) and the Royal Free London Trust.

## I

- <a id="icu">**ICU**</a>

	Intensive Care Unit, a specialist hospital ward that provide treatment and monitoring for people who require life support.


- <a id="ids">**IDS**</a>

	Immutable Data Store is the database that receives all live [HL7](#hl7) messages being sent by the systems within the hospital
	e.g. Epic, WinPath, CoPath, glucose monitors etc. This
    database is currently never deleted, and thus holds a record of all live HL7 messages sent since the time point at
    which [Epic](#epic) was turned on.

- <a id="indexing">**Indexing**</a>

	A database index allows a query to efficiently retrieve data from a database. Indexes are related to specific
    tables and consist of one or more keys.

- <a id="inttest">**Integration testing**</a>

	Testing that different modules of software are working together.

## J

- <a id="join">**Join**</a>

	A JOIN clause is used to combine rows from two or more tables, based on a related column between them, e.g. all
    the lab results for a patient the information for which are kept in different tables in the [USD](#usd)

## K

- <a id="key">**Key**</a>

	Keys are used to establish and identify relationships between database tables and also to uniquely identify any
    record or row of data inside a table.

## L

- <a id="linting">**Linting**</a>

	Automatic checking of source code for errors and style problems. While there are a lot of tests that can be
    automated, at the same time there are limitations to these automated checks.

## M

- <a id="mdt">**MDT**</a>

	Multi-disciplinary team.

- <a id="mrn">**MRN**</a>

	Medical Record Number assigned to a patient arriving in the hospital. Also referred to as [Hospital number](#hos_num). These are the canonical internal representation of identity (as opposed to [NHS Number](#nhs_num)) which is an external identifier). MRNs try to be mapped 1:1 to real people. This is practically difficult, so while a single person may have many MRNs over the course of their life, they should most of the time only have 1 active MRN within a given Trust. Much of the information relating to a patient
    can be retrieved by either the MRN or [CSN](#csn).

## N

-  <a id="nhs">**NHS**</a>

	National Health Service

- <a id="nhs_num">**NHS Number**</a>

	Number assigned to each individual to provide a unique reference number to the inividual within the NHS. If you are born in the UK this number is assigned at birth.

-  <a id="nihr">**NIHR**</a>

	[National Insistute for Health Research](https://www.nihr.ac.uk/) funds, enables and delivers world-leading health and social care research that improves people's health and wellbeing and promotes economic growth.

## O

- <a id="omop">**OMOP**</a>

	[Observational Medical Outcomes Partnership](https://www.ohdsi.org/omop/) was A public-private partnership
    established to inform the appropriate use of observational healthcare databases for studying the effects of medical
    products. Is now superseeded by
    [Observational Health Data Science and Informatics](https://www.ohdsi.org/data-standardization/the-common-data-model/).

- <a id="openehr">**openEHR**</a>

	[openEHR](https://www.openehr.org/) is the name of a technology for e-health, consisting of open specifications, clinical models and software that can be used to create standards, and build information and interoperability solutions for healthcare.

- <a id="openemr">**OpenEMR**</a>

	[OpenEMR](https://github.com/openemr/openemr) is an open source electronic health records and medical practice
    management solution.

## P

- <a id="poc">**POC**</a>

	Point Of Care testing; these are tests that can done with results generated at bedside in situ. Examples include
    basic urine analysis and glucose level monitoring.

- <a id="pk">**Primary Key**</a>

	A primary key is a special [relational database](#db) table column (or combination of columns) designated to uniquely identify each table record.

## Q

## R

- <a id="r">**R**</a>

	[R](https://www.r-project.org/) is a free software environment for statistical computing and graphics.

- <a id="rabbit">**RabbitMQ**</a>

	[RabbitMQ](https://www.rabbitmq.com/) is a message-brokering software used in the [EMAP pipeline](#emap) to buffer communications between the different services.
	(See further documentation on use of [RabbitMQ in EMAP](./technical_overview/technologies_used/RabbitMQ.md))

- <a id="rass">**RASS**</a>

	[Richmond Agitation Sedation Scale](https://en.wikipedia.org/wiki/Richmond_Agitation-Sedation_Scale).

- <a id="db">**Relational database**</a>

	A relational database is a collection of data items with pre-defined relationships between them.
	These items are organized as a set of tables with columns and rows.
	Each row in a table could be marked with a unique identifier called a [primary key](#pk), and rows among multiple tables can be made related using [foreign keys](#fk).

- <a id="db">**RSDG**</a>

	The UCL [Research Software Development Group](https://www.ucl.ac.uk/isd/services/research-it/research-software-development) are professional software developers with particular expertise in creating software for academic research.

## S

- <a id="sde">**SDE**</a>


	Smart Data Elements, used within EPIC as a more customisable way to input form-based information.

	Similar to [flowsheets](#flowsheets), but much more based on form answers rather than clinical measurements.

- <a id="set">**setter**</a>

	Term used to refer to computer code used to set the value of data e.g. a function setName('my name') would be used to set the 'name' piece of data to the value 'my name'. Counterpart of [getter](#get).

- <a id="shard">**Sharding**</a>

	Is a process of splitting a single database into smaller pieces, e.g. to spread load and therefore increase the
    response time of the database.

- <a id="shadowchron">**Shadow chronicles**</a>

	Shadow chronicles is a copy (~1-5 seconds behind) which is used to generate reports. Strictly speaking,
    chronicles is the name of the application used to access this data, but the data itself is also referred to by the
    name.

- <a id="sip">**SIP**</a>

	Strategic Integration Platform acts as a central controller for all electronic messages sent within the
    Trust. It routes messages from various sources ([POC](#poc), [HSL](#hsl), Imaging) to be recorded in the
    appropriate databases.

- <a id="star">**SPC**</a>

	Statistical Process Control.


- <a id="star">**Star**</a>

  The [EMAP database](#emap) that contains the processed data and can be queried by users.

## T

- <a id="tdl">**TCI**</a>

	To Come In (a patient is TCI for ward X if they are on the way to the ward but not admitted).

- <a id="tdl">**TDL**</a>

	The Doctors Laboratory provide the biochemistry and microbiology analysis for the hospital.
	Made up of a number of partners [HSL](#hsl) , [UCLH](#uclh) and the Royal Free London Trust.


- <a id="trust">**Trust**</a>

	NHS trusts are public sector bodies established by parliamentary order by the secretary of state for health to provide healthcare services to the [NHS](#nhs).

## U

- <a id="uclh">**UCLH**</a>

	[UCL Hospitals NHS Foundation Trust](https://www.uclh.nhs.uk/about-us/who-we-are) oversees a number of different
    hospitals in London, providing acute and specialist care.

- <a id="unittessts">**Unit tests**</a>

	A method by which units of source code are individually tested for errors and corrected if necessary.

- <a id="uds">**UDS**</a>

	Uniform Data System. This is the storage space for the [Star database](#star).

## V

## W

## X

## Y

## Z
