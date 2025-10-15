# 🤖 Dancing_Robot  
**Audio-Driven TurtleBot3 Project**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![GitHub issues](https://img.shields.io/github/issues/Minhah-Saleem/Dancing_Robot)](https://github.com/Minhah-Saleem/Dancing_Robot/issues)
[![GitHub stars](https://img.shields.io/github/stars/Minhah-Saleem/Dancing_Robot)](https://github.com/Minhah-Saleem/Dancing_Robot/stargazers)

---

## 🧭 Table of Contents
- [Project Overview](#project-overview)
- [Motivation & Objectives](#motivation--objectives)
- [Architecture & Workflow](#architecture--workflow)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
- [Usage](#usage)
  - [Training / Classification](#training--classification)
  - [Controlling Robot](#controlling-robot)
- [Dataset](#dataset)
- [Results & Demonstration](#results--demonstration)
- [Limitations & Future Work](#limitations--future-work)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

---

## 🎯 Project Overview
**Dancing_Robot** integrates *audio processing* and *robot control* using the **TurtleBot3** platform.  
Instead of relying on visual or distance sensors, the robot responds to **audio cues** (like beats or genre) and moves in rhythm — effectively, *it dances to music!*

The project demonstrates:
- Audio feature extraction and classification  
- Machine learning model integration  
- Real-time motion mapping to robot control via ROS or simulation

---

## 💡 Motivation & Objectives

### Motivation
Robots can perceive the world beyond sight. This project explores how *sound* can be used as a control input for robot motion.

### Objectives
- Capture and analyze audio signals (music/sound)
- Extract audio features (e.g., MFCCs)
- Train a classifier to distinguish patterns or genres
- Map each classification to specific robot motion commands
- Control or simulate a TurtleBot3’s movement based on sound

---

## 🧩 Architecture & Workflow


Audio Input
│
▼
Feature Extraction (Librosa)
│
▼
Scaler + Classifier (scikit-learn)
│
▼
Predicted Label → Movement Mapping
│
▼
Robot Control (ROS / Gazebo / TurtleBot3)


**Modules:**
1. **Audio Processing** – Extracts features from sound clips.  
2. **Model Training** – Builds an ML classifier (`classifier.joblib`).  
3. **Inference Loop** – Predicts classes for real-time audio input.  
4. **ROS Interface** – Publishes corresponding velocity commands.  

---

## ⚙️ Getting Started

### Prerequisites

Make sure you have:
- Python **3.7+**
- **ROS Noetic** (or compatible version)
- **TurtleBot3** packages
- **Gazebo** simulator (optional)
- Python libraries:
  - `numpy`, `librosa`, `scikit-learn`, `joblib`, `matplotlib`

### Installation

```bash
# Clone the repository
git clone https://github.com/Minhah-Saleem/Dancing_Robot.git
cd Dancing_Robot

# (Optional) Create a virtual environment
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install required packages
pip install -r requirements.txt
````

If you’re running inside ROS, ensure your workspace is properly sourced:

```bash
source /opt/ros/noetic/setup.bash
```

---

## 🚀 Usage

### 🧠 Training / Classification

To train your own model on a dataset (e.g., GTZAN):

```bash
python audio_processing_to_robot.py --mode train
```

* Extracts features
* Trains a classifier
* Saves:

  * `classifier.joblib`
  * `scaler.joblib`

### 🤖 Controlling the Robot

After training, run inference to control the robot or simulation:

```bash
python audio_processing_to_robot.py --mode run
```

This script:

* Reads audio input (live or from file)
* Predicts the sound class
* Publishes velocity commands to the TurtleBot3

Adjust topic names and robot parameters as needed in your ROS configuration.

---

## 🎵 Dataset

Default: [**GTZAN Music Genre Dataset**](https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification)

You can also use your own dataset:

* Organize by folder (each genre → separate folder)
* Modify the data loader accordingly

---

## 📊 Results & Demonstration

Include demo results, accuracy scores, and visuals.
You can embed videos or GIFs like this:

> 🎬 *Example Output:*
> The robot moves faster for upbeat music and slower for calm tracks.

```text
Genre → Movement Mapping
-------------------------
Rock      → Spin in place
Jazz      → Slow wave motion
Classical → Smooth forward movement
Pop       → Circle dance
```

*(Add GIFs or links to YouTube demo videos here!)*

---

## 🚧 Limitations & Future Work

| Limitation                   | Future Direction                       |
| ---------------------------- | -------------------------------------- |
| Real-time inference lag      | Optimize model and threading           |
| Background noise sensitivity | Use noise reduction and VAD            |
| Simple motion mapping        | Add continuous tempo-based control     |
| Simulated environment        | Deploy on physical TurtleBot3 hardware |

---

## 🤝 Contributing

Contributions, issues, and pull requests are welcome!

To contribute:

```bash
# Fork and clone the repo
git checkout -b feature/your-feature
# Make your changes
git commit -m "Add your feature"
git push origin feature/your-feature
```

Then create a **Pull Request** on GitHub.

---

## 📜 License

This project is licensed under the **MIT License**.
See the [LICENSE](LICENSE) file for more details.

---

## 🙏 Acknowledgments

* **GTZAN Dataset** – For audio data
* **TurtleBot3 / ROS Community** – For robotics framework
* **Librosa**, **scikit-learn**, **Joblib** – For feature extraction & ML
* Special thanks to all open-source contributors 💙

---

> 🕺 *Let your robot feel the rhythm!*

Would you like me to include a **"Demo GIF placeholder section"** with Markdown code you can later replace with your real robot video or simulation GIF?
```
