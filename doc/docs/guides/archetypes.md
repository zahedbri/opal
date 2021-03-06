# Core Clinical Archetypes

Opal ships with a wide range of core clinical concepts implemented as Abstract Subrecords.
Applications that are generated via the `$ opal startproject` command will automatically
contain concrete implementations of these models in the application.

## Common Metadata fields

All subrecords will contain the following fields, which are not repeated individually


Field|Type|Length
-----|----|---
created_by | FK | User ID
created | Date
updated_by | FK User ID
update | Date

The details of each individual archetype are set out below:

## Patient Subrecords

### Demographics

Field|Type|Length
-----|----|---
hospital_number|Char|255
nhs_number|Char|255
date_of_birth|Date|
place_of_birth| FKorFT(Destination)
ethnicity|FKorFT(Ethnicity)
surname | Char| 255
first_name | Char| 255
middle_name | Char| 255
sex| FKorFT(Gender)

### Allergies

Field|Type|Length
-----|----|---
drug | FKorFT(Drug)
provisional | Boolean
details | Char|255


## Episode Subrecords

### Location

Field|Type|Length
-----|----|---
category | Char | 255
hospital | Char| 255
ward | Char | 255
bed | Char | 255

### Treatment

Field|Type|Length
-----|----|---
drug | FKorFT(Drug) |
dose | Char | 255
route | FKorFT(Drugroute)
start_date | Date
end_date | Date
frequency | FKorFT(Drugfreq)

### Diagnosis

Field|Type
-----|----
condition | FKorFT(Condition)
provisional | Boolean
details | Text
date_of_diagnosis | Date

### PastMedicalHistory

Field|Type|Length
-----|----|---
condition | FKorFT(Condition)
year | Char | 4
details | Char | 255

### SymptomComplex

Field|Type|Length
-----|----|---
symptoms | ManyToMany(Symptom)
duration | Char | 255
details | Text

### ReferralRoute

Field|Type|Length
-----|----|---
internal | NullBoolean
referral_organisation | FKorFT(ReferralOrganisation)
referral_name | Char | 255
date_of_referral | Date
referral_team | FKorFT(Speciality)
referral_type | FKorFT(ReferralType)

### PatientConsultation

Field|Type|Length
-----|----|---
when | Datetime
initials | Char | 255
reason_for_interaction | FKorFT(Patient_consultation_reason_for_interaction)
discussion | Text
