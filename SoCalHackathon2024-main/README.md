# Link Demo : 
Link1 : https://www.youtube.com/watch?v=TNiw3K0_gpU

Link2 : https://www.youtube.com/watch?v=ytsUsYFrEZg

# VoiceBridge 🎯

**AI-Powered Computer Control for Enhanced Accessibility**

[![SoCalHackathon2024](https://img.shields.io/badge/SoCalHackathon-2024-blue.svg)](https://github.com/quachphu/Hackathon)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python](https://img.shields.io/badge/Python-3.8+-green.svg)](https://python.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.5+-blue.svg)](https://typescriptlang.org)

## 📖 Overview

VoiceBridge is an innovative accessibility tool that bridges the gap between technology and users with impairments. Using advanced AI vision and natural language processing, it enables users to control their computers through voice commands, making technology truly inclusive.

### 🎯 Mission
> *"Making technology accessible to everyone, regardless of physical limitations"*

## ✨ Key Features

- 🖥️ **Screen Analysis** - AI-powered visual understanding of your screen
- 🗣️ **Voice Control** - Natural language commands for computer interaction
- 🖱️ **Smart Clicking** - Intelligent UI element detection and interaction
- ⌨️ **Text Input** - Voice-to-text typing capabilities
- 🌐 **Browser Integration** - Chrome extension for web navigation
- 📜 **Page Navigation** - Forward/backward navigation with voice commands
- 🔄 **Scrolling Control** - Smooth scrolling with voice commands

## 🏗️ Architecture

VoiceBridge uses a multi-service architecture combining AI, computer vision, and automation:

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   DAIN Service  │    │   Python Flask   │    │ Chrome Extension│
│   (TypeScript)  │◄──►│      API         │    │   (JavaScript)  │
│                 │    │   (Port 3000)    │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
         │                       │                       │
         ▼                       ▼                       ▼
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   OpenAI GPT-4  │    │   PyAutoGUI      │    │  Browser APIs   │
│   Vision API    │    │   Screen Control │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

## 🛠️ Tech Stack

### **Core Services**
- **DAIN Protocol** - AI service framework
- **Node.js/TypeScript** - Main service layer
- **Python Flask** - Computer automation API
- **Chrome Extension** - Browser integration

### **AI & Vision**
- **OpenAI GPT-4 Vision** - Screen analysis and understanding
- **EasyOCR** - Optical Character Recognition
- **Computer Vision (OpenCV)** - Image processing
- **Levenshtein Distance** - Text similarity matching

### **Automation**
- **PyAutoGUI** - Screen automation (clicking, typing, scrolling)
- **Screen Capture** - Real-time screen analysis
- **Keyboard/Mouse Control** - System-level automation

### **Development**
- **TypeScript 5.5+** - Type-safe development
- **Hono** - Lightweight web framework
- **Zod** - Schema validation
- **Axios** - HTTP client

## 🚀 Quick Start

### Prerequisites
- Node.js 18+
- Python 3.8+
- OpenAI API Key
- DAIN API Key

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/quachphu/Hackathon.git
cd SoCalHackathon2024-main
```

2. **Install Node.js dependencies**
```bash
npm install
```

3. **Install Python dependencies**
```bash
cd api
pip install flask opencv-python pyautogui easyocr levenshtein matplotlib numpy
```

4. **Environment Setup**
```bash
# Create .env.development file
cp .env.development.example .env.development

# Add your API keys
DAIN_API_KEY=your_dain_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
```

5. **Chrome Extension Setup**
- Open Chrome and go to `chrome://extensions/`
- Enable "Developer mode"
- Click "Load unpacked" and select the `extension/` folder

### Running the Application

1. **Start the Python Flask API**
```bash
cd api
python main.py
# Server runs on http://localhost:3000
```

2. **Start the DAIN Service**
```bash
npm run dev
# Service runs on port 2022
```

3. **Test the connection**
```bash
curl http://localhost:3000/analyze_screen
```

## 📋 API Reference

### Flask API Endpoints

| Endpoint | Method | Description |
|----------|---------|-------------|
| `/analyze_screen` | GET | Capture and analyze current screen |
| `/write_text` | POST | Type text on screen |
| `/press_key` | POST | Emulate key presses |
| `/click_request` | POST | Click on specified UI element |
| `/scroll` | POST | Scroll page up/down |
| `/navigate_page` | POST | Navigate forward/backward |
| `/open` | POST | Open new tab/window |

### DAIN Service Tools

- **analyze-screen** - Analyzes user's screen content
- **click-request** - Clicks on specified text/buttons
- **scroll-page** - Controls page scrolling
- **navigate-page** - Page navigation controls
- **write-string** - Text input functionality
- **press-key** - Keyboard emulation
- **open-tab** - Tab management

## 🎮 Usage Examples

### Voice Commands
```
"What's on my screen?"          → Analyzes current screen content
"Click on the login button"     → Finds and clicks login button
"Scroll down"                   → Scrolls page downward
"Type 'Hello World'"           → Types the specified text
"Press Enter"                   → Presses Enter key
"Go back"                       → Navigates to previous page
"Open new tab"                  → Opens a new browser tab
```

### Programmatic Usage
```typescript
// Analyze screen
const analysis = await dainService.tools.analyzeScreen({
  question: "What's displayed on the screen?"
});

// Click on element
await dainService.tools.clickRequest({
  question: "Click on the submit button"
});

// Type text
await dainService.tools.writeString({
  question: "Enter my email address"
});
```

## 🔧 Configuration

### DAIN Configuration (`dain.json`)
```json
{
  "project-id": "",
  "api-key": "MUST PUT IN .env.development as DAIN_API_KEY=YOUR_API_KEY",
  "main-file": "src/index.ts",
  "static-dir": "static",
  "out-dir": "dist",
  "environment": "development",
  "version": "1.0.0",
  "runtime": "node"
}
```

### Python API Configuration
- **Port**: 3000 (configurable in `main.py`)
- **Image Storage**: `../temp/image.png`
- **OCR Language**: English (`["en"]`)

## 🎯 Use Cases

### Accessibility
- **Motor Impairments** - Voice control for users with limited hand mobility
- **Visual Impairments** - Screen reading and navigation assistance
- **Cognitive Assistance** - Simplified computer interaction

### Productivity
- **Hands-free Computing** - Multitasking while controlling computer
- **Voice Automation** - Streamlined workflow automation
- **Remote Control** - Computer control from distance

## 🏆 Hackathon Achievements

**SoCalHackathon2024** - Building inclusive technology that bridges accessibility gaps

### What We Built
- Complete AI-powered accessibility suite
- Real-time screen analysis and control
- Natural language computer interaction
- Cross-platform browser integration

### Technical Challenges Overcome
- Real-time OCR and computer vision integration
- Seamless AI service communication
- Precise UI element detection and interaction
- Cross-service architecture coordination

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guidelines](CONTRIBUTING.md).

### Development Setup
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Commit changes: `git commit -m 'Add amazing feature'`
4. Push to branch: `git push origin feature/amazing-feature`
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

**DFPP Team**
- **Dichill** - AI Integration & Computer Vision
- **Fahat** - Backend Development & API Design  
- **Paola** - Frontend & User Experience
- **Phu** - System Architecture & Automation

## 🙏 Acknowledgments

- **DAIN Protocol** - For the amazing AI service framework
- **OpenAI** - For powerful vision and language models
- **SoCalHackathon2024** - For the opportunity to build inclusive technology
- **Accessibility Community** - For inspiration and feedback

## 📞 Support

- 📧 Email: [your-email@example.com]
- 🐛 Issues: [GitHub Issues](https://github.com/quachphu/Hackathon/issues)
- 💬 Discussions: [GitHub Discussions](https://github.com/quachphu/Hackathon/discussions)

---

**Made with ❤️ for accessibility and inclusion**
