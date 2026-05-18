---
layout: project_post
title: EcoCloud
description: discover, visualize, and reduce cloud computing emissions.
year: 2026
tags:
  - Python
  - Next.js
  - Google Cloud
  - Sustainability
  - Web App
---

<div style="position: relative; width: 100%; padding-bottom: 56.25%; margin: 1.25rem 0; overflow: hidden; border-radius: 0.25rem; background: #111;">
  <iframe
    src="https://www.youtube.com/embed/JFMHQNzzQFc"
    title="EcoCloud Pulse product demo"
    style="position: absolute; inset: 0; width: 100%; height: 100%; border: 0;"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    allowfullscreen>
  </iframe>
</div>

[EcoCloud](https://ecocloud-pulse.com) was my senior capstone project: **a cloud sustainability platform for discovering, visualizing, and reducing the carbon impact of Google Cloud infrastructure.**

The main idea was to make sustainability part of normal infrastructure operations instead of a separate after-the-fact report. EcoCloud scans cloud resources, maps them to region-level carbon intensity, shows telemetry and policy findings in a dashboard, and uses EcoGuard to enforce sustainability rules before new infrastructure is deployed.

## What It Does

EcoCloud Pulse combines several pieces into one workflow:

- **EcoCloud Pulse** - a Next.js dashboard for Google sign-in, project claiming, resource scanning, governance settings, region details, telemetry, and EcoGuard history. Globe view shows cloud regions, carbon hotspots, region markers, scan results, and resource-level details.
- **Cloud scanning API** - a FastAPI backend that scans Google Cloud projects, pulls regional carbon intensity data, summarizes telemetry, and exposes project-scoped data to the dashboard.
- **EcoPilot** - an AI assistant that helps explain findings and suggest lower-carbon infrastructure actions.
- **EcoGuard** - a CLI and Cloud Function enforcement path that evaluates VM deployments against organization/project governance before allowing them to proceed.

The product loop we were building toward was:
>`observe -> recommend -> enforce -> optimize -> verify`

## My Role

I was the CTO and a lead developer for the project. I helped define the technical direction, built major parts of the frontend and backend, led the EcoGuard implementation, contributed heavily to the EcoCloud Pulse dashboard, and handled a large amount of the project management needed to keep the team moving.

In practice, that meant I worked across the full stack: frontend dashboard polish, backend API design, cloud telemetry, database migrations, CLI behavior, authentication, Google Cloud deployment, tests, and documentation.

### Key Work 

I built the initial Next.js dashboard and connected it to the backend API, then expanded it into the main EcoCloud Pulse experience with region markers, project scanning, telemetry displays, and region detail views. On the backend, I worked on cloud resource scanning, carbon intensity lookup, telemetry endpoints, project-scoped access, and debugging support. I also built much of the project governance system, including project claiming, scoped scans, organization/member access, governance settings, and database migrations. 

#### EcoGuard

EcoGuard was the enforcement layer I developed for the project. Instead of only showing that a region or deployment was high-carbon, EcoGuard made it possible to check deployments before they happened.

The flow worked roughly like this:

1. A developer submits a VM deployment through the `ecoguard` CLI.
2. A Google Cloud Function forwards the request to the EcoCloud API.
3. The API resolves the claimed project, loads effective governance settings, checks regional carbon intensity, and returns a decision.
4. If the request violates policy, EcoGuard requires a justification.
5. The AI-backed exception path can allow or deny the request.
6. The final request and deployment outcome are stored for dashboard review.

I implemented the EcoGuard backend endpoints, CLI behavior, install/init flow, machine registration, install tokens, per-project routing, and installable package structure. I also moved the design toward project-scoped install tokens so each claimed GCP project could have its own machine credential instead of relying on one shared service token.

## What I Learned

EcoCloud was a good lesson in product-shaped engineering. The hard part was not just building a dashboard or calling cloud APIs. The hard part was making the system feel coherent:

- scan real infrastructure,
- show carbon and telemetry context,
- explain what matters,
- enforce policy when developers deploy,
- and keep enough history for review and accountability.

The project also made clear that sustainability tooling needs strong data foundations. Carbon intensity, CPU, network, and disk telemetry were useful, but future versions would need billing data, latency handling, and stronger feasibility checks.
