SmartSafetyMonitor is a Streamlit-based AI hub for workplace and video intelligence tasks.

It combines multiple mini-apps in one interface:
- PPE detection (safety violations)
- Face recognition (registration + matching)
- Traffic sign detection
- Scenario search in video using text prompts
- Voice transcription

## Project Structure

Main app and modules are under `ai_projects_hub/`.

- `ai_projects_hub/main_app.py`: Streamlit launcher and navigation
- `ai_projects_hub/projects/ppe_detection/`: PPE monitoring app
- `ai_projects_hub/projects/face_recognition/`: face database + recognition
- `ai_projects_hub/projects/sign_detection/`: traffic sign detection
- `ai_projects_hub/projects/scenario_search/`: text-to-scene matching
- `ai_projects_hub/projects/voice_transcription/`: Whisper-based transcription
- `ai_projects_hub/config/settings.py`: shared settings and defaults
- `ai_projects_hub/models/`: local model weights (not committed)
- `ai_projects_hub/face_db/`: embeddings and saved face images

## Requirements

- Python 3.10+ recommended
- Webcam (for real-time features)
- GPU optional but recommended for better performance

## Setup

From repository root:

```powershell
python -m venv venv
.\venv\Scripts\Activate.ps1
pip install -r ai_projects_hub/requirements.txt
```

## Environment Variables

Create `ai_projects_hub/.env` if you need API-backed features.

Example:

```env
ROBOFLOW_API_KEY=your_key_here
```

## Model Files
Use the download guide:
- [MODEL_DOWNLOADS.md](MODEL_DOWNLOADS.md)

Expected local files after download:
- `ai_projects_hub/models/yolo9c.pt`
- `ai_projects_hub/models/yolo9e.pt`

## Run The App

```powershell
cd ai_projects_hub
streamlit run main_app.py
```

Then open the local Streamlit URL shown in terminal (usually `http://localhost:8501`).

## Notes
- Some features rely on camera/microphone permissions.
- First model load can take time depending on your machine.

## Troubleshooting
- If model file errors appear, verify paths under `ai_projects_hub/models/`.
- If sign detection fails, confirm `ROBOFLOW_API_KEY` is set.
- If webcam is not detected, close apps using the camera and restart Streamlit.
