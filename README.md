# AI Kidney Stone Detection Portal 🩺🔍

An intelligent computer vision system powered by **Ultralytics YOLOv8** designed to automate the detection and segmentation of kidney stones in medical imaging (including standard image formats and DICOM scans).

This project features a clean, high-performance training pipeline via Jupyter Notebook and a premium, responsive dark-themed **Flask web application** for real-time inference and side-by-side medical visualization.

---

## 🌟 Features

- **YOLOv8 Core**: Employs deep learning models trained specifically for robust kidney stone detection.
- **Medical Format Compatibility**: Supports standard formats (`.png`, `.jpg`, `.jpeg`) as well as professional medical imaging DICOM (`.dcm`) scans.
- **Side-by-Side Diagnostic Preview**: Renders an original scan alongside the AI-annotated scan with detection overlays for clarity.
- **Fully Isolated Environment**: Designed with robust security standards (e.g., pre-configured `.gitignore` to prevent secret/credential leaks and avoid massive directory bloat).

---

## 📁 Repository Structure

```text
├── .gitignore                      # Configured to ignore .venv, kaggle.json, zip datasets
├── Yolo.ipynb                      # Training, dataset download, and validation pipeline
├── confusion_matrix_normalized.png  # Model diagnostic performance chart
├── manage.py                       # Helper script
├── requirements.txt                # Core deep learning framework dependencies
├── yolov8n.pt                      # YOLOv8 pre-trained network weights
└── Kidney/                         # Main Web Application Directory
    ├── app.py                      # Flask web server (routing & upload handler)
    ├── yolo_infer.py               # Inference wrapper using PyTorch & OpenCV
    ├── requirements.txt            # Web portal specific dependencies
    ├── yolov8n.pt                  # Dedicated inference model weights
    └── templates/                  # Responsive web views (Flask templates)
        ├── index.html              # Diagnostic upload portal dashboard
        └── result.html             # Comparative diagnostic analysis results
```

---

## 🛠️ Setup & Installation

Follow these steps to configure your local development environment:

### 1. Clone the Project
```bash
git clone https://github.com/Venkatkarthik07/Kidney-Stone-Detection.git
cd Kidney-Stone-Detection
```

### 2. Create & Activate a Virtual Environment
We recommend using an isolated Python environment (Python 3.8+ recommended):
```bash
# Windows
python -m venv .venv
.venv\Scripts\activate

# macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies
Install the required packages in your activated environment:
```bash
pip install -r requirements.txt
pip install -r Kidney/requirements.txt
```

*(Alternatively, run this unified installation command):*
```bash
pip install ultralytics Flask Werkzeug pillow pydicom opencv-python pyyaml
```

---

## 🚀 Execution & Usage

### Running the Web Portal
Launch the Flask web server:
```bash
python Kidney/app.py
```

Once running, open your web browser and navigate to:
👉 **[http://127.0.0.1:5000](http://127.0.0.1:5000)**

### Using the App
1. **Upload Scan**: Drag and drop or click to choose any CT/MRI scan (`.png`, `.jpg`, `.jpeg` or medical `.dcm`).
2. **Real-time Inference**: Click submit (or drop) to run the image through the YOLOv8 neural network.
3. **Analyze Results**: View the side-by-side comparison of the original scan vs. the AI-annotated detection bounding boxes.

---

## 📊 Model Training & Evaluation

The full training pipeline is documented inside the `Yolo.ipynb` Jupyter Notebook.
- **Dataset Source**: Automatically downloads medical datasets from Kaggle using Kaggle API credentials.
- **Performance Evaluation**: You can view the `confusion_matrix_normalized.png` inside the root folder to inspect the classification metrics and validation scores of the YOLOv8 model.

---

## 🔒 Security & Best Practices

To protect private credentials and maintain a clean repository structure, this project adheres to standard devops principles:
- **Ignored Files**: The `.venv/` virtual environment, custom dataset zips (`kidney-stone-images.zip`), and private credentials (`kaggle.json`) are excluded from tracking inside `.gitignore`.
- Keep your `kaggle.json` inside the root folder locally, but rest assured it will **never** be pushed to GitHub.
