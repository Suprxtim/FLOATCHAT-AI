FloatChat 🌊 **AI-Powered Chat Interface for Argo Oceanographic Data Analysis** FloatChat is a complete, runnable full-stack application that combines the power of AI with comprehensive oceanographic data analysis. Built for hackathons, demos, and educational purposes, it provides an intuitive chat interface to explore and visualize Argo float data from the world's oceans. ## ✨ Features ### Backend (Python + FastAPI) - **📊 Argo Data Integration**: Downloads and preprocesses datasets from multiple sources - **🤖 AI-Powered Analysis**: Integrates with DeepSeek R1 Distill Qwen 14B API for intelligent responses - **🎨 Advanced Visualizations**: Generates interactive plots using Matplotlib, Seaborn, and Plotly - **🌍 Multilingual Support**: Accepts user queries in any language - **⚡ High Performance**: Modular architecture with caching and error handling - **📈 Rich Data Insights**: Temperature, salinity, depth, and location analysis ### Frontend (React + Tailwind CSS) - **💬 Beautiful Chat Interface**: Responsive, modern UI with smooth animations - **📱 Mobile-Friendly**: Works seamlessly across all device sizes - **🌙 Dark/Light Mode**: Automatic theme switching - **🔄 Real-time Updates**: Live visualization rendering - **🎯 Smart Suggestions**: Context-aware query recommendations - **🎨 Interactive Plots**: Embedded Plotly visualizations with fullscreen support - **🔊 Voice Input**: Speech-to-text capability (ready for implementation) ## 🚀 Quick Start ### Prerequisites - Python 3.8+ - Node.js 16+ - npm or yarn - DeepSeek API key ### 1. Clone and Setup
bash
# Clone the repository
git clone <your-repo-url>
cd floatchat

# Setup backend
cd backend
pip install -r requirements.txt

# Setup environment variables
cp .env.template .env
# Edit .env and add your DEEPSEEK_API_KEY

# Setup frontend
cd ../frontend
npm install
### 2. Configure Environment Edit backend/.env with your configuration:
env
# DeepSeek API Configuration
DEEPSEEK_API_KEY=your_deepseek_api_key_here
DEEPSEEK_API_URL=https://api.deepseek.com/v1/chat/completions

# Server Configuration
HOST=localhost
PORT=8000
CORS_ORIGINS=["http://localhost:3000"]

# Data Configuration
ARGO_DATA_DIR=./data/argo
PLOTS_DIR=./static/plots

# Logging Configuration
LOG_LEVEL=INFO
LOG_FILE=./logs/floatchat.log
### 3. Run the Application **Terminal 1 - Backend:**
bash
cd backend
uvicorn app:app --reload
**Terminal 2 - Frontend:**
bash
cd frontend
npm start
**Access the application:** - Frontend: http://localhost:3000 - Backend API: http://localhost:8000 - API Documentation: http://localhost:8000/docs ## 📋 API Endpoints ### Main Endpoints - POST /query - Process user queries and generate responses - GET /health - System health check - GET /data/summary - Dataset summary statistics - GET /data/preview - Preview of available data - GET /docs - Interactive API documentation ### Query Endpoint Example
bash
curl -X POST "http://localhost:8000/query" \
     -H "Content-Type: application/json" \
     -d '{
       "message": "Show me temperature profiles from the Atlantic Ocean",
       "language": "en",
       "include_visualization": true
     }'
