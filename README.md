
# RAT Project

![RAT Project](https://img.shields.io/badge/license-MIT-blue.svg)
![CI](https://github.com/your-username/rat-project/workflows/CI%20Pipeline/badge.svg)
![GitHub stars](https://img.shields.io/github/stars/your-username/rat-project)
![GitHub forks](https://img.shields.io/github/forks/your-username/rat-project)

A **platform-independent Remote Access Tool (RAT)** for educational purposes, designed to run on **Windows**, **Linux**, **Android**, and **iOS**. This project demonstrates advanced remote control features with a modern tech stack, ensuring security, modularity, and ease of use.

> **⚠️ Warning**: This project is for **educational purposes only**. Use it only on devices you own or have explicit permission to access. Unauthorized use is illegal and unethical.

## Features
- **Shell Command Execution**: Run commands remotely on the target device.
- **Application-Based Keylogger**: Capture keystrokes and passwords, tied to specific applications.
- **Camera**: Live streaming and snapshot capture.
- **Screen Streaming**: Real-time screen monitoring across devices (WebRTC).
- **Location Tracking**: GPS or IP-based geolocation.
- **Microphone Recording**: Capture audio from the target device.
- **File Management**: List, upload, and download files.
- **Cross-Platform GUI**: Built with React Native for mobile and desktop.
- **Security**: HTTPS, JWT authentication, and comprehensive logging.

## Tech Stack
- **Server**: Node.js, WebSocket, HTTPS
- **Client**: React Native, WebRTC
- **Keylogger**: C++ (node-keylogger for performance)
- **Dependencies**: opencv4nodejs, react-native-webrtc, jsonwebtoken, and more
- **CI/CD**: GitHub Actions

## Installation

### Prerequisites
- **Node.js**: v18 or higher ([Download](https://nodejs.org))
- **React Native**: For mobile GUI ([Setup Guide](https://reactnative.dev/docs/environment-setup))
- **OpenSSL**: For SSL certificates
- **FFmpeg**: For video streaming ([Download](https://ffmpeg.org))
- **Android**:
  - Android Studio, Java SDK
  - Optional: Termux for server
- **iOS**:
  - Xcode, CocoaPods
  - Optional: Pythonista for server
- **C++ Compiler**: For node-keylogger (e.g., g++)

### Dependencies
```bash
npm install ws express https jsonwebtoken socket.io opencv4nodejs node-keylogger react-native-webrtc react-native-camera react-native-geolocation-service react-native-fs
```

### Steps
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/rat-project.git
   cd rat-project
   ```

2. **Generate SSL Certificates**:
   ```bash
   openssl req -x509 -newkey rsa:2048 -keyout certs/server.key -out certs/server.crt -days 365 -nodes
   ```

3. **Install Server Dependencies**:
   ```bash
   cd server
   npm install
   ```

4. **Install Client Dependencies**:
   ```bash
   cd client
   npm install
   ```

5. **Configure Environment**:
   - Edit `config/config.js`:
     - `SERVER_HOST`: Your server IP (e.g., `192.168.1.100`).
     - `SERVER_PORT`: Default is 9999.
     - `JWT_SECRET`: Set a strong secret key.
   - For production, use environment variables:
     ```bash
     export SERVER_HOST=your.ip.address
     export JWT_SECRET=your_secret_key
     ```

6. **Setup Mobile Environment**:
   - **Android**:
     ```bash
     npx react-native run-android
     ```
     - Ensure Android Studio is configured with an emulator or physical device.
   - **iOS**:
     ```bash
     cd client/ios
     pod install
     npx react-native run-ios
     ```

## Usage
1. **Start the Server**:
   ```bash
   cd server
   node src/server.js
   ```
   - Server runs at `https://<SERVER_HOST>:9999`.

2. **Start the Client**:
   - **Mobile**:
     ```bash
     cd client
     npx react-native run-android  # or run-ios
     ```
   - **Desktop (Browser)**:
     ```bash
     cd client
     npx serve
     ```
     - Access at `http://localhost:3000`.

3. **Interact via GUI**:
   - Execute shell commands.
   - Start/stop keylogger, view logs (including application-specific passwords).
   - Capture photos or stream camera.
   - Monitor screen in real-time.
   - Record audio, manage files, or track location.

## Permissions
- **Android**:
  - Camera: `CAMERA`
  - Microphone: `RECORD_AUDIO`
  - Location: `ACCESS_FINE_LOCATION`
  - Storage: `READ_EXTERNAL_STORAGE`, `WRITE_EXTERNAL_STORAGE`
  - Add to `client/android/app/src/main/AndroidManifest.xml`:
    ```xml
    <uses-permission android:name="android.permission.CAMERA" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    ```

- **i personally don't know what to do with this information. I'm going to assume you're a developer and you know what you're doing. If you need help with this, please let me know!**:
  - Camera: `NSCameraUsageDescription`
  - Microphone: `NSMicrophoneUsageDescription`
  - Location: `NSLocationWhenInUseUsageDescription`
  - Add to `client/ios/ratclient/Info.plist`:
    ```xml
    <key>NSCameraUsageDescription</key>
    <string>Camera access for photo and streaming</string>
    <key>NSMicrophoneUsageDescription</key>
    <string>Microphone access for audio recording</string>
    <key>NSLocationWhenInUseUsageDescription</key>
    <string>Location access for tracking</string>
    ```

## Troubleshooting
- **Server Not Connecting**:
  - Verify `SERVER_HOST` and `SERVER_PORT` in `config.js`.
  - Open port 9999 in firewall:
    ```bash
    sudo ufw allow 9999
    ```
- **Camera/Screen Streaming Issues**:
  - Ensure camera permissions are granted.
  - Verify FFmpeg installation.
- **Keylogger Not Capturing**:
  - Check `node-keylogger` installation and OS permissions.
  - Run server with elevated privileges if needed:
    ```bash
    sudo node src/server.js
    ```
- **Mobile Build Errors**:
  - Ensure Android Studio/Xcode is correctly configured.
  - Clear React Native cache:
    ```bash
    cd client
    npx react-native start --reset-cache
    ```

## Security
- **HTTPS**: All communications are encrypted.
- **JWT Authentication**: Connections require valid tokens.
- **Logging**: All actions are logged in `logs/` directory.
- **Ethical Use**: Use only on authorized devices with explicit consent.

## Contributing
We welcome contributions! See [CONTRIBUTING.md](.github/CONTRIBUTING.md) for details.

## Architecture
For a detailed overview, see [ARCHITECTURE.md](docs/ARCHITECTURE.md).

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Contact
- Email: [email@example.com](mailto:email@example.com)
- GitHub Issues: [Open an Issue](https://github.com/your-username/rat-project/issues)

## Acknowledgments
- Built for educational purposes under teacher guidance.
- Inspired by open-source remote access tools.

**Happy Hacking! 🚀**
```

#### docs/ARCHITECTURE.md
Proje mimarisi.
```markdown
# Architecture

## Overview
The RAT Project is a client-server application designed for remote device control. It uses a modular architecture to ensure scalability, maintainability, and cross-platform compatibility.

## Components
1. **Server**:
   - **Tech**: Node.js, WebSocket, HTTPS
   - **Role**: Handles client requests, executes commands, and streams data (camera, screen).
   - **Modules**:
     - Keylogger: Captures keystrokes with application context.
     - Camera: Manages photo capture and streaming.
     - Screen: Streams desktop/mobile screen via WebRTC.
     - Location: Retrieves GPS/IP-based coordinates.
     - Microphone: Records audio.
     - File: Manages file operations.

2. **Client**:
   - **Tech**: React Native, WebSocket
   - **Role**: Provides a user-friendly GUI for interacting with the server.
   - **Features**: Command execution, real-time streaming, log visualization.

3. **Communication**:
   - **Protocol**: WebSocket over HTTPS
   - **Security**: JWT for authentication, SSL/TLS for encryption.

## Data Flow
1. Client authenticates with JWT and connects to the server via WebSocket.
2. Client sends commands (e.g., `keylog_start`, `camera_photo`).
3. Server processes requests using appropriate modules.
4. Server streams data (e.g., screen frames, keylogs) back to the client.
5. Client renders data in the GUI.

## Scalability
- **Modular Design**: New features can be added as server modules.
- **WebSocket**: Low-latency, real-time communication.
- **Cross-Platform**: Supports multiple OS via React Native and Node.js.

## Security Considerations
- HTTPS and JWT ensure secure communication.
- Logs track all actions for auditing.
- Permissions are explicitly required for sensitive operations (camera, microphone).

## Future Improvements
- Add peer-to-peer streaming for lower latency.
- Implement persistent storage for logs and recordings.
- Enhance mobile screen streaming with native APIs.
```
