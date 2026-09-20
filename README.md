# Universal Specialist Agent Factory

Universal Specialist Agent Factory (USAF) is a minimal but production-minded framework for defining, certifying, and executing specialized agents with explicit capabilities and policy-bound execution.

## What it provides

- typed agent specifications
- explicit capability declarations
- policy-aware execution permits
- deterministic runtime execution checks
- testable validation and failure modes
- GitHub-ready repository structure for contribution and release

## Repository goals

This repository is intentionally designed as the foundation for an open-source agent platform. The first milestone is not a massive app; it is a reliable core:

- define an agent
- validate its capabilities
- authorize execution via a permit
- execute within a bounded policy model
- audit the result

## Quick start

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -e .[dev]
pytest -q
```

## Example

```python
from usaf import AgentFactory, AgentSpec, Capability

factory = AgentFactory()
agent = factory.build(
    AgentSpec(
        name="market-analyst",
        role="research",
        capabilities=(
            Capability("read_market_data", "Read market feeds"),
            Capability("run_simulation", "Run local simulation"),
        ),
    )
)

permit = factory.runtime.request(agent, "read_market_data")
result = factory.runtime.execute(agent, "read_market_data", value={"market": "BTC/USD"}, permit=permit)
print(result)
```

## Architecture

The core is intentionally small and explicit:

- `AgentSpec` defines the contract for an agent
- `Capability` defines the allowed action surface
- `AgentFactory` validates and creates agents
- `ExecutionRuntime` issues permits and executes only authorized actions

## Development

```bash
pytest -q
python -m ruff check src tests
```

## Security

Please review `SECURITY.md` before reporting issues.

## License

MIT
