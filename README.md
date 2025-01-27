# Facial Recognition Attendance System

This project demonstrates the implementation of facial recognition technology to create a real-time attendance system. The application uses a webcam to detect faces, matches them against a pre-defined dataset of known faces, and records attendance in an Excel-compatible CSV file.

## Features

- **Face Recognition**: Detects and identifies faces using the `face_recognition` library.
- **Real-Time Detection**: Leverages a live webcam feed to recognize faces on the fly.
- **Attendance Logging**: Automatically logs the name and timestamp of identified individuals in a CSV file.
- **Labeling Unknown Faces**: Identifies unknown faces and ensures they are not marked in attendance.

---

## Setup Instructions

### Prerequisites

Ensure you have the following installed:
- Python 3.7 or higher
- pip (Python package installer)
- A webcam (for live detection)

### Required Python Libraries

Install the dependencies by running:

```bash
pip install opencv-python
pip install numpy
pip install face_recognition
```

### Directory Structure

Organize your project as follows:

```
Facial-Recognition-Attendance/
├── ImagesAttendance/         # Folder containing images of known individuals
│   ├── Person1.jpg
│   ├── Person2.jpg
│   └── ...
├── Attendance.csv            # Output file for attendance logs
├── basics.py                 # Script for basic face recognition
├── attendance.py             # Main script for the attendance system
└── README.md                 # Project documentation
```

---

## Usage

### 1. Prepare Known Faces
- Save images of individuals whose attendance you want to track in the `ImagesAttendance/` folder.
- Name the files as the individual's name (e.g., `JohnDoe.jpg`).

### 2. Run the Attendance System

Execute the main script to start the webcam-based attendance system:

```bash
python attendance.py
```

The system will:
1. Detect faces in the live webcam feed.
2. Compare detected faces with the known encodings.
3. Log the name and timestamp of recognized individuals in `Attendance.csv`.

---

## Code Overview

### `basics.py`
This script demonstrates basic facial recognition functionality:
- Loading and encoding images.
- Comparing two images and calculating facial distances.
- Visualizing face matches with bounding boxes.

### `attendance.py`
The main script for the attendance system:
- Encodes all known faces from the `ImagesAttendance` directory.
- Captures frames from the webcam and identifies faces.
- Logs attendance for recognized individuals in `Attendance.csv`.

---

## Example CSV Output

The `Attendance.csv` file will have the following format:

```
Name,Time
John Doe,14:30:45
Jane Smith,14:35:12
```

---

## Customization

### Threshold for Unknown Faces
To adjust the threshold for recognizing unknown faces, modify the comparison condition in `attendance.py`:

```python
if faceDis[matchIndex] < 0.50:
    name = classNames[matchIndex].upper()
else:
    name = 'Unknown'
```

Increase or decrease `0.50` based on your accuracy needs.

---

## Notes

- This project uses the [face_recognition](https://github.com/ageitgey/face_recognition) library, which requires `dlib`. Ensure your system can compile C++ libraries if you're installing it on a fresh environment.
- For optimal performance, use high-quality images for known faces.
- Full credit to Adam Geitgy for writing [this article](https://medium.com/@ageitgey/machine-learning-is-fun-part-4-modern-face-recognition-with-deep-learning-c3cffc121d78) which put me onto this project idea!

---

## License

This project is open-source. You can reuse my code however you like, mine was pretty inspired by other programmers as well.

---

Feel free to reach out about this or any of my other projects!
