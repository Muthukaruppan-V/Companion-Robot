# Companion-Robot

This is a smart and interactive Companion Robot designed to assist humans, especially the elderly and children, by recognizing emotions and responding in real time using natural language. The system integrates facial emotion recognition, voice-based conversation via OpenAI's ChatGPT API, and touch-based interaction using embedded hardware on a Raspberry Pi 4B.

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
Microcontroller Board  | Raspberry Pi 4B  
Embedded Components    | Servo motors, capacitive touch sensor, OLED display  
Programming Stack      | Python, OpenCV, TensorFlow/Keras, I2C, GPIO, Linux  

Installation and Setup
----------------------

Raspberry Pi Backend
--------------------

1. Update and upgrade the Raspberry Pi OS

   sudo apt update  
   sudo apt upgrade

2. Clone the Repository

   git clone <your-repo-url>  
   cd companion-robot

3. Create a virtual environment and install dependencies

   python3 -m venv venv  
   source venv/bin/activate  
   pip install -r requirements.txt

4. Add your OpenAI API Key

   Create a file named `.env` and add the following line:

   OPENAI_API_KEY=your_openai_api_key_here

5. Run the Application

   python3 main.py

Hardware Setup
--------------

- Connect the components to Raspberry Pi GPIO as follows:
  - Touch Sensor to appropriate GPIO pin (e.g., GPIO 17)
  - Servo Motor(s) to GPIO PWM-capable pins (e.g., GPIO 18)
  - OLED Display via I2C (typically SDA to GPIO 2, SCL to GPIO 3)
  - USB Camera or Pi Camera for emotion detection input
  - Microphone and speaker or USB audio interface for voice I/O

Project Structure
-----------------

companion-robot/  
│  
├── main.py                   - Central script for emotion and voice control  
├── emotion_model/            - Trained DCNN model and helper functions  
├── speech_interface/         - Voice recognition and TTS modules  
├── hardware_control/         - Scripts for GPIO, servo, touch, and display  
├── utils/                    - Utility functions (e.g., camera interface)  
├── requirements.txt          - Python dependencies  
└── .env                      - API key configuration (not included in repo)

Functional Modules
------------------

1. Emotion Detection

- Uses a DCNN model trained on FER-2013  
- Processes live video feed using OpenCV on Raspberry Pi  
- Maps detected emotion to speech output and servo gestures

2. Conversational AI

- Captures and converts voice input to text  
- Sends the text query to ChatGPT API  
- Converts text response to speech using TTS engine

3. Embedded Interactions

- Servo motors express physical gestures like nodding  
- Touch sensor triggers conversational mode or reactions  
- OLED screen provides visual feedback with emotion-related icons or text

Future Enhancements
-------------------

- Multimodal Emotion Detection using facial expressions, voice tone, and posture  
- On-Device Inference using TensorFlow Lite for faster real-time performance  
- Context-Aware Conversations with memory for personalized interaction  
- Emotionally Modulated Speech with expressive TTS  
- Multi-language Support to expand usability across cultures
