---

<h1 align="center">
  🌌✨ <br>
  <b>NASA Exoplanet Detection AI Platform</b>  
  <br>
  <sub>🚀 A Deep Learning Odyssey Beyond the Stars 🚀</sub>
</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Framework-FastAPI-0?style=for-the-badge&logo=fastapi&logoColor=white&color=0A9E8C">
  <img src="https://img.shields.io/badge/Frontend-React-0?style=for-the-badge&logo=react&logoColor=white&color=61DAFB">
  <img src="https://img.shields.io/badge/AI-PyTorch-red?style=for-the-badge&logo=pytorch&logoColor=white">
  <img src="https://img.shields.io/badge/Team-BugBusters-blueviolet?style=for-the-badge">
</p>

---

## 🌠 Overview
> 🧠 A next-gen **AI-powered deep learning platform** that detects **exoplanets** from NASA data — combining science, design, and intelligence.  
> Powered by **React**, **FastAPI**, and **PyTorch**, this system predicts celestial candidates **in real-time** using **WebSocket streaming**.  

<p align="center">
  <img src="https://github.com/teambugbusters00/nasa-exoplanet-ai/assets/space-banner.gif" width="800px" alt="space banner">
</p>

---

## 🪐 Features at Warp Speed

| 🌌 Category | 🚀 Description |
|-------------|----------------|
| **AI-Powered Analysis** | Hybrid CNN + Transformer model trained on NASA Exoplanet Archive |
| **Live Predictions** | Real-time WebSocket-based inference with instant visualization |
| **Universal CSV Parser** | Auto column mapping for multiple dataset formats |
| **Dynamic Visuals** | Stunning charts and animations via Recharts + Framer Motion |
| **Dark Space UI** | Responsive, futuristic, gradient-styled interface |

--/*
YouTubeLivePlayer.jsx
A reusable React component to embed and auto-play a YouTube live/video inside your React app.

Features:
- Uses react-player (recommended) with a plain iframe fallback
- Autoplay (muted) to satisfy browser autoplay policies
- Attempts to resume playback when the tab becomes visible again
- Reconnects / replays when the video ends (good for live streams that re-start)
- Tailwind-friendly classes for quick styling

Install:
npm install react-player

Usage:
import YouTubeLivePlayer from './YouTubeLivePlayer';

<YouTubeLivePlayer
  youtubeId="l13uVoMQdgo"            // or full url
  className="w-full h-96 rounded-2xl shadow-xl"
  muted={true}
  autoPlay={true}
  loop={true}
/>

Notes:
- Browsers block autoplay with sound. Keep muted:true if you want autoplay to work consistently.
- For a real "always-on" behavior you may want to ensure your server hosting the app is always running (e.g. deployed on Render/Netlify/Vercel) and optionally show a message if playback is blocked.
- Live streams sometimes return an "ended" event when they transition — the component tries to reload the player in that case.
*/

import React, { useRef, useEffect, useState } from 'react';
import ReactPlayer from 'react-player/youtube';

export default function YouTubeLivePlayer({
  youtubeId = 'l13uVoMQdgo',
  url = null,
  className = 'w-full h-80',
  autoPlay = true,
  muted = true,
  loop = true,
  controls = true,
}) {
  const playerRef = useRef(null);
  const [playing, setPlaying] = useState(autoPlay);
  const [key, setKey] = useState(0); // force remount when needed

  const videoUrl = url || `https://www.youtube.com/watch?v=${youtubeId}`;

  // Try to resume playback when tab becomes visible
  useEffect(() => {
    function handleVisibility() {
      if (document.visibilityState === 'visible') {
        // small timeout to allow browser to regain focus
        setTimeout(() => setPlaying(true), 200);
      }
    }
    document.addEventListener('visibilitychange', handleVisibility);
    return () => document.removeEventListener('visibilitychange', handleVisibility);
  }, []);

  // If the player stops (ended/error), try to reload the player
  function handleEnded() {
    if (loop) {
      // force remount the player to prompt a reconnect
      setKey(k => k + 1);
      setPlaying(true);
    } else {
      setPlaying(false);
    }
  }

  function handleError(e) {
    // on network errors or player errors, attempt a retry after a short delay
    console.warn('YouTube player error:', e);
    setTimeout(() => {
      setKey(k => k + 1);
      setPlaying(true);
    }, 2000);
  }

  return (
    <div className={`relative overflow-hidden bg-black ${className}`}>
      <div className="absolute inset-0 flex items-center justify-center">
        <ReactPlayer
          key={key}
          ref={playerRef}
          url={videoUrl}
          playing={playing}
          loop={loop}
          muted={muted}
          controls={controls}
          width="100%"
          height="100%"
          onEnded={handleEnded}
          onError={handleError}
          config={{
            youtube: {
              playerVars: {
                autoplay: autoPlay ? 1 : 0,
                controls: controls ? 1 : 0,
                rel: 0,
                modestbranding: 1,
                playsinline: 1,
                disablekb: 0,
              },
            },
          }}
        />
      </div>

      {/* Small overlay controls / hints */}
      <div className="absolute left-3 top-3 bg-black/40 text-white text-xs px-2 py-1 rounded-md backdrop-blur">
        {muted ? 'Autoplay (muted)' : 'Autoplay'}
      </div>
    </div>
  );
}-

