# Companion-Robot
===============

This is a smart and interactive Companion Robot designed to assist humans, especially the elderly and children, by recognizing emotions and responding in real time using natural language. The system integrates facial emotion recognition, voice-based conversation via OpenAI's ChatGPT API, and touch-based interaction using embedded hardware.

Features
--------

- Real-Time Emotion Detection  
  Detects human emotions using facial expression analysis powered by deep learning.

- Voice Conversation with ChatGPT  
  Supports spoken conversations by converting speech to text, sending it to a large language model, and reading back the response using synthesized speech.

- Touch-Based Interaction  
  Detects human touch using capacitive sensors to trigger personalized responses.

- Visual Feedback via OLED Display  
  Displays facial expressions, emojis, or text messages on a compact screen.

- Physical Feedback using Servo Motors  
  Simulates gestures like nodding or shaking the head to reflect conversational intent and emotions.

Core Technologies
-----------------

Category               | Technologies Used
----------------------|-------------------------------
Emotion Detection      | DCNN model trained on FER-2013 dataset
Voice Input/Output     | SpeechRecognition, pyttsx3 or gTTS
Language Model         | OpenAI ChatGPT API
Microcontroller        | ESP32 with Arduino-compatible components
Embedded Components    | Servo motors, capacitive touch sensor, OLED display
Programming Stack      | Python, C++ (Arduino), OpenCV, TensorFlow/Keras

Installation and Setup
----------------------

Python Backend (PC)
-------------------

1. Clone the Repository

   git clone <your-repo-url>
   cd companion-robot

2. Create a virtual environment and install dependencies

   python -m venv venv  
   source venv/bin/activate  
   pip install -r requirements.txt

3. Add your OpenAI API Key

   Create a file named .env and add the following line:

   OPENAI_API_KEY=your_openai_api_key_here

4. Run the Application

   python main.py

Embedded (ESP32 Setup)
----------------------

- Use Arduino IDE to upload the firmware from the embedded folder.
- Connect:
  - Touch Sensor to appropriate GPIO pin
  - Servo Motor(s) to GPIO pins
  - OLED Display to I2C pins (SCL and SDA)
- Ensure serial communication between ESP32 and Python backend is active.

Project Structure
-----------------

companion-robot/  
│  
├── main.py                   - Central script for emotion and voice control  
├── emotion_model/            - Trained DCNN model and helper functions  
├── speech_interface/         - Voice recognition and TTS modules  
├── embedded/                 - Arduino code for ESP32  
├── utils/                    - Utility scripts (touch input, camera interface)  
├── requirements.txt          - Python dependencies  
└── .env                      - API key configuration (not included in repo)

Functional Modules
------------------

1. Emotion Detection

- Uses a DCNN model trained on FER-2013
- Processes live video from a camera using OpenCV
- Maps detected emotion to both speech and gestures

2. Conversational AI

- Converts voice input to text
- Sends the query to ChatGPT API
- Converts text reply to speech for voice response

3. Embedded Interactions

- Servo motors execute gestures based on emotions or voice intent
- Touch sensor activates or deactivates interaction state
- OLED screen shows emoticons or messages based on context

Future Enhancements
-------------------

- Multimodal Emotion Detection using facial, voice, and posture data  
- On-Device Inference using TensorFlow Lite on edge devices  
- Context-Aware Conversations with memory of previous interactions  
- Emotionally Modulated Speech through advanced voice synthesis  
- Multi-language Support for regional and global users  
