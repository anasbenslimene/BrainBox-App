# 🧠 BrainBox

> [!NOTE]
> This project was developed as part of my summer internship in July 2025.

A premium, interactive, and beautifully animated cognitive training application built with Flutter. **BrainBox** helps users challenge and improve their mental agility, reflexes, memory, and logical reasoning through custom-built mini-games. 

The application utilizes **Firebase** for user authentication and records personal bests and global leaderboards in **Cloud Firestore**, accompanied by rich feedback, animations, and sound effects.

---

## 📋 Table of Contents
1. [Key Features](#-key-features)
2. [The Mini-Games](#-the-mini-games)
3. [Architecture & Project Structure](#-architecture--project-structure)
4. [Tech Stack & Dependencies](#-tech-stack--dependencies)
5. [Installation & Setup](#-installation--setup)
6. [Future Improvements](#-future-improvements)

---

## ✨ Key Features

*   **Secure User Onboarding**: 
    *   Secure signup and sign-in powered by [Firebase Auth](https://firebase.google.com/docs/auth).
    *   Email verification flow to ensure genuine accounts.
    *   Custom profile setup where users choose their unique username.
*   **Persistent High Scores & Leaderboard**:
    *   Personal scores and game statistics are automatically stored and queried from [Cloud Firestore](https://firebase.google.com/docs/firestore).
    *   A dedicated global scoring overview showcasing high scores across all participants.
*   **Dynamic Visuals & Audio**:
    *   Vibrant, theme-consistent color schemes (Deep Purple, Accent Pink, custom game badges).
    *   Fluid micro-animations (fading, sliding, scaling) provided by [flutter_animate](https://pub.dev/packages/flutter_animate).
    *   Interactive audio cues for correct/incorrect answers and game completion.

---

## 🎮 The Mini-Games

BrainBox features four distinct mental challenges, each targetting a different cognitive domain:

### 1. 🧠 Mental Math
*   **Target**: Mathematical speed and accuracy.
*   **Difficulty levels**: Easy (numbers 1-10), Medium (10-50), Hard (20-100).
*   **Rules**: Solve 10 randomized equations using addition, subtraction, or multiplication under a strict 10-second countdown per question.
*   **Key Source Code**: [`mental_math_game.dart`](file:///c:/developpement/flutter-apps/brainbox_app/lib/games/mental_math_game.dart)

### 2. 🎨 Visual Memory
*   **Target**: Visual memory and pattern retention (similar to "Simon Says").
*   **Difficulty levels**: Easy (3-step sequences), Medium (5-step sequences), Hard (7-step sequences).
*   **Rules**: Watch the color sequence light up on the screen, then tap the colored pads in the exact same sequence. Complete 10 rounds to win.
*   **Key Source Code**: [`memory_color_game.dart`](file:///c:/developpement/flutter-apps/brainbox_app/lib/games/memory_color_game.dart)

### 3. ⚡ Reflexes and Colors
*   **Target**: Inhibitory control and reaction speed (based on the psychological *Stroop Effect*).
*   **Difficulty levels**: Easy (2 colors), Medium (3 colors), Hard (4 colors).
*   **Rules**: A color name is written on screen, but it is colored with a different font color. Tap the button that matches the *written* text, not the font color! Complete 10 rapid rounds.
*   **Key Source Code**: [`reflexes_color_game.dart`](file:///c:/developpement/flutter-apps/brainbox_app/lib/games/reflexes_color_game.dart)

### 4. 🧩 Logic Quiz
*   **Target**: Deduction, arithmetic logic, and verbal reasoning.
*   **Difficulty levels**: Easy, Medium, Hard.
*   **Rules**: Answer 10 logic riddles, pattern-recognition challenges, and sequence puzzles. 
*   **Review Feature**: Features a dedicated screen at the end of the quiz summarizing wrong answers, highlighting the correct option versus the option chosen.
*   **Key Source Code**: [`logic_quiz_game.dart`](file:///c:/developpement/flutter-apps/brainbox_app/lib/games/logic_quiz_game.dart)

---

## 📂 Architecture & Project Structure

The project code is organized cleanly into functional layers:

```text
lib/
│
├── main.dart                      # App entry point with Firebase initialization and Auth-state listening
│
├── screens/                       # User interfaces and view controllers
│   ├── welcome_screen.dart         # Intro screen with Sign In / Register choices
│   ├── registration_screen.dart    # Creates new accounts and sends verification emails
│   ├── signin_screen.dart          # Validates credentials and checks email verification
│   ├── username_screen.dart        # Screen where new users define their display name
│   ├── play_screen.dart            # Main dashboard to play games, see scores, and read instructions
│   ├── games_list_screen.dart      # Selector list of all mini-games
│   └── best_scores_screen.dart     # Displays Firestore query of top scores
│
├── games/                         # Game menus and logic controllers
│   ├── mental_math_menu.dart       # Difficulty selector for Mental Math
│   ├── mental_math_game.dart       # Game screen and timer logic for math calculations
│   ├── memory_color_menu.dart      # Difficulty selector for Visual Memory
│   ├── memory_color_game.dart      # Displays flashing color sequence and listens to taps
│   ├── reflexes_color_menu.dart    # Difficulty selector for Reflex game
│   ├── reflexes_color_game.dart    # Layout and evaluation logic for Stroop test
│   ├── logic_quiz_menu.dart        # Difficulty selector for Logic Quiz
│   └── logic_quiz_game.dart        # Logic questions dataset, animation controllers, and mistake reviewer
│
└── widgets/                       # Reusable custom UI components
    └── my_button.dart              # Custom styled button shared across forms
```

---

## 🛠️ Tech Stack & Dependencies

*   **SDK**: [Dart SDK ^3.8.1](https://dart.dev/) & [Flutter SDK](https://flutter.dev/)
*   **Backend & DB**: 
    *   [`firebase_core`](https://pub.dev/packages/firebase_core) for Firebase initialization.
    *   [`firebase_auth`](https://pub.dev/packages/firebase_auth) for secure credentials control.
    *   [`cloud_firestore`](https://pub.dev/packages/cloud_firestore) for tracking leaderboards and history records.
*   **Utilities**:
    *   [`audioplayers`](https://pub.dev/packages/audioplayers) to output game status audio effects.
    *   [`flutter_animate`](https://pub.dev/packages/flutter_animate) for adding fluid UI micro-interactions.

---

## 🚀 Installation & Setup

Follow these steps to run **BrainBox** locally:

### 1. Prerequisites
Ensure you have the Flutter SDK configured:
```bash
flutter doctor
```

### 2. Clone the Repository
```bash
git clone <repository_url>
cd brainbox_app
```

### 3. Install Dependencies
```bash
flutter pub get
```

### 4. Configure Firebase
To activate authentication and scoring:
1. Create a project in the [Firebase Console](https://console.firebase.google.com/).
2. Register an Android and/or iOS application.
3. Download the configuration files (`google-services.json` for Android, `GoogleService-Info.plist` for iOS) and place them in their respective native folders:
   *   **Android**: `android/app/google-services.json`
   *   **iOS**: `ios/Runner/GoogleService-Info.plist`
4. Alternatively, use [FlutterFire CLI](https://firebase.flutter.dev/docs/cli) to automatically configure:
   ```bash
   flutterfire configure
   ```

### 5. Launch the App
Start a simulator/emulator or connect a physical device, then run:
```bash
flutter run
```

---

## 🔮 Future Improvements

*   **Leaderboard Filters**: Enable users to view global rankings sorted by specific games or difficulties.
*   **Offline Mode**: Allow playing games without an active internet connection, localizing score persistence until network reconnection.
*   **New Game Modes**: Additional mini-games testing spatial awareness, verbal logic, and processing speed.
*   **Push Notifications**: Daily reminders or high-score challenges.
