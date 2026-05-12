# Unisara AI Chatbot

Unisara AI Chatbot is a Flutter-based university assistant for the University of Technology Sarawak (UTS). It provides a conversational interface where users can ask university-related questions and receive responses from a combination of local UTS knowledge data and Google Gemini AI.

## Overview

The application is designed to make university information easier to access through a chat-style interface. It uses Firebase for authentication and chat history storage, a local JSON knowledge base for structured UTS information, and the `google_generative_ai` package to generate AI responses when a question is not handled by the local knowledge rules.

## Features

- AI-powered university chatbot interface
- Local UTS knowledge base using `assets/UnisaraKnowledge.json`
- Google Gemini integration through `google_generative_ai`
- Firebase Authentication support
- Google sign-in support
- Facebook sign-in support
- User registration, login, verification, and password reset screens
- Chat history storage using Cloud Firestore
- New chat session support
- Cross-platform Flutter project structure for Android, iOS, web, Windows, macOS, and Linux

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Flutter |
| Language | Dart |
| AI Model | Google Gemini |
| Authentication | Firebase Authentication |
| Database | Cloud Firestore |
| Local Knowledge Base | JSON asset |
| Supported Platforms | Android, iOS, Web, Windows, macOS, Linux |

## Project Structure

```text
Unisara-AI-Chatbot/
|-- android/                  # Android platform files
|-- assets/                   # Images and UTS knowledge JSON
|-- ios/                      # iOS platform files
|-- lib/
|   |-- authentication/       # Firebase, Google, and Facebook auth logic
|   |-- models/               # Message and app model files
|   |-- screens/              # Login, register, chat, menu, profile screens
|   |-- utils/                # Gemini AI, constants, UI helper widgets
|   `-- main.dart             # App entry point
|-- web/                      # Web platform files
|-- windows/                  # Windows platform files
|-- macos/                    # macOS platform files
|-- linux/                    # Linux platform files
|-- firebase.json
|-- pubspec.yaml
`-- README.md
```

## Prerequisites

Before running the project, install:

- [Flutter SDK](https://docs.flutter.dev/get-started/install)
- Dart SDK bundled with Flutter
- Android Studio or Visual Studio Code
- Firebase project configured for the target platform
- A Google Gemini API key

Check your Flutter installation:

```bash
flutter doctor
```

## Installation

Clone the repository:

```bash
git clone https://github.com/Dexufy/Unisara-AI-Chatbot.git
cd Unisara-AI-Chatbot
```

Install dependencies:

```bash
flutter pub get
```

## Configuration

### Firebase

This project uses Firebase Core, Firebase Authentication, and Cloud Firestore.

Make sure your Firebase project is configured for the platform you want to run:

- Android: `android/app/google-services.json`
- iOS/macOS: Firebase plist configuration if required
- Web: Firebase web configuration

The app initializes Firebase in:

```text
lib/main.dart
lib/models/model/firebase_options.dart
```

If you create a new Firebase project, regenerate the Firebase options with FlutterFire CLI:

```bash
dart pub global activate flutterfire_cli
flutterfire configure
```

### Gemini API Key

The Gemini API key is read from:

```text
lib/utils/constants.dart
```

For development, update the API key value there. For production, avoid committing real API keys directly to the repository. Use environment-based configuration or a secure backend service instead.

## Running the Application

Run on the connected default device:

```bash
flutter run
```

Run on Chrome:

```bash
flutter run -d chrome
```

Run on Android:

```bash
flutter run -d android
```

List available devices:

```bash
flutter devices
```

## Main Application Flow

1. The app starts from `lib/main.dart`.
2. Firebase is initialized using `DefaultFirebaseOptions`.
3. The authentication page decides whether the user should log in, register, or access the app.
4. Users can sign in using email/password, Google, or Facebook.
5. After authentication, users can open the UniSara chat screen.
6. User messages are processed by `GeminiAI.generateResponse()`.
7. The app checks the local UTS knowledge base first for known university information.
8. If no local rule matches, the prompt is sent to Gemini for a generated response.
9. Messages are stored in Firestore under chat history.

## Knowledge Base

The chatbot uses:

```text
assets/UnisaraKnowledge.json
```

This file stores structured information about UTS, including university details, schools, programmes, staff, accreditation, collaborations, and useful links. The data is loaded in:

```text
lib/utils/gemini_ai.dart
```

To expand the chatbot's university-specific answers, update `UnisaraKnowledge.json` and add matching handling logic in `GeminiAI.generateResponse()`.

## Dependencies

Main dependencies from `pubspec.yaml`:

- `google_generative_ai`
- `firebase_core`
- `firebase_auth`
- `cloud_firestore`
- `google_sign_in`
- `flutter_login_facebook`
- `cached_network_image`
- `intl`
- `http`

## Build

Build an Android APK:

```bash
flutter build apk
```

Build for web:

```bash
flutter build web
```

Build for Windows:

```bash
flutter build windows
```

## Troubleshooting

If dependencies fail to load, run:

```bash
flutter clean
flutter pub get
```

If Firebase does not initialize correctly, confirm that the Firebase configuration files match the package name, bundle ID, or web app configuration.

If Gemini responses fail, check that the API key is valid and that the device has internet access.

If an asset does not load, confirm that the filename matches the entry in `pubspec.yaml`.

## Future Improvements

- Move API key handling to a safer environment-based or backend-based approach
- Improve the local knowledge matching logic
- Add source references for university answers
- Add admin tools for updating the knowledge base
- Add multi-language support
- Add voice input and text-to-speech
- Add automated tests for authentication and chat flows

## Author

Developed by **Ethan Dexter Jimbai**.

GitHub: [@Dexufy](https://github.com/Dexufy)

## License

This project is developed for educational purposes. Add a license file if the project will be distributed publicly or reused by others.
