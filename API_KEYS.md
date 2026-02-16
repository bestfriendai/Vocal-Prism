# API Keys Configuration

## Overview

**Vocal Prism is a fully offline transcription application.** It does not require any external API keys to function. All transcription is performed locally on your Mac using OpenAI's Whisper model via the whisper.cpp implementation.

## Required Resources (Bundled)

The app requires the following resources to be bundled in the application:

### 1. whisper-cli Executable

The precompiled whisper command-line tool for audio transcription.

- **Location**: `Vocal Prism/Resources/whisper-cli`
- **Purpose**: Core transcription engine
- **Source**: [whisper.cpp](https://github.com/ggerganov/whisper.cpp)
- **Cost**: Free (Open Source - MIT License)

### 2. Whisper Model Files

AI models for speech recognition. At least one model is required.

| Model | Size | Use Case |
|-------|------|----------|
| ggml-base.en.bin | ~142 MB | Default, balanced |
| ggml-tiny.en.bin | ~75 MB | Fastest, lower accuracy |
| ggml-small.en.bin | ~466 MB | Better accuracy |
| ggml-medium.en.bin | ~1.5 GB | High accuracy |
| ggml-large.bin | ~2.9 GB | Best accuracy |

- **Location**: `Vocal Prism/Resources/`
- **Source**: [Whisper.cpp Models](https://github.com/ggerganov/whisper.cpp/tree/master/models)
- **Cost**: Free (Open Source - MIT License)

### 3. CoreML Encoder (Optional)

For hardware-accelerated transcription on Apple Silicon.

- **Location**: `Vocal Prism/Resources/ggml-base.en-encoder.mlmodelc`
- **Purpose**: GPU/Neural Engine acceleration

## No External API Keys Required

### What's NOT Needed

- ❌ OpenAI API Key
- ❌ AWS Credentials
- ❌ Google Cloud API Key
- ❌ Azure Speech Services
- ❌ Any Third-Party Transcription Service
- ❌ Payment Method

### Why No API Keys?

Vocal Prism uses a **local-only** transcription approach:

1. **whisper-cli**: A compiled version of whisper.cpp that runs entirely on your Mac
2. **On-device processing**: Audio is transcribed locally, never sent to any server
3. **Privacy-first**: Your audio files never leave your computer
4. **No recurring costs**: One-time setup, no per-minute charges

## Configuration

### App Settings

The app uses `@AppStorage` for user preferences:

```swift
@AppStorage("selectedModelId") private var selectedModelId = "base.en"
@AppStorage("selectedLanguage") private var selectedLanguage = "Auto"
@AppStorage("selectedThreads") private var threadCount = 4
```

### Environment Variables

No environment variables are required. All configuration is stored in:

- **UserDefaults**: App preferences (model, language, thread count)
- **Application Support**: Downloaded models and transcription history

## Troubleshooting

### "whisper-cli not found" Error

**Solution**: Ensure Resources are properly added to target:
1. Open `Vocal Prism.xcodeproj` in Xcode
2. Select the "Vocal Prism" target
3. Go to "Build Phases" → "Copy Bundle Resources"
4. Verify `whisper-cli` is listed

### Model Files Missing

**Solution**:
1. Download models from [whisper.cpp models](https://github.com/ggerganov/whisper.cpp/tree/master/models)
2. Place in `Vocal Prism/Resources/` folder
3. Add to Xcode target

## Additional Resources

- **whisper.cpp GitHub**: https://github.com/ggerganov/whisper.cpp
- **Whisper Models**: https://github.com/ggerganov/whisper.cpp/tree/master/models
- **Swift Charts**: Built into SwiftUI (macOS 13+)

## Cost Summary

| Component | Cost |
|-----------|------|
| whisper-cli | Free |
| Whisper Models | Free |
| Swift Charts | Free (built-in) |
| App Development | Your time |

---

**Total API Keys Required: 0**
