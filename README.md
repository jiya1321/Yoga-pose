# ✨ AI Yoga Pose Detection System ✨

A real-time AI-powered yoga trainer built using MediaPipe Pose, OpenCV, NumPy, and Flask.

The system detects yoga poses through body joints and skeleton tracking, compares them with ideal pose angles, gives live feedback, captures mistakes, and generates reports.

---

# 🧩 Highlights

* 🦴 Real-time skeleton and joint detection using MediaPipe Pose
* 📷 Webcam-based yoga pose tracking
* 🎯 Detects poses using body landmarks and joint angles
* 📊 Confidence percentage and accuracy score
* 🧍 Full-body and upper-body pose support
* 📸 Screenshot capture for incorrect poses
* 📄 PDF report generation with screenshots and suggestions
* 📝 Real-time feedback system
* ⏱️ Session timer and statistics dashboard
* ➕ Add Custom Pose feature
* 💾 Save trained model locally
* 🎨 Dark modern UI with webcam overlay and pose stats

# ⚙️ Features Breakdown

## 1. Add Custom Pose

* User clicks "Add Custom Pose"
* Webcam records body movement for 5–10 seconds
* MediaPipe extracts all 33 body landmarks
* Pose name is saved with extracted keypoints
* The model is retrained with the new pose
* Trained model is saved locally

## 2. Start Yoga Session

* Starts webcam feed
* Detects body joints and skeleton in real time
* Shows:

  * Pose name
  * Confidence score
  * Accuracy percentage
  * Session timer
  * Real-time feedback
* Tracks correct and incorrect poses
* Saves screenshots for incorrect poses

## 3. Select Pose + Evaluation

* User selects a predefined or custom pose
* System compares live pose with saved reference angles
* Calculates joint angles for:

  * Shoulders
  * Elbows
  * Hips
  * Knees
  * Ankles
  * Torso
* Generates confidence and accuracy score

---

# 🦴 MediaPipe Skeleton Tracking

The system uses MediaPipe Pose with all 33 body landmarks.

Important landmarks:

* Nose
* Shoulders
* Elbows
* Wrists
* Hips
* Knees
* Ankles
* Feet
* Torso

Skeleton connections are drawn using official MediaPipe body connections only.

---

# 📊 Confidence Logic

* 0–30% → Incorrect pose
* 30–60% → Partially correct pose
* 60–80% → Almost correct pose
* 80–100% → Correct pose

The pose is marked correct only if the confidence stays above 80% for a few seconds.

---

# 🛠️ Tech Stack

* Python
* MediaPipe
* OpenCV
* NumPy
* Flask / Streamlit
* Scikit-learn / TensorFlow
* ReportLab / FPDF

---

# ⚡ Installation

```bash
pip install mediapipe==0.10.9
pip install opencv-python
pip install numpy
pip install flask
pip install scikit-learn
pip install reportlab
```

Or install everything using:

```bash
pip install -r requirements.txt
```

---

# 🔧 Environment Setup

## Backend

```env
FLASK_ENV=development
FLASK_APP=app.py
MODEL_PATH=models/pose_model.pkl
DATASET_PATH=data/
SCREENSHOT_PATH=screenshots/
REPORT_PATH=reports/
```

---

# ▶️ Run the Backend

```bash
cd backend
python app.py
```


# 📄 PDF Report Includes

* Pose name
* Accuracy percentage
* Correct / incorrect count
* Session duration
* Mistakes detected
* Suggestions for correction
* Screenshots of incorrect poses
* Final session summary
