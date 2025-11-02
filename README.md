# 🎮 Hand Gesture Keyboard Controller (MediaPipe)

A hands-free controller that translates specific hand gestures into **Left** ($\leftarrow$) and **Right** ($\rightarrow$) keyboard key presses using a webcam. This is ideal for controlling applications like simple racing games, character movement, or advancing slideshow presentations.



---

## 🖐️ Usage and Controls (How to Use It)

The application window titled "Frame" will open, displaying your webcam feed. Keep your hand visible for control.

| Action | Required Hand Gesture | Code Logic | Resulting Key Press |
| :--- | :--- | :--- | :--- |
| **Move Left** | **All Fingers Closed (Closed Fist)** | `count_fingers_open == 0` | `keyboard.press(Key.left)` |
| **Move Right** | **All Fingers Open (Open Palm)** | `count_fingers_open == 5` | `keyboard.press(Key.right)` |
| **Neutral / Stop** | **Hand is not detected** | `results.multi_hand_landmarks == None` | `keyboard.release(Key.right)` and `keyboard.release(Key.left)` |

> **Note:** Press the **'q' key** on your physical keyboard to safely exit the application and release all virtual key presses.

---

## 💡 Technologies Used

This project relies on the synergy of powerful, open-source libraries:

* **Python:** The core programming language.
* **MediaPipe:** Provides the **high-performance Hand Solutions** for accurate, real-time landmark tracking.
* **OpenCV (`cv2`):** Used for managing the **webcam feed** (capturing video) and displaying the output window.
* **pynput:** The essential library used to **interface with the operating system** to simulate virtual keyboard key presses and releases.

---

## 🔎 Detailed Overview: Start-to-End Guide

### 1. What It Does
This program uses the MediaPipe Hands framework to detect and track a single hand in real-time. It monitors the state of your five fingers (open or closed) and uses that information to simulate keyboard presses using the `pynput` library.

### 2. Code Implementation Details
The logic determines finger state by comparing the tip landmark position to the joint landmarks. The total count of open fingers dictates which keyboard command is issued. The use of `pynput.keyboard.Controller` allows for continuous pressing of keys while the gesture is held.

---

## 🛠️ Installation and Setup

### Prerequisites
* Python 3.x installed.
* A working webcam (internal or external).

### Installation

1.  **Create `requirements.txt`** (if necessary):
    ```
    opencv-python
    mediapipe
    pynput
    ```
2.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

### How to Run It (.py)

Make sure your webcam is available and not in use by other applications.

Run the main script from your terminal:

```bash
python virtual_keyboard.py
