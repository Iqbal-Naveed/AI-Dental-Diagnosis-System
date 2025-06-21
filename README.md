# AI Dental Diagnosis System 🦷

An AI-powered system for diagnosing dental conditions from images. Built using deep learning models (e.g., CNNs) to detect dental issues like cavities, gum disease, or root problems.

## 🚀 Features

* **Image-based Diagnosis** – Upload X-ray or intraoral images for automated dental issue detection
* **Heatmap Visualization** – Highlighting the specific areas of concern
* **Batch & Real-time Processing** – Analyze single or multiple cases at once
* **Model Flexibility** – Easily switch between or retrain diagnosis models
* **REST API** – Integrate diagnostics into other systems or frontends

---

## 📁 Project Structure

```
AI-Dental-Diagnosis-System/
├── models/                 # Pre-trained or checkpointed models
├── data/                   # Sample images for testing or training
├── src/                    # Core source code
│   ├── app.py             # Main app or API server
│   ├── utils.py           # Helpers (preprocessing, postprocessing)
│   ├── models.py          # Model architecture definitions
│   └── inference.py       # Image loading + diagnosis pipeline
├── requirements.txt        # Python dependencies
├── Dockerfile              # (Optional) For containerized deployment
├── README.md               # (This file)
└── LICENSE                 # Project license
```

---

## ⚙️ Installation

1. **Clone the repo**

   ```bash
   git clone https://github.com/Iqbal-Naveed/AI-Dental-Diagnosis-System.git
   cd AI-Dental-Diagnosis-System
   ```

2. **Create & activate virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

4. **Download model checkpoints**
   Place pre-trained weights into `models/`, e.g.:

   ```
   models/
   └── dental_model.pth
   ```

---

## 🚀 Usage

### Run locally

```bash
python src/app.py --model models/dental_model.pth --image data/test_xray.jpg
```

It outputs:

* **Diagnosis result** (e.g., “Cavity detected in upper molar”)
* **Heatmap overlay image** saved in `outputs/`

### Using the API

Start the server:

```bash
python src/app.py --host 0.0.0.0 --port 5000
```

Send POST requests to `/predict`:

```bash
curl -X POST "http://localhost:5000/predict" \
     -F "image=@data/test_xray.jpg" \
     -F "model=models/dental_model.pth"
```

Response:

```json
{
  "diagnosis": "Gum recession detected",
  "confidence": 0.93,
  "heatmap_url": "/outputs/heatmap_001.png"
}
```

---

## 🛠️ Model Training (Optional)

If you want to train a new model:

1. Prepare a training dataset under `data/train/` with labeled images.
2. Modify hyperparameters in `src/train.py`.
3. Run training:

   ```bash
   python src/train.py \
       --data_dir data/train \
       --epochs 30 \
       --batch_size 16 \
       --save_path models/new_model.pth
   ```

---

## 🧪 Testing

Use pytest or unittest:

```bash
pytest tests/
```

Includes checks for:

* Image preprocessing
* Model inference logic
* API endpoints

---

## 📦 Docker Deployment (Optional)

Build and run:

```bash
docker build -t ai-dental-diagnosis .
docker run -p 5000:5000 ai-dental-diagnosis
```

---

## 📘 Configuration

Available flags:

| Flag                | Description                         |
| ------------------- | ----------------------------------- |
| `--model`           | Path to model checkpoint            |
| `--image` / `--dir` | Single image or directory of images |
| `--host`, `--port`  | For API server binding              |
| `--gpu`             | Enable GPU (if CUDA is available)   |

Override defaults as needed.

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make changes & tests
4. Commit: `git commit -m "Add diagnoses for X"`
5. Push & open a PR

Please respect the [Code of Conduct](CODE_OF_CONDUCT.md).

---

## ⚖️ License

This project is licensed under the [MIT License](LICENSE).

---

## 👥 Acknowledgements

* Dental imaging community for annotated datasets
* Research on CNN-based medical imaging
* Inspiration from [@Iqbal‑Naveed](https://github.com/Iqbal-Naveed)

---

## 🚧 Roadmap

* Integrate additional pathology models
* Build a web UI with image upload/feedback
* Extend dataset diversity (e.g. pediatric cases)

---

### ✅ That's it!

