# Cheating Daddy Documentation

This document provides a comprehensive overview of the Cheating Daddy application, its architecture, and its core functionalities. It is intended for developers who want to understand, maintain, or extend the project.

## 1. Project Overview

Cheating Daddy is a real-time AI assistant that provides contextual help during video calls, interviews, presentations, and meetings. It uses screen capture and audio analysis to understand the context of the conversation and provides relevant information and suggestions to the user through a transparent, always-on-top overlay. The AI is powered by Google's Gemini API.

### 1.1. Core Features

-   **Live AI Assistance**: Real-time help powered by Google Gemini 2.0 Flash Live.
-   **Screen & Audio Capture**: Analyzes what the user sees and hears to provide contextual responses.
-   **Multiple Profiles**: Offers different AI personas for various scenarios, such as interviews, sales calls, and exams.
-   **Transparent Overlay**: An always-on-top window that can be positioned anywhere on the screen.
-   **Click-through Mode**: Allows the user to interact with applications behind the overlay.
-   **Cross-platform**: Works on macOS, Windows, and Linux.
-   **Stealth Features**: Includes measures to avoid detection by screen recording and proctoring software.

## 2. Architecture

The application is built with Electron, allowing for the creation of a cross-platform desktop application using web technologies. The frontend is built with LitElement, a simple and lightweight library for creating web components.

### 2.1. Main Process (`src/index.js`)

The main process is the entry point of the application. It is responsible for:

-   Creating and managing the main browser window (`BrowserWindow`).
-   Handling application lifecycle events (e.g., `whenReady`, `window-all-closed`).
-   Setting up IPC (Inter-Process Communication) handlers to communicate with the renderer process.
-   Initializing stealth features and random process names.
-   Managing the Gemini API session.

### 2.2. Renderer Process (`src/utils/renderer.js` and UI Components)

The renderer process is responsible for rendering the user interface. It is composed of:

-   **`src/index.html`**: The main HTML file that loads the UI components.
-   **`src/components/app/CheatingDaddyApp.js`**: The root LitElement component that manages the application's state and views.
-   **UI Views (`src/components/views/`)**: A collection of LitElement components that represent the different screens of the application (e.g., `MainView`, `AssistantView`, `CustomizeView`).
-   **`src/utils/renderer.js`**: A script that acts as a bridge between the UI components and the main process. It exposes a global `cheddar` object that provides a unified API for interacting with the application's core functionalities.

### 2.3. Communication (IPC)

The main and renderer processes communicate using Electron's IPC modules (`ipcMain` and `ipcRenderer`). This allows the UI to request actions from the main process (e.g., start a Gemini session, capture the screen) and the main process to send updates to the UI (e.g., new AI responses, status changes).

## 3. Core Functionalities

### 3.1. Gemini API Integration (`src/utils/gemini.js`)

This is the core of the AI functionality. It handles:

-   **Session Management**: Initializes and manages the connection to the Gemini API.
-   **Audio Processing**: Processes audio from the system and microphone, converts it to a suitable format, and sends it to the Gemini API for transcription.
-   **Image Processing**: Captures screenshots, converts them to base64, and sends them to the Gemini API for analysis.
-   **Prompt Engineering**: Constructs system prompts based on the selected profile and user-defined custom instructions.
-   **Reconnection Logic**: Implements a reconnection mechanism to handle interruptions in the connection to the Gemini API.

### 3.2. Audio Capture (`src/audioUtils.js`)

The application captures audio from different sources depending on the operating system:

-   **macOS**: Uses a custom command-line tool (`SystemAudioDump`) to capture system audio.
-   **Windows**: Uses the `getDisplayMedia` API with loopback audio to capture system audio.
-   **Linux**: Attempts to capture system audio via `getDisplayMedia` and falls back to microphone input.

The captured audio is then processed and sent to the Gemini API for transcription and analysis.

### 3.3. Screen Capture

The application uses the `getDisplayMedia` API to capture the screen. Screenshots are taken at a configurable interval or manually by the user. The captured images are then sent to the Gemini API to provide visual context for the AI's responses.

### 3.4. Stealth Features (`src/utils/stealthFeatures.js`)

To avoid detection, the application implements several stealth features:

-   **Hiding from Taskbar and Mission Control**: The application window is hidden from the Windows taskbar and macOS Mission Control.
-   **Randomized Window Title and Process Name**: The window title and process name are randomized to make the application less identifiable.
-   **Content Protection**: The application attempts to prevent screenshots and screen recordings of its window.
-   **Randomized User Agent**: The user agent of the browser window is randomized.

### 3.5. User Interface (`src/components/`)

The UI is built with LitElement and is composed of several components:

-   **`CheatingDaddyApp.js`**: The main application component that manages the views and state.
-   **`AppHeader.js`**: The header component that displays the application's status and provides navigation controls.
-   **Views**: Each view corresponds to a different screen of the application, such as the main view for starting a session, the assistant view for displaying AI responses, and the customize view for configuring settings.

## 4. Configuration (`src/config.js`)

The application's configuration is managed through a JSON file. The `config.js` file provides functions for reading and writing the configuration, which includes settings such as whether the user has completed the onboarding process, the selected stealth level, and the layout mode.

## 5. How to Contribute

To contribute to the development of Cheating Daddy, please follow these steps:

1.  **Fork the repository.**
2.  **Create a new branch for your feature or bug fix.**
3.  **Make your changes and ensure that the code follows the project's coding style and conventions.**
4.  **Test your changes thoroughly.**
5.  **Submit a pull request with a clear description of your changes.**
