# Real-Time Face Recognition Attendance System

An AI-assisted real-time attendance monitoring system built using OpenCV and DeepFace.  
The system performs live face detection, face recognition, attendance tracking, session monitoring, and runtime telemetry visualization with multiple reliability-focused enhancements.

---

# Overview

This project was initially started as a group-based attendance automation system to reduce manual attendance tracking.  
Later, the system was independently improved to address recognition instability, improve runtime reliability, and enhance the overall user experience.

The project evolved from a basic webcam attendance system into a more stable and interview-ready real-time monitoring application through multiple iterative improvements.

---

# Key Features

## Core Features
- Real-time webcam-based face detection
- Face recognition using DeepFace embeddings
- Automatic attendance marking
- Session duration tracking
- CSV attendance report generation
- Permission-based attendance handling
- Email notification support

---

## Reliability & System Enhancements

### Temporal Anti-Flicker Stabilization
- Rolling prediction buffer
- Majority-vote confirmation logic
- Sticky identity switching mechanism
- Reduces rapid label flickering between frames

### Face Quality Validation
Geometry-based validation before recognition:
- Minimum face size check
- Edge-boundary validation
- Face aspect-ratio validation

This prevents low-quality detections from entering the recognition pipeline.

### Real-Time Telemetry Overlay
Live runtime monitoring includes:
- FPS counter
- Total faces detected
- Recognized faces count
- Unregistered faces count

### Attendance Cooldown System
Prevents repeated attendance confirmations within a short duration using cooldown-based gating logic.

### Recent Activity Panel
Displays recent recognition events with:
- Timestamp
- Detection status
- Recognition labels

### Improved Recognition UX
- Replaced generic "Unknown" labels with "Unregistered Face"
- Added "Detecting..." transitional state for stabilization buffering

---

# Tech Stack

| Component | Technology |
|---|---|
| Programming Language | Python |
| Face Detection | OpenCV Haar Cascades |
| Face Recognition | DeepFace |
| Numerical Processing | NumPy |
| Data Handling | Pandas |
| Runtime Visualization | OpenCV |
| Email Notifications | SMTP |

---

# System Workflow

1. Webcam captures live video frames
2. OpenCV detects faces in the frame
3. Face quality validation filters poor detections
4. DeepFace generates embeddings
5. Embeddings are matched against stored embeddings database
6. Temporal stabilizer confirms recognition consistency
7. Attendance is recorded
8. Telemetry and activity panels update in real-time
9. Attendance logs are exported to CSV

---

# Project Structure

```bash
attendance/
│
├── main.py
├── recognition.py
├── attendance.py
├── utils.py
├── email_service.py
├── config.py
├── requirements.txt
├── README.md
│
├── assets/
│   ├── screenshot1.png
│   ├── screenshot2.png
│
└── .gitignore
```

---

# Major Improvements Added During Development

## 1. Temporal Stabilization System
The initial recognition system suffered from prediction flickering across consecutive frames.

Solution:
- Implemented rolling-window confirmation logic
- Added sticky identity switching
- Added detection buffering

Impact:
- Improved recognition consistency
- Reduced unstable predictions

---

## 2. Runtime Telemetry System
The initial system lacked runtime observability.

Solution:
- Added FPS monitoring
- Added detection statistics overlay

Impact:
- Easier debugging
- Better performance visibility
- More professional demo presentation

---

## 3. Face Quality Validation Layer
Recognition was being attempted even on poor-quality face detections.

Solution:
- Added geometric face validation checks

Impact:
- Reduced unnecessary recognition attempts
- Improved recognition reliability

---

# Challenges Faced

## Recognition Flickering
The recognition labels frequently switched between frames due to single-frame prediction instability.

### Solution
Implemented temporal smoothing and majority-vote stabilization.

---

## Poor Face Input Quality
Low-quality detections negatively affected recognition consistency.

### Solution
Added lightweight geometric validation before inference.

---

## Lack of Runtime Monitoring
No visibility into FPS or recognition activity.

### Solution
Implemented telemetry overlay and activity history panel.

---

# Current System Capabilities

The current system supports:

- Stable real-time face recognition
- Attendance session tracking
- Live telemetry monitoring
- Detection activity visualization
- Face quality validation
- Cooldown-based attendance gating
- CSV report generation
- Email notification workflow

---

# How to Run

## 1. Clone Repository

```bash
git clone https://github.com/YOUR_USERNAME/real-time-face-recognition-attendance-system.git
cd real-time-face-recognition-attendance-system
```

---

## 2. Install Dependencies

```bash
pip install -r requirements.txt
```

---

## 3. Add Dataset

Create a `dataset/` directory.

Example:

```bash
dataset/
├── person1/
│   ├── img1.jpg
│   ├── img2.jpg
│
├── person2/
│   ├── img1.jpg
```

---

## 4. Run Application

```bash
python main.py
```

---

# Future Improvements

Possible future extensions:
- Face tracking instead of position-based stabilization
- Deep learning-based face quality assessment
- Web dashboard for attendance analytics
- Database integration
- Multi-camera support
- Cloud deployment

---

# Screenshots

Add screenshots inside the `assets/` folder and reference them here.

Example:

```markdown
![System Screenshot](assets/screenshot1.png)
```

---

# Notes

- Dataset images and generated attendance logs are excluded from the repository for privacy and repository cleanliness.
- Gmail email functionality requires App Password authentication instead of a normal Gmail password.

---

# License

This project is licensed under the MIT License.