## 🎨 Interface Highlights

🌙 **Dark Galactic Theme** — Neon cyan + deep indigo  
⚙️ **Framer Motion Animations** — Smooth transitions like orbital motion  
🪄 **Drag & Drop Uploads** — Interactive CSV upload zone  
📊 **Data Galaxy Dashboard** — Visualize predictions in orbit-like charts  

<p align="center">
  <img src="https://github.com/teambugbusters00/nasa-exoplanet-ai/assets/dashboard-preview.gif" width="700px" alt="dashboard animation">
</p>

---

## 🧩 Tech Stack

| 🌌 Layer | 🧠 Technology |
|----------|---------------|
| **Frontend** | React 18, Material-UI, Framer Motion, React Router, Recharts |
| **Backend** | FastAPI, WebSockets, PyTorch, Pandas, NumPy, Scikit-learn |
| **AI Models** | CNN + Transformer Hybrid & MLP (catalog-based) |
| **Deployment** | Render Cloud / GitHub Actions |

---

## 🧠 Model Architecture

🌍 Input Light Curve → 🧮 Preprocessing → 🧠 CNN Feature Extraction → 🔄 Transformer Attention → 🎯 Exoplanet Prediction (Probability)

---

## ⚙️ Quick Start Guide

```bash
# 🛰️ Clone Repository
git clone https://github.com/teambugbusters00/nasa-exoplanet-ai.git
cd nasa-exoplanet-ai

# 🧩 Install Backend Dependencies
pip install -r requirements.txt

# 🪐 Install Frontend Dependencies
npm install

🚀 Run Locally

# Backend
python api_predict.py
# Frontend
npm start

> 🌍 Visit http://localhost:3000 and begin your interstellar exploration.




---

☁️ Deploy to Render

🌐 One-Click Setup

1. Push your code to GitHub


2. Login to Render.com


3. Connect the repo → Add a Web Service



Build Command

pip install -r requirements.txt && npm install && npm run build

Start Command

python api_predict.py

Add these Environment Variables:

PORT=8000
NODE_ENV=production


---

🗂️ Project Structure

nasa-space-app/
├── public/
│   ├── index.html
│   ├── sample_exoplanet_data.csv
│   └── mixed_exoplanet_results.csv
├── src/
│   ├── App.js
│   ├── index.js
│   └── components/
│       ├── Header.js
│       ├── Homepage.js
│       ├── Dashboard.js
│       └── Contact.js
├── api_predict.py
├── models.py
├── preprocess.py
├── dataset.py
├── train.py
├── requirements.txt
├── package.json
└── README.md


---

🔧 API Endpoints

🔹 POST /predict_csv

Upload a CSV for batch analysis:

curl -X POST -F "file=@candidates.csv" http://localhost:8000/predict_csv

🔹 WebSocket /ws

const ws = new WebSocket("ws://localhost:8000/ws");
ws.send(JSON.stringify({ candidate }));


---

📊 Example CSV

kepid,koi_period,koi_time0bk,koi_depth,koi_duration,koi_prad,koi_teq,koi_insol,koi_slogg,koi_srad,koi_steff,koi_smass,koi_sage
K00001,3.23,2458321.56,150.5,2.45,1.2,1200.5,1.8,4.2,1.1,5800.5,1.05,4.5
K00002,5.67,2458325.89,89.3,3.12,0.8,950.2,0.9,4.5,0.9,5200.8,0.85,2.1


---

👥 Stellar Crew

👨‍🚀 Name	🧭 Role	🔗 Profile

Hema Harshini Pydimarri	Technical Lead & Research	LinkedIn
Sukeerthi Langu	AI Research Scientist	LinkedIn
Vijay Jangid	AI/ML Developer	LinkedIn



---

📈 Model Performance

Metric	Result

🧮 Accuracy	99.2%
⚡ Inference Time	< 1 sec
🌐 WebSocket Ready	✅
🧰 Multi-format CSVs	✅



---

🔬 Research Applications

🪐 Automated Exoplanet Vetting

☀️ False Positive Detection

🌟 Planet Priority Scoring

🌌 Multi-Mission Compatibility (Kepler, TESS, etc.)



---

🌍 Future Upgrades

[ ] Planet Type Multi-class Classification

[ ] Uncertainty Quantification

[ ] NASA Database Integration

[ ] 3D Orbit Visualizer

[ ] Android Companion App



---

🤝 Contributing

# Fork it 🚀
git checkout -b feature/amazing-feature
# Commit it 🌟
git commit -m "Add amazing feature"
# Push it 🪄
git push origin feature/amazing-feature

Then open a Pull Request 💫


---

📜 License

Licensed under MIT License
See LICENSE for details.


---

🛰️ Acknowledgments

🌌 NASA Exoplanet Archive for the data

🔥 PyTorch team for the AI framework

🧩 Material-UI for the design system

💻 React Community for the ecosystem

