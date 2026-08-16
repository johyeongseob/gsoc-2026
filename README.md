# Google Summer of Code 2026 - Final Work Product

**Contributor:** Hyeongseob Jo  
**Organization:** Intel / OpenVINO  
**Project:** Predictive Maintenance Pipeline  
**Repository:** [intel/predictive-maintenance-pipeline](https://github.com/intel/predictive-maintenance-pipeline)

This document summarizes my Google Summer of Code 2026 work on the Intel OpenVINO predictive maintenance pipeline. The goal of the project was to improve the pipeline so that it can support chatbot-based analysis, structured SQL querying, modular inference execution, and new predictive-maintenance use cases.

## Project Goals

The main goals of my work were:

- Integrate a unified chatbot interface for pipeline analysis.
- Add SQL schema support for querying inference results.
- Connect inference outputs with agent-based analysis.
- Refactor the inference pipeline into modular handlers.
- Make the agent graph configurable by use case.
- Add new infrastructure use cases and validation tests.

## Work Summary

### Task 1: Chatbot Integration

I implemented and improved the chatbot flow so users can ask natural-language questions about pipeline results. The chatbot can route questions to the appropriate backend mode, such as analysis, evidence, or SQL.

Key work:

- Added automatic intent routing for user questions.
- Connected the chatbot to analysis and SQL backends.
- Added predefined questions and improved web UI behavior.
- Maintained conversation flow for repeated user questions.

### Task 2: SQL Schema and Agent for Sensor Data

I extended the pipeline so inference results can be stored in SQLite and queried through natural language.

Key work:

- Added configurable SQL schema support.
- Stored image, sensor, and fused inference results in SQLite.
- Connected SQLCoder-based natural-language querying.
- Added support for sensor-related metadata in queryable outputs.

### Task 3a: Inference Dispatcher Refactoring

I refactored the inference execution flow so `run_inference_oep.py` became a thin CLI entry point instead of containing all inference logic directly.

Key work:

- Added inference handler interface and registry.
- Added dispatcher-based handler selection.
- Moved inference execution into handler modules.
- Moved output writing and visualization into separate modules.
- Added configurable agent graph support through `agents.active`.
- Added a new use-case scaffold script.

Main modules added or updated:

- `src/inference/handler.py`
- `src/inference/registry.py`
- `src/inference/dispatcher.py`
- `src/inference/inference_runner.py`
- `src/inference/output_writer.py`
- `src/inference/visualization.py`
- `src/agents/graph_builder.py`
- `scripts/new_usecase.py`

### Task 3b: New Use-Case Expansion

I started extending the pipeline to support additional infrastructure use cases. Each use case uses a separate configuration, schema, model path, prompt file, and tests.

#### Oil and Gas Pipeline Use Case

The Oil and Gas Pipeline use case uses tabular sensor data to predict pipeline condition and thickness loss.

Dataset:

- Predictive Maintenance Oil and Gas Pipeline dataset
- Source: [Kaggle - MIT License](https://www.kaggle.com/datasets/muhammadwaqas023/predictive-maintenance-oil-and-gas-pipeline-data)

Model:

- Multi-layer perceptron model exported to OpenVINO IR
- Input: tabular sensor feature vector
- Outputs:
  - pipeline condition classification
  - predicted thickness loss regression

Key work:

- Added `oil_gas_pipeline` use-case configuration.
- Extended `SensorFlatHandler` for regression + classification output.
- Added SQLite columns for degradation analysis.
- Added regression-style policy filtering.
- Updated analysis output for degradation statistics.
- Added an Oil and Gas specific `corrosion_agent`.
- Connected corrosion-related chatbot routing.
- Added Web UI support for the new use case.
- Added tests for routing, SQLite output, and agent artifacts.
- Added use-case documentation under `docs/`.

Validation:

- CLI inference processed 1,000 sensor samples.
- SQLite output was generated successfully.
- Agent outputs were generated successfully:
  - `analysis_summary.txt`
  - `evidence_trail.txt`
  - `corrosion_summary.txt`
- Chat routing correctly detected corrosion-related questions.

#### Solar Panel Defects Use Case

The Solar Panel Defects use case is based on the PVEL-AD solar cell electroluminescence image dataset.

Current status:

- Dataset and model were reviewed.
- The provided OpenVINO model is a YOLO-style object detection model.
- Mentor confirmed that this use case should proceed as:
  - `task=detect`
  - `modality=image`

Planned work:

- Add an OpenVINO YOLO detection handler.
- Add solar panel defect configuration and schema.
- Store detection results in SQLite.
- Connect the use case to agents and chat.
- Add tests for detection output and SQL/chat integration.

## Pull Requests

- Task 1, Task 2, and Task 3a: [PR #5](https://github.com/intel/predictive-maintenance-pipeline/pull/5)
- Task 3b - Oil and Gas Pipeline: [PR #6](https://github.com/intel/predictive-maintenance-pipeline/pull/6)

## Testing and Validation

During the project, I used CLI runs, Web UI checks, SQLite validation, and pytest-based tests.

Examples:

```bash
python run_inference_oep.py --config config/gas_detection/config.yaml
python run_inference_oep.py --config config/oil_gas_pipeline/config.yaml
python scripts/run_agent_orchestration.py --use-case oil_gas_pipeline
python -m pytest tests/test_agent_composition.py
python -m pytest tests/test_oil_gas_chat_routing.py tests/test_oil_gas_agent_outputs.py -v
```

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

This document is intended as the public GSoC final work product summary. It links to the upstream pull requests and summarizes what was implemented, validated, and left for future work.
