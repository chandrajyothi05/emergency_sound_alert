# 🚨 Emergency Sound Detection System (Android + ML)

## Overview

An Android application that detects emergency sounds (siren, explosion, glass breaking, etc.) in real-time using an on-device machine learning model and alerts the user with a full-screen popup, vibration, and visual signals.

---

## Features

* Real-time sound classification (offline, on-device)
* Background detection using foreground service
* Full-screen emergency alerts (even on lock screen)
* Vibration + color-coded visual alerts
* False positive reduction using voting system
* Loud noise detection using dB threshold

---

## Tech Stack

* **Android:** Java, Android Studio (API 29+)
* **ML Model:** TensorFlow Lite
* **Backend/Training:** Python, TensorFlow/Keras
* **Audio Processing:** Librosa, NumPy

---

## Project Structure

```id="d3x91a"
backend/    # Model training, preprocessing
frontend/   # Android application
```

---

## How to Run (Frontend - Android App)

1. Open project in **Android Studio**
2. Connect device (API 29+)
3. Run the app
4. Grant microphone permission
5. Start monitoring

---

## Backend (Model Training)

```bash id="j2k7wp"
cd backend
pip install -r requirements.txt
python src/preprocess_audio_multiclass.py
python src/train_model_multiclass.py
```

---

## Dataset

* ESC-50 dataset + custom collected audio
* Classes include:

  * Siren
  * Glass Breaking
  * Baby Crying
  * Car Horn
  * Explosion
  * Non-emergency

> Dataset is not included in this repository

---

## Model Details

* CNN-based classifier (TensorFlow Lite)
* Input: MFCC features (40 × 216)
* Output: 6 sound classes
* Uses augmentation (noise, pitch shift, clipping, etc.)

---

## Detection Logic

* 5-second audio window processing
* MFCC feature extraction
* Model inference
* Voting system (2/3 agreement required)
* dB threshold for loud noise detection

---

## Permissions Used

* Microphone access
* Foreground service
* Full-screen intent
* Vibration

---

## Limitations

* Some class confusion (e.g., explosion vs glass)
* Performance depends on audio quality
* Requires proper device permissions

---

## Academic Context

Developed as a **3rd Year (Semester 6) Mini Project**
for Computer Science Engineering.

Focus areas:

* Machine Learning deployment
* Android development
* Real-time audio processing

---

## Authors

* Chandrajyothi Parambi Biju
* Lida Francis
* Maria Elizabeth Tomy
* Maria G Peter
  
