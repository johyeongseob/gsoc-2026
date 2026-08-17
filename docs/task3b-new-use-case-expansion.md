# Task 3b: New Use Case Expansion

I started extending the pipeline to support additional infrastructure use cases. Each use case uses a separate configuration, schema, model path, prompt file, and tests.

## Oil and Gas Pipeline Use Case

The Oil and Gas Pipeline use case uses tabular sensor data to predict pipeline condition and thickness loss.

### Dataset

- Predictive Maintenance Oil and Gas Pipeline dataset
- Source: [Kaggle - MIT License](https://www.kaggle.com/datasets/muhammadwaqas023/predictive-maintenance-oil-and-gas-pipeline-data)

### Model

- Multi-layer perceptron model exported to OpenVINO IR
- Input: tabular sensor feature vector
- Outputs:
  - pipeline condition classification
  - predicted thickness loss regression

### Key Work

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

### Validation

- CLI inference processed 1,000 sensor samples.
- SQLite output was generated successfully.
- Agent outputs were generated successfully:
  - `analysis_summary.txt`
  - `evidence_trail.txt`
  - `corrosion_summary.txt`
- Chat routing correctly detected corrosion-related questions.

## Solar Panel Defects Use Case

The Solar Panel Defects use case is based on the PVEL-AD solar cell electroluminescence image dataset.

### Current Status

- Dataset and model were reviewed.
- The provided OpenVINO model is a YOLO-style object detection model.
- Mentor confirmed that this use case should proceed as:
  - `task=detect`
  - `modality=image`

### Planned Work

- Add an OpenVINO YOLO detection handler.
- Add solar panel defect configuration and schema.
- Store detection results in SQLite.
- Connect the use case to agents and chat.
- Add tests for detection output and SQL/chat integration.
