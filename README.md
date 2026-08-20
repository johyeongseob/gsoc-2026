# Google Summer of Code 2026 Project

**Contributor:** Hyeongseob Jo  
**Organization:** Intel / OpenVINO  
**Project:** Agentic AI for Predictive Maintenance using OpenVINO  
**Repository:** [intel/predictive-maintenance-pipeline](https://github.com/intel/predictive-maintenance-pipeline)

**GSoC Project Page:** [Project Details](https://summerofcode.withgoogle.com/programs/2026/projects/yvVZsgrT)

**Intel Mentors:**
- Hassnaa Moustafa
- Anand Bodas
- Rohit Verma

This repository summarizes my Google Summer of Code (GSoC) 2026 leveraging Intel Metro AI Suite Predictive Maintenance Pipeline using OpenVINO for AI Inference. The detailed work is organized into features to clearly present each contribution.


## Demo
The demo shows the unified chat interface routing natural-language questions to the appropriate backend mode.

![Chat system demo](assets/chat_system.gif)


## Work Summary

- [Feature 1: Chatbot Integration](docs/task1-unified-chat-interface.md) - Added intent routing and a unified chat flow for analysis, evidence, and SQL questions.
- [Feature 2: SQL Schema and Sensor Agent Support](docs/task2-input-schema.md) - Extended schema-aware SQLite querying and agent outputs for sensor-based predictive maintenance results.
- [Feature 3a: Inference Dispatcher Refactoring](docs/task3a-inference-refactor.md) - Refactored inference into handlers, output writers, config builders, and reusable runner modules.
- [Feature 3b - Dataset E: Oil and Gas Pipeline](docs/task3b-dataset-e-oil-gas-pipeline.md) - Added condition classification, thickness-loss regression, and corrosion analysis for pipeline sensor data.
- [Feature 3b - Dataset A1: Solar Panel Defects](docs/task3b-dataset-a1-solar-panel-defects.md) - Added OpenVINO object detection and agent analysis for solar-cell electroluminescence images.

## Datasets Used

| Dataset | Description | Applicable Use Case | Multimodal | Access |
|---|---|---|---|---|
| Pipeline Defect Dataset | Pipeline inspection images annotated for six defect classes: Deformation, Obstacle, Rupture, Disconnect, Misalignment, and Deposition. | Pipeline defect object detection | No — visual data | [Kaggle](https://www.kaggle.com/datasets/simplexitypipeline/pipeline-defect-dataset) |
| MultimodalGasData | Thermal-camera images aligned with measurements from seven MQ-series gas sensors across Mixture, NoGas, Perfume, and Smoke classes. | Multimodal gas classification and sensor-aware analysis | Yes — thermal images and gas-sensor data | [Mendeley Data](https://data.mendeley.com/datasets/zkwgkjkjn9/2) |
| Predictive Maintenance Oil and Gas Pipeline Data | Tabular pipeline records with operational and material attributes for three condition classes—Normal, Moderate, and Critical—and thickness-loss prediction. | Pipeline condition classification, thickness-loss regression, and corrosion analysis | No — tabular sensor data | [Kaggle](https://www.kaggle.com/datasets/muhammadwaqas023/predictive-maintenance-oil-and-gas-pipeline-data) |
| PVEL-AD | Single-channel electroluminescence solar-cell images annotated with bounding boxes across 12 defect classes. | Solar-panel defect object detection | No — electroluminescence images | [GitHub](https://github.com/binyisu/PVEL-AD) |

## The Current State

Feature 3b - Dataset A2 is currently in progress.

## What's Left to Do

Feature 3b - Datasets G and H remain to be completed.

## Pull Requests

- Feature 1, Feature 2, and Feature 3a: [PR #5](https://github.com/intel/predictive-maintenance-pipeline/pull/5)
- Feature 3b - Oil and Gas Pipeline: [PR #6](https://github.com/intel/predictive-maintenance-pipeline/pull/6)
- Feature 3b - Solar Panel Defect: [PR #8](https://github.com/intel/predictive-maintenance-pipeline/pull/8)

## Testing and Validation
Detailed validation commands and examples are available in [Pipeline Run and Validation](docs/pipeline-run-and-validation.md).

![Pipeline orchestration demo](assets/orchestration.gif)


## Final Submission Note

This repository is intended as the public GSoC final work product summary. It links to the upstream pull requests and summarizes what was implemented, validated, and left for future work.
