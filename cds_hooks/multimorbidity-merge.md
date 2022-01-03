# <mark>`multimorbidity-merge`</mark>

| Metadata | Value
| ---- | ----
| specificationVersion | 1.2
| hookVersion | 2.2
| hookMaturity | [0 - Draft](../../specification/1.0/#hook-maturity-model)

## Workflow

<mark>The `multimorbidity-merge` hook is triggered when the practitioner is assessing the severity of a clinical condition displayed by the current patient.</mark>

## Context
<mark>The context contains information on the diagnosis of the patient with respect to the multimorbidity scenario.</mark>

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
<mark>`patientId`</mark> | REQUIRED | Yes | *string* | <mark>FHIR `patient.id` identifier of current patient.</mark>
<mark>`encounterId`</mark> | REQUIRED | Yes | *string* | <mark>FHIR `encounter.id` identifier of current encounter.</mark>
<mark>`multimorbidity`</mark> | REQUIRED | Yes | *object* | <mark>FHIR Bundle of Condition resources with `active` *code* in *clinicalStatus*, and `confirmed` *code* in *verificationStatus*.</mark>

### Example
```json
{
  "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea",
  "hook": "multimorbidities-merge",
  "context": {
    "patientId": "dummyPatient",
    "encounterId": "285064-0",
    "multimorbidity": {
      "resourceType": "Bundle",
      "entry": [
        {
          "resource": {
            "resourceType": "Condition",
            "id": "family-history",
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
                  "code": "312824007",
                  "display": "Family history of cancer of colon"
                }
              ]
            },
            "subject": {
              "reference": "Patient/example"
            }
          }
        },
        {
          "resource": {
            "resourceType": "Condition",
            "id": "DB",
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
                  },
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
                  "code": "46635009",
                  "display": "Diabetes mellitus type 1"
                }
              ]
            },
            "subject": {
              "reference": "Patient/1677163"
            }
          }
        },
        {
          "resource": {
            "resourceType": "Condition",
            "id": "DB",
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
                  },
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
              "reference": "Patient/1677163"
            }
          }
        },
        {
          "resource": {
            "resourceType": "Condition",
            "id": "DB",
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
                  },
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
                  "code": "15705241000119106",
                  "display": "Chondrocalcinosis of bilateral shoulders (disorder)"
                }
              ]
            },
            "subject": {
              "reference": "Patient/1677163"
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
