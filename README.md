# Text-to-Image SDXL

![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white)
![Diffusers](https://img.shields.io/badge/Hugging%20Face-Diffusers-FFD21E?logo=huggingface&logoColor=black)
![Model](https://img.shields.io/badge/Model-Stable%20Diffusion%20XL-6C5CE7)

A notebook-based text-to-image generation project that demonstrates inference with **Stable Diffusion XL (SDXL)** through Hugging Face Diffusers.

> **Project status:** Educational/experimental inference notebook. The repository preserves the original notebook workflow and does not claim to provide a production serving API or model training pipeline.

## Overview

The project turns a natural-language prompt into an image using the SDXL text-to-image pipeline. Runtime configuration—including the prompt, negative prompt, inference steps, and guidance scale—is supplied in the notebook and can be tracked with Weights & Biases.

### Workflow

```text
Text prompt + optional negative prompt
              │
              ▼
   SDXL pipeline loaded with Diffusers
              │
              ▼
     GPU acceleration when available
              │
              ▼
          Generated image
```

## Features

- Text-conditioned image generation with `StableDiffusionXLPipeline`.
- Automatic CUDA detection with CPU fallback in the notebook workflow.
- Configurable positive and negative prompts.
- Configurable inference steps and guidance scale.
- Optional SDXL base/refiner components exposed by the notebook.
- Optional experiment configuration and tracking through Weights & Biases.
- Jupyter-first workflow that is easy to inspect, modify, and extend.

## Technology stack

| Area | Technology |
| --- | --- |
| Language | Python |
| Interface | Jupyter Notebook |
| Generative model | Stable Diffusion XL 1.0 |
| Inference | Hugging Face Diffusers and PyTorch |
| Model formats | Hugging Face model checkpoints / SafeTensors-compatible dependencies |
| Experiment tracking | Weights & Biases (`wandb`) |

## Repository structure

```text
text-to-image-sdxl/
├── text_to_image.ipynb   # Original SDXL inference notebook
├── models/               # Local model assets, when used; do not commit large weights
├── README.md             # Project documentation
├── requirements.txt      # Python dependencies for the notebook
└── .gitignore            # Python, Jupyter, ML artifact, and secret exclusions
```

The notebook remains the source of truth for the runnable implementation. No source-code rewrite or notebook conversion is required.

## Setup

### Requirements

- Python 3.9 or newer
- Jupyter Notebook or JupyterLab
- A CUDA-capable GPU is strongly recommended for practical SDXL inference
- Sufficient disk space and memory for the selected SDXL checkpoints
- Access to the Hugging Face model repositories used by the notebook
- A Weights & Biases account only if experiment tracking is enabled

### Installation

```bash
git clone https://github.com/Awaisiqbal-Code/text-to-image-sdxl.git
cd text-to-image-sdxl

python -m venv .venv
# macOS/Linux
source .venv/bin/activate
# Windows PowerShell: .venv\\Scripts\\Activate.ps1

python -m pip install --upgrade pip
pip install -r requirements.txt
jupyter lab
```

Open `text_to_image.ipynb` in Jupyter and run the cells from top to bottom.

## Usage

The notebook uses the SDXL base model identifier:

```text
stabilityai/stable-diffusion-xl-base-1.0
```

The SDXL refiner identifier is also referenced by the notebook workflow:

```text
stabilityai/stable-diffusion-xl-refiner-1.0
```

The notebook selects CUDA when available and otherwise falls back to CPU. Edit the prompt, negative prompt, and generation configuration in the notebook before running inference.

### Example prompts

Use prompts appropriate to your own experiment, for example:

- `A cinematic photograph of a mountain cabin at sunrise, detailed natural lighting`
- `A futuristic research laboratory in a dense rainforest, architectural photography`
- `A watercolor illustration of a quiet coastal village, soft morning light`

The notebook also contains its original demonstration prompt and generation configuration. Those values have intentionally not been duplicated here so the notebook remains the authoritative executable example.

### Input and output

- **Input:** text prompt, optional negative prompt, and generation parameters.
- **Processing:** SDXL text-to-image inference through Diffusers and PyTorch.
- **Output:** one or more generated images returned by the pipeline and displayed or saved according to the notebook cells.

## Demo

No generated image assets are included in the repository at the time of this documentation update. To add a portfolio-ready demo:

1. Generate a few representative outputs with the notebook.
2. Save them under a directory such as `assets/demo/`.
3. Add captions and Markdown image links here.
4. Confirm that the files are safe to publish and do not contain private prompts or data.

## Model limitations and responsible use

- SDXL output quality and speed depend heavily on available GPU memory, inference settings, and prompt wording.
- CPU execution may be impractical for interactive use.
- Generated images can contain artifacts, inaccurate text, anatomical errors, or biased representations.
- Outputs should be reviewed before publication or downstream use.
- Model and generated-content usage must follow the applicable model, dataset, and platform licenses.

## Future improvements

Potential extensions, without changing the current notebook behavior, include:

- Add a small, documented demo-output gallery.
- Expose generation settings through a lightweight UI or configuration file.
- Add reproducible seeds and output metadata.
- Add notebook validation or a smoke-test workflow for the documented environment.
- Document GPU-memory guidance for common hardware configurations.

## Credits and acknowledgements

- [Stability AI](https://stability.ai/) for the Stable Diffusion XL model family.
- [Hugging Face Diffusers](https://github.com/huggingface/diffusers) for the inference pipelines.
- [PyTorch](https://pytorch.org/) for tensor computation and hardware acceleration.
- [Weights & Biases](https://wandb.ai/) for optional experiment tracking.

## License

No license file was present or added because the repository does not currently provide an explicit license for this project. Add a license only after confirming that the project author has the right to do so and selecting terms that cover both the project code and the applicable model usage.

## Author

Developed by [Awaisiqbal-Code](https://github.com/Awaisiqbal-Code).

If this project is useful, consider starring the repository and opening an issue with reproducibility notes or improvement ideas.
