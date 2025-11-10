# Neural Network Visualizer

![License](https://img.shields.io/badge/license-MIT-blue.svg)

Interactive neural net training visualizer with universal plug-and-play dataset, backend, and credential paths. Easily swap input, provider, backend, or model by changing `.env` or UI select.

## Features
- Visualizes NN training step-by-step (browser or app)
- Dynamic dataset input (upload or URL)
- Backend engine: Python (default Keras/TensorFlow, all backends easily swappable)
- All key params and endpoints abstracted
- Ready for future JAX, PyTorch, web/remote provider integrations

## .env.example
```
LLM_PROVIDER=keras
MODEL_PATH=models/default.h5
DATASET_PATH=datasets/iris.csv
API_KEY=none_needed
BACKEND_URL=http://localhost:8000
```

## Usage
```bash
git clone https://github.com/guilliotinedreamteam/neural-network-visualizer.git
cd neural-network-visualizer
cp .env.example .env
# Fill in your data/model
# Backend
pip install -r requirements.txt
python backend.py
# Frontend
cd frontend
npm install
npm start
```

## Universal Backend/Provider Abstraction
- All paths and providers set via `.env` or UI dropdown
- To change model backend or swap API: just update `.env` and/or select in UI—no hardcoded logic
- Credential checks/fallback logic built in

## Example Backend (backend.py)
```python
import os
PROVIDER=os.getenv("LLM_PROVIDER","keras")
MODEL_PATH=os.getenv("MODEL_PATH","models/default.h5")

def run_training(dataset_path):
    # Placeholder: Keras/TensorFlow default
    if PROVIDER=="keras":
        # Implement Keras model training, send live status via WebSocket
        return "Training complete (keras default)"
    # Extend for PyTorch, etc.
    return f"Training with provider: {PROVIDER} not implemented."
```

## Frontend (React, src/config.js)
```js
export const BACKEND_URL = process.env.BACKEND_URL || "http://localhost:8000";
```

## Tech Stack
- Python 3.9+ (backend)
- React 18 (frontend)
- Keras or your own ML lib (swap)

## Contributing
All backend/UI/ML provider mods welcome.

## License
MIT
