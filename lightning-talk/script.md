# GSoC 2026 Lightning Talk

Target: within 2 minutes 30 seconds. English presentation, 3 slides.
The spoken script contains 259 words. Timings are rehearsal targets. Read it aloud to check your actual delivery time.

| Time | Content | Duration |
| --- | --- | --- |
| 0:00–0:15 | Slide 1: Introduction | 15 seconds |
| 0:15–0:45 | Slide 1: Problem and goal | 30 seconds |
| 0:45–1:40 | Slide 2: Core contributions | 55 seconds |
| 1:40–2:25 | Slide 3: Results and closing | 45 seconds |
| 2:25–2:30 | Buffer | 5 seconds |

## Slide 1 — Agentic AI for Predictive Maintenance

### 0:00–0:15 Introduction

Hi, I'm Hyeongseob Jo, a machine learning engineer with a research background in manufacturing. This summer, I contributed to the Intel OpenVINO Toolkit organization through Google Summer of Code.

### 0:15–0:45 Problem and goal

My project extended Intel Metro AI Suite's predictive maintenance pipeline. A model can detect a defect, but an operator still needs to understand the result and inspect the evidence. My goal was to make that investigation easier, while making the pipeline easier to extend. OpenVINO runs the models, and AI agents help users explore the results.

Delivery note: Use the question on the slide to emphasize the operator's problem. Advance to slide 2 at 0:45.

## Slide 2 — One question interface

### 0:45–1:40 Core contributions

Here is the main user-facing change. Previously, users had to choose analysis, evidence, or SQL mode before asking a question. I replaced that choice with automatic intent routing in both the web interface and the command line. Users can now ask a question directly. Behind the interface, I expanded the database to keep raw sensor values and metadata, so answers can refer back to the source records. I also split the inference code into focused handlers and shared components. This lets new models reuse the same pipeline instead of adding more logic to one large script.

Delivery note: Point to the question and the Analysis Agent response. Explain the database and inference improvements shown at the bottom, then advance to slide 3 at 1:40. Pronounce SQL as S-Q-L.

## Slide 3 — Five new use cases, one shared pipeline

### 1:40–2:25 Results and closing

Using that structure, I added five use cases, covering tabular sensors, images, audio with text, and satellite raster data with text. For example, the solar defect detector achieved an F1 score of about zero point eight three across nineteen thousand test images. I validated the workflows and confirmed pipeline inference on an Intel NPU. My biggest lesson was that useful AI needs evidence people can inspect, alongside the prediction. Thank you to my mentors and the OpenVINO community!

Delivery note: You do not need to read all five use-case names aloud. The solar-cell image is a dataset example with a ground-truth box, not a model prediction. The F1 score applies only to the solar defect detection evaluation.

## Rehearsal and timing adjustments

- The spoken script contains 259 words. At about 120–125 words per minute, allowing for transitions and pauses, aim to finish within 2 minutes 30 seconds. Record a rehearsal to check your timing.
- If you are still on slide 2 at 1:40, skip: “This lets new models reuse the same pipeline instead of adding more logic to one large script.”
- If you need to shorten the talk further, omit the F1 evaluation sentence on slide 3. The main narrative will still work.
- Explain the embedded screenshot rather than running a live demo.

## Sources

- [Medium project article](../medium/article.md)
- [Unified chat interface](../docs/feature1-unified-chat-interface.md)
- [SQL schema support](../docs/feature2-sql-schema-support.md)
- [Inference refactoring](../docs/feature3-inference-refactor.md)
- [Solar defect detection evaluation](../docs/feature4-solar-panel-defects.md)
- [Pipeline and NPU validation](../docs/pipeline-run-and-validation.md)
