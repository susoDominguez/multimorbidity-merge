# <mark>`DB-HT-OA-merge_2`</mark>

| Metadata | Value
| ---- | ----
| specificationVersion | 1.0
| hookVersion | 2,0
| hookMaturity | [0 - Draft](../../specification/1.0/#hook-maturity-model)

## Workflow

<mark>The `multimorbidities-merge` hook is triggered when the practitioner is assessing the severity of a clinical condition displayed by the current patient.</mark>

## Context
<mark>The context contains information on the diagnosis of the patient with respect to the multimorbidity scenario.</mark>

Field | Optionality | Prefetch Token | Type | Description
----- | -------- | ---- | ---- | ----
<mark>`encounterId`</mark> | REQUIRED | Yes | *string* | <mark>identifier of current encounter</mark>
<mark>`patientId`</mark> | REQUIRED | Yes | *string* | <mark>identifier of current patient</mark>
<mark>`multimorbidities`</mark> | REQUIRED | Yes | *array* | <mark>Array of FHIR Condition resources</mark>

### Example
```json
{
    "hookInstance": "d1577c69-dfbe-44ad-ba6d-3e05e953b2ea",
    "hook": "multimorbidities-merge",
    "context": {
        "encounterId": "285064-0",
        "patientId": "1677163",
        "multimorbidities": [{
                "resource": {
                    "resourceType": "Condition",
                    "id": "DB",
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
            {
                "resource": {
                    "resourceType": "Condition",
                    "id": "DB",
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
            {
                "resource": {
                    "resourceType": "Condition",
                    "id": "DB",
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
        ]
    }
}
```

## Change Log

Version | Description
---- | ----
1.0 | FHIR resource parameters
