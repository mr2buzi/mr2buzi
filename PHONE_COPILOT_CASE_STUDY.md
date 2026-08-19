# Phone Copilot — Public Engineering Case Study

Phone Copilot is a local-first, supervised messaging assistant for an Android phone. It observes message context, retrieves relevant examples, creates a reply plan, drafts a response and validates the result before it can be shown or sent.

The production repository stays private because development data includes personal conversations and contact information. Raw messages, names, phone-number filenames, photos and runtime logs are not published here.

## Architecture

1. An ADB or WhatsApp Web adapter collects visible conversation context.
2. A FastAPI controller classifies the conversation function and relationship context.
3. Retrieval ranks human-approved corrections, same-contact examples, same-relationship examples and safe templates.
4. A reply plan defines what the next message must accomplish.
5. A local or external model drafts candidate text.
6. Local validators enforce identity, duplication, safety, style and conversation constraints.
7. Failed candidates can be retried or repaired; sending remains policy-gated and review-first by default.

The system includes a local vector index, identity constraints, conversation memory, provider routing, diagnostic views and a 3D vector-map interface.

## Safety model

Automatic sending is disabled by default. Explicit mode, target/profile, relationship, critic, duplicate, blacklist, rate-limit, confidence and emergency-stop gates must all pass before an automated action is allowed. Provider output cannot bypass local validation.

## Verification evidence

A documented browser regression run completed 550 sequential turns with zero final failures:

- 416 accepted on the first attempt
- 14 accepted after retry
- 120 accepted after repair

Failures were handled through root-cause changes to classification, planning or validation, followed by focused tests and a full rerun. This is engineering regression evidence, not a claim of 550 independent users. Informal Snapchat trials are likewise not presented as a unique-user count.

## Access

A controlled walkthrough of the private architecture and test evidence can be provided without exposing the underlying personal dataset.
