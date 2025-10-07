# 🚀 NASA Space App - Render Deployment Guide

## Overview
This document provides comprehensive instructions for deploying the NASA Exoplanet Detection Dashboard to Render.com.

## Architecture
The application is deployed as two separate services:
- **Backend Service**: Python FastAPI for ML model inference
- **Frontend Service**: React.js dashboard for user interface

## Deployment Configuration

### Backend Service (`nasa-exoplanet-backend`)
- **Runtime**: Python 3.9.0
- **Build Command**: `pip install -r requirements.txt`
- **Start Command**: `python api_predict.py`
- **Health Check**: `/`

### Frontend Service (`nasa-exoplanet-frontend`)
- **Runtime**: Node.js 18.17.0
- **Build Command**: `npm install && npm run build`
- **Start Command**: `npm start`
- **Health Check**: `/`

## Environment Variables

### Backend Environment Variables
```yaml
PYTHON_VERSION=3.9.0
```

### Frontend Environment Variables
```yaml
NODE_VERSION=18.17.0
REACT_APP_API_URL=https://nasa-exoplanet-backend.onrender.com
```

## Dependencies

### Python Dependencies (requirements.txt)
```
numpy==1.24.3
pandas==2.0.3
scipy==1.11.1
scikit-learn==1.3.0
matplotlib==3.7.2
torch==2.0.1
torchvision==0.15.2
torchaudio==2.0.2
tqdm==4.65.0
fastapi==0.104.1
uvicorn[standard]==0.24.0
python-multipart==0.0.6
pytorch-lightning==2.0.6
tensorboard==2.14.0
shap==0.42.1
```

### Node.js Dependencies (package.json)
- React 18.2.0
- Material-UI (MUI) 5.14.0
- Axios 1.6.0
- Recharts 2.8.0
- React Router DOM 6.8.0

## Required Files for Deployment

### Backend Files
- `api_predict.py` - Main FastAPI application
- `models.py` - ML model definitions
- `nasa_model.pth` - Trained PyTorch model
- `requirements.txt` - Python dependencies
- `nasa_dataset.npz` - Training dataset

### Frontend Files
- `src/index.js` - React entry point
- `src/App.js` - Main React component
- `src/components/` - All React components
- `package.json` - Node.js dependencies
- `public/` - Static assets

## Deployment Steps

### 1. Deploy Backend First
1. Create a new Web Service in Render
2. Connect your GitHub repository
3. Configure service:
   - **Name**: `nasa-exoplanet-backend`
   - **Runtime**: `Python 3`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python api_predict.py`
   - **Environment Variables**: `PYTHON_VERSION=3.9.0`

### 2. Deploy Frontend Second
1. Create another Web Service in Render
2. Connect the same GitHub repository
3. Configure service:
   - **Name**: `nasa-exoplanet-frontend`
   - **Runtime**: `Node.js`
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`
   - **Environment Variables**:
     - `NODE_VERSION=18.17.0`
     - `REACT_APP_API_URL=https://nasa-exoplanet-backend.onrender.com`

### 3. Verify Deployment
1. Check backend service logs for:
   - Model loading success
   - Server starting on correct port
   - API endpoints responding

2. Check frontend service logs for:
   - npm install completion
   - Build process success
   - React app starting

## API Endpoints

### Backend API Endpoints
- `GET /` - Health check and React app fallback
- `POST /predict_csv` - CSV file upload and prediction
- `WebSocket /ws` - Real-time prediction endpoint
- `WebSocket /ws/stream` - Streaming data endpoint

### Frontend Routes
- `/` - Dashboard homepage
- `/upload` - CSV upload interface
- `/realtime` - Real-time analysis
- `/results` - Prediction results display
- `/about` - Project information
- `/documentation` - Technical documentation
- `/contact` - Contact information

## Troubleshooting

### Common Issues

#### Backend Issues
1. **Model Loading Failure**
   - Check that `nasa_model.pth` exists in the root directory
   - Verify model file size and integrity
   - Check logs for specific error messages

2. **Port Binding Issues**
   - Ensure `host='0.0.0.0'` in api_predict.py
   - Check PORT environment variable is set correctly

3. **Memory Issues**
   - Large model may require more memory
   - Monitor Render service metrics

#### Frontend Issues
1. **Build Failures**
   - Check Node.js version compatibility
   - Verify all dependencies are installed
   - Check for syntax errors in React components

2. **API Connection Issues**
   - Verify `REACT_APP_API_URL` points to correct backend service
   - Check CORS configuration in backend

### Log Monitoring
1. **Backend Logs**: Monitor for model loading and API errors
2. **Frontend Logs**: Monitor for build and runtime errors
3. **Search for "error"** in logs for quick issue identification

## Performance Optimization

### Backend Optimizations
- Model loading is cached after first load
- Efficient batch processing for CSV files
- WebSocket connections for real-time updates

### Frontend Optimizations
- React build optimization for production
- Component lazy loading
- Efficient state management

## File Structure
```
nasa-space-app/
├── api_predict.py          # Backend API
├── models.py              # ML models
├── nasa_model.pth         # Trained model
├── requirements.txt       # Python dependencies
├── src/                   # React frontend
│   ├── App.js
│   ├── index.js
│   └── components/
├── public/                # Static assets
├── package.json           # Node.js dependencies
└── render.yaml           # Deployment config
```

## Support

For deployment issues:
1. Check the troubleshooting section above
2. Review Render service logs
3. Verify all required files are present
4. Check environment variable configuration
5. Test API endpoints individually

## Version History
- **v1.0.0**: Initial deployment configuration
- **v1.1.0**: Updated with dual-service architecture
- **v1.2.0**: Added specific dependency versions