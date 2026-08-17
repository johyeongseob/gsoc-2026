# Google Summer of Code 2026 - Final Work Product

**Contributor:** Hyeongseob Jo  
**Organization:** Intel / OpenVINO  
**Project:** Agentic AI for Predictive Maintenance using OpenVINO  
**Repository:** [intel/predictive-maintenance-pipeline](https://github.com/intel/predictive-maintenance-pipeline)

**GSoC Project Page:** [Project Details](https://summerofcode.withgoogle.com/myprojects/details/yvVZsgrT)

**Mentors:**
- Hassnaa Moustafa
- Anand Bodas
- Rohit1 Verma

This repository summarizes my Google Summer of Code 2026 work on the Intel OpenVINO predictive maintenance pipeline. The detailed work is organized by task so each contribution area can be reviewed independently.

## Work Summary

- [Task 1: Chatbot Integration](docs/task1-chatbot-integration.md) - Added intent routing and a unified chat flow for analysis, evidence, and SQL questions.
- [Task 2: SQL Schema and Sensor Agent Support](docs/task2-sql-schema-sensor-agent.md) - Extended schema-aware SQLite querying and agent outputs for sensor-based predictive maintenance results.
- [Task 3a: Inference Dispatcher Refactoring](docs/task3a-inference-dispatcher-refactoring.md) - Refactored inference into handlers, output writers, config builders, and reusable runner modules.
- [Task 3b: New Use Case Expansion](docs/task3b-new-use-case-expansion.md) - Expanded the pipeline to new infrastructure use cases, including Oil and Gas Pipeline and Solar Panel Defects.

## Pull Requests

- Task 1, Task 2, and Task 3a: [PR #5](https://github.com/intel/predictive-maintenance-pipeline/pull/5)
- Task 3b - Oil and Gas Pipeline: [PR #6](https://github.com/intel/predictive-maintenance-pipeline/pull/6)

## Testing and Validation

Detailed validation commands and examples are available in [Testing and Validation](docs/testing-and-validation.md).

## Current State

Completed:

- Chatbot routing and analysis integration
- SQLite-backed result querying
- Modular inference dispatcher refactor
- Configurable agent graph
- New use-case scaffold script
- Oil and Gas Pipeline use case

In progress:

- Solar Panel Defects use case

## Remaining Work

The remaining work before final submission is:

- Complete the Solar Panel Defects use case.
- Add tests for the solar panel defect detection flow.
- Update final documentation and PR links.
- Share this report with mentors before submitting the final GSoC evaluation.

## Challenges and Lessons Learned

During this project, I learned how to connect model inference, structured database storage, LLM-based analysis, and web UI interaction into one pipeline. I also learned the importance of keeping use-case behavior configurable, writing clear tests, and making PRs easier to review with focused commits and documentation.

The most important engineering lesson was that adding a new model is only one part of the system. The output schema, SQL querying, agent prompts, chatbot routing, tests, and documentation all need to work together for the use case to be useful.

## Final Submission Note

This repository is intended as the public GSoC final work product summary. It links to the upstream pull requests and summarizes what was implemented, validated, and left for future work.
