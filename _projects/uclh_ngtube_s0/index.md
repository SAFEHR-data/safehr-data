---
layout: project
title: Detecting misplaced NG tubes
status: ongoing
tags: imaging, safety
authors:
- SAFEHR team

tabs:
- {
    name: uclh-ngt-s0-quarto,
    type: html,
    source: omop_concepts_frequency_table.html,
    label: Data summary
  }
- {
  name: uclh-ngt-s0-ehr-data,
  type: md,
  source: _03_data.md,
  label:  Synthetic EHR
  }
- {
  name: uclh-ngt-s0-image-data,
  type: md,
  source: _04_image.md,
  label:  Synthetic CXR
  }
---

A Nasogastric tube (NGT) is a thin tube that is passed into the stomach via the nose for short- to medium-term nutritional support, medication administration or aspiration of stomach contents. NGTs are amongst the most commonly used catheters in critically ill patients in intensive care units (ICU) and high-dependency units and departments where patients require nutritional-support (i.e., Stroke units). Due to increases in the number of hospitalized patients, it is estimated that approximately 10 million NGTs are used annually in Europe, 1 million of which in the UK (~1.2 million in the US).

Previous research highlights a variety of complications associated with NGT placement, which can range from minor cases of nose bleeds to inhalation of stomach contents into the lung and even death. Instances of unknowingly misplaced NGTs being used for feeding, with the feed entering the patients lungs are classified by the NHS as Never Events: “serious incidents that are entirely preventable because guidance or safety recommendations providing strong systemic protective barriers are available at a national level, and should have been implemented by all healthcare providers”.

While all this highlights the importance for feeding tubes in particular to be placed properly and used safely, clinical studies demonstrate that up to 3% of NGTs are reported as misplaced into the airways, causing complications in up to 40% of these cases.

Given the serious complications that can occur from NGT misplacement, UCLH has a detailed policy  describing the indications and technique of NGT insertion alongside nationally agreed standards for positioning verification. This includes training and guidelines for doctors or reporting radiographers  when checking NGT position radiographically. In this policy, the first line of test in confirming the correct positioning of a feeding tube is by obtaining a sample of fluid from the stomach that shows a level of acidity indicative of the stomach. However, since this cannot be achieved successfully for some patients, and with a large proportion of ICU patients receiving anti-acid medication, the use of CXRs remains the most definitive test for checking NGT placement.

Due to the large number of CXRs obtained each day, especially in intensive and emergency care, and with a limited number of radiologists available, image interpretation can be substantially delayed. Thus, current practices indicate that it is often emergency and ICU doctors who check the CXR to verify the NGT’s correct positioning and suitability for use prior to the radiology report being issued.  Yet, such assessments by non-radiologists working in stressful situations when hospitals are capacity, are prone to both human error and some delays in assessment. This means that sub-optimally positioned NGTs can be missed initially, but are often picked up by the radiologists later. This emphasizes the importance of early detection of misplaced NGTs to allow for more timely correction and prevent any additional complications.

We envision two main use scenarios in which an accurate, instant detection and notification of NGT misplacements from CXRs could benefit clinical practice:

(1) As an early alert to ICU doctors or nurses, it will enable prompt, data driven decision-making and NGT adjustment for more effective and safe use.
(2) As an early alert to help prioritize the review of most urgent CXRs by local (UCLH) radiologists to reduce delays in notifying ICU doctors of potentially unrecognized NGT misplacement.

Initially, this work focuses on developing a machine learning model to identify misplaced NG tubes on CXR. We will also study ML integration within the ICU at UCLH due to its already established all-digital end-to-end radiology workflow, and to ensure that the sickest, most dependent patients in the hospital will get treatment faster and more safely. In parallel, we will study requirements for future ML system roll outs to any other inpatient area that frequently places NGTs. In a first instance, this will include Stroke Departments within UCLH.

The work can also generate a training opportunity leveraging known cases of misplaced NGTs or cases that were hard to interpret on CXRs. The training datasets can upskill ICU and Stroke ward doctors who often have little experience of assessing such CXRs in routine practice.
