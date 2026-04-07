
uv


# On macOS and Linux.
curl -LsSf https://astral.sh/uv/install.sh | sh

uv init

uv add -r requirements.txt

uv add --dev pytest pytest-mock bandit ruff

uv run pytest

uv sync

[tool.pytest.ini_options]
pythonpath = ["."]
testpaths = ["tests"]


Python linter
https://docs.astral.sh/ruff/

uv run ruff check .


uv run bandit -r . -x ./tests