# <mark>`multimorbidity-merge`</mark>

| Metadata | Value
| ---- | ----
| specificationVersion | 1.2
| hookVersion | 2.2
| hookMaturity | [0 - Draft](../../specification/1.0/#hook-maturity-model)

## Workflow

<mark>The `multimorbidity-interactions-detection` hook is triggered when the practitioner opens a new patient record in the electronic health record system..</mark>

## Context
<mark>The context contains information on the active diagnoses of the patient with respect to the multimorbidity scenario.</mark>

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
<mark>`patientId`</mark> | REQUIRED | Yes | *string* | <mark>FHIR `patient.id` identifier of current patient.</mark>
<mark>`encounterId`</mark> | REQUIRED | Yes | *string* | <mark>FHIR `encounter.id` identifier of current encounter.</mark>
<mark>`clinicalConditions`</mark> | REQUIRED | Yes | *object* | <mark>FHIR Bundle of Condition resources with *category* representing a Diagnosis or problem list item *code*, and  either `active` or `recurrent` or `relapse` *code* in *clinicalStatus*, and `confirmed` or `provisional` *code* in *verificationStatus*.</mark>

### Example
```json
{
  "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea",
  "hook": "multimorbidity-interactions-detection",
  "context": {
    "patientId": "123456",
    "encounterId": "78910",
    "clinicalConditions": {
      "resourceType": "Bundle",
      "entry": [
        {
          "resource": {
            "resourceType": "Condition",
            "id": "OA",
            "clinicalStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
                  "code": "relapse"
                }
              ]
            },
            "verificationStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
                  "code": "confirmed"
                }
              ]
            },
            "category": [
              {
                "coding": [
                  {
                    "system": "http://terminology.hl7.org/CodeSystem/condition-category",
                    "code": "problem-list-item",
                    "display": "Problem List Item"
                  }
                ]
              }
            ],
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "394991004",
                  "display": "Exacerbation of osteoarthritis"
                }
              ]
            },
            "subject": {
              "reference": "Patient/123456"
            }
          }
        },
        {
          "resource": {
            "resourceType": "Condition",
            "id": "DM",
            "clinicalStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
                  "code": "active"
                }
              ]
            },
            "verificationStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
                  "code": "confirmed"
                }
              ]
            },
            "category": [
              {
                "coding": [
                  {
                    "system": "http://terminology.hl7.org/CodeSystem/condition-category",
                    "code": "encounter-diagnosis",
                    "display": "Encounter Diagnosis"
                  }
                ]
              }
            ],
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "46635009",
                  "display": "Diabetes mellitus type 1"
                }
              ]
            },
            "subject": {
              "reference": "Patient/123456"
            }
          }
        },
        {
          "resource": {
            "resourceType": "Condition",
            "id": "HT",
            "clinicalStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-clinical",
                  "code": "active"
                }
              ]
            },
            "verificationStatus": {
              "coding": [
                {
                  "system": "http://terminology.hl7.org/CodeSystem/condition-ver-status",
                  "code": "confirmed"
                }
              ]
            },
            "category": [
              {
                "coding": [
                  {
                    "system": "http://snomed.info/sct",
                    "code": "439401001",
                    "display": "Diagnosis"
                  }
                ]
              }
            ],
            "code": {
              "coding": [
                {
                  "system": "http://snomed.info/sct",
                  "code": "73410007",
                  "display": "Benign secondary renovascular hypertension (disorder)"
                }
              ]
            },
            "subject": {
              "reference": "Patient/dummy"
            }
          }
        }
      ]
    }
  }
}

```

## Change Log

Version | Description
---- | ----
1.0 | FHIR resource parameters
