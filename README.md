# Stable Diffusion 2.1 Image Generation

A Python script for generating high-quality images using the Stable Diffusion 2.1 model from Hugging Face. This project includes GPU acceleration, customizable hyperparameters, and easy-to-use visualization of generated images.

## Features

- 🎨 **High-Quality Image Generation** - Uses Stable Diffusion 2.1 model
- ⚡ **GPU Acceleration** - Automatic GPU detection and optimization
- 🎛️ **Configurable Hyperparameters** - Adjust guidance scale, inference steps, and more
- 🖼️ **Visualization** - Built-in matplotlib support for comparing generated images
- 💾 **Reproducibility** - Seed-based reproducible image generation
- 📦 **Memory Optimization** - Optional xformers integration for efficient memory usage

## Requirements

- Python 3.8+
- PyTorch with CUDA support (for GPU acceleration)
- Hugging Face Diffusers library
- Matplotlib for visualization

## Installation

1. Clone the repository:
```bash
git clone https://github.com/rjtsh/GEN_AI_StableDiffusion.git
cd GEN_AI_StableDiffusion
```

2. Install dependencies:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
pip install diffusers transformers huggingface-hub pillow matplotlib xformers
```

3. (Optional) Login to Hugging Face for improved model access:
```bash
huggingface-cli login
```

## Usage

### Basic Usage

Run the script directly:
```bash
python gen_ai_stable_diffusion.py
```

### Customization

Edit the hyperparameter configuration section in the script:

```python
# === Hyperparameter Configuration ===
prompt = "A futuristic city skyline at sunset, ultra detailed, digital art"
guidance_scales = [5, 15]                  # Classifier-free guidance scales
num_inference_steps_list = [20, 50]        # Inference steps (higher = better quality but slower)
seed = 42                                  # Set to int for reproducibility, or None for random
width = 512                                # Image width
height = 512                               # Image height
```

### Parameter Explanations

| Parameter | Description | Range |
|-----------|-------------|-------|
| **prompt** | Text description of the image to generate | Any string |
| **guidance_scale** | Controls adherence to the prompt (higher = more adherent) | 5-20 (recommended) |
| **num_inference_steps** | Number of denoising steps (higher = better quality, slower) | 20-100 |
| **seed** | Random seed for reproducibility (None = random) | 0-2^32-1 |
| **width/height** | Image dimensions (must be multiple of 8) | 384-768 recommended |

## Performance Tips

- **GPU Required**: A GPU with at least 6GB VRAM is recommended for optimal performance
- **Memory Optimization**: The script automatically enables xformers if available for efficient memory usage
- **Batch Generation**: To generate multiple images, increase `num_inference_steps_list` or `guidance_scales`
- **Quality vs Speed**: Lower inference steps (20) = faster, higher steps (50+) = better quality

## Output

The script generates a 2x2 grid of images showing different combinations of:
- Guidance scales (rows)
- Inference steps (columns)

Each subplot displays:
- The generated image
- Guidance scale and inference steps used
- Overall prompt and image dimensions

## Model Information

- **Model**: Stable Diffusion 2.1 (community variant)
- **Source**: [sd2-community/stable-diffusion-2-1](https://huggingface.co/sd2-community/stable-diffusion-2-1)
- **License**: OpenRAIL License
- **Precision**: fp16 (half precision for memory efficiency)

## GPU Support

The script automatically detects GPU availability:
- ✅ GPU detected: Runs on CUDA for faster generation
- ⚠️ GPU not detected: Falls back to CPU (slower)

### For Google Colab

If running on Google Colab, enable GPU acceleration:
1. Go to Runtime → Change runtime type
2. Select GPU as Hardware accelerator

## Troubleshooting

### Out of Memory (OOM) Error
- Reduce image dimensions (e.g., 512x512 → 384x384)
- Reduce inference steps
- Disable xformers (comment out the enable_xformers line)

### Model Download Issues
- Ensure internet connection is stable
- Check Hugging Face token if using private models
- Clear cache: `rm -rf ~/.cache/huggingface`

### xformers Warning
- Optional but recommended for memory efficiency
- Install via: `pip install xformers`

## License

This project uses Stable Diffusion 2.1, which is licensed under the OpenRAIL License. See the [license](https://huggingface.co/stabilityai/stable-diffusion-2-1/blob/main/LICENSE-MODEL) for details.

## References

- [Stable Diffusion 2.1 Documentation](https://huggingface.co/sd2-community/stable-diffusion-2-1)
- [Diffusers Library](https://huggingface.co/docs/diffusers)
- [PyTorch Documentation](https://pytorch.org/docs/stable/index.html)

## Contributing

Feel free to submit issues and pull requests!

## Author

Created by [rjtsh](https://github.com/rjtsh)
