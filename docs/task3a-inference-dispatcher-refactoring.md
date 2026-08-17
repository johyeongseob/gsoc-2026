# Task 3a: Inference Dispatcher Refactoring

I refactored the inference execution flow so `run_inference_oep.py` became a thin CLI entry point instead of containing all inference logic directly.

## Key Work

- Added inference handler interface and registry.
- Added dispatcher-based handler selection.
- Moved inference execution into handler modules.
- Moved output writing and visualization into separate modules.
- Added configurable agent graph support through `agents.active`.
- Added a new use-case scaffold script.

## Main Modules Added or Updated

- `src/inference/handler.py`
- `src/inference/registry.py`
- `src/inference/dispatcher.py`
- `src/inference/inference_runner.py`
- `src/inference/output_writer.py`
- `src/inference/visualization.py`
- `src/agents/graph_builder.py`
- `scripts/new_usecase.py`

## Result

The inference pipeline became easier to extend. New use cases can now be added through config files, handler modules, and scaffolded use-case folders instead of editing one large script.
