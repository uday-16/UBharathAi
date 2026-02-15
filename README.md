# 🇮🇳 OXCITIZEN - Voice-First Citizen Services App

Your trusted mobile companion for all citizen services in India.

## Features
- 🎤 Voice-first interface (Hindi + English)
- 🏥 Health services & hospitals
- 🎓 Education & scholarships
- 💼 Jobs & career guidance
- 🎁 Government schemes
- ⚖️ Legal help
- 🚨 Emergency services
- 🔐 OTP-based authentication

## Tech Stack
- React Native / Flutter
- TypeScript
- Firebase (Auth, Firestore, Cloud Messaging)
- Redux Toolkit / Zustand
- Axios
- React Navigation

## Prerequisites
- Node.js >= 16.x
- npm or yarn
- React Native CLI / Flutter SDK
- Android Studio (for Android)
- Xcode (for iOS, macOS only)

## Installation

```bash
# Clone repository
git clone <your-repo-url>
cd OXCITIZEN-MOBILE

# Install dependencies
npm install
# or
yarn install

# iOS only - Install pods
cd ios && pod install && cd ..

# Copy environment variables
cp .env.example .env.development
# Edit .env.development with your API keys
```

## Running Locally

### Android
```bash
# Start Metro bundler
npm start

# In another terminal
npm run android
```

**Localhost URL**: App runs on Android Emulator or physical device
**Metro Bundler**: http://localhost:8081

### iOS
```bash
npm run ios
```

**Localhost URL**: App runs on iOS Simulator or physical device

## Development

```bash
# Run in development mode
npm run dev

# Run tests
npm test

# Lint code
npm run lint

# Format code
npm run format
```

## Building for Production

### Android APK
```bash
cd android
./gradlew assembleRelease
# Output: android/app/build/outputs/apk/release/app-release.apk
```

### iOS Archive
```bash
# Open Xcode
open ios/OXCitizen.xcworkspace
# Product > Archive
```

## Project Structure
See [ARCHITECTURE.md](docs/ARCHITECTURE.md)

## Contributing
See [CONTRIBUTING.md](docs/CONTRIBUTING.md)

## License
MIT
