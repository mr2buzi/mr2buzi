# Deadline — Public Engineering Case Study

[Open the live application](https://deadline-dun-seven.vercel.app/)

Deadline is an accountability product built around time-bound goals, evidence submission, debriefs and an integrity-aware scoreboard. The production source is private; this document explains the engineering decisions without publishing credentials or operational configuration.

## System

- React 19, TypeScript and Vite frontend
- Firebase Authentication, Firestore, Storage and Gen 2 Cloud Functions
- Stripe subscription, portal and webhook integration paths
- TanStack Query and React Router
- Vercel and Firebase deployment workflow

## Engineering work

- Server-authoritative entitlements to prevent client-side tier spoofing
- Idempotent callable operations and payment reconciliation
- Firestore rules that separate private user records from deliberately public profile data
- Evidence/debrief gates and difficulty-weighted scoring
- High-entropy public identifiers, search limits and App Check enforcement paths
- CI covering type checks, Cloud Functions builds, application builds and smoke tests
- Upload type/size controls and analytics abuse protection

## Verification

The live application provides product-level evidence. Repository-side checks cover TypeScript, Functions builds, the production build and emulator-backed smoke paths.

Live payments remain gated behind deployment environment, Stripe dashboard, webhook, App Check and legal checks. This case study does not claim those manual production gates are complete.

## Why the source is private

The repository includes product configuration and unreleased commercial work. A controlled source walkthrough can be provided when appropriate.
