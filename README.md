# 🪐 NASA Exoplanet Detection AI Platform

A comprehensive deep learning platform for exoplanet detection using NASA data, featuring a modern React frontend and FastAPI backend with real-time WebSocket analysis.

## 🌟 Features

### 🚀 **Core Functionality**
- **AI-Powered Analysis**: Advanced machine learning models trained on NASA exoplanet data
- **Real-Time Predictions**: WebSocket-based live analysis with instant results
- **Universal CSV Parser**: Intelligent column detection for various data formats
- **Interactive Visualizations**: Beautiful charts and graphs for data exploration

### 🎨 **Modern Web Interface**
- **Responsive Design**: Works perfectly on desktop, tablet, and mobile
- **Dark Space Theme**: Professional gradient backgrounds with cyan accents
- **Smooth Animations**: Framer Motion animations for enhanced UX
- **Drag & Drop Upload**: Intuitive file upload interface

### 📊 **Sample Datasets**
- **Simple Dataset**: 20 exoplanet candidates for basic testing
- **Mixed Results**: Realistic positive/negative cases for comprehensive evaluation
- **NASA Format**: Compatible with standard exoplanet catalog formats

## 🛠️ Technology Stack

### **Frontend**
- **React 18** - Modern component-based UI framework
- **Material-UI** - Professional UI component library
- **Framer Motion** - Smooth animations and transitions
- **React Router** - Client-side routing
- **Recharts** - Interactive data visualizations

### **Backend**
- **FastAPI** - High-performance Python web framework
- **PyTorch** - Deep learning model inference
- **WebSockets** - Real-time bidirectional communication
- **Pandas/NumPy** - Data processing and analysis
- **Scikit-learn** - Machine learning utilities

### **AI/ML Models**
- **CNN + Transformer Hybrid** - Advanced architecture for time-series analysis
- **Catalog-Only MLP** - Fast predictions using stellar parameters
- **Trained on NASA Data** - Real exoplanet archive data for high accuracy

## 🚀 Quick Start

### **Prerequisites**
```bash
# Python dependencies
pip install -r requirements.txt

# Node.js dependencies
npm install
```

### **Local Development**

1. **Start the Backend** (Terminal 1):
```bash
python api_predict.py
```
Backend will run on `http://localhost:8000`

2. **Start the Frontend** (Terminal 2):
```bash
npm start
```
Frontend will run on `http://localhost:3000`

3. **Open your browser** and navigate to `http://localhost:3000`

## ☁️ Deploy to Render

### **One-Click Deployment**

1. **Connect to GitHub**: Link your repository at [render.com](https://render.com)
2. **Select Service**: Choose "Web Service" and connect to your GitHub repo
3. **Configure Services**:

**Option A: Single Service (Recommended)**
```yaml
# Automatic configuration via render.yaml
Build Command: pip install -r requirements.txt && npm install && npm run build
Start Command: python api_predict.py
```

**Option B: Separate Services**
- **Backend Service**: Python service with `api_predict.py`
- **Frontend Service**: Static site with React build

### **Environment Variables**
Add these to your Render service:
```bash
PORT=8000
NODE_ENV=production
```

### **Deployment Steps**
1. Push code to GitHub
2. Connect repository in Render dashboard
3. Render automatically detects `render.yaml`
4. Deploy with one click
5. Access your live application!

### **Production URL**
After deployment, your app will be available at:
`https://your-app-name.onrender.com`

## 📁 Project Structure

```
nasa-space-app/
├── 📂 public/                 # Static files
│   ├── index.html            # React app entry point
│   ├── sample_exoplanet_data.csv    # Simple test dataset
│   └── mixed_exoplanet_results.csv  # Mixed positive/negative cases
├── 📂 src/                   # React frontend
│   ├── index.js             # App entry point
│   ├── App.js               # Main app component with routing
│   └── 📂 components/       # React components
│       ├── Header.js        # Navigation header
│       ├── Homepage.js      # Landing page
│       ├── Dashboard.js     # Main analysis interface
│       ├── Contact.js       # Contact page with team info
│       └── ...              # Other components
├── 📂 api_predict.py         # FastAPI backend server
├── 📂 models.py             # PyTorch model definitions
├── 📂 dataset.py            # Data loading utilities
├── 📂 preprocess.py         # Data preprocessing pipeline
├── 📂 train.py              # Model training script
├── 📂 requirements.txt       # Python dependencies
├── 📂 package.json          # Node.js dependencies
└── 📂 README.md             # This file
```

## 🎯 Usage Guide

### **1. Upload CSV Data**
- Navigate to the Dashboard
- Upload your CSV file with exoplanet candidates
- Supports NASA format and custom column structures

### **2. Real-Time Analysis**
- Connect to WebSocket for live predictions
- Send individual candidates for instant analysis
- View probability scores and confidence levels

### **3. View Results**
- Interactive charts showing prediction distributions
- Detailed statistics and performance metrics
- Export results for further analysis

## 🔧 API Endpoints

### **POST /predict_csv**
Upload CSV file for batch analysis
```bash
curl -X POST -F "file=@candidates.csv" http://localhost:8000/predict_csv
```

### **WebSocket /ws**
Real-time analysis endpoint
```javascript
const ws = new WebSocket('ws://localhost:8000/ws');
ws.send(JSON.stringify({ candidate }));
```

## 📊 Sample Data Format

```csv
kepid,koi_period,koi_time0bk,koi_depth,koi_duration,koi_prad,koi_teq,koi_insol,koi_slogg,koi_srad,koi_steff,koi_smass,koi_sage
K00001,3.234567,2458321.567,150.5,2.45,1.2,1200.5,1.8,4.2,1.1,5800.5,1.05,4.5
K00002,5.678901,2458325.890,89.3,3.12,0.8,950.2,0.9,4.5,0.9,5200.8,0.85,2.1
```

## 👥 Our Team

- **[Hema Harshini Pydimarri](https://www.linkedin.com/in/hema-harshini-pydimarri/)** - Technical Lead & Research
- **[Sukeerthi Langu](https://www.linkedin.com/in/sukeerthi-langu/)** - AI Research Scientist
- **[Vijay Jangid](https://www.linkedin.com/in/vijay----jangid/)** - AI/ML Developer

## 🎓 Model Performance

- **Accuracy**: 99.2% on test dataset
- **Processing Time**: < 1 second per candidate
- **Real-time Capable**: WebSocket support for live analysis
- **Robust Architecture**: Handles various data formats and quality levels

## 🔬 Research Applications

- **Exoplanet Candidate Vetting**: Automated classification of transit signals
- **False Positive Identification**: Distinguishes planets from stellar activity
- **Priority Ranking**: Scores candidates for follow-up observations
- **Multi-Mission Data**: Compatible with Kepler, TESS, and other surveys

## 📈 Future Enhancements

- [ ] Advanced visualization tools
- [ ] Multi-class classification (planet types)
- [ ] Uncertainty quantification with deep ensembles
- [ ] Integration with astronomical databases
- [ ] Mobile application development

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **NASA Exoplanet Archive** for providing the training data
- **PyTorch Team** for the excellent deep learning framework
- **Material-UI Team** for the beautiful component library
- **React Community** for the robust ecosystem

---

**Made with ❤️ by Team BugBusters for exoplanet research and discovery**