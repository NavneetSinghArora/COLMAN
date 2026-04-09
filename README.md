# COLMAN: Collaborative Multi-Agent Navigation

[![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/license-Proprietary-red.svg)](LICENSE)
[![AI2-THOR](https://img.shields.io/badge/Simulator-AI2--THOR-green.svg)](https://ai2thor.allenai.org/)

**COLMAN** is a state-of-the-art framework for **COLlaborative Multi-Agent Navigation** and interaction. Built upon the [AI2-THOR](https://ai2thor.allenai.org/) simulation environment and inspired by [Cordial-Sync](https://github.com/allenai/cordial-sync), this project focuses on multi-agent communication, visual-path navigation, object detection, and precise object manipulation in photo-realistic 3D indoor scenes.

---

## 🚀 Key Features

- 🤝 **Multi-Agent Collaboration**: Synchronized navigation and task execution using multiple agents.
- 📍 **Visual-Path Navigation**: Egocentric visual perception for intelligent pathfinding.
- 🔍 **Object Detection & Movement**: Advanced modules for identifying and interacting with objects (pickup, movement, etc.).
- 🛠️ **CLI Interface**: A powerful Command Line Interface (`attention_and_move`) for training, dataset preparation, and evaluation.
- 🏗️ **Modular Architecture**: Clean separation between simulator logic, core models, and specialized services.

---

## 📂 Project Structure

The project is organized into several key directories:

| Directory | Description |
| :--- | :--- |
| `src/core` | Contains the core logic, including models, simulator wrappers, and domain services. |
| `src/scripts` | Entry point scripts for the CLI and standalone utilities (dataset preparation, image stitching). |
| `resources` | Configuration files for project-wide settings and AI2-THOR simulator parameters. |
| `output` | Storage for training checkpoints, embeddings, birds-eye view images, and logs. |
| `hummel` | Integration modules for high-performance computing (HPC) environments. |

---

## 🛠️ Installation

### 1. Clone the Repository
```bash
git clone https://github.com/NavneetSinghArora/COLMAN.git
cd COLMAN
```

### 2. Set Up Environment
We recommend using [Conda](https://docs.anaconda.com/anaconda/install/) to manage dependencies:

```bash
conda create -n colman python=3.8
conda activate colman
```

### 3. Install Dependencies
Install the package in editable mode to ensure all entry points are registered:

```bash
pip install -e .
```

> [!NOTE]
> This project requires **PyTorch** and **AI2-THOR**. Refer to `setup.py` for specific version requirements matched to your OS (Linux/macOS).

---

## 🎮 Usage

The project uses the `attention_and_move` CLI for all major operations.

### Training
Start local training with various options (GPU, learning rate, epochs, etc.):
```bash
attention_and_move training --start --platform OSXIntel64 --gpu 1 --epochs 50
```

### Dataset Preparation
Collect egocentric agent views across different scenes to build a custom dataset:
```bash
attention_and_move dataset --create --scene LivingRoom --scene Kitchen
```

### Utilities
- `src/scripts/stitch_images.py`: Combine multiple egocentric views for panoramic or bird-eye analysis.
- `src/scripts/prepare_train_val_test.py`: Split collected data into standard machine learning folds.

---

## ⚙️ Configuration

System behavior is managed through `.properties` files in the `resources/` folder:

- **`project/configuration.properties`**: Global project settings, such as object detection thresholds.
- **`simulator/configuration.properties`**: AI2-THOR specific settings:
    - `number_of_agents`: Set to `2` by default for collaborative tasks.
    - `agent_mode`: Choose between `default`, `locobot`, or `arm` (ManipulaTHOR).
    - `target_object`: Define the goal for navigation tasks (e.g., `Television`, `Sofa`).

---

## 🧠 Core Architecture

- **`Environment.py`**: A Singleton class that manages the AI2-THOR controller, agent teleportation, and scene randomization.
- **`GlobalVariables.py`**: A centralized class holding project-wide properties, accessible across all modules.
- **Model modularity**: Separate modules for RL-based navigation, goal-oriented object detection, and multi-agent signaling.

---

## 📚 References & Acknowledgments

This project is part of a **Computer Vision Master Project** and builds upon significant research in Embodied AI.

- **[AI2-THOR](https://ai2thor.allenai.org/)**: The House Of inteRactions.
- **[Cordial-Sync](https://github.com/allenai/cordial-sync)**: Collaborative Robot Navigation via DIALogue.
- **[NavneetSinghArora/AI2Thor](https://github.com/NavneetSinghArora/AI2Thor)**: Supporting utilities and research.
- **[NavneetSinghArora/EmbodiedAI](https://github.com/NavneetSinghArora/EmbodiedAI)**: Related work in embodied agents.

---

## 📄 License

(c) Copyright by author. See `LICENSE` for details.
