# <mark>`multimorbidities-merge`</mark>

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
<mark>`patientId`</mark> | OPTIONAL | Yes | *string* | <mark>FHIR `patient.id`identifier of current patient</mark>
<mark>`multimorbidity`</mark> | REQUIRED | Yes | *object* | <mark>FHIR Bundle of Condition resources with `active` or `recurrence` or `relapse` clinicalStatus</mark>

### Example
```json
{
  "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea",
  "hook": "multimorbidities-merge",
  "context": {
    "patientId": "1677163",
    "multimorbidity": {
      "resourceType": "Bundle",
      "entry": [
        {
          "resource": {
            "resourceType": "Condition",
            "id": "DB",
            "clinicalStatus" : "recurrent",
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
            "clinicalStatus" : "active",
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
            "clinicalStatus" : "recurrent",
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
