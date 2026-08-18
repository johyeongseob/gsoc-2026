# Pipeline Run and Validation

During the project, I validated the pipeline through CLI inference runs, agent orchestration runs, chat-system checks, SQLite output inspection, and Web UI testing.

## Inference Validation

Inference can be run from the CLI with a use-case config file:

```bash
python run_inference_oep.py --config config/<use-case>/config.yaml
```

Examples:

```bash
python run_inference_oep.py --config config/gas_detection/config.yaml
python run_inference_oep.py --config config/oil_gas_pipeline/config.yaml
```

This verifies that the selected model and handler run successfully and that inference outputs are written to JSONL and SQLite.

## Agent Orchestration Validation

Agent orchestration can be run after inference outputs are available:

```bash
python scripts/run_agent_orchestration.py --use-case <use-case>
```

Example:

```bash
python scripts/run_agent_orchestration.py --use-case oil_gas_pipeline
```

This verifies that the configured agents run successfully and produce artifacts such as policy, analysis, evidence, and use-case-specific summaries.

## Chat System Validation

The CLI chat interface can be launched with a use-case config:

```bash
python interactive_chat.py --config config/<use-case>/config.yaml
```

Example:

```bash
python interactive_chat.py --config config/oil_gas_pipeline/config.yaml
```

This verifies natural-language routing across analysis, evidence, SQL, and use-case-specific modes such as corrosion.
