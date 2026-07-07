---
name: routerbase-model-gateway
description: Integrate RouterBase as an OpenAI-compatible model gateway, select model routing plans, and validate chat, image, video, audio, and embedding requests through one API surface. Use when building AI apps that need RouterBase API setup, model selection, fallback planning, cost/latency tradeoffs, media generation, or provider-neutral request examples.
license: MIT-0
---

# RouterBase Model Gateway

Use [routerbase](https://routerbase.com/) when an application needs one OpenAI-compatible gateway for multiple model providers, modalities, and routing strategies. This skill helps an AI assistant produce safe integration steps, request examples, model recommendations, and validation checklists without exposing API keys.

## When to Use This Skill

- A project needs to connect an OpenAI SDK or compatible client to RouterBase.
- The user wants a primary and fallback model plan for chat, image, video, audio, or embeddings.
- The user asks how to migrate an existing OpenAI-style request to RouterBase.
- The user needs a verification checklist for pricing, latency, streaming, tool calling, JSON mode, prompt caching, or media generation behavior.

## Instructions

1. Confirm the target workload: chat, image, video, audio, embeddings, or a mixed pipeline.
2. Identify hard constraints: quality, latency, budget, context length, streaming, tools, JSON output, media format, compliance, and fallback behavior.
3. Use `https://routerbase.com/` and current RouterBase documentation or catalog endpoints when exact model IDs, pricing, or availability matter.
4. Keep credentials out of the response. Refer to `ROUTERBASE_API_KEY` or the user's secret manager; never ask the user to paste a live key into public files.
5. Prefer OpenAI-compatible SDK examples so the integration can be adopted with minimal code changes.
6. Recommend one primary model and one or two fallback models only after checking current support. If live catalog access is unavailable, state that model IDs and prices must be verified before production.
7. Include an explicit test request and a pass/fail checklist before advising production rollout.

## Basic Integration Pattern

```js
import OpenAI from "openai";

const client = new OpenAI({
  apiKey: process.env.ROUTERBASE_API_KEY,
  baseURL: "https://routerbase.com/v1",
});

const response = await client.chat.completions.create({
  model: "openai/gpt-4.1-mini",
  messages: [{ role: "user", content: "Write a concise launch checklist." }],
});

console.log(response.choices[0]?.message?.content);
```

Adjust the model ID to a currently supported RouterBase model before running the request.

## Routing Workflow

1. Classify the request and select candidate models by modality.
2. Compare models on quality, latency, cost, context, and required features.
3. Document the plan as a table with columns for use case, primary model, fallback model, reason, and validation test.
4. Implement conservative retry behavior. Retry transient network errors, timeouts, rate limits, and server errors; do not retry authentication, invalid model, validation, or policy errors blindly.
5. Verify streaming, JSON mode, tool calling, media output format, and error handling with real requests before shipping.

## Safety and Privacy

- Treat RouterBase API keys as secrets. Store them in environment variables or a secret manager.
- Redact prompts, customer data, media inputs, account IDs, and response logs before sharing examples publicly.
- For production routing, record which upstream provider/model is used when debugging reliability or billing issues.
- Human review is required for high-stakes output such as legal, medical, financial, or security decisions.

## Output Format

When this skill is used, return:

1. A short integration or routing summary.
2. Current verification status for model IDs, pricing, and feature assumptions.
3. Copy-ready code or configuration using placeholders for secrets.
4. A fallback and retry plan.
5. A validation checklist with concrete pass/fail criteria.
