# Model Download Guide

This project expects model files locally, but they are too large for normal Git history. Keep them in external model storage and download them into the repo folder structure.

## Required Local Files

Place these files exactly here:
- `ai_projects_hub/models/yolo9c.pt`
- `ai_projects_hub/models/yolo9e.pt`

Optional/related data:
- `ai_projects_hub/face_db/embeddings.json`

## Example Download (PowerShell)

Release tag: `v1.0-models`

```powershell
$ErrorActionPreference = 'Stop'

New-Item -ItemType Directory -Force -Path "ai_projects_hub/models" | Out-Null

Invoke-WebRequest "https://github.com/rashxmxn/SmartSafetyMonitor/releases/download/v1.0-models/yolo9c.pt" -OutFile "ai_projects_hub/models/yolo9c.pt"
Invoke-WebRequest "https://github.com/rashxmxn/SmartSafetyMonitor/releases/download/v1.0-models/yolo9e.pt" -OutFile "ai_projects_hub/models/yolo9e.pt"
```

## Verify Files

```powershell
Get-ChildItem ai_projects_hub/models/*.pt | Select-Object Name,Length
```

## Team Workflow Recommendation

- Keep model files out of regular Git commits.
- Keep only download instructions (this file) in Git.
- Pin model versions in filenames, release tags, or URL paths.
- If model weights change, update this file and release notes together.
