# Relay Asset Studio

A creative production workflow that keeps product context, generated imagery, editable composition, approval, and asset history together.

**AI creative systems · Ecommerce production · Human review**<br>
**Status:** public case study covering a deployed internal predecessor and a separate working local service.

[Visual case study](https://saraward.ai/asset-studio) · [Validation evidence](docs/validation.md) · [Sara Ward](https://saraward.ai)

## The Problem

An image generator handles only one step in campaign production. The operator still needs the right product source, accurate copy, editable typography, appropriate dimensions, a review decision, and a usable destination. Moving between disconnected tools loses the context behind the final file.

## What I Built

- A workflow connecting commerce context, creative sources, generation, editing, review, and reuse.
- Human control over source selection, copy, crop, scale, layout, rejection, and final approval.
- Separate source imagery and finished compositions, with metadata describing their relationship.
- An independent Node.js service with its own owner access, asset storage, workflow records, and evaluation records.

## Workflow

Product context and source selection → generation or upload → editable composition → checks and human review → approved asset and provenance → configured handoff.

An operator can revise or reject the work. Generation success alone does not make an asset suitable for release.

## My Role

Product and workflow design, creative controls, application development, AI integration, evaluation design, and operating documentation. I translated production requirements into the decisions and controls an operator needs to finish and review an asset.

## Technology

**Independent service:** JavaScript / Node.js, a browser interface, asset storage, workflow records, and metadata/evaluation sidecars.<br>
**Workflow:** commerce context, AI-assisted image and copy generation, editable composition, and human approval.

This repository is documentation-only. Start with the visual case study and validation record; the private applications are not distributed here.

## AI vs Deterministic Logic

| Responsibility | Owner | Why |
| --- | --- | --- |
| Generate image and copy candidates | AI assistance | Produces options within the creative brief |
| Check required structure, storage boundaries, and workflow state | Deterministic code | Repeatable constraints need predictable enforcement |
| Assess product fidelity and creative suitability | Human review; evaluation research supports the independent workflow | A successful generation request does not establish that an asset is usable |
| Approve a finished version | Human operator | Release is an explicit creative decision |
| Preserve asset history and evaluation records | Application services | Future reuse needs context and traceability |

## QA & Human Oversight

The implementations provide different evidence:

| Implementation | Evidence and limits |
| --- | --- |
| **Internal Asset Studio** | The published case study documents a deployed creative workspace with Collections, Designer, Asset Repo, metadata, and human approval. It explicitly reports that the automated image evaluator was removed. |
| **Independent Relay Asset Studio** | Working local Node.js service with separate storage and evaluation records. Six service checks passed on September 15, 2026. Dedicated production deployment remains pending. External campaign writes are disconnected. |

The local tests cover service identity, interface delivery and syntax, a local owner session, asset/metadata/evaluation record creation, upload boundaries, and a disconnected campaign-write route. They do not establish model accuracy, full browser usability, all approval paths, or production readiness. The [validation record](docs/validation.md) explains the exact assertions and limits.

## Architecture

```mermaid
flowchart LR
    A[Product context and sources] --> B[Generate or upload]
    B --> C[Edit copy and composition]
    C --> D[Checks and human review]
    D -->|Revise| C
    D -->|Approve| E[Asset and provenance]
    E --> F[Configured handoff]
```

This is the conceptual production workflow. Deployment status and test coverage are listed separately above.

## Outcome

The internal workspace connects collection context, design, review, and asset reuse. The independent implementation provides a working local service with its own storage and evaluation records. No campaign-performance, adoption, revenue, or time-saving metric is claimed.

## What I Learned

Creative production needs reviewable outputs, editable controls, and asset history as well as generation. Evaluation evidence must stay attached to the implementation it actually tested; a check passing in a local successor does not prove the deployed predecessor has that capability.

## Confidentiality

This public case study describes the system architecture and workflow while omitting proprietary source code, credentials, customer data, and internal infrastructure.
