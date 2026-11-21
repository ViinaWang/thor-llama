# Thor llama.cpp Builder

Automated GitHub Actions build of [llama.cpp](https://github.com/ggerganov/llama.cpp) for the **NVIDIA Thor** platform (aarch64 + Blackwell iGPU SM 10.1).

## Target

| Item | Value |
|------|-------|
| Architecture | ARM64 (aarch64) |
| CUDA SM | 10.1 (Blackwell Thor iGPU) |
| CUDA Toolkit | 12.8 |
| Build type | Release (-O3) |

## Usage

1. Push to `main` or trigger via `workflow_dispatch` (Actions → Run workflow)
2. Wait ~10 minutes
3. Download artifact `llama-cuda-thor.tar.gz`
4. Transfer to board and extract:

```bash
tar xzf llama-cuda-thor.tar.gz -C /home/nvidia/llama
export LD_LIBRARY_PATH=/home/nvidia/llama:$LD_LIBRARY_PATH
./llama-cli -m model.gguf -p "Hello Thor" -ngl 99
```

## Artifacts

- `llama-cli` — single-turn inference
- `llama-server` — OpenAI-compatible API server
- `llama-benchmark` — performance measurement
- `llama-quantize` — model quantization
- `libcudart.so.12`, `libcublas.so.12` — CUDA runtime (bundled for safety)
