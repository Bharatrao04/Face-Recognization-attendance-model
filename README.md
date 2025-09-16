Face Recognition Attendance System (Windows)

Overview
This project uses your webcam and the face_recognition library to recognize known faces and log attendance to `Attendance.csv`.

Features
- Detects and recognizes faces in real time from the webcam
- Logs Name, Time, and Date to `Attendance.csv`
- Uses filenames as labels for recognized people

Requirements
- Windows 10/11
- Python 3.11.x installed and on PATH
- Webcam access allowed for Python

Quick Start (Windows PowerShell)
1) Create and activate a virtual environment
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -V
```

2) Install dependencies
```powershell
python -m pip install --upgrade pip
pip install --only-binary=:all: dlib-bin==19.24.6
pip install face-recognition==1.3.0 opencv-python==4.12.0.88 numpy==2.2.6
```

If activation is blocked:
```powershell
Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
.\.venv\Scripts\Activate.ps1
```

If dlib install fails, try an alternate prebuilt wheel:
```powershell
pip install --only-binary=:all: dlib-bin==19.24.2
# or
pip install --only-binary=:all: dlib-bin==19.24.2.post1
```

3) Add known faces
- Put one or more face images into the `Images_Attendance` folder.
- Allowed extensions: .jpg .jpeg .png .bmp .webp
- The filename (without extension) is the label, e.g., `Alice.jpg` -> label `ALICE`.

4) Run
```powershell
python AttendanceProject.py
```
- A webcam window opens; recognized faces show a green box and label.
- Press Enter to exit. New records are appended to `Attendance.csv`.

Project Files
- `AttendanceProject.py`: Main app. Reads images, encodes faces, opens webcam, logs attendance.
- `main.py`: Simple two-image comparison demo (optional).
- `Images_Attendance/`: Place labeled face images here.
- `Attendance.csv`: Attendance log output.

Troubleshooting
- No module named cv2: Ensure the venv is activated and `opencv-python` is installed in it.
- dlib build error: Use `dlib-bin` as shown above; do not compile from source on Windows.
- Webcam doesn’t open: Close other apps using the camera and allow Camera access to Python in Windows Settings.
- No known faces found: Add at least one valid image into `Images_Attendance` with a face clearly visible.
- Recognition unreliable: Use clear, front-facing photos with good lighting; avoid very small or blurry images.

Notes
- Filenames map to labels. To change a displayed name, rename the corresponding image file.
- The script skips non-image files and unreadable images in `Images_Attendance`.
