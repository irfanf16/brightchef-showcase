# BrightChef — AI-Powered Recipe Platform

**AI platform · Laravel 9 + OpenAI**

AI-generated recipes and meal planning, with generation queued through Horizon so slow model calls never block a request.

> **Source code is private.** This repository documents the architecture and engineering work.

## My role
Backend engineer

## Engineering highlights

**Queued AI generation.** Recipe generation is slow and rate-limited, so requests are dispatched to Redis queues supervised by Laravel Horizon — users get an immediate response while generation completes in the background, with retry and backoff handled by the queue rather than the request cycle.

**Action-based domain layer.** `lorisleiva/laravel-actions` gives each operation (generate, refine, save, scale portions) one implementation usable as controller, job, or CLI command — important when the same generation logic runs both synchronously and queued.

**Structured AI output.** Prompt design targets parseable structured responses rather than free text, so generated recipes map directly onto ingredient, step and nutrition models instead of needing fragile post-hoc parsing.

**API-first.** Sanctum-authenticated API designed for a mobile client.


## Screenshots

<!-- ![Recipe Generation](docs/recipe-generation.png) -->
<!-- ![Meal Plan](docs/meal-plan.png) -->

_Screenshots pending — see `docs/README.md`._

## Stack

`Laravel 9` · `PHP` · `MySQL` · `Redis` · `Horizon` · `OpenAI` · `Sanctum`
