# Dancing_Robot
Audio-Driven TurtleBot3 
Objective
 • Develop a TurtleBot3 system that navigates based on audio cues. The project begins with audio pattern classification to control movements in gazebo environment.
 Novelty
 • Using audio signals as direct inputs for navigating a robot. This involves interpreting audio cues to generate directional commands, which is a creative intersection of audio processing and robotics
 Music Dataset: https://www.kaggle.com/datasets/andradaolteanu/gtzan-dataset-music-genre-classification

Dancing_Robot

Audio-Driven TurtleBot3

A project that enables a TurtleBot3 robot to respond and navigate based on audio cues.
The system integrates audio pattern classification with robotics control — interpreting musical or audio signals to send movement commands to the TurtleBot3 (in simulation or real-world).

🎯 Objective & Motivation

Use audio signals (e.g. music, sound patterns) as direct inputs for robot locomotion

Bridge audio processing / machine learning with robotics control

Demonstrate an interactive, multimodal system: sound → classification → motion

📂 Repository Structure
.
├── audio_processing_to_robot.py   # Core logic: audio feature extraction → robot commands  
├── Music_Classification.ipynb     # Notebook showing audio classification workflow  
├── classifier.joblib              # Trained audio classifier  
├── scaler.joblib                  # Feature scaling object  
└── README.md                      # This documentation file

⚙️ How It Works — Pipeline Overview

Audio Feature Extraction

Load audio signals (e.g. WAV, mp3)

Compute features (MFCCs, spectral, chroma, etc.)

Apply scaling / normalization

Audio Classification

Use a trained classifier (classifier.joblib) to predict the audio class / pattern

Classes might represent different commands, gestures, or behaviors

Command Mapping & Robot Control

Map each recognized audio class to a robot movement command (e.g. forward, turn, stop)

Send commands to the TurtleBot3 control interface (in Gazebo simulation or real hardware)

(Optional) Real-Time Loop

Continuously listen to audio

Classify and stream commands in real time

🔍 Usage
1. Prerequisites & Setup

Python 3.x

Install dependencies (e.g. librosa, numpy, scikit-learn, rospy, pyaudio)

Ensure TurtleBot3 is properly configured or simulated in Gazebo

Install dependencies:

pip install -r requirements.txt


(If requirements.txt isn’t included, manually install libraries such as librosa, numpy, scikit-learn, and rospy.)

2. Train / Prepare the Classifier (optional)

If you want to retrain your own classifier:

Open the Jupyter notebook:

jupyter notebook Music_Classification.ipynb


Run all cells to extract features, train, and evaluate the model.

Save the trained model:

joblib.dump(model, "classifier.joblib")
joblib.dump(scaler, "scaler.joblib")

3. Run the Audio-to-Robot Script
python audio_processing_to_robot.py --audio_input path/to/audio.wav


The script reads an audio file, classifies it, and sends the corresponding motion command to the TurtleBot3.

Modify mappings in the script to define how each class maps to a movement.

Example mapping snippet:

if predicted_class == "upbeat":
    move_forward()
elif predicted_class == "calm":
    rotate()
else:
    stop()

4. Extend & Customize

Add new music genres or sound patterns as training data

Experiment with deep learning (CNN/RNN-based) audio models

Incorporate real-time microphone streaming

Introduce gesture + audio control for hybrid interaction

🧪 Example Outputs & Behavior

The robot moves or responds differently to different audio classes

In Gazebo simulation, TurtleBot3 dances or moves rhythmically

On real hardware, the robot physically performs the mapped motion

Future additions could include:

Demo GIFs of robot motion

Audio input vs. command logs

Real-time performance visualization

🚀 Potential Improvements & Ideas

Real-time audio streaming (live microphone classification)

Deep learning classifiers (CNN, RNN, or CRNN architectures)

Two-way feedback: robot sensors influence its movement rhythm

Gesture or speech commands combined with audio-based control

Multi-robot choreography for synchronized motion

📚 Related Work / Dataset

Dataset used (for reference): GTZAN Music Genre Dataset (Kaggle)

Conceptual inspiration: Audio-to-movement mapping in robotic art and performance systems

🧠 Technical Notes

Audio features: MFCC, chroma STFT, spectral centroid, zero-crossing rate

Model type: Scikit-learn classifier (can be replaced with deep learning)

Robot commands: ROS / TurtleBot3 motion commands via rospy

Supported inputs: .wav, .mp3 (converted internally to mono, 22050 Hz)

📄 Citation

If you use or build upon this work, please cite:

@misc{dancing_robot2025,
  author = {Minhah Saleem},
  title = {Audio-Driven TurtleBot3: Dancing Robot},
  year = {2025},
  url = {https://github.com/Minhah-Saleem/Dancing_Robot}
}

👩‍💻 Author & Contact

Minhah Saleem
AI / Robotics Integrator
📍 Seoul, Republic of Korea

Feel free to open issues or reach out if you want to collaborate, test, or extend this project.

❤️ Acknowledgements

TurtleBot3 by ROBOTIS for open-source ROS integration

Librosa and Scikit-learn for fast prototyping in audio ML

Gazebo for providing a great testing environment

This README is crafted to provide clarity, motivation, and guidance for extending the Dancing Robot project — bridging sound, intelligence, and motion.
