# Google Summer of Code 2026 Work Product

**Contributor:** Hyeongseob Jo  
**Organization:** Intel / OpenVINO  
**Project:** Agentic AI for Predictive Maintenance using OpenVINO  
**Repository:** [intel/predictive-maintenance-pipeline](https://github.com/intel/predictive-maintenance-pipeline)

**GSoC Project Page:** [Project Details](https://summerofcode.withgoogle.com/programs/2026/projects/yvVZsgrT)

**Mentors:** 
- Hassnaa Moustafa
- Anand Bodas
- Rohit Verma

This repository summarizes my Google Summer of Code (GSoC) 2026 work on the Intel OpenVINO predictive maintenance pipeline. The detailed work is organized by task so each contribution area can be reviewed independently.

## Demo

![Chat system demo](assets/chat_system.gif)

The demo shows the unified chat interface routing natural-language questions to the appropriate backend mode.
## Work Summary

- [Task 1: Chatbot Integration](docs/task1-unified-chat-interface.md) - Added intent routing and a unified chat flow for analysis, evidence, and SQL questions.
- [Task 2: SQL Schema and Sensor Agent Support](docs/task2-input-schema.md) - Extended schema-aware SQLite querying and agent outputs for sensor-based predictive maintenance results.
- [Task 3a: Inference Dispatcher Refactoring](docs/task3a-inference-refactor.md) - Refactored inference into handlers, output writers, config builders, and reusable runner modules.
- [Task 3b: New Use Case Expansion](docs/task3b-new-use-case.md) - Expanded the pipeline to new infrastructure use cases, including Oil and Gas Pipeline and Solar Panel Defects.

## Pull Requests

- Task 1, Task 2, and Task 3a: [PR #5](https://github.com/intel/predictive-maintenance-pipeline/pull/5)
- Task 3b - Oil and Gas Pipeline: [PR #6](https://github.com/intel/predictive-maintenance-pipeline/pull/6)
- Task 3b - Solar Panel Defect: [PR #8](https://github.com/intel/predictive-maintenance-pipeline/pull/8)

## Testing and Validation

![Pipeline orchestration demo](assets/orchestration.gif)

Detailed validation commands and examples are available in [Pipeline Run and Validation](docs/pipeline-run-and-validation.md).


## Final Submission Note

This repository is intended as the public GSoC final work product summary. It links to the upstream pull requests and summarizes what was implemented, validated, and left for future work.


