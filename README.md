# 🎵 Real-Time Emotion-Based Music Recommendation Web App

A Python-based web application that detects user emotions in real-time using computer vision and recommends personalized music playlists based on the detected mood. Built with Streamlit, OpenCV, DeepFace, and Spotify API integration.

## 🌟 Features

- **Real-time Emotion Detection**: Captures webcam feed and analyzes facial expressions
- **7 Emotion Categories**: Happy, Sad, Angry, Fear, Surprise, Disgust, Neutral
- **Smart Music Mapping**: Automatically maps emotions to appropriate music genres
- **Spotify Integration**: Fetches real playlists from Spotify API (optional)
- **Beautiful UI**: Modern, responsive interface built with Streamlit
- **Live Camera Feed**: Real-time video processing with emotion overlay
- **Music Recommendations**: Personalized playlist suggestions based on mood

## 🎯 Emotion to Music Mapping

| Emotion | Music Genre | Description |
|---------|-------------|-------------|
| 😊 Happy | Pop/Dance | Upbeat and energetic music |
| 😢 Sad | Acoustic/Chill | Calming and soothing music |
| 😠 Angry | Rock/Metal | Powerful and intense music |
| 😨 Fear | Ambient/Calm | Peaceful and relaxing music |
| 😲 Surprised | Electronic/Funk | Energetic and fun music |
| 🤢 Disgusted | Alternative/Indie | Unique and interesting music |
| 😐 Neutral | Lo-fi/Instrumental | Relaxed and chill music |

## 🏗️ Project Structure

```
facialmusicapp/
├── app.py                 # Main Streamlit application
├── camera.py             # Webcam handling and video capture
├── emotion_detection.py  # Emotion recognition using DeepFace
├── recommendation.py     # Music recommendation and Spotify integration
├── requirements.txt      # Python dependencies
└── README.md            # Project documentation
```

## 🚀 Installation & Setup

### Prerequisites

- Python 3.8 or higher
- Webcam (built-in or external)
- Internet connection (for Spotify API)

### Step 1: Clone the Repository

```bash
git clone <repository-url>
cd facialmusicapp
```

### Step 2: Create Virtual Environment (Recommended)

