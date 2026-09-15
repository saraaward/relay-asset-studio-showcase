# Validation evidence

[Back to project](../README.md)

## Existing independent service checks

Run locally on September 15, 2026 using the private independent service's existing `npm test` command. Result: **6 passed, 0 failed**.

| Check | What the assertion establishes |
| --- | --- |
| Independent service identity | The health response identifies the service and reports no CRM runtime dependency |
| Standalone interface | Supported local routes serve the expected Asset Studio interface |
| Interface syntax | Inline JavaScript parses successfully |
| Local owner session and asset records | A local owner session can create a test upload, metadata, and an evaluation sidecar; the deliberately invalid image is recorded as a failed evaluation |
| Upload target boundary | An upload aimed outside the independent service is rejected |
| External campaign boundary | The disconnected campaign-write route returns a blocking response |

The suite starts a local service and uses a synthetic image in temporary storage. It does not send a campaign or call an image-generation provider.

## Limits of this evidence

- Local owner behavior does not prove every production authentication condition.
- A failed evaluation record does not prove calibrated vision-model accuracy or enforcement of every approval path.
- Serving the interface does not constitute a complete browser usability test.
- No production deployment, efficiency metric, adoption total, or revenue outcome was measured by this run.

## Keep the implementations distinct

The [published internal Asset Studio case study](https://saraward.ai/asset-studio) describes the deployed predecessor and its current human-approval workflow. The independent service has its own QA and storage work. Results from one implementation should not be used as evidence for the other.

## Implementation details

- The internal workspace uses human approval; its published case study reports that the automated image evaluator was removed.
- The independent service has separate storage and evaluation records. Dedicated production deployment remains pending, and external campaign writes are disconnected.
- Local checks validate selected service behavior. They do not establish model accuracy, full browser usability, every approval path, or production readiness.
