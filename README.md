# Mammary Carcinoma Diagnosis Identification Using CNN-RNN

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.7+](https://img.shields.io/badge/Python-3.7%2B-blue.svg)](https://www.python.org/downloads/)
[![Django 2.1](https://img.shields.io/badge/Django-2.1-green.svg)](https://www.djangoproject.com/)
[![TensorFlow 1.14](https://img.shields.io/badge/TensorFlow-1.14-orange.svg)](https://www.tensorflow.org/)

## Overview

This project implements a web-based application for **mammary carcinoma (breast cancer) diagnosis** from ultrasound images using a hybrid **CNN-RNN** model. The system classifies breast tumors into three categories: **Benign**, **Malignant**, and **Normal**.

Key highlights:
- Trained CNN-RNN model achieves high accuracy on ultrasound dataset.
- Django-powered web interface for image upload and real-time prediction.
- Pre-trained model and dataset included.
- Simple login system (admin/admin) to access prediction tool.

The model was developed following research on deep learning for medical image analysis, combining **Convolutional Neural Networks (CNN)** for feature extraction and **Recurrent Neural Networks (RNN with LSTM)** for sequential processing.

## Features

- **Image Upload & Prediction**: Upload mammogram/ultrasound images and get instant classification with confidence score.
- **Visual Results**: Predicted label overlaid on the input image.
- **User Authentication**: Basic login to access the prediction screen.
- **Responsive UI**: Clean, medical-themed interface with static CSS.
- **Model Metrics**: Training history, confusion matrix, ROC-AUC plots in Jupyter notebook.
- **Dataset**: 100+ labeled ultrasound images (benign, malignant, normal) with masks.

## Tech Stack

| Component | Technology | Version |
|-----------|------------|---------|
| Backend | Django | 2.1.7 |
| ML Framework | TensorFlow/Keras | 1.14.0 / 2.3.1 |
| Frontend | HTML/CSS | Custom templates |
| Database | SQLite | Default |
| Image Processing | OpenCV | 4.1.1 |
| Visualization | Matplotlib/Seaborn | 3.1.1 / 0.10.1 |
| Others | NumPy, Pandas, Scikit-learn | Various |

Full dependencies in `BreastCancer-CNN-RNN/requirements.txt`.

## Project Structure

```
mini project/
├── README.md
├── .gitignore
├── BreastCancer-CNN-RNN/          # Main Django project
│   ├── manage.py
│   ├── db.sqlite3
│   ├── requirements.txt
│   ├── run.bat                    # Run Jupyter notebook
│   ├── runServer.bat              # Start Django server
│   ├── MAMMARY CARCINOMA...ipynb  # Model training notebook
│   ├── Dataset/                   # Training images (benign/malignant/normal + masks)
│   ├── model/                     # Saved model weights & history
│   │   ├── cnn_weights.hdf5
│   │   ├── cnn_history.pckl
│   │   └── X.txt.npy, Y.txt.npy
│   ├── testImages/                # Sample test images
│   ├── Cancer/                    # Django project settings
│   ├── CancerApp/                 # Django app
│   │   ├── views.py               # Prediction logic
│   │   ├── urls.py
│   │   ├── templates/             # HTML pages
│   │   └── static/                # CSS, images
│   └── SCREENS.docx               # Screenshots/docs
└── Python Softwares/              # Miscellaneous installers (not part of core project)
```

## Quick Demo

1. **Home Page**: Landing page with project info.
2. **Login**: Use `admin` / `admin`.
3. **Upload**: Select image, get prediction like \"Malignant Score 0.95\" overlaid.

## Setup Instructions

### Prerequisites
- Python 3.7+ (tested with 3.7)
- Git

### Step 1: Clone & Navigate
```bash
git clone https://github.com/SHIVA-KUMAR-D/BreastCancerDetection-CNN-RNN.git
cd "BreastCancer-CNN-RNN"
```

### Step 2: Install Dependencies
```bash
pip install -r requirements.txt
```
*Note: Older TF 1.14 may require specific Python 3.7 env. Consider virtualenv.*

### Step 3: Run Server
```bash
python manage.py runserver
```
Or use `runServer.bat` (Windows).

Visit `http://127.0.0.1:8000/index.html`

### Optional: Re-train Model
```bash
# Run Jupyter
jupyter notebook MAMMARY CARCINOMA....ipynb
```
Or `run.bat`.

## Usage

1. Open `http://127.0.0.1:8000/`.
2. Click **User Login** → `admin` / `admin`.
3. Go to **Upload File** → Choose ultrasound image.
4. View prediction on processed image.

**Sample Predictions** (from notebook):
- Works on 32x32 resized grayscale/RGB ultrasound scans.

## Model Details

- **Architecture**: CNN (Conv2D + MaxPool) → Flatten → RepeatVector → LSTM → Dense(256) → Softmax(3 classes).
- **Training**: 15 epochs, Adam optimizer, categorical crossentropy.
- **Data**: ~500 images shuffled/split 80/20, normalized [0-1].
- **Performance**: High accuracy (check notebook for metrics/confusion matrix/ROC).
- **Prediction Flow**:
  1. Load `model/cnn_weights.hdf5`.
  2. Preprocess: Resize 32x32, /255.
  3. Predict → Argmax → Overlay text.

## Dataset

- **Source**: Ultrasound images of breast tissue.
- **Classes**: Benign (non-cancerous), Malignant (cancerous), Normal.
- **Size**: 100+ images per class + mask variants.
- Located in `Dataset/{benign,malignant,normal}/`.

**Note**: For production, use larger datasets like BreakHis or CBIS-DDSM.

## Screenshots & Documentation

- See `SCREENS.docx` for UI captures.
- Notebook includes training plots, test predictions.

## Limitations & Improvements

- Hardcoded login (add proper auth).
- TF 1.14 outdated → Migrate to TF 2.x / PyTorch.
- No user registration/models usage.
- Add API endpoint for integration.
- Deploy to Heroku/Vercel with gunicorn.
- Enhance UI with Bootstrap/JS.

## License

MIT License - feel free to use/modify.

## Acknowledgments

- Dataset: Public ultrasound breast images.
- Inspired by CNN-RNN hybrid for medical imaging.

---

*Built with ❤️ for early breast cancer detection.*

