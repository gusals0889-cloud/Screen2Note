# Screen2Note

> Offline OCR-powered screen capture utility that instantly converts selected screen regions into organized markdown notes.

## Repository Structure
```text
GitHub Repository
├─ src/            # C# source code
├─ Release/        # Built executable (.exe) and required DLLs
├─ Dependencies/   # Tesseract OCR binaries & language data
└─ README.md       # This documentation
```

## Download
- **Executable:** `Release/Screen2Note.exe`
- **Report:** [report.html](report.html)

## Project Overview
Screen2Note captures a selected region of the screen, runs local OCR, and appends the result to a markdown log. It is designed to make quick note-taking from on-screen content fast, simple, and private.

## Getting Started
1. Install Tesseract OCR and configure its path in `settings.json`.
2. Run `Release/Screen2Note.exe`.
3. Press `Ctrl + Alt + C` to capture a region.
4. The captured image and recognized text will be saved to the `Logs/` directory.

## Build Instructions
```bash
git clone https://github.com/yourusername/Screen2Note.git
cd Screen2Note
dotnet publish -c Release -r win-x64 --self-contained -o Release/
```

## License
MIT License.