**Response:**
json
{
  "text_response": "Here's an analysis of temperature profiles...",
  "plot_url": "/static/plots/temp_profile_abc123.html",
  "data_summary": {
    "records_found": 15420,
    "profiles": 1250,
    "date_range": ["2023-01-01", "2024-01-01"]
  },
  "query_type": "data_query",
  "timestamp": "2024-01-15T10:30:00Z",
  "success": true
}
## 🎯 Example Queries Try these sample questions with FloatChat: ### Data Analysis - "Show me temperature profiles from the Atlantic Ocean" - "What's the relationship between temperature and salinity?" - "Compare ocean temperatures between summer and winter" - "Find the deepest measurements in the Pacific" ### Visualizations - "Create a map of recent ocean measurements" - "Show temperature trends over time" - "Visualize salinity distribution by depth" - "Generate a 3D scatter plot of ocean data" ### Educational - "How do Argo floats work?" - "What is the thermocline?" - "Explain ocean salinity patterns" - "What causes El Niño?" ## 🏗️ Architecture ### Backend Structure
backend/
├── app.py              # Main FastAPI application
├── config.py           # Configuration management
├── data_utils.py       # Argo data handling
├── llm_utils.py        # DeepSeek API integration
├── viz_utils.py        # Visualization generation
├── requirements.txt    # Python dependencies
├── .env.template      # Environment template
├── static/            # Generated plots
└── logs/              # Application logs
### Frontend Structure
frontend/
├── src/
│   ├── components/
│   │   ├── ChatBox.js      # Chat message container
│   │   ├── Message.js      # Individual message display
│   │   ├── PlotDisplay.js  # Interactive plot viewer
│   │   └── InputBox.js     # Message input interface
│   ├── App.js             # Main application component
│   ├── index.js           # React entry point
│   └── index.css          # Global styles
├── public/               # Static assets
├── package.json          # Dependencies
└── tailwind.config.js    # Tailwind configuration
## 🎨 Visualization Types FloatChat automatically generates appropriate visualizations: 1. **Temperature-Depth Profiles** - Oceanographic depth profiles 2. **T-S Diagrams** - Temperature vs Salinity scatter plots 3. **Geographic Maps** - Spatial distribution of measurements 4. **Time Series** - Temporal trends and patterns 5. **Regional Comparisons** - Box plots by geographic regions 6. **Correlation Heatmaps** - Relationships between variables 7. **3D Scatter Plots** - Multi-dimensional data exploration 8. **Depth Distributions** - Measurement depth histograms ## 🔧 Configuration Options ### Backend Configuration - **Data Sources**: Configure Argo data URLs and local storage - **API Settings**: DeepSeek API endpoint and authentication - **Visualization**: Plot styling and output formats - **Logging**: Detailed logging configuration - **CORS**: Frontend URL whitelist ### Frontend Configuration - **API Endpoint**: Backend server URL - **Theme Settings**: Dark/light mode preferences - **Animation Settings**: Motion and transition configurations - **Responsive Breakpoints**: Mobile/tablet/desktop layouts ## 🚀 Deployment ### Docker Deployment (Recommended) 1. **Create Dockerfile for backend:**
dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8000
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "8000"]
2. **Build and run:**
bash
# Backend
docker build -t floatchat-backend ./backend
docker run -p 8000:8000 --env-file backend/.env floatchat-backend

# Frontend
cd frontend && npm run build
# Serve build folder with nginx or similar
### Cloud Deployment **Backend options:** - Heroku, Railway, or DigitalOcean Apps - AWS Lambda with FastAPI - Google Cloud Run **Frontend options:** - Netlify or Vercel (static hosting) - AWS S3 + CloudFront - GitHub Pages ## 🔍 Troubleshooting ### Common Issues **Backend won't start:** - Check Python version (3.8+ required) - Verify all dependencies are installed - Ensure .env file exists with valid API key **Frontend build errors:** - Clear node_modules: rm -rf node_modules && npm install - Check Node.js version (16+ recommended) - Verify all peer dependencies **API connection issues:** - Check CORS settings in backend config - Verify backend is running on correct port - Check firewall/network restrictions **Visualization not loading:** - Check browser console for errors - Verify static file serving is configured - Check plot file permissions ### Debug Mode Enable debug logging:
env
LOG_LEVEL=DEBUG
Check logs:
bash
tail -f backend/logs/floatchat.log
## 🤝 Contributing 1. Fork the repository 2. Create a feature branch: git checkout -b feature-name 3. Make your changes 4. Add tests if applicable 5. Commit: git commit -m 'Add feature' 6. Push: git push origin feature-name 7. Create a Pull Request ### Development Guidelines - Follow PEP 8 for Python code - Use ESLint/Prettier for JavaScript - Write descriptive commit messages - Add documentation for new features - Test on multiple browsers/devices ## 📊 Performance ### Optimization Features - **Data Caching**: Intelligent caching of processed datasets - **Lazy Loading**: Progressive loading of visualizations - **Code Splitting**: Optimized React bundle sizes - **Image Optimization**: Compressed plot outputs - **API Rate Limiting**: Prevents API abuse ### Monitoring - Built-in health checks - Request/response logging - Error tracking and reporting - Performance metrics ## 🔒 Security - Environment variable protection - CORS configuration - Input validation and sanitization - Rate limiting - Secure file handling ## 📜 License MIT License - see LICENSE file for details ## 🙏 Acknowledgments - **Argo Program**: For providing global oceanographic data - **DeepSeek**: For AI language model capabilities - **FastAPI**: For robust backend framework - **React**: For powerful frontend development - **Plotly**: For interactive visualizations - **Tailwind CSS**: for beautiful styling ## 📞 Support For questions, issues, or contributions: - Create an issue on GitHub - Check existing documentation - Review API documentation at /docs --- **Built with ❤️ for oceanographic research and education**
