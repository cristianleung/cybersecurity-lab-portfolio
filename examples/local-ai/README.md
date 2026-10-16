# Local AI reference deployment

This CPU-only example uses Docker Desktop in Linux-container mode (or Docker Engine with Compose on Linux), named data volumes, and one private Compose network. Open WebUI reaches Ollama at `http://ollama:11434`; the model API has no published host port. The UI is mapped to `http://localhost:3000` on the local host. The native Windows Ollama installation shown in the original screenshots is not required by this container-only example.

Run from the repository root:

```sh
docker compose -f examples/local-ai/compose.yaml config --quiet
docker compose -f examples/local-ai/compose.yaml up -d
docker compose -f examples/local-ai/compose.yaml exec ollama ollama pull llama3.2:1b
docker compose -f examples/local-ai/compose.yaml exec ollama ollama list
docker compose -f examples/local-ai/compose.yaml ps
```

Allow Ollama to finish starting before pulling the model. The example model is a reference choice, not a claim about the model used in the original exercise. Available memory, disk, and network access determine whether a model can be downloaded and run.

Check backend connectivity from Open WebUI:

```sh
docker compose -f examples/local-ai/compose.yaml exec open-webui python -c "import urllib.request; r=urllib.request.urlopen('http://ollama:11434/api/tags', timeout=10); print(r.status); print(r.read().decode())"
```

Open `http://localhost:3000`, create the initial account if prompted, select the downloaded model, and submit a short prompt. A model listing and generated response are the functional checks. `depends_on` controls startup order, not service readiness. Inspect `docker compose -f examples/local-ai/compose.yaml logs` if a check fails.

Stop the deployment with `docker compose -f examples/local-ai/compose.yaml down`. Named volumes remain. Choose this Compose method or the report's equivalent `docker run` method; do not run both against port 3000.

The upstream quick-start tags `ollama/ollama:latest` and `ghcr.io/open-webui/open-webui:main` can change. Record resolved image digests when reproducing a specific run. Docker Compose configuration was validated during editing; the images and model were not downloaded or run here.

Sources: [Ollama](https://github.com/ollama/ollama), [Open WebUI quick-start](https://github.com/open-webui/open-webui#how-to-install-).
