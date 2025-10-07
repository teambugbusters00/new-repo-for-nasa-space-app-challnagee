# NASA Space App - Exoplanet Detection Dashboard

A fullstack web application for exoplanet detection using machine learning and NASA's exoplanet dataset.

## Features

- **Real-time Exoplanet Detection**: Upload CSV files for batch prediction or use real-time analysis
- **Interactive Dashboard**: Modern React-based UI with data visualization
- **Machine Learning Model**: PyTorch-based neural network for exoplanet classification
- **WebSocket Support**: Real-time communication for live data streaming
- **Responsive Design**: Mobile-friendly interface with Material-UI components

## Project Structure

```
nasa-space-app-repo/
├── backend/                 # Python FastAPI backend
│   ├── api_predict.py      # Main API server with ML model
│   ├── models.py           # PyTorch model definitions
│   ├── dataset.py          # Data loading and preprocessing
│   ├── preprocess.py       # Data preprocessing utilities
│   └── train.py           # Model training script
├── frontend/               # React frontend application
│   ├── src/               # React source code
│   │   ├── components/    # React components
│   │   ├── App.js        # Main App component
│   │   └── index.js      # Entry point
│   ├── public/           # Static assets
│   └── package.json      # Node.js dependencies
├── data/                 # Sample datasets
│   ├── sample_exoplanet_data.csv
│   ├── mixed_exoplanet_results.csv
│   └── test_candidates.csv
├── render.yaml          # Render deployment configuration
├── requirements.txt     # Python dependencies
└── README.md           # This file
```

## Deployment on Render

This application is configured for deployment on [Render](https://render.com) with the following setup:

1. **Service Type**: Web Service
2. **Runtime**: Python 3.11.0
3. **Build Command**:
   ```bash
   python --version &&
   pip install -r requirements.txt &&
   cd frontend &&
   npm install &&
   npm run build &&
   cd ..
   ```
4. **Start Command**: `python backend/api_predict.py`

## Local Development

### Backend Setup
```bash
cd backend
pip install -r ../requirements.txt
python api_predict.py
```

### Frontend Setup
```bash
cd frontend
npm install
npm start
```

## API Endpoints

- `POST /predict_csv` - Upload CSV file for batch prediction
- `WebSocket /ws` - Real-time prediction endpoint
- `WebSocket /ws/stream` - Streaming data endpoint
- `GET /` - Serve React application

## Machine Learning Model

The application uses a PyTorch-based neural network that analyzes exoplanet candidate data to predict the probability of a candidate being a confirmed exoplanet. The model processes 13 features including:

- Orbital period
- Transit time
- Impact parameter
- Planet radius
- Stellar properties

## Data Format

The model expects CSV files with the following columns (or variations that can be intelligently mapped):

- `koi_period` - Orbital period in days
- `koi_time0bk` - Transit reference time
- `koi_depth` - Transit depth (ppm)
- `koi_duration` - Transit duration (hours)
- `koi_prad` - Planet radius (Earth radii)
- `koi_teq` - Equilibrium temperature (K)
- `koi_insol` - Insolation flux
- `koi_slogg` - Stellar surface gravity
- `koi_srad` - Stellar radius (Solar radii)
- `koi_steff` - Stellar effective temperature (K)
- `koi_smass` - Stellar mass (Solar masses)
- `koi_sage` - Stellar age (Gyr)

## Technologies Used

- **Backend**: Python, FastAPI, PyTorch, scikit-learn, pandas
- **Frontend**: React, Material-UI, Recharts, Axios
- **Deployment**: Render
- **Machine Learning**: PyTorch, Lightning Bolts
- **Real-time**: WebSockets, Socket.io

## License

This project was developed for the NASA Space Apps Challenge.
