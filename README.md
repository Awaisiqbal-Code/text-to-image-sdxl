<div align="center">

# Text-to-Image SDXL

**A notebook-based Stable Diffusion XL inference project for generating images from natural-language prompts.**

[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)](https://jupyter.org/)
[![Diffusers](https://img.shields.io/badge/Hugging%20Face-Diffusers-FFD21E?logo=huggingface&logoColor=black)](https://github.com/huggingface/diffusers)
[![Model](https://img.shields.io/badge/Model-Stable%20Diffusion%20XL-6C5CE7)](https://stability.ai/stable-diffusion)

[Explore the notebook](./text_to_image.ipynb) · [View the setup guide](#setup)

</div>

## Project status

**Educational / experimental inference project.** This repository demonstrates SDXL image generation in a Jupyter Notebook. It is not presented as a production API, hosted application, model-training system, or benchmarked serving solution.

## Overview

This project converts a text prompt into an image with **Stable Diffusion XL (SDXL)** using the Hugging Face **Diffusers** library and **PyTorch**. The notebook exposes the main generation inputs—prompt, negative prompt, inference steps, and guidance scale—while selecting CUDA when available and falling back to CPU otherwise.

The original notebook remains the source of truth for the runnable implementation. The model architecture, inference logic, model configuration, and notebook behavior have not been rewritten as part of this presentation layer.

## Why this project

- Demonstrates practical integration of a modern text-to-image diffusion model.
- Provides an inspectable, notebook-first workflow for experimentation.
- Shows how prompts and generation parameters affect image synthesis.
- Uses standard tools from the Python and generative-AI ecosystem.

## Workflow

```text
Prompt + optional negative prompt
                │
                ▼
      SDXL pipeline via Diffusers
                │
                ▼
      PyTorch inference on CUDA/CPU
                │
                ▼
          Generated image output
```

## Technology stack

| Category | Technology | Role |
| --- | --- | --- |
| Language | Python | Runtime and notebook code |
| Interface | Jupyter Notebook / JupyterLab | Interactive execution environment |
| Generative model | Stable Diffusion XL 1.0 | Text-to-image synthesis |
| Inference | Hugging Face Diffusers | SDXL pipeline integration |
| Compute | PyTorch | Tensor computation and device acceleration |
| Tracking | Weights & Biases | Optional experiment configuration/tracking |

## Features

- Text-conditioned image generation with `StableDiffusionXLPipeline`.
- Positive and negative prompt configuration.
- Configurable inference steps and guidance scale.
- CUDA detection with CPU fallback in the notebook workflow.
- SDXL base and refiner model identifiers referenced by the notebook.
- Optional Weights & Biases integration.
- A transparent Jupyter workflow that can be read and modified cell by cell.

## Repository structure

```text
text-to-image-sdxl/
├── text_to_image.ipynb   # SDXL inference notebook and executable workflow
├── models/               # Local model assets when used; large weights are ignored
├── README.md             # Project documentation and setup guide
├── requirements.txt      # Notebook and inference dependencies
└── .gitignore            # Python, Jupyter, ML artifact, and secret exclusions
```

## Setup

### Prerequisites

- Python 3.9 or newer
- Jupyter Notebook or JupyterLab
- A CUDA-capable GPU is strongly recommended for practical SDXL inference
- Enough memory and disk space for the selected SDXL checkpoints
- Access to the Hugging Face model repositories used by the notebook
- A Weights & Biases account only when optional tracking is enabled

### Installation

```bash
git clone https://github.com/Awaisiqbal-Code/text-to-image-sdxl.git
cd text-to-image-sdxl

python -m venv .venv

# macOS/Linux
source .venv/bin/activate

# Windows PowerShell
# .venv\Scripts\Activate.ps1

python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter lab
```

Open `text_to_image.ipynb` in Jupyter and run the cells from top to bottom.

> **PyTorch note:** The unpinned `torch` entry allows installation of a build appropriate for the local hardware. For CUDA acceleration, follow the official [PyTorch installation selector](https://pytorch.org/get-started/locally/) if the default package is not suitable for your CUDA environment.

## Usage

The notebook references these SDXL model identifiers:

```text
stabilityai/stable-diffusion-xl-base-1.0
stabilityai/stable-diffusion-xl-refiner-1.0
```

To generate an image:

1. Start JupyterLab using the command above.
2. Open `text_to_image.ipynb`.
3. Review or edit the prompt, negative prompt, and generation configuration.
4. Run the notebook cells in order.
5. Inspect the generated image output produced by the pipeline.

### Example prompts

Copy and adapt any of the following prompts:

```text
A cinematic photograph of a mountain cabin at sunrise, detailed natural lighting
```

```text
A futuristic research laboratory in a dense rainforest, architectural photography
```

```text
A watercolor illustration of a quiet coastal village, soft morning light
```

The notebook also contains its original demonstration prompt and configuration; the notebook remains the authoritative executable example.

### Input and output

| Stage | Description |
| --- | --- |
| Input | A text prompt, optional negative prompt, and generation parameters |
| Processing | SDXL inference through Diffusers and PyTorch |
| Output | Generated image output displayed or saved according to the notebook workflow |

## Demo

No generated image assets are currently included in the repository, so no fabricated gallery is shown here.

To add a portfolio-ready demo later:

1. Run the notebook and generate representative outputs.
2. Save approved images under a directory such as `assets/demo/`.
3. Add Markdown image links and short captions to this section.
4. Check that prompts, outputs, and any embedded metadata are safe to publish.

## Limitations and responsible use

- Output quality and generation speed depend on hardware, memory, prompts, and inference settings.
- CPU execution may be impractical for interactive SDXL use.
- Generated images may contain visual artifacts, inaccurate text, anatomical errors, or biased representations.
- Review outputs before publication or downstream use.
- Follow the applicable model, dataset, software, and platform licenses.

## Future improvements

Possible presentation or experimentation extensions include:

- Add a documented gallery of repository-hosted demo outputs.
- Add reproducible seeds and output metadata.
- Document GPU-memory guidance for common hardware configurations.
- Add notebook validation or an environment smoke test.
- Provide a lightweight interface without changing the current notebook workflow.

## Credits and acknowledgements

- [Stability AI](https://stability.ai/) for the Stable Diffusion XL model family.
- [Hugging Face Diffusers](https://github.com/huggingface/diffusers) for the inference pipelines.
- [PyTorch](https://pytorch.org/) for tensor computation and hardware acceleration.
- [Weights & Biases](https://wandb.ai/) for optional experiment tracking.

## License

No license file is currently included. Licensing should be added only after confirming the author’s rights and selecting terms that appropriately cover the project code and applicable model usage.

## Author

Developed by [Awaisiqbal-Code](https://github.com/Awaisiqbal-Code).

For reproducibility questions or documentation improvements, open an issue in the repository with the relevant environment details and notebook cell context.
