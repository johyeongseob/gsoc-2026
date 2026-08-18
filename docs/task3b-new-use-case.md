# Task 3b: New Use Case Expansion

This task extended the pipeline toward additional infrastructure use cases. Each use case uses a separate configuration, schema, model path, prompt file, and test coverage so dataset-specific behavior can be added without changing the core pipeline structure.

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

- Added the `oil_gas_pipeline` use-case configuration, schema, and documentation.
- Extended the sensor inference flow for condition classification and thickness-loss regression.
- Added degradation-aware SQLite output, policy filtering, and analysis summaries.
- Added a corrosion-specific agent and connected corrosion-related chat routing.
- Added Web UI support and tests for routing, SQLite output, and agent artifacts.

### Validation

- CLI inference processed 1,000 sensor samples.
- SQLite output was generated successfully.
- Agent outputs were generated successfully:
  - `analysis_summary.txt`
  - `evidence_trail.txt`
  - `corrosion_summary.txt`
- Chat routing correctly detected corrosion-related questions.

### Use Case Result

The Oil and Gas Pipeline use case was validated through inference output, SQLite storage, agent summaries, and corrosion-specific chat routing.

![Task 3b Oil and Gas Pipeline result](../assets/task3/task3b-oil-gas-pipeline.png)

## Solar Panel Defects Use Case

The Solar Panel Defects use case detects defects in single-channel electroluminescence images of solar cells.

### Dataset

- PVEL-AD solar cell anomaly detection dataset
- Modality: single-channel electroluminescence images
- Task: object detection
- Test set: 19,150 images with XML bounding-box annotations
- Source: [PVEL-AD](https://github.com/binyisu/PVEL-AD)

### Model

- YOLO-style object detection model exported to OpenVINO IR
- Input: `[1, 1, 640, 640]`
- Output: `[1, 16, 8400]`
  - 4 bounding-box coordinates
  - 12 defect-class scores
  - 8,400 candidate boxes
- Inference device: Intel integrated GPU using OpenVINO FP32

### Key Work

- Added the `solar_panel_defects` configuration, schema, prompts, and policy.
- Implemented `OpenVINODetectHandler` for single-channel YOLO inference, filtering, NMS, and coordinate restoration.
- Stored bounding-box detections in JSONL and SQLite with `modality_source: electroluminescence`.
- Integrated policy, analysis, and evidence agents with tested CLI and Web UI chat support.

### Validation

- Full evaluation on all 19,150 test images produced:
  - precision: 0.8789
  - recall: 0.7822
  - F1 score: 0.8277
- Inference on a 100-image serving sample produced:
  - 217 raw detections at the detector confidence threshold
  - 131 policy-kept detections at the 0.5 policy threshold
  - 86 filtered detections
- Analysis, evidence, and SQL chat modes were verified in both the CLI and Web UI.


### Use Case Result

The Solar Panel Defects use case was validated through OpenVINO object detection, JSONL and SQLite storage, agent-generated analysis and evidence reports, and CLI and Web UI chat queries.

![Task 3b Solar Panel Defects result](../assets/task3/task3b-solar-panel-defect.png)


