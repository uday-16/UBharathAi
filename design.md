# System Design Document: OXCITIZEN (UBharatAIConnect)

## 1. High-Level Architecture
The system follows a typical mobile client-server architecture, heavily relying on **Firebase** for backend services to ensure real-time capabilities and ease of scaling.

### **Architecture Diagram (Conceptual)**
```mermaid
graph TD
    User((User)) -->|Voice/Touch| WebApp[Web App (React+Vite)]
    WebApp -->|AI Processing| Gemini[Google Gemini AI]
    WebApp -->|Routing| ReactRouter[React Router]
    WebApp -->|Styling| Tailwind[Tailwind CSS]
```

## 2. Frontend Architecture (Web App)
The frontend is built using **React** with **Vite** and **TypeScript** for high performance and strict type safety.

### **Directory Structure Strategy**
- **`src/screens`**: Page components (Home, Health, Education, Community).
- **`src/components`**: Reusable UI atoms (Buttons, Cards, VoiceInput) and molecules (forms).
- **`src/services`**: AI integration and API services.
- **`src/context`**: Global state (Theme, Auth, Language).
- **`src/hooks`**: Custom hooks for logic reuse.

### **Key Components**
1.  **AppRouter**: Handles navigation between public and protected routes.
2.  **AIAssistant**: A global floating component that provides context-aware help.
3.  **CommunityCard**: Specialized component for displaying local resources/jobs.
4.  **LanguageSwitcher**: Global accessible control for language preference.

## 3. Data Design (Firestore Schema)

### **Collections**
- **`users`**
    - `uid`: string (Primary Key)
    - `phoneNumber`: string
    - `language_preference`: 'en' | 'hi'
    - `location`: GeoPoint

- **`services`** (Catalog of available services)
    - `id`: string
    - `category`: 'health' | 'education' | 'jobs' | ...
    - `title`: string
    - `description`: string
    - `external_link`: string

- **`user_logs`**
    - `userId`: string
    - `activity`: string
    - `timestamp`: timestamp

## 4. Integration Design

### **Authentication**
- **Provider**: Firebase Auth (Phone Number Provider).
- **Flow**: User enters phone -> OTP sent -> Auto-verify/Enter OTP -> Authenticated.

### **AI Integration (Gemini)**
- **Input**: Text or Transcribed Voice.
- **Processing**: Send prompt to Gemini API with context (User location, language).
- **Output**: Structured JSON or markdown response rendered by the UI.

### **External APIs**
- **Location**: Browser Geolocation API.
- **Synthesis**: Web Speech API for Text-to-Speech (TTS).
- **Recognition**: Web Speech API for Speech-to-Text (STT).

## 5. UI/UX Guidelines - "Beautiful & Best"
- **Aesthetic**: Premium "Digital India" - Clean, modern, trustworthy.
- **Colors**:
    - **Primary**: Deep Saffron (#FF9933) - Vibrancy & Energy.
    - **Secondary**: India Green (#138808) - Growth & Agriculture.
    - **Accent**: Chakra Blue (#000080) - Truth & Trust.
    - **Background**: Soft Off-White / Light Gray for readability.
- **Typography**: `Inter` or `Hind` for multi-language legibility.
- **Interactions**:
    - **Voice**: Pulsing animations for active listening.
    - **Hover**: Subtle lift and shadow (Glassmorphism).
    - **Transitions**: Smooth fade-ins using CSS transitions or Framer Motion (if added).
- **Accessibility**:
    - **Contrast**: WCAG AA compliant.
    - **Touch Targets**: Min 44px for easy tapping on low-end devices.
