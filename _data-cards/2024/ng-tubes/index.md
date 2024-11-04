---
title: Nagogastric feeding tube misplacement
toc: true
toc_sticky: false
excerpt: Medical imaging to detect misplaced NG tubes
---

## Summary

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


## Synthetic OMOP

These data are modelled using the OMOP Common Data Model v5.3.

### CSV files

The name of the file corresponds to the table in the OMOP CDM.

<iframe src="https://widgets.figshare.com/articles/25676298/embed?show_title=0" width="568" height="351" allowfullscreen frameborder="0"></iframe>

### Correlated Data Source

- NG tube vocabularies

### Generation Rules

- The patient's age should be between 18 and 100 at the moment of the visit.
- Ethnicity data is using 2021 census data in England and Wales ([Census in England and Wales 2021](https://www.ons.gov.uk/peoplepopulationandcommunity/culturalidentity/ethnicity/bulletins/ethnicgroupenglandandwales/census2021))  .
- Gender is equally distributed between Male and Female (50% each).
- Every person in the record has a link in procedure_occurrence with the concept "Checking the position of nasogastric tube using X-ray"
- 2% of person records have a link in procedure_occurrence with the concept of "Plain chest X-ray"
- 60% of visit_occurrence has visit concept "Inpatient Visit", while 40% have "Emergency Room Visit"

#### Notes

- Version 0
- Generated by man-made rule/story generator
- Structural correct, all tables linked with the relationship
- We used national ethnicity data to generate a realistic distribution (see below)



### 2011 Race Census figure in England and Wales

| Ethnic Group                                                                                   | Population(%) |
|------------------------------------------------------------------------------------------------|---------------|
| Asian or Asian British: Bangladeshi | 1.1 |
| Asian or Asian British: Chinese | 0.7 |
| Asian or Asian British: Indian | 3.1 |
| Asian or Asian British: Pakistani | 2.7 |
| Asian or Asian British: any other Asian background | 1.6 |
| Black or African or Caribbean or Black British: African | 2.5 |
| Black or African or Caribbean or Black British: Caribbean | 1 |
| Black or African or Caribbean or Black British: other Black or African or Caribbean background | 0.5 |
| Mixed multiple ethnic groups: White and Asian | 0.8 |
| Mixed multiple ethnic groups: White and Black African | 0.4 |
| Mixed multiple ethnic groups: White and Black Caribbean | 0.9 |
| Mixed multiple ethnic groups: any other Mixed or multiple ethnic background | 0.8 |
| White: English or Welsh or Scottish or Northern Irish or British | 74.4 |
| White: Irish | 0.9 |
| White: Gypsy or Irish Traveller | 0.1 |
| White: any other White background | 6.4 |
| Other ethnic group: any other ethnic group | 1.6 |
| Other ethnic group: Arab | 0.6 |

## Example (synthetic) images

### Model

A Hugging Face Unconditional image generation Diffusion Model was used for training. [1] Unconditional image generation models are not conditioned on text or images during training. They only generate images that resemble the training data distribution. The model usually starts with a seed that generates a random noise vector. The model will then use this vector to create an output image similar to the images used to train the model.
The training script initializes a UNet2DModel and uses it to train the model. [2] The training loop adds noise to the images, predicts the noise residual, calculates the loss, saves checkpoints at specified steps, and saves the generated models.

### Training Dataset

The RANZCR CLiP dataset was used to train the model. [3] This dataset has been created by The Royal Australian and New Zealand College of Radiologists (RANZCR) which is a not-for-profit professional organisation for clinical radiologists and radiation oncologists. The dataset has been labelled with a set of definitions to ensure consistency with labelling. The normal category includes lines that were appropriately positioned and did not require repositioning. The borderline category includes lines that would ideally require some repositioning but would in most cases still function adequately in their current position. The abnormal category included lines that required immediate repositioning. 30000 images were used during training. All training images were 512x512 in size.
Computational Information
Training has been conducted using RTX 6000 cards with 24GB of graphics memory. A checkpoint was created after each epoch was saved with 220 checkpoints being generated so far. Each checkpoint takes up 1GB space in memory. Generating each epoch takes around 6 hours. Machine learning libraries such as TensorFlow, PyTorch, or scikit-learn are used to run the training, along with additional libraries for data preprocessing, visualization, or deployment.

<iframe src="https://widgets.figshare.com/articles/25676277/embed?show_title=0" width="568" height="351" allowfullscreen frameborder="0"></iframe>

### References

1. https://huggingface.co/docs/diffusers/en/training/unconditional_training#unconditional-image-generation
2. https://github.com/huggingface/diffusers/blob/096f84b05f9514fae9f185cbec0a4d38fbad9919/examples/unconditional_image_generation/train_unconditional.py#L356
3. https://www.kaggle.com/competitions/ranzcr-clip-catheter-line-classification/data
