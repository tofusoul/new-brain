---
title: Prefect
date: 2023-10-26
---
> workflow orchastration platform in pure python

- nice so far just write python functions!
- these are notes from [the docs](https://docs.prefect.io/)
# Flows
> 💡 Flows are the most central notion in Prefect. It's a:
> - container for workflow logic as code, 
> - any [[Python]] function can be a flow

## @flow
the `@flow` decorator adds the following features to a python function
- Every invocation of the function is tracked, and all state transitions reported to the API - giving observability to executions
- inpute arguments are type checked and coerced to the right types
- retries can be performed on failiours
- timeouts can be enforeced to prevent unintentional long run workflows 
## Flow Runs
A *flow run* is a single execution of the flow function 
- can be run by calling the flow manually
- can be *deployed* to the cloud or a server
- runs can be invoked on a schedule.
how ever the flow is run:
- the prefect api moniters the run and captures the runstate for observability
- if your flow contains tasks or other flows, Prefect will track the relationship of each run.
# Tasks
- Tasks must be called from Flows

# Deployments
# Work Pools and Workers
# Schedules
# Resultes
# Artifacts
# States
# Blocks
# Task Runners
# Event 
# Automations
# Block and Agent based Deployments
