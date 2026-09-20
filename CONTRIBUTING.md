# Contributing

Thanks for contributing to the Universal Specialist Agent Factory.

## Development setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -e .[dev]
```

## Workflow

1. Create a branch for your work.
2. Keep changes small and focused.
3. Add or update tests for behavior changes.
4. Run the validation commands.
5. Update the changelog when behavior or compatibility changes.
6. Open a pull request with clear context.

## Validation

```bash
pytest -q
python -m ruff check src tests
```

## Code expectations

- Prefer explicit, typed interfaces.
- Keep modules focused and testable.
- Avoid hidden side effects.
- Preserve deterministic behavior where possible.
- Document public API behavior.

## Documentation

When you change public behavior, update the relevant docs and examples.
