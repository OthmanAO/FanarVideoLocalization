# Fanar Video Localization Pipeline 🎥🗣️🌍

This project provides a complete pipeline for **localizing English videos into Arabic**, using the [Fanar API](https://fanar.qa). It performs:

1. **Audio extraction** from video  
2. **Speech-to-text** transcription  
3. **Grammar correction** via LLM  
4. **Text translation** to Arabic  
5. **Natural Arabic reformulation** for TTS  
6. **Text-to-speech synthesis**  
7. **Recombination of audio and video**

---

## 🚀 Features

- Extracts audio from any video file
- Transcribes speech using Fanar STT model
- Enhances and grammatically corrects transcripts using Fanar Chat
- Translates English to Arabic using Fanar MT
- Prepares Arabic text for smooth TTS rendering
- Generates natural-sounding Arabic audio using Fanar TTS
- Merges audio with the original video (with removed audio)
- **YouTube video download** support with automatic title extraction
- **Smart model selection** based on audio length (STT-1 for short, STT-LF-1 for long)
- **Automatic filename generation** with original title + "arabic dub" suffix

---

## 📁 Project Structure

```
QCRI2025/
├── dubbing_ui.py          # Main Streamlit application
├── en_audio_to_ar_audio.py # Core processing functions
├── fanar_chat.py          # Fanar API client utilities
├── cleanup.py             # Cleanup script for temporary files
├── requirements.txt       # Python dependencies
├── README.md             # This file
└── .gitignore            # Git ignore rules
```

---

## 🧹 Cleanup

The project generates temporary files during processing. To clean up:

```bash
python cleanup.py
```

This removes:
- Temporary audio/video files
- Transcription and translation files
- Demucs output directories
- Python cache files

---

## 🔧 Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Set your Fanar API key in `.env` file
3. Run the app: `streamlit run dubbing_ui.py`

---

## 📝 Usage

1. Upload a video file or paste a YouTube URL
2. The app will automatically:
   - Extract audio and determine duration
   - Select appropriate transcription model
   - Process through the full pipeline
   - Generate final video with Arabic dub
3. Download the final video with descriptive filename
