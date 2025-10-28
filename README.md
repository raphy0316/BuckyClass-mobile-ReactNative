# BuckyClass (React Native + Expo)

An education-focused mobile app built with React Native and Expo. It provides course discovery, course detail analytics (grade distribution, instructors, sections), real-time course group chats and 1:1 private chats via Firebase Realtime Database, user authentication with Firebase, and review submission to a backend API.

## Features

- Authentication (Firebase Email/Password)
- Welcome splash video using `expo-av`
- Home dashboard with popular content and lightweight charts
- Course search and listing (requires login)
- Course details with grade distribution pie chart, instructors, sections
- Course group chat and 1:1 private chat with image upload (Firebase Storage)
- Chat list pulled from Firebase Realtime Database
- Review submission to backend API (secured with Firebase ID token)
- Profile and Edit Profile screens (local demo state for now)

## Tech Stack

- React Native 0.76, React 18
- Expo SDK 52
- React Navigation 7 (stack + bottom tabs)
- Firebase (modular v11): Auth, Realtime Database, Storage, Firestore (initialized)
- UI helpers: `expo-linear-gradient`, `expo-image-picker`, `expo-av`
- Charts: `react-native-chart-kit`, `react-native-svg`
- Icons: `react-native-vector-icons/Ionicons`

## Project Structure

```
.
├─ index.ts                  # Expo entry, registers App
├─ app.json                  # Expo app config (icons, permissions, fonts)
├─ assets/                   # Images, fonts, splash, video
├─ src/
│  ├─ App.tsx                # Navigation container (stack + tabs)
│  ├─ firebaseConfig.ts      # Firebase initialization (update with your keys)
│  ├─ components/
│  │  └─ BottomNavBar.tsx
│  ├─ screens/
│  │  ├─ HomeScreen/
│  │  ├─ CoursesScreen/
│  │  ├─ CourseDetail/
│  │  ├─ ChatListScreen/
│  │  ├─ CourseChatScreen.tsx
│  │  ├─ PrivateChatScreen.tsx
│  │  ├─ ReviewScreen.tsx
│  │  ├─ ProfileScreen.tsx
│  │  ├─ EditProfileScreen.tsx
│  │  ├─ SignIn/ (SignIn, SignUp flow)
│  │  └─ WelcomeScreen.tsx   # Splash video → SignIn
│  └─ types/
│     └─ navigation.ts       # Route type definitions
```

Note: There is an `app/` directory (Expo Router scaffold), but this app uses React Navigation via `src/App.tsx`.

## Prerequisites

- Node.js 18+ and npm
- Expo CLI (installed via `npx` automatically)
- For Android: Android Studio + emulator or a physical device with Expo Go
- For iOS: Xcode + simulator (macOS) or a physical device with Expo Go

## Getting Started

1) Install dependencies

```bash
npm install
```

2) Configure Firebase

- Create a Firebase project and enable:
  - Authentication (Email/Password)
  - Realtime Database (create a database)
  - Storage (for image uploads)
- Copy your Firebase config and update `src/firebaseConfig.ts`:

```ts
// src/firebaseConfig.ts
const firebaseConfig = {
  apiKey: "<YOUR_API_KEY>",
  authDomain: "<YOUR_PROJECT>.firebaseapp.com",
  databaseURL: "https://<YOUR_PROJECT>-default-rtdb.firebaseio.com",
  projectId: "<YOUR_PROJECT>",
  storageBucket: "<YOUR_PROJECT>.appspot.com",
  messagingSenderId: "<ID>",
  appId: "<APP_ID>",
};
```

3) Backend API

- The app calls a backend at `https://grow-ruddy.vercel.app` for courses, sections, and reviews.
- Endpoints expect a valid Firebase ID token via `Authorization: Bearer <token>`.
- If you host your own backend, update the hardcoded URLs in:
  - `src/screens/CoursesScreen/CoursesScreen.tsx`
  - `src/screens/CourseDetail/CourseDetailsScreen.tsx`
  - `src/screens/ReviewScreen.tsx`

4) Run the app

```bash
# Start Expo
npm run start

# Or launch directly
npm run android
npm run ios
npm run web
```

When the Metro bundler opens, you can scan the QR code in Expo Go (Android/iOS) or press the shortcut to open an emulator/simulator.

## Key Screens and Flows

- SignIn / SignUp: Email/password with Firebase Auth
- Welcome: Plays `assets/start.mp4` then routes to SignIn
- Home: Highlights, simple analytics, links into course details
- Courses: Search and list fetched from backend (requires login)
- Course Details: Grade distribution pie chart, instructors, sections; actions to open Course Chat or write a Review
- Chat List: Pulls available chats from Realtime Database
- Course Chat: Group chat per course (text + image upload to Storage)
- Private Chat: 1:1 chat (text + images)
- Review: Submits a review to the backend with Firebase ID token
- Profile / Edit Profile: Demo profile and local avatar selection

## Configuration Notes

- iOS photo library permission is declared in `app.json`.
- Custom fonts (Nunito) are loaded in `src/App.tsx` and declared in `app.json`.
- If you encounter issues with Reanimated or Gesture Handler, clear caches and restart:

```bash
expo start -c
```

## Scripts

```json
{
  "start": "expo start",
  "android": "expo start --android",
  "ios": "expo start --ios",
  "web": "expo start --web"
}
```

## Troubleshooting

- Ensure you are logged in before accessing courses and reviews (ID token required).
- Verify Firebase Realtime Database rules allow authenticated read/write for development.
- If images do not upload in chat, check Firebase Storage rules and app permissions.

## License

This repository does not declare a license. Add one if you intend to distribute or open-source the project.


