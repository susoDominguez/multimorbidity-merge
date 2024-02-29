# <mark>`DB-HT-OA-merge`</mark>

| Metadata | Value
| ---- | ----
| specificationVersion | 1.0
| hookVersion | 2,0
| hookMaturity | [0 - Draft](../../specification/1.0/#hook-maturity-model)

## Workflow

<mark>The `DB-HT-OA-merge` hook is triggered when the practitioner is assessing the severity of the current patient's diabetes or hypertension or osteoarthritis.</mark>

## Context
<mark>The context contains information on the diagnoses of the patient with respect to the multimorbidity scenario.</mark>

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
<mark>`encounterId`</mark> | REQUIRED | Yes | *string* | <mark>identifier of current encounter</mark>
<mark>`patientId`</mark> | REQUIRED | Yes | *string* | <mark>identifier of current patient</mark>
<mark>`practitionerId`</mark> | REQUIRED | Yes | *string* | <mark>identifier of current practitioner</mark>
<mark>`diabetes`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest diabetes diagnoses, if existing. Then, field `clinicalStatus` is either *active* or *recurrence* or *relapse*, and `verificationStatus` is either *confirmed* or *provisional*.</mark>
<mark>`hypertension`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest hypertension diagnoses, if existing. Then, field `clinicalStatus` is either *active* or *recurrence* or *relapse*, and `verificationStatus` is either *confirmed* or *provisional*.</mark>
<mark>`osteoarthritis`</mark> | OPTIONAL | No | *object* | <mark>FHIR Condition resource with the latest osteoarthritis diagnosis, if existing. Then, field `clinicalStatus` is either *active* or *recurrence* or *relapse*, and `verificationStatus` is either *confirmed* or *provisional*.</mark>

### Example
```json
{
    "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea",
    "hook": "DB-HT-OA-merge",
    "context": {
        "encounterId": "285064-0",
        "patientId": "dummyPatient",
        "diabetes": {
            "resource": {
                "resourceType": "Condition",
                "id": "DB",
                "clinicalStatus": "active",
                "verificationStatus": "confirmed",
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
                    "coding": [{
                        "system": "http://snomed.info/sct",
                        "code": "46635009",
                        "display": "Diabetes mellitus type 1"
                    }]
                },
                "subject": {
                    "reference": "Patient/1677163"
                }
            }
        },
        "hypertension": {
            "resource": {
                "resourceType": "Condition",
                "id": "HT",
                "clinicalStatus": "active",
                "verificationStatus": "confirmed",
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
                    "coding": [{
                        "system": "http://snomed.info/sct",
                        "code": "73410007",
                        "display": "Benign secondary renovascular hypertension (disorder)"
                    }]
                },
                "subject": {
                    "reference": "Patient/1677163"
                }
            }
        },
        "osteoarthritis": {
            "resource": {
                "resourceType": "Condition",
                "id": "oa",
                "clinicalStatus": "active",
                "verificationStatus": "confirmed",
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
                    "coding": [{
                        "system": "http://snomed.info/sct",
                        "code": "15705241000119106",
                        "display": "Chondrocalcinosis of bilateral shoulders (disorder)"
                    }]
                },
                "subject": {
                    "reference": "Patient/1677163"
                }
            }
        }
    }
}
```

## Change Log

Version | Description
---- | ----
1.0 | FHIR resource parameters
