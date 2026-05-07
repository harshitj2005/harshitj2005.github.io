---
layout: home
title: Harshit Jain
description: >-
  Harshit Jain — Associate Principal Engineer specializing in distributed systems,
  GraphQL federation, and microservices architecture. 12+ years building systems
  that hold under production load.
image:
  path: /assets/img/avatar.jpg
  alt: Harshit Jain
---

## I design systems that hold when everything else breaks.

**Associate Principal Engineer · Distributed Systems Architect · TypeScript / NestJS / GraphQL**

Enterprise systems fail in predictable ways: cascading timeouts, split-brain message queues, workflow state that evaporates mid-transaction. I've spent a decade building the architecture that intercepts those failures before users ever feel them — using Saga patterns to coordinate long-running distributed transactions, Circuit Breakers to contain blast radius, and BPMN process orchestration to turn business workflows into auditable, recoverable state machines.

The stack is mostly TypeScript, NestJS, and Node.js at the core, with Kafka and RabbitMQ handling message routing, Docker and Kubernetes on GCP and Azure for deployment, and GraphQL Federation stitching the API surface together across autonomous teams. The problems I'm drawn to aren't the ones that are hard to write — they're the ones that are hard to get right when load spikes at 2am and the on-call engineer is three timezones away.

---

### Featured Work

An e-commerce platform's order fulfillment system was generating a flood of customer service tickets: broken states, partial refunds that never resolved, transactions stranded in failure with no clean path back. The root problem wasn't a bug — it was an architecture that had no answer for partial failure across distributed services. I redesigned the fulfillment flow using the Saga pattern, making each step a compensatable transaction so that when anything failed downstream, rollback cascaded automatically and completely. Customer service tickets dropped 70%. Annual revenue increased 20%. Around the same period, a separate set of critical APIs running at 200ms average response time was quietly capping the platform's growth ceiling — a team of 20+ engineers rebuilt them on Redis, Fastify, and NestJS with circuit breaker patterns throughout, bringing average response time to 4ms. When the architecture is right, the numbers tend to follow.

---
