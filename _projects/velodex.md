---
layout: project_post
title: Velodex
description: fixed gear build archive and community platform
year: 2026
tags:
  - Next.js
  - Web App
---

<img src="/img/projects/velodex.png" alt="Velodex homepage screenshot" style="max-width: 100%; height: auto;">

[Velodex](https://velodex.net) is a build-first fixed gear platform for documenting bikes, parts, riders, and clubs.

The idea is simple: give fixed gear riders a cleaner place to save and browse real builds. Instead of an algorithm feed or a generic cycling social network, Velodex is centered around structured bike specs, photos, component lists, profiles, likes, and lightweight club activity.

It is still very much in progress. I have the live site up at [velodex.net](https://velodex.net), but I am still ironing out product details, cleanup work, contributor setup, and a few rough edges before opening the repository publicly. The plan is to make Velodex open-source soon once the project is in a shape I am comfortable handing to other people.

## What It Does

Velodex currently supports:

- public build discovery with search and filters
- rider garages and profile pages
- structured frame and component details
- bike photo uploads
- likes and related-build discovery
- clubs, member management, and lightweight club posts

The stack is a single Next.js App Router application with TypeScript, Clerk authentication, Supabase Postgres, Drizzle ORM, Supabase Storage, and Playwright smoke tests.

## Early Launch

One of the coolest signals so far was how quickly people found it. Within the first 24 hours after publishing the site, Velodex had users from more than 8 cities worldwide. That was enough validation to make the project feel worth polishing properly instead of leaving it as a private side experiment.

## Next

Right now I am focusing on the boring but important work: tightening the UI, cleaning up the repo, improving smoke coverage, checking for anything that should not be public, and documenting a local setup path for future contributors.

Once that is done, I want Velodex to become an open-source home for fixed gear build documentation.
