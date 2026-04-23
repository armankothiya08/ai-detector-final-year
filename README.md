# 🤖 AI Content Detector

A web-based application that detects whether content (text, code, or images) is AI-generated or human-created using Google's Gemini API.

![AI Content Detector](https://img.shields.io/badge/AI-Content%20Detector-blue)
![Python](https://img.shields.io/badge/Python-3.8+-green)
![Flask](https://img.shields.io/badge/Flask-3.0.0-lightgrey)
![License](https://img.shields.io/badge/License-MIT-yellow)

## ✨ Features

- **📝 Text Detection**: Analyze articles, essays, summaries, and written content
- **💻 Code Detection**: Identify AI-generated code across multiple programming languages
- **🖼️ Image Detection**: Detect AI-generated images from tools like Midjourney, DALL-E, Stable Diffusion
- **🎯 Confidence Scores**: Get detailed confidence levels (0-100%) for each detection
- **📊 Detailed Analysis**: Understand the reasoning behind each detection
- **🎨 Modern UI**: Clean, responsive interface with drag-and-drop support
- **⚡ Real-time Analysis**: Fast detection powered by Google Gemini AI

## 🏗️ Technology Stack

### Backend
- **Flask** - Python web framework
- **Google Gemini API** - AI content analysis
- **Flask-CORS** - Cross-origin resource sharing
- **Pillow** - Image processing
- **python-dotenv** - Environment configuration

### Frontend
- **HTML5** - Structure
- **CSS3** - Modern styling with gradients and animations
- **Vanilla JavaScript** - API communication and interactivity

## 📁 Project Structure

```
AiDetector/
├── backend/
│   ├── app.py              # Flask API server
│   ├── detector.py         # Gemini AI integration
│   ├── requirements.txt    # Python dependencies
│   ├── .env               # Environment variables (create this)
│   └── .env.example       # Environment template
├── frontend/
│   ├── index.html         # Main HTML page
│   ├── css/
│   │   └── style.css      # Styling
│   └── js/
│       └── app.js         # Frontend logic
├── plans/                 # Project documentation
└── README.md             # This file
```

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)
- Google Gemini API key ([Get one here](https://makersuite.google.com/app/apikey))
- Modern web browser

### Installation

1. **Clone or download the project**
   ```bash
   cd d:/AiDetector
   ```

2. **Install backend dependencies**
   ```bash
   cd backend
   pip install -r requirements.txt
   ```

3. **Configure environment variables**
   ```bash
   # Copy the example file
   copy .env.example .env
   
   # Edit .env and add your Gemini API key
   GEMINI_API_KEY=your_actual_api_key_here
   FLASK_ENV=development
   PORT=5000
   ```

4. **Start the backend server**
   ```bash
   python app.py
   ```
   
   You should see:
   ```
   Starting AI Detector API on port 5000...
   * Running on http://0.0.0.0:5000
   ```

5. **Open the frontend**
   
   Open `frontend/index.html` in your web browser, or use a local server:
   ```bash
   cd frontend
   python -m http.server 8000
   ```
   Then visit: `http://localhost:8000`

## 📖 Usage

### Text Detection

1. Click on the **"📝 Text Detection"** tab
2. Paste or type your text in the textarea
3. Click **"Analyze Text"**
4. View the results showing:
   - AI-generated or Human-created verdict
   - Confidence score (0-100%)
   - Detailed reasoning

**Example AI-generated text**:
```
Artificial intelligence has revolutionized numerous industries by providing 
innovative solutions to complex problems. Machine learning algorithms enable 
systems to learn from data and improve their performance over time.
```

**Example human-written text**:
```
So I was at the store yesterday and totally forgot what I needed lol. Ended 
up buying random stuff and still forgot the milk. Classic me!
```

### Code Detection

1. Click on the **"💻 Code Detection"** tab
2. Select the programming language from the dropdown
3. Paste your code in the textarea
4. Click **"Analyze Code"**
5. View the detection results

**Supported Languages**: Python, JavaScript, Java, C++, C#, PHP, Ruby, Go, Rust, TypeScript, and more

### Image Detection

1. Click on the **"🖼️ Image Detection"** tab
2. Either:
   - Drag and drop an image onto the upload area
   - Click "Choose File" to select an image
3. Preview the uploaded image
4. Click **"Analyze Image"**
5. View the detection results

**Supported Formats**: JPG, PNG, GIF, WEBP, BMP (Max 5MB)

## 🔧 API Endpoints

### Health Check
```http
GET /api/health
```

### Text Detection
```http
POST /api/detect/text
Content-Type: application/json

{
  "content": "Text to analyze"
}
```

### Code Detection
```http
POST /api/detect/code
Content-Type: application/json

{
  "content": "Code to analyze",
  "language": "python"
}
```

### Image Detection
```http
POST /api/detect/image
Content-Type: multipart/form-data

image: [file]
```

For detailed API documentation, see [`plans/api-reference.md`](plans/api-reference.md)

## 🎯 How It Works

1. **User Input**: User provides content (text, code, or image)
2. **Frontend Validation**: Input is validated for type and size
3. **API Request**: Content is sent to Flask backend
4. **Gemini Analysis**: Backend uses Gemini AI to analyze the content
5. **Response Parsing**: Results are structured and formatted
6. **Display Results**: Frontend shows verdict, confidence, and reasoning

### Detection Models

- **Text & Code**: Uses `gemini-pro` model
- **Images**: Uses `gemini-pro-vision` model

## 📊 Detection Accuracy

The detector analyzes various factors:

### Text Analysis
- Writing style consistency
- Vocabulary patterns
- Sentence structure
- Personal experiences
- Grammar perfection
- Tone authenticity

### Code Analysis
- Code structure
- Comment style
- Naming conventions
- Error handling
- Formatting patterns
- Complexity level

### Image Analysis
- Visual artifacts
- Pattern consistency
- Anatomical accuracy
- Lighting/shadows
- Texture quality
- Composition style

## ⚙️ Configuration

### Environment Variables

Create a `.env` file in the `backend/` directory:

```env
GEMINI_API_KEY=your_gemini_api_key_here
FLASK_ENV=development
PORT=5000
```

### API Rate Limits (Free Tier)

- 60 requests per minute
- 1,500 requests per day

## 🐛 Troubleshooting

### Backend won't start

**Problem**: `ModuleNotFoundError`
```bash
# Solution: Install dependencies
cd backend
pip install -r requirements.txt
```

**Problem**: `GEMINI_API_KEY not found`
```bash
# Solution: Check .env file exists and contains your API key
```

### Frontend issues

**Problem**: CORS errors
```bash
# Solution: Ensure backend is running and flask-cors is installed
pip install flask-cors
```

**Problem**: "Failed to fetch" errors
```bash
# Solution: Verify backend is running on http://localhost:5000
# Check browser console for specific errors
```

### API issues

**Problem**: "Invalid API key"
```bash
# Solution: Verify API key in .env file is correct
# Get a new key from https://makersuite.google.com/app/apikey
```

**Problem**: "Rate limit exceeded"
```bash
# Solution: Wait a minute before trying again
# Free tier: 60 requests/minute, 1500/day
```

## 📚 Documentation

- [`project-summary.md`](plans/project-summary.md) - Complete project overview
- [`quick-start.md`](plans/quick-start.md) - Fast setup guide
- [`ai-detector-architecture.md`](plans/ai-detector-architecture.md) - System architecture
- [`implementation-guide.md`](plans/implementation-guide.md) - Implementation details
- [`api-reference.md`](plans/api-reference.md) - API documentation
- [`workflow-diagrams.md`](plans/workflow-diagrams.md) - Visual workflows

## 🔒 Security

- API keys stored server-side only
- Input validation on all endpoints
- File size limits (5MB for images)
- CORS configured for security
- No sensitive data in error messages

## 🚧 Limitations

- Detection is probabilistic, not 100% accurate
- Free tier has rate limits
- Best results with English content
- Image size limited to 5MB
- Depends on Gemini API availability

## 🔮 Future Enhancements

- [ ] Batch processing for multiple files
- [ ] Result history and analytics
- [ ] Export results (PDF/CSV)
- [ ] User authentication
- [ ] Custom confidence thresholds
- [ ] Browser extension
- [ ] Mobile app
- [ ] Multiple AI model support

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is open source and available under the MIT License.

## 🙏 Acknowledgments

- **Google Gemini AI** - For the powerful AI detection capabilities
- **Flask** - For the excellent web framework
- **Community** - For inspiration and support

## 📞 Support

For issues, questions, or suggestions:

1. Check the [troubleshooting section](#-troubleshooting)
2. Review the [documentation](plans/)
3. Check the browser console for errors
4. Verify backend logs for API issues

## 🌟 Show Your Support

If you find this project useful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting bugs
- 💡 Suggesting new features
- 📖 Improving documentation

---

**Built with ❤️ using Google Gemini AI**

*Detect AI content with confidence!*
