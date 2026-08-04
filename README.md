# Creatify (creatify)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Creatify is an AI avatar and marketing-video generation platform that turns product URLs, scripts, images, and text into short-form video ads narrated by ultra-realistic AI avatars. The Creatify API (base `https://api.creatify.ai/api`, authenticated with `X-API-ID` / `X-API-KEY` headers) exposes AI Avatar (Lipsync v1/v2 and Aurora image-to-avatar), Link-to-Video, AI Shorts and Custom Template video generation, Text-to-Speech and voice cloning, a 1500+ Persona/avatar catalog, a voice catalog, and a music library. Generation is asynchronous - create a job, then poll the job by id or receive a webhook - with billing metered in credits.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/creatify/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/creatify/refs/heads/main/apis.yml)

## Access Model (Honest Note)

The Creatify API is real and documented at [docs.creatify.ai](https://docs.creatify.ai), but it is **not open**: API access requires an active paid subscription, and credentials (`X-API-ID` + `X-API-KEY`) are issued from the in-app API Dashboard at [app.creatify.ai](https://app.creatify.ai). Creatify's public docs describe a dedicated **API Starter** ($99/mo, 500 credits) and **API Pro** ($299/mo, 2,000 credits) tier plus Enterprise, in addition to the consumer Free/Starter/Pro plans. Every generation endpoint follows an **asynchronous create-then-poll** pattern (POST to create a job, GET the job by `id` to check `status`/`progress`, or supply a `webhook_url`), and all output is metered in **credits** (typically ~5 credits per 30 seconds of video, ~1 credit per 30 seconds of audio).

The endpoints and paths in this entry are grounded in Creatify's live API reference where a reference page was available (AI Avatar Lipsync v1/v2, Link-to-Video, AI Shorts, Text-to-Speech, Personas, Voices). A few paths for product areas without a fully-published reference page (Product-to-Video, Music categories/tracks, AI Editing) are **honestly modeled** from Creatify's documented product areas and the platform's consistent `/api/{resource}/` + `/api/{resource}/{id}/` convention, and are flagged as modeled in the OpenAPI and review files. Verify exact request/response schemas against the live docs before building.

## Tags

- AI Avatars
- Video Generation
- AI Video
- Generative AI
- Marketing Video
- Text to Speech
- UGC Ads
- AI Avatar

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### Creatify AI Avatar API

Turn text or audio plus a chosen avatar/persona into ultra-realistic talking-head videos. Lipsync v1 (single scene) and Lipsync v2 (multi-scene, with per-scene characters, voices, and backgrounds), plus the Aurora image-to-avatar model. Asynchronous - POST to create, then GET the job by id to poll status.

- **Human URL:** [https://docs.creatify.ai/api-documentation/ai-avatar/lipsync-v2](https://docs.creatify.ai/api-documentation/ai-avatar/lipsync-v2)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- AI Avatars
- AI Video
- Video Generation
- Lipsync
- Aurora

#### Properties

- [Documentation](https://docs.creatify.ai/api-documentation/ai-avatar/lipsync-v2)
- [API Reference](https://docs.creatify.ai/api-reference/text-to-speech)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Link-to-Video API

Transform a product or landing-page URL into a short-form video ad. Create a link from a URL (`POST /links/`), generate a link-to-video job, and render it (`POST /link_to_videos/{id}/render/`). Async create-then-poll; billed per 30 seconds of rendered video.

- **Human URL:** [https://docs.creatify.ai/api-reference/link_to_videos/post-apilink_to_videos_render](https://docs.creatify.ai/api-reference/link_to_videos/post-apilink_to_videos_render)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Video Generation
- Marketing Video
- URL to Video
- AI Video

#### Properties

- [Documentation](https://docs.creatify.ai/quickstart)
- [API Reference](https://docs.creatify.ai/api-reference/link_to_videos/post-apilink_to_videos_render)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify AI Shorts API

Convert a text script into a high-impact, viral short-form video (`POST /ai_shorts/`, `GET /ai_shorts/{id}/`). Accepts script, aspect ratio, and a visual style. Note - Creatify documents AI Shorts as deprecated in favor of Link-to-Video and AI Avatar; retained here for completeness.

- **Human URL:** [https://docs.creatify.ai/api-documentation/ai-shorts/ai-shorts](https://docs.creatify.ai/api-documentation/ai-shorts/ai-shorts)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Text to Video
- AI Video
- Short Form Video
- Generative AI

#### Properties

- [Documentation](https://docs.creatify.ai/api-documentation/ai-shorts/ai-shorts)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Custom Templates API

Generate videos from customizable, brand-ready templates by supplying template variables (`POST /custom_templates/`, `GET /custom_templates/{id}/`). Async create-then-poll; billed per 30 seconds of rendered video.

- **Human URL:** [https://docs.creatify.ai/api-reference](https://docs.creatify.ai/api-reference)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Marketing Video
- Templates
- Video Generation

#### Properties

- [API Reference](https://docs.creatify.ai/api-reference)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Product-to-Video API

Create studio-quality video ads from product images (`POST /product_to_video/`, `GET /product_to_video/{id}/`). Billed per image and per 30 seconds of generated footage. Endpoint paths are modeled from Creatify's documented product-to-video product area.

- **Human URL:** [https://docs.creatify.ai/api-documentation/product-to-video/product-to-video](https://docs.creatify.ai/api-documentation/product-to-video/product-to-video)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Marketing Video
- Product Video
- AI Video

#### Properties

- [Documentation](https://docs.creatify.ai/api-documentation/product-to-video/product-to-video)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Text-to-Speech API

Generate ultra-realistic voiceovers from text (up to 8000 characters) using AI voices and accents (`POST /text_to_speech/`, `GET /text_to_speech/{id}/`). Supports a `webhook_url` for status updates. Billed 1 credit per 30 seconds of audio.

- **Human URL:** [https://docs.creatify.ai/api-reference/text-to-speech/post-text-to-speech](https://docs.creatify.ai/api-reference/text-to-speech/post-text-to-speech)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Text to Speech
- Voiceover
- Audio
- Generative AI

#### Properties

- [Documentation](https://docs.creatify.ai/api-reference/text-to-speech)
- [API Reference](https://docs.creatify.ai/api-reference/text-to-speech/post-text-to-speech)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Personas API

Browse the catalog of 1500+ realistic AI avatars/personas and manage custom avatars (BYOA). List personas (`GET /personas/`, `GET /personas/paginated/`) and get a persona by id (`GET /personas/{id}/`) to reference in avatar and link-to-video jobs.

- **Human URL:** [https://docs.creatify.ai/api-reference/personas/get-apipersonas-paginated](https://docs.creatify.ai/api-reference/personas/get-apipersonas-paginated)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- AI Avatars
- Personas
- Avatar Catalog

#### Properties

- [API Reference](https://docs.creatify.ai/api-reference/personas/get-apipersonas-paginated)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Voices API

List the available AI voices and accents (`GET /voices/`, `GET /voices/paginated/`) used by Text-to-Speech and AI Avatar jobs, and manage cloned custom voices. Voice ids are referenced as the accent/voice on generation endpoints.

- **Human URL:** [https://docs.creatify.ai/api-reference](https://docs.creatify.ai/api-reference)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Voices
- Voice Cloning
- Text to Speech

#### Properties

- [API Reference](https://docs.creatify.ai/api-reference)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify Music API

Access the background-music library - list music categories (`GET /music_categories/`) and tracks (`GET /musics/`) - to attach soundtracks to generated videos. Read-only catalog endpoints; no credit cost to browse.

- **Human URL:** [https://docs.creatify.ai/api-reference](https://docs.creatify.ai/api-reference)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- Music
- Background Music
- Media Library

#### Properties

- [API Reference](https://docs.creatify.ai/api-reference)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Creatify AI Editing API

Automatically enhance and stylize an existing video with professional templates (`POST /ai_editing/`, `GET /ai_editing/{id}/`). Async create-then-poll.

- **Human URL:** [https://docs.creatify.ai/api-documentation/ai-editing/ai-editing](https://docs.creatify.ai/api-documentation/ai-editing/ai-editing)
- **Base URL:** `https://api.creatify.ai/api`

#### Tags

- AI Video
- Video Editing
- Marketing Video

#### Properties

- [Documentation](https://docs.creatify.ai/api-documentation/ai-editing/ai-editing)
- [OpenAPI](openapi/creatify-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/creatify.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/creatify.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [Authentication](authentication/creatify-authentication.yml)
- [Domain Security](security/creatify-domain-security.yml)
- [LinkedIn](https://www.linkedin.com/company/creatify-ai)
- [Website](https://creatify.ai)
- [Documentation](https://docs.creatify.ai)
- [Plans](plans/creatify-plans-pricing.yml)
- [Rate Limits](rate-limits/creatify-rate-limits.yml)
- [Fin Ops](finops/creatify-finops.yml)
- [Blog](https://creatify.ai/blog)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
