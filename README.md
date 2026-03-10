# Side-Step Training Queue Web Form

A browser-based configuration tool for [Side-Step](https://github.com/koda-dernet/Side-Step) - the LoRA/DoRA/LoKR trainer for ACE-Step 1.5 music generation models.

**🚀 [Use the Live Form](https://mmoalem.github.io/side-step-jobs-queue-webform/)**

## What is This?

This is a web-based form that generates CLI commands and batch/shell scripts for Side-Step training jobs. Instead of manually writing complex command-line arguments, use this form to:

- Configure training parameters through an intuitive interface
- Queue multiple jobs for overnight training runs
- Generate cross-platform batch files (Windows .bat / Linux/Mac .sh)
- Switch between training and preprocessing tasks
- Access comprehensive tooltips explaining every parameter

**No installation required** - runs entirely in your browser. Your data never leaves your machine.

## Features

### 📋 Two Task Types

- **Training** - Train LoRA/DoRA/LoKR/LoHA/OFT adapters on preprocessed tensors
- **Preprocessing** - Convert raw audio files to .pt training tensors

### 🎯 Comprehensive Configuration

- **All adapter types**: LoRA, DoRA, LoKR, LoHA, OFT with full parameter control
- **Training hyperparameters**: Learning rate, batch size, epochs, optimizers, schedulers
- **Memory optimization**: Gradient checkpointing, encoder offloading, data loading settings
- **Advanced options**: CFG dropout, loss weighting, checkpointing strategies
- **Cross-platform paths**: Works with Windows, Linux, and macOS file paths

### 💡 User-Friendly Features

- **Interactive tooltips**: Click the blue `?` icons for detailed explanations of each parameter
- **Job queue manager**: Configure multiple jobs and run them sequentially
- **Live command preview**: See the generated CLI command as you configure
- **Smart defaults**: Beta 1 defaults pre-configured (3e-4 LR, adamw8bit optimizer)
- **Platform detection**: Automatic Windows/Linux data loading defaults

### 📦 Export Options

- **Download as .bat** (Windows)
- **Download as .txt** (to bypasses Windows security blocking - just rename to .bat after download)
- **Download as .sh** (Linux/Mac)
- **Copy to clipboard** (paste into terminal)

## Quick Start

### Option 1: Use the Live Form (Recommended)

**[Open the form in your browser](https://mmoalem.github.io/side-step-jobs-queue-webform/)**

1. Select task type (Training or Preprocessing)
2. Fill in your paths and parameters
3. Click "Add to Queue"
4. Download your batch file
5. Run it!

### Option 2: Run Locally

```bash
# Clone the repository
git clone https://github.com/mmoalem/side-step-jobs-queue-webform.git
cd side-step-jobs-queue-webform

# Open in your browser
# Just open sidestep_form_clean_beta1.html in any browser
```

No web server needed - it's a standalone HTML file.

## Usage Example

### Basic Training Job

1. **Select "Training"** task type
2. **Fill in required paths:**
   - Checkpoint Directory: `E:\ACE-Step\checkpoints`
   - Dataset Directory: `E:\my_dataset\tensors`
   - Output Directory: `E:\output\my_lora`
3. **Configure adapter:**
   - Adapter Type: LoRA
   - Rank: 128
   - Alpha: 256
4. **Set training params:**
   - Learning Rate: 0.0003 (3e-4)
   - Batch Size: 2
   - Epochs: 800
5. **Add to queue** and download .bat file

Generated command:
```bash
uv run sidestep --yes train \
  --checkpoint-dir "E:\ACE-Step\checkpoints" \
  --dataset-dir "E:\my_dataset\tensors" \
  --output-dir "E:\output\my_lora" \
  --model base \
  --rank 128 \
  --alpha 256 \
  --batch-size 2 \
  --epochs 800
```

### Queue Multiple Jobs

1. Configure first job → Add to Queue
2. Configure second job (different dataset/parameters) → Add to Queue
3. Configure third job → Add to Queue
4. Switch to "Job Queue" tab
5. Download batch file
6. Run overnight!

## Requirements

- **Side-Step Beta 1+** installed ([Installation Guide](https://github.com/koda-dernet/Side-Step))

## Windows Security Note

Windows may block downloaded .bat files with "internet security settings prevented files from being opened."

**Solution:** Use the **"Download as .txt"** button, then rename the file from `.txt` to `.bat` on your computer. Files renamed locally don't get the security flag.

## What Commands Does This Generate?

This form generates Beta 1 compatible commands:

```bash
# Training command structure:
uv run sidestep --yes train \
  --checkpoint-dir "..." \
  --dataset-dir "..." \
  --output-dir "..." \
  --model [turbo|base|sft] \
  --rank 128 \
  --alpha 256 \
  [... additional parameters ...]

# Preprocessing command structure:
uv run sidestep --yes preprocess \
  --checkpoint-dir "..." \
  --audio-dir "..." \
  --output "..." \
  --model [turbo|base|sft]
```

All commands use the Beta 1 CLI syntax with correct parameter names and flag placement.

## Beta 1 Compatibility

This form is designed for **Side-Step Beta 1 and later**. Key updates from Alpha:

- ✅ Uses `sidestep train` (not `python train.py fixed`)
- ✅ Global flags placed correctly (`--yes` before `train`)
- ✅ Uses `--model` instead of `--model-variant`
- ✅ No `--base-model` parameter (auto-detected)
- ✅ Default LR: 3e-4, Default optimizer: adamw8bit
- ✅ Separate preprocessing commands via `sidestep preprocess`

## Tooltips Guide

Click the blue `?` icons throughout the form for detailed explanations:

- **Parameter explanations** with analogies
- **Valid input values** and examples
- **When to change** vs. leave default
- **Impact badges**: 🔴 VRAM | 🟠 Speed | 🟢 Quality | ⚪ Neutral

Perfect for both beginners learning Side-Step and advanced users fine-tuning parameters.

## File Structure

```
.
├── sidestep_form_clean_beta1.html    # Main form (use this one)
├── sidestep_debug_form.html          # Debug version with console logging
├── BETA1_MIGRATION_GUIDE.md          # Alpha → Beta 1 migration guide
├── ALL_UPDATES_SUMMARY.md            # Form update history
└── README.md                          # This file
```

## Credits

- **Side-Step**: [koda-dernet/Side-Step](https://github.com/koda-dernet/Side-Step) - The underlying LoRA trainer
- **ACE-Step 1.5**: Music generation model by Stability AI
- **Form Design**: Built with pure HTML/CSS/JavaScript - no frameworks

## License

MIT License - Free to use, modify, and distribute.

## Contributing

Issues and pull requests welcome! If you find bugs or have feature requests, please open an issue.

## Disclaimer

This is an **unofficial community tool** for Side-Step. It is not affiliated with or endorsed by the Side-Step developers or Stability AI. Always verify generated commands before running them.

## Support

- **Side-Step Issues**: [Side-Step GitHub Issues](https://github.com/koda-dernet/Side-Step/issues)
- **Form Issues**: [This Repository's Issues](https://github.com/mmoalem/side-step-jobs-queue-webform/issues)

## Changelog

### v1.0 - Beta 1 Support
- Full Beta 1 CLI compatibility
- Training and preprocessing task types
- Job queue manager
- Cross-platform batch file generation
- Comprehensive tooltips for all parameters
- Download as .txt to bypass Windows security
- Smart defaults matching Beta 1

---

**[🚀 Start using the form now!](https://mmoalem.github.io/side-step-jobs-queue-webform/)**
