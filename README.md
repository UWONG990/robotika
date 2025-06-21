# REPOSITORI ROBOTIKA
Nama: Dwijo Utomo Rahino Putro  
Npm: 22081010220  
Link Demo: https://youtu.be/uZ5q_Poyh3o  

# 🤖 AMBATRON - Automated Monitoring Bot for Anomalies

**AMBATRON** (Automated Monitoring Bot for Anomalies) is a surveillance robot built with an ESP32 microcontroller and computer vision system. The robot moves forward by default and automatically stops when it detects visual anomalies using a trained detection model (such as YOLO). This project explores the integration of robotics and machine learning to simulate anomaly detection in real-world environments.

---

## 📸 Core Features

- 🧠 Detects anomalies using image recognition (e.g., brainrot, unusual objects)
- 🤖 ESP32-controlled movement: forward, left, right, reverse, and stop
- 📷 Real-time detection using laptop webcam
- 🔌 Serial communication between Python (host) and ESP32 (robot)
- 🧪 Manual and automatic modes for testing and control

---

## 📁 Project Structure

```
robotika/
├── esp32-code/             # Arduino code for ESP32 control
│   └── ambatron.ino
├── python/                 # Python code for detection and communication
│   └── ambatron_control.py
├── model/                  # Folder for trained YOLO or classifier model
│   └── best.pt (optional)
├── dataset/                # Optional: training data for detection model
│   ├── images/
│   └── labels/
├── README.md
└── requirements.txt
```

---

## 🚀 How It Works

1. **Default Behavior:** The robot moves forward continuously.
2. **Camera Input:** A webcam captures live frames.
3. **Detection Model:** Python processes frames using a trained model (YOLO/classifier).
4. **Anomaly Detected:** Python sends a stop signal (`b'0'`) to ESP32 over serial.
5. **Safe Again:** Python sends a go signal (`b'1'`) to resume movement.

---

## ⚙️ How to Run

### 1. Upload ESP32 Code

Open `esp32-code/ambatron.ino` in Arduino IDE, select your ESP32 board and upload.

### 2. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 3. Run the Python Program

```bash
cd python/
python ambatron_control.py
```

Choose between:
- **Manual Mode:** Control robot with keyboard
- **Automatic Mode:** Camera detects anomalies automatically

---

## 🧠 Model Training (Optional)

To train your own anomaly detector:

1. Label images using [LabelImg](https://github.com/tzutalin/labelImg) or [Roboflow](https://roboflow.com)
2. Save labels in YOLO format
3. Create `data.yaml` for YOLOv5
4. Train with:

```bash
python train.py --img 640 --batch 16 --epochs 50 --data data.yaml --weights yolov5s.pt --name ambatron
```

---

## 📌 Example Labels for Detection

| Class ID | Label Name     | Description                         |
|----------|----------------|-------------------------------------|
| 0        | normal          | Normal images / safe environment    |
| 1        | brainrot        | Visually chaotic/meme objects       |
| 2        | ronda           | Human patrol or watch-like figure   |
| 3        | flaming_plane   | Surreal or threatening object       |

---

## 📷 Sample Use Cases

- Detecting memes or visual anomalies
- Prototyping AI-powered patrol robots
- Integrating YOLO with robotics platforms

---

## 👤 Author

**Dwijo Utomo Rahino Putro**  
GitHub: [@UWONG990](https://github.com/UWONG990)

---

## 📄 License

This project is licensed under the MIT License.
