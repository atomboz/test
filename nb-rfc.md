# TM Apps New Infra

## Meta

- RFC Name: TM apps new infra
- Start Date: 2023-08-26
- RFC PR: [https://github.com/SPHTech/baas-rfcs/pull/5](https://github.com/SPHTech/baas-rfcs/pull/5)
- Status: WIP | **In-Review** | Approved | Obsolete

## Summary

PROD infra setup for TM new apps' backend services.

## Motivation

Since TM apps is new, taking the chance to directly deploy the apps features onto the new AWS account (mobile-backend-prd, 794223216134) instead of the current mobile backend AWS production account (sphmedianmprd, 453223658634), and save the migration efforts later.

## Detailed Design

- Option 1:
  - Deploy the new lambdas for TM apps' backend features / APIs to the current mobile backend PROD AWS account (453223658634), tapping on the current resources setup like CloudWatch, Redis cache, APIGW etc. as outlined in [current mobile backend architecture diagram](https://sph.atlassian.net/wiki/spaces/MB/pages/812187653/Backend+as+a+Service+BaaS+Overview).
- Option 2:
  - Deploy the new infra to the new AWS account (794223216134) as outlined in the [TM PROD architecture diagram](https://sph.atlassian.net/wiki/spaces/MB/pages/1512603673/TM+Apps+PROD+Infra).

### Requirements

- [User story from TM Product manager](https://sph.atlassian.net/browse/TM-1740)
- [Spec page from TM Product manager](https://sph.atlassian.net/wiki/spaces/PROD/pages/1475772546/TM+ENG+Article+Translation)

## Drawbacks

- Option 1:
  - Double works involving new infra setup & testing are required in future for migration to the new AWS account.
- Option 2:
  - Besides setting up the new lambdas, additional IAM role / permission is required for cross account lambda invocation as APIGW is still centralised at sphmedianmprd account. Kinesis is needed for logs subscription.

## Rationale and alternatives

Although Option 2 has additional infra setup, it saves the double efforts in future works & testing needed for migration since mobile backend team has already started migrating some of the existing services to the new AWS account.

## Prior Art

N.A.

## Unresolved question

To be added if any.