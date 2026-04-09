# Screen2Note

## 프로젝트 개요
Screen2Note는 Windows 환경에서 화면의 일부분을 선택해 캡처하고, 로컬에 설치된 Tesseract OCR을 사용해 한국어·영어 텍스트를 추출한 뒤 마크다운 파일에 자동으로 저장해 주는 오프라인 전용 유틸리티입니다. .NET 6.0 (C#) 기반이며 개인정보 보호를 최우선으로 설계되었습니다.

## 주요 기능
- **전역 핫키** (`Ctrl + Alt + C`) 로 즉시 화면 캡처
- 투명 오버레이를 이용한 영역 선택
- 로컬 Tesseract OCR (한국어·영어) 지원
- 캡처 이미지와 추출 텍스트를 **Markdown** 형태로 자동 저장
- 날짜별 노트 파일(`notes_YYYY-MM-DD.md`)에 누적 기록
- JSON 기반 `settings.json` 으로 핫키, 저장 경로, OCR 옵션 등 사용자 맞춤 설정
- 시스템 트레이 아이콘 및 알림 지원

## 설치 방법
1. **Tesseract 설치**
   - 공식 Windows 설치 프로그램을 다운로드합니다: https://github.com/tesseract-ocr/tesseract
   - `tesseract.exe` 를 PATH에 추가하거나 실행 파일과 같은 폴더에 배치합니다.
   - `eng`와 `kor` 언어팩을 `tessdata` 폴더에 넣습니다 (`eng.traineddata`, `kor.traineddata`).
2. **실행 파일 다운로드**
   - GitHub Release 페이지에서 최신 ZIP 파일을 받아 원하는 위치에 압축을 풉니다.
3. **프로그램 실행**
   - `Screen2Note.exe` 를 실행하면 시스템 트레이에 아이콘이 나타납니다.

## 빌드 방법
```bash
# 저장소 복제
git clone https://github.com/<your-username>/Screen2Note.git
cd Screen2Note

# .NET 6 SDK가 설치돼 있어야 함
# Release 빌드 및 self-contained 배포 파일 생성
dotnet publish -c Release -r win-x64 --self-contained
```
빌드 결과물은 `src/Screen2Note/bin/Release/net6.0/win-x64/publish/` 디렉터리에 생성됩니다.

## 사용 방법
- **Ctrl + Alt + C** 를 눌러 캡처 모드를 시작합니다.
- 마우스로 영역을 드래그하여 선택하고 마우스를 놓으면 캡처가 완료됩니다.
- 프로그램이 자동으로 PNG 파일을 저장하고 Tesseract 로 OCR을 수행한 뒤, 결과를 날짜별 Markdown 파일에 추가합니다.
- 완료되면 시스템 트레이에 알림이 표시됩니다.

## 폴더 구조
```text
Screen2Note/
├─ src/                     # C# 소스 코드
│   ├─ Program.cs
│   ├─ MainForm.cs
│   ├─ CaptureForm.cs
│   ├─ OCRHelper.cs
│   ├─ NoteGenerator.cs
│   ├─ SettingsManager.cs
│   └─ SettingsForm.cs
├─ Release/                # `dotnet publish` 로 만든 실행 파일 및 종속 DLL
│   ├─ Screen2Note.exe
│   ├─ *.dll               # 필요 라이브러리들
│   └─ ...
├─ docs/ (optional)        # 추가 문서
├─ settings.json            # 첫 실행 시 생성되는 사용자 설정 파일
└─ README.md                # 현재 문서
```

## 기여 방법
- Fork 후 feature 브랜치를 만들고, 작업이 끝나면 Pull Request를 제출해 주세요.
- 코드 스타일, 커밋 메시지 규칙 등은 `CONTRIBUTING.md` 를 참고합니다.

## 라이선스
본 프로젝트는 MIT 라이선스를 따릅니다. 자세한 내용은 `LICENSE` 파일을 확인하세요.
