# musubi-sdk

Small sync and async Python clients for the [Musubi HTTP API](https://github.com/sourceblender/musubi). This package installs `httpx` and the client code; it does not install the Musubi server, storage, or deploy stack.

```python
from musubi_sdk import AsyncMusubiClient

async with AsyncMusubiClient(base_url="https://musubi.example/v1", token="your-scoped-token") as client:
    result = await client.retrieve(namespace="team/agent/episodic", query_text="handoff", mode="fast")
```

The initial source was extracted from `sourceblender/musubi`'s `src/musubi/sdk` at commit `5d769ed4`; import paths changed from `musubi.sdk` to `musubi_sdk`. The copied client contract tests run here. The extraction is being integrated with core and plugins under [musubi #848](https://github.com/sourceblender/musubi/issues/848); this repository is not a claim that installed consumers have migrated.

## Develop

```sh
uv sync --locked --group dev --python 3.12
uv run --python 3.12 pytest -q
uv run --python 3.12 ruff check src tests
uv run --python 3.12 ruff format --check src tests
uv run --python 3.12 mypy src/musubi_sdk
uv build --wheel
```

Apache-2.0. See [LICENSE](LICENSE).
