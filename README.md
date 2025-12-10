# FloatChat 🌊
AI-Powered Chat Interface for Argo Oceanographic Data Analysis

FloatChat is a full-stack application that combines AI-driven natural language queries with real oceanographic data from Argo floats. Designed for hackathons, demos, and educational use, it provides an intuitive chat interface to explore, visualize, and analyze global ocean data.

---

## ✨ Features

### 🔧 Backend (Python + FastAPI)
- Argo Data Integration — Downloads and preprocesses datasets  
- AI-Powered Analysis — Uses DeepSeek R1 Distill Qwen 14B  
- Advanced Visualizations — Matplotlib, Seaborn, Plotly  
- Multilingual Support  
- High Performance — Caching, async, error handling  
- Rich Data Insights — Temperature, salinity, depth, location  

### 🎨 Frontend (React + Tailwind CSS)
- Modern Chat UI — Clean, responsive, animated  
- Mobile-Friendly  
- Dark/Light Mode  
- Real-time Plot Rendering  
- Smart Suggestions  
- Interactive Visualizations  
- Optional speech input  

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- Node.js 16+
- npm or yarn
- DeepSeek API Key

---

## 1️⃣ Clone & Setup

```bash
git clone <your-repo-url>
cd floatchat
```

### Backend Setup
```bash
cd backend
pip install -r requirements.txt
cp .env.template .env
```

### Frontend Setup
```bash
cd ../frontend
npm install
```

---

## 2️⃣ Configure Environment Variables

`backend/.env`:

```env
DEEPSEEK_API_KEY=your_key_here
DEEPSEEK_API_URL=https://api.deepseek.com/v1/chat/completions

HOST=localhost
PORT=8000
CORS_ORIGINS=["http://localhost:3000"]

ARGO_DATA_DIR=./data/argo
PLOTS_DIR=./static/plots

LOG_LEVEL=INFO
LOG_FILE=./logs/floatchat.log
```

---

## 3️⃣ Run FloatChat

### Backend
```bash
cd backend
uvicorn app:app --reload
```

### Frontend
```bash
cd frontend
npm start
```

Access:
- UI → http://localhost:3000  
- API → http://localhost:8000  
- Docs → http://localhost:8000/docs  

---

## 📡 API Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/query` | POST | AI + data processing |
| `/health` | GET | Server health |
| `/data/summary` | GET | Summary statistics |
| `/data/preview` | GET | Dataset preview |
| `/docs` | GET | API documentation |

---

### Example Query

```bash
curl -X POST "http://localhost:8000/query" \
-H "Content-Type: application/json" \
-d '{
  "message": "Show me temperature profiles from the Atlantic Ocean",
  "language": "en",
  "include_visualization": true
}'
```

---

## 🎯 Example Queries

### Data Analysis
- "Show temperature profiles from the Atlantic"
- "How does salinity vary with depth?"
- "Compare temperatures by season"
- "Find deepest Pacific measurements"

### Visualizations
- "Generate a temperature-depth profile"
- "Show a salinity map"
- "Plot a T-S diagram"
- "Create a correlation heatmap"

### Educational
- "How do Argo floats work?"
- "Explain thermoclines"
- "What causes El Niño?"

---

## 🏗️ Architecture

### Backend
```
backend/
├── app.py
├── config.py
├── data_utils.py
├── llm_utils.py
├── viz_utils.py
├── requirements.txt
├── .env.template
├── static/
└── logs/
```

### Frontend
```
frontend/
├── src/
│   ├── components/
│   ├── App.js
│   ├── index.js
│   └── index.css
├── public/
├── package.json
└── tailwind.config.js
```

---

## 📊 Visualization Types
- Temperature vs Depth  
- Salinity vs Depth  
- T-S Diagrams  
- Time-Series Trends  
- Geographic Maps  
- Regional Comparisons  
- Correlation Heatmaps  
- 3D Plots  

---

## 🚀 Deployment

### Dockerfile (Backend)

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

## 🤝 Contributing

1. Fork repository  
2. Create feature branch  
3. Commit changes  
4. Create PR  

---

## 🔒 Security
- Environment variables  
- Rate limiting  
- Input validation  
- Secure file handling  

---

## 📜 License
MIT License

---

## 🙏 Acknowledgments
- Argo Program  
- DeepSeek  
- FastAPI  
- React  
- Plotly  
- TailwindCSS  

---

**Built for oceanographic exploration and research 🌊**
