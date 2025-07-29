**Demo Link**
Youtube : https://www.youtube.com/watch?v=_7xOIJ-e7Bc&t=30s

# Gaucho Grubs : The best UCSB dining hall app!🌮

**The Ultimate UCSB Dining Hall App - Smart Wait Times & Personalized Dining**

[![Demo Video](https://img.shields.io/badge/Demo-YouTube-red.svg)](https://www.youtube.com/watch?v=_7xOIJ-e7Bc&t=30s)
[![React Native](https://img.shields.io/badge/React_Native-0.76.6-blue.svg)](https://reactnative.dev/)
[![Python](https://img.shields.io/badge/Python-3.8+-green.svg)](https://python.org)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-Database-blue.svg)](https://postgresql.org)
[![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4-orange.svg)](https://openai.com)

## 📖 Overview

Gaucho Grubs revolutionizes the UCSB dining experience by solving two critical problems: **unpredictable wait times** and **time-consuming menu navigation**. Using cutting-edge computer vision and AI, we transform dining hall live feeds into actionable wait time predictions while providing personalized menu recommendations tailored to your dietary needs.

### 🎯 The Problem We Solve
- **Long dining hall lines** with no accurate wait time estimates
- **Difficulty finding menu items** that match dietary restrictions
- **Lack of historical data** to plan optimal dining times
- **Limited personalization** in campus dining apps

## ✨ Key Features

### 🤖 **AI-Powered Wait Time Prediction**
- Real-time computer vision analysis using **YOLO v3**
- Live camera feed processing from UCSB Dining Cam API
- Accurate wait time calculations based on crowd density
- Historical trend analysis with interactive charts

### 🍽️ **Smart Menu Filtering**
- Automatic dietary preference filtering (Vegan, Vegetarian, Nut-free)
- Real-time menu scraping from UCSB dining websites
- Personalized recommendations based on user preferences
- Nutritional information and allergen warnings

### 💬 **Intelligent Dining Assistant**
- **LangChain-powered chatbot** with OpenAI GPT integration
- Natural language queries about menu items and recommendations
- Query analytics for university insights
- Contextual dining hall suggestions

### 📊 **Data Analytics & Insights**
- Historical wait time patterns by day and hour
- Interactive charts showing optimal dining times
- Personal dining statistics ("2024 Wrapped")
- Most visited locations and favorite items tracking

### 🎨 **Beautiful Mobile Experience**
- Native **React Native** app with **Expo Router**
- Smooth animations with **Reanimated** and **Animatable**
- Clean, intuitive UI optimized for mobile
- Real-time updates and seamless navigation

## 🏗️ System Architecture

```
┌─────────────────────┐    ┌────────────────────┐    ┌─────────────────────┐
│   React Native      │    │   Flask Backend     │    │   UCSB Dining API   │
│   Mobile App        │◄──►│   (Port 5000)      │◄──►│   Live Camera Feed  │
│   (Expo Router)     │    │                    │    │                     │
└─────────────────────┘    └────────────────────┘    └─────────────────────┘
         │                           │                           │
         ▼                           ▼                           ▼
┌─────────────────────┐    ┌────────────────────┐    ┌─────────────────────┐
│   User Interface    │    │   PostgreSQL       │    │   Computer Vision   │
│   • Wait Times     │    │   Database         │    │   • YOLO v3         │
│   • Menu Filter    │    │   • Users          │    │   • OpenCV          │
│   • AI Chat        │    │   • Menu Items     │    │   • Person Detection│
│   • Analytics      │    │   • Wait Times     │    │                     │
└─────────────────────┘    └────────────────────┘    └─────────────────────┘
         │                           │                           │
         ▼                           ▼                           ▼
┌─────────────────────┐    ┌────────────────────┐    ┌─────────────────────┐
│   AI Services       │    │   Data Processing   │    │   External APIs     │
│   • OpenAI GPT     │    │   • Web Scraping   │    │   • UCSB Dining     │
│   • LangChain      │    │   • Image Analysis  │    │   • Menu Websites   │
│   • Recommendations│    │   • Analytics       │    │                     │
└─────────────────────┘    └────────────────────┘    └─────────────────────┘
```

## 🛠️ Tech Stack

### **Frontend (React Native)**
- **React Native 0.76.6** - Cross-platform mobile development
- **Expo Router 4.0** - File-based navigation system
- **TypeScript** - Type-safe development
- **React Native Reanimated** - Smooth animations
- **React Native Chart Kit** - Data visualization
- **Expo Vector Icons** - Comprehensive icon library

### **Backend (Python Flask)**
- **Flask** - Lightweight web framework
- **PostgreSQL** - Robust relational database
- **psycopg2** - PostgreSQL adapter
- **Flask-CORS** - Cross-origin resource sharing
- **python-dotenv** - Environment variable management

### **Computer Vision & AI**
- **YOLO v3** - Real-time object detection
- **OpenCV (cv2)** - Computer vision processing
- **OpenAI GPT-4** - Natural language processing
- **LangChain** - AI application framework
- **NumPy** - Numerical computing

### **Data & APIs**
- **UCSB Dining Cam API** - Live camera feeds
- **Web Scraping** - Menu data collection
- **PostgreSQL Database** - Persistent data storage
- **RESTful APIs** - Backend communication

### **Development Tools**
- **Expo CLI** - React Native development
- **Jest** - Testing framework
- **ESLint** - Code linting
- **TypeScript** - Static type checking

## 🚀 Quick Start

### Prerequisites
- **Node.js 18+** - JavaScript runtime
- **Python 3.8+** - Backend development
- **PostgreSQL 13+** - Database server
- **Expo CLI** - React Native development
- **OpenAI API Key** - AI functionality

### Installation

#### 1. **Clone Repository**
```bash
git clone https://github.com/quachphu/Hackathon.git
cd UCSB-main
```

#### 2. **Backend Setup**
```bash
cd backend

# Install Python dependencies
pip install flask psycopg2-binary flask-cors python-dotenv
pip install opencv-python numpy requests langchain-openai

# Download YOLO v3 weights (required for computer vision)
wget https://pjreddie.com/media/files/yolov3.weights

# Set up environment variables
cp .env.example .env
# Edit .env with your credentials:
# OPENAI_API_KEY=your_openai_api_key_here
```

#### 3. **Database Setup**
```sql
-- Create PostgreSQL database
CREATE DATABASE gaucho;

-- Create tables
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(255),
    email VARCHAR(255),
    wants_v INTEGER DEFAULT 0,
    wants_vgn INTEGER DEFAULT 0,
    wants_w_nuts INTEGER DEFAULT 1
);

CREATE TABLE dining_hall_menu (
    id SERIAL PRIMARY KEY,
    dining_hall VARCHAR(255),
    item_name VARCHAR(255),
    food_station VARCHAR(255),
    is_v INTEGER DEFAULT 0,
    is_vgn INTEGER DEFAULT 0,
    is_w_nuts INTEGER DEFAULT 0
);

CREATE TABLE wait_time (
    id SERIAL PRIMARY KEY,
    timestamp TIMESTAMP,
    dining_hall VARCHAR(255),
    wait_time INTEGER
);

CREATE TABLE queries (
    id SERIAL PRIMARY KEY,
    user_id INTEGER,
    query_text TEXT,
    queries_today INTEGER,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 4. **Frontend Setup**
```bash
cd frontend/gaucho

# Install dependencies
npm install

# Install Expo CLI globally (if not already installed)
npm install -g @expo/cli
```

#### 5. **Database Configuration**
Update `backend/app.py` with your PostgreSQL credentials:
```python
db_config = {
    'dbname': 'gaucho',
    'user': 'your_username',
    'password': 'your_password',
    'host': 'localhost',
    'port': 5432
}
```

### Running the Application

#### 1. **Start Backend Services**
```bash
# Terminal 1: Start Flask API
cd backend
python app.py
# Runs on http://localhost:5000

# Terminal 2: Start Computer Vision Service
python images.py
# Continuously processes camera feeds
```

#### 2. **Start Frontend**
```bash
# Terminal 3: Start React Native app
cd frontend/gaucho
npx expo start

# Choose your platform:
# - Press 'i' for iOS simulator
# - Press 'a' for Android emulator
# - Scan QR code with Expo Go app
```

#### 3. **Verify Installation**
```bash
# Test backend API
curl http://localhost:5000/wait_time?dining_hall=carrillo

# Expected response:
# {"average_wait_time": 5.2}
```

## 📱 App Features

### **Home Screen - Dining Hall Overview**
- Real-time wait times for all 3 dining halls
- Visual indicators for crowd levels
- Operating hours and location info
- Quick access to detailed menus

### **Smart Menu Filtering**
- **Dietary Preferences**: Vegan, Vegetarian, Nut allergies
- **Food Stations**: Organized by dining area
- **Real-time Updates**: Menu changes throughout the day
- **Visual Indicators**: Clear dietary restriction badges

### **AI Dining Assistant**
- **Natural Language Queries**: "I want chicken today"
- **Personalized Recommendations**: Based on preferences
- **Contextual Responses**: Time-aware suggestions
- **Query Analytics**: Popular items tracking

### **Wait Time Analytics**
- **Historical Charts**: Interactive bar charts by day/hour
- **Optimal Timing**: Best times to visit each dining hall
- **Live Updates**: Real-time wait time changes
- **Trend Analysis**: Weekly and daily patterns

### **User Account & Preferences**
- **Dietary Restrictions**: Customizable food preferences
- **2024 Wrapped**: Personal dining statistics
- **Visit History**: Most frequented locations
- **Favorite Items**: Most ordered menu items

## 🔧 API Reference

### **Wait Time Endpoints**

#### Get Current Wait Time
```http
GET /wait_time?dining_hall={location}
```
**Parameters:**
- `dining_hall`: `carrillo` | `de-la-guerra` | `portola`

**Response:**
```json
{
  "average_wait_time": 5.2
}
```

### **Menu Endpoints**

#### Get Filtered Menu
```http
GET /menu?userId={id}&dining_hall={location}
```
**Parameters:**
- `userId`: User ID for personalized filtering
- `dining_hall`: Dining hall location

**Response:**
```json
[
  {
    "id": 1,
    "dining_hall": "carrillo",
    "item_name": "Grilled Chicken Breast",
    "food_station": "Grill",
    "is_v": 0,
    "is_vgn": 0,
    "is_w_nuts": 1
  }
]
```

### **AI Chatbot Endpoints**

#### Get AI Recommendation
```http
GET /recommend?user_query={query}&user_id={id}&daily_query_number={count}
```
**Parameters:**
- `user_query`: Natural language food query
- `user_id`: User identifier
- `daily_query_number`: Query count for analytics

**Response:**
```json
"Based on your preferences, I recommend the Grilled Chicken at Carrillo (Grill Station) or the Buddha Bowl at Portola (Healthy Station). Both are available now with minimal wait times!"
```

### **User Management**

#### Update User Preferences
```http
POST /update_preferences
Content-Type: application/json

{
  "id": 1,
  "wants_v": 1,
  "wants_vgn": 0,
  "wants_w_nuts": 1
}
```

## 🤖 Computer Vision System

### **YOLO v3 Implementation**
Our computer vision system uses YOLO v3 for real-time person detection:

```python
# Load pre-trained YOLO model
net = cv2.dnn.readNet("yolov3.weights", "yolov3.cfg")

def count_people(image_path):
    img = cv2.imread(image_path)
    blob = cv2.dnn.blobFromImage(img, 0.00392, (416, 416), (0, 0, 0), True, crop=False)
    net.setInput(blob)
    outputs = net.forward(output_layers)
    
    count = 0
    for output in outputs:
        for detection in output:
            scores = detection[5:]
            class_id = np.argmax(scores)
            confidence = scores[class_id]
            if confidence > 0.5 and class_id == 0:  # Person class
                count += 1
    return count
```

### **Wait Time Calculation**
```python
# Calculate wait time based on people count
people_count = count_people(image_path)
wait_time = people_count * 20  # 20 seconds per person average
```

### **Data Processing Pipeline**
1. **Image Capture**: Fetch from UCSB Dining Cam API every 20 seconds
2. **Person Detection**: YOLO v3 identifies people in queue
3. **Wait Time Calculation**: People count × average service time
4. **Database Storage**: Store timestamped wait times
5. **API Serving**: Provide real-time and historical data

## 📊 Database Schema

### **Users Table**
```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(255),
    email VARCHAR(255),
    wants_v INTEGER DEFAULT 0,      -- Wants vegetarian
    wants_vgn INTEGER DEFAULT 0,    -- Wants vegan
    wants_w_nuts INTEGER DEFAULT 1  -- Allergic to nuts (0 = allergic)
);
```

### **Menu Items Table**
```sql
CREATE TABLE dining_hall_menu (
    id SERIAL PRIMARY KEY,
    dining_hall VARCHAR(255),       -- carrillo, de-la-guerra, portola
    item_name VARCHAR(255),
    food_station VARCHAR(255),      -- Grill, Salad Bar, etc.
    is_v INTEGER DEFAULT 0,         -- Is vegetarian
    is_vgn INTEGER DEFAULT 0,       -- Is vegan  
    is_w_nuts INTEGER DEFAULT 0     -- Contains nuts
);
```

### **Wait Times Table**
```sql
CREATE TABLE wait_time (
    id SERIAL PRIMARY KEY,
    timestamp TIMESTAMP,
    dining_hall VARCHAR(255),
    wait_time INTEGER               -- Wait time in seconds
);
```

### **Query Analytics Table**
```sql
CREATE TABLE queries (
    id SERIAL PRIMARY KEY,
    user_id INTEGER,
    query_text TEXT,
    queries_today INTEGER,
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 🎯 Usage Examples

### **Check Wait Times**
```javascript
// Get current wait time for Carrillo
const response = await fetch('http://localhost:5000/wait_time?dining_hall=carrillo');
const data = await response.json();
console.log(`Wait time: ${data.average_wait_time} minutes`);
```

### **Filter Menu by Dietary Preferences**
```javascript
// Get vegan options for user
const menuResponse = await fetch('http://localhost:5000/menu?userId=1&dining_hall=portola');
const menuItems = await menuResponse.json();
const veganItems = menuItems.filter(item => item.is_vgn === 1);
```

### **AI Chatbot Query**
```javascript
// Ask for recommendations
const query = "I want something healthy with protein";
const aiResponse = await fetch(
  `http://localhost:5000/recommend?user_query=${encodeURIComponent(query)}&user_id=1&daily_query_number=1`
);
const recommendation = await aiResponse.json();
```

## 🏆 Hackathon Achievements

**Built at UCSB Hackathon** - Transforming campus dining through technology

### **What We Accomplished**
- ✅ **Real-time computer vision** processing of live camera feeds
- ✅ **AI-powered chatbot** with natural language understanding  
- ✅ **Complete mobile app** with native performance
- ✅ **Scalable backend architecture** handling multiple data sources
- ✅ **Advanced data analytics** with historical insights

### **Technical Challenges Overcome**
- **Computer Vision Integration**: Successfully implemented YOLO v3 for real-time person detection
- **API Coordination**: Seamless integration between UCSB APIs, AI services, and mobile app
- **Real-time Updates**: Live wait time calculations with 20-second refresh cycles
- **Database Optimization**: Efficient queries for real-time menu filtering
- **Mobile Performance**: Smooth animations and responsive UI on React Native

### **Impact & Innovation**
- **Quantitative Solution**: First app to provide accurate wait time predictions for UCSB dining
- **AI Integration**: Advanced natural language processing for dining recommendations  
- **User-Centric Design**: Addressing real student pain points with data-driven solutions
- **Scalable Architecture**: Framework applicable to dining systems at other universities

## 🚀 Future Enhancements

### **Near-term Goals**
- **Model Fine-tuning**: Improve YOLO accuracy with UCSB-specific training data
- **Nutrition Integration**: Add detailed nutritional information and calorie tracking
- **Push Notifications**: Alert users when wait times drop below thresholds
- **Social Features**: Share dining experiences and reviews

### **Long-term Vision**
- **Multi-Campus Expansion**: Deploy framework to other UC campuses
- **Advanced ML**: Implement deep learning for food recommendation systems
- **IoT Integration**: Connect with dining hall sensors for enhanced accuracy
- **University Partnership**: Official integration with UCSB dining services

### **Potential Applications**
- **Library Queue Management**: Apply computer vision to study space availability
- **Campus Event Planning**: Crowd analysis for optimal event timing
- **Transportation Analytics**: Bus stop wait time predictions
- **Facility Management**: General campus space utilization insights

## 🤝 Contributing

We welcome contributions from the community! Here's how to get involved:

### **Development Workflow**
1. **Fork the repository**
2. **Create feature branch**: `git checkout -b feature/amazing-feature`
3. **Make changes**: Follow our coding standards
4. **Test thoroughly**: Ensure all features work as expected
5. **Commit changes**: `git commit -m 'Add amazing feature'`
6. **Push to branch**: `git push origin feature/amazing-feature`
7. **Open Pull Request**: Describe your changes and their impact

### **Areas for Contribution**
- **Computer Vision**: Improve person detection accuracy
- **Mobile UI/UX**: Enhance user interface and animations
- **Backend Optimization**: Database query performance
- **AI Features**: Expand chatbot capabilities
- **Testing**: Add comprehensive test coverage
- **Documentation**: Improve setup guides and API docs

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👥 Team

**Amazing team that built this in record time!**

- **Judah Boyce** - Full-stack Developer - Database design and API optimization
- **Ivan Li** - AI/Computer Vision  
- **Phu Quach** - AI/Computer Vision, LangChain integration and chatbot development 

## 🙏 Acknowledgments

- **UCSB Hackathon** - For the opportunity to build innovative solutions
- **UCSB Dining Services** - For providing live camera feed access
- **OpenAI** - For powerful language model capabilities
- **React Native Community** - For excellent mobile development tools
- **YOLO Authors** - For open-source computer vision framework

## 📞 Support & Contact
- **📧 General Questions**: [quachphuwork@example.com]
- **🎓 UCSB Students**: Visit us at the next hackathon!

---

**Built with ❤️ for the UCSB community - Making dining smarter, one meal at a time!** 🌮✨