```bash
python -m venv venv

# On Windows
venv\Scripts\activate

# On macOS/Linux
source venv/bin/activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Spotify API Setup (Optional)

1. Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
2. Create a new app
3. Copy your **Client ID** and **Client Secret**
4. Enter them in the app's sidebar when running

## 🎮 How to Run

### Basic Usage (Without Spotify)

```bash
streamlit run app.py
```

### With Spotify Integration

1. Set up Spotify API credentials (see Step 4 above)
2. Run the app: `streamlit run app.py`
3. Enter your Spotify credentials in the sidebar
4. Click "Setup Spotify" to enable API integration

## 📱 Usage Guide

### 1. Start the Application
- Run `streamlit run app.py` in your terminal
- The app will open in your default web browser

### 2. Camera Setup
- Click "🎥 Start Camera" to begin webcam capture
- Ensure your face is visible in the camera view
- The app will automatically detect and analyze your emotions

### 3. Emotion Detection
- Show different facial expressions to test the system
- View real-time emotion analysis with confidence scores
- See emotion breakdown charts for all detected emotions

### 4. Music Recommendations
- Based on your detected emotion, the app suggests music genres
- View recommended playlists (Spotify or default)
- Click playlist links to open in Spotify

### 5. Stop Camera
- Click "⏹️ Stop Camera" when you're done
- This releases webcam resources

## 🔧 Configuration Options

### Camera Settings
- **Resolution**: Default 640x480 (configurable in `camera.py`)
- **FPS**: 30 frames per second
- **Backend**: OpenCV with automatic camera detection

### Emotion Detection
- **Model**: DeepFace with OpenCV backend
- **Confidence Threshold**: 0.3 (configurable in `emotion_detection.py`)
- **Detection Frequency**: Every 2 seconds to optimize performance

### Spotify Integration
- **API Version**: Latest Spotify Web API
- **Authentication**: Client Credentials Flow
- **Rate Limits**: Respects Spotify API limits

## 🛠️ Customization

### Adding New Emotions
Edit `emotion_detection.py`:
```python
self.emotion_labels['new_emotion'] = '😊 New Emotion'
self.emotion_to_genre['new_emotion'] = 'New Genre'
```

### Modifying Music Mappings
Edit `recommendation.py`:
```python
self.emotion_to_genre['happy'] = {
    'genres': ['pop', 'dance', 'electronic'],
    'mood': 'upbeat',
    'energy': 'high',
    'description': 'Your custom description'
}
```

### Changing Camera Settings
Edit `camera.py`:
```python
self.cap.set(cv2.CAP_PROP_FRAME_WIDTH, 1280)  # Change width
self.cap.set(cv2.CAP_PROP_FRAME_HEIGHT, 720)   # Change height
```

## 🐛 Troubleshooting

### Common Issues

#### Camera Not Working
- **Problem**: "Could not open camera" error
- **Solution**: 
  - Check if webcam is connected and not in use by other applications
  - Try different camera indices (0, 1, 2)
  - Ensure camera permissions are granted

#### Emotion Detection Fails
- **Problem**: "Face could not be detected" error
- **Solution**:
  - Ensure good lighting conditions
  - Position face clearly in camera view
  - Check if face is not too close or far from camera

#### Spotify API Issues
- **Problem**: "Spotify setup failed" error
- **Solution**:
  - Verify Client ID and Client Secret are correct
  - Check internet connection
  - Ensure Spotify app is properly configured

#### Performance Issues
- **Problem**: App runs slowly or freezes
- **Solution**:
  - Reduce camera resolution in `camera.py`
  - Increase emotion detection interval in `app.py`
  - Close other applications using webcam

### Error Messages

| Error | Meaning | Solution |
|-------|---------|----------|
| "Camera could not be opened" | Webcam access denied | Check permissions and close other apps |
| "Face could not be detected" | No face in frame | Improve lighting and positioning |
| "Spotify setup failed" | API credentials invalid | Verify credentials and internet connection |
| "Module not found" | Dependencies missing | Run `pip install -r requirements.txt` |

## 📚 Technical Details

### Technologies Used

- **Frontend**: Streamlit (Python web framework)
- **Computer Vision**: OpenCV (webcam capture and image processing)
- **AI/ML**: DeepFace (emotion recognition)
- **Music API**: Spotify Web API (playlist fetching)
- **Image Processing**: PIL/Pillow (image manipulation)
- **Data Visualization**: Streamlit charts and graphs

### Architecture

```
User Interface (Streamlit)
         ↓
Camera Handler (OpenCV)
         ↓
Emotion Detector (DeepFace)
         ↓
Music Recommender (Spotify API)
         ↓
Playlist Display & Links
```

### Performance Considerations

- **Emotion Detection**: Limited to every 2 seconds to prevent system overload
- **Camera Feed**: 30 FPS capture with real-time display
- **Memory Usage**: Optimized frame processing to minimize memory footprint
- **API Calls**: Rate-limited Spotify API calls to respect service limits

## 🔒 Privacy & Security

- **Local Processing**: All emotion detection happens locally on your device
- **No Data Storage**: No personal data or images are stored or transmitted
- **Secure API**: Spotify credentials are handled securely and not logged
- **Camera Access**: Webcam access is only active when explicitly started

## 🤝 Contributing

This is a minor project for CSE students. Feel free to:

1. **Fork** the repository
2. **Create** a feature branch
3. **Make** your improvements
4. **Submit** a pull request

### Suggested Improvements

- Add more emotion categories
- Implement music mood analysis
- Create custom playlist generation
- Add user preference learning
- Implement offline mode

## 📄 License

This project is created for educational purposes as part of a CSE minor project. Feel free to use, modify, and distribute for learning purposes.

## 🙏 Acknowledgments

- **DeepFace**: For emotion recognition capabilities
- **OpenCV**: For computer vision and webcam handling
- **Streamlit**: For the beautiful web interface
- **Spotify**: For music API and playlist data
- **Open Source Community**: For the amazing libraries that made this possible

## 📞 Support

For questions or issues:

1. Check the troubleshooting section above
2. Review the code comments for implementation details
3. Create an issue in the repository
4. Contact your project supervisor or instructor

---

**🎵 Happy Listening! 🎵**

*Built with ❤️ for Computer Science Education*
