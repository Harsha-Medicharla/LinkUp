# LiveConnect

A real-time collaboration platform that enables developers to connect via WebRTC for seamless video conferencing, screen sharing, and collaborative coding sessions.

![LiveConnect]

## Features

- **Real-time Video Conferencing**: Connect with team members using high-quality WebRTC video and audio
- **Room-based Collaboration**: Create or join rooms with unique IDs for team meetings
- **Simple Interface**: Clean, intuitive UI built with Material UI components
- **Direct Peer-to-Peer Connection**: Secure and low-latency communication with WebRTC
- **Reactive Design**: Responsive interface that works across devices

## Technology Stack

- **Frontend**: React 19 with Material UI
- **Real-time Communication**: WebRTC
- **Signaling**: Firebase Firestore
- **Deployment**: Firebase Hosting

## Prerequisites

Before you begin, ensure you have:

- Node.js (v16 or newer)
- npm or yarn
- A Firebase account with a new project created
- Basic understanding of React and JavaScript

## Setup & Installation

### 1. Clone the repository
```bash
git clone https://github.com/Harsha-Medicharla/LiveConnect.git
cd LiveConnect
```

### 2. Install dependencies
```bash
npm install
```

### 3. Create Firebase Project
1. Go to the [Firebase Console](https://console.firebase.google.com/)
2. Create a new project named "LiveConnect" (or your preferred name)
3. Enable Firestore database
4. Set up Firebase Hosting
5. Get your Firebase configuration values

### 4. Configure Environment Variables
Create a `.env` file in the root directory with the following variables:
```
REACT_APP_API_KEY=your-api-key
REACT_APP_AUTH_DOMAIN=your-project-id.firebaseapp.com
REACT_APP_PROJECT_ID=your-project-id
REACT_APP_STORAGE_BUCKET=your-project-id.appspot.com
REACT_APP_MESSAGING_SENDER_ID=your-sender-id
REACT_APP_APP_ID=your-app-id
REACT_APP_MEASUREMENT_ID=your-measurement-id
```

### 5. Start the development server
```bash
npm start
```

This will launch the application on [http://localhost:3000](http://localhost:3000)

## Usage Guide

### Creating a Room
1. Click "Open camera & microphone" to enable your media devices
2. Click "Create room" to generate a new room with a unique ID
3. Share the displayed room ID with participants

### Joining a Room
1. Click "Open camera & microphone" to enable your media devices
2. Click "Join room"
3. Enter the room ID shared with you
4. Click "Join"

### During a Session
- Both participants will see each other's video feeds
- Your own feed is mirrored and muted to prevent echo
- Click "Hangup" to end the session and clean up resources

# Deploy

## 1️⃣ Install Firebase CLI (If Not Installed)  
```bash
npm install -g firebase-tools
```

## 2️⃣ Login to Firebase  
```bash
firebase login
```

## 3️⃣ Initialize Firebase in Your Project  
Navigate to your React project folder:  
```bash
cd /path/to/your/project
```
Then run:  
```bash
firebase init
```
- **Choose Hosting** (Use arrow keys to select it, then press spacebar to check it)  
- **Select your Firebase project** (Or create a new one)  
- **Set "public" directory to `build`**  
- **Choose "Yes" for single-page app (SPA)**  
- **Choose "No" for automatic builds & deploys via GitHub (optional)**  

## 4️⃣ Build the React App  
Make sure the app is production-ready:  
```bash
npm run build
```

## 5️⃣ Deploy to Firebase  
```bash
firebase deploy
```

🎉 **Your React app is now live on Firebase Hosting!**  


## Development Notes

# WebRTC Overview

WebRTC (Web Real-Time Communication) enables real-time audio, video, and data sharing directly between web browsers and mobile apps.

## WebRTC Connection Flow

Before two peers can communicate, they need to establish a connection.

**Signaling**: Both users connect to a Signaling Server to exchange session information (SDP) required to establish a connection. The signaling process involves exchanging metadata and control messages between the peers to negotiate the session setup.

**NAT Discovery**: Each user communicates with STUN (Session Traversal Utilities for NAT) Servers to discover their public IP addresses and ports which are used to generate their ICE candidates. ICE (Interactive Connectivity Establishment) candidates represent potential communication pathways between peers, including direct connections or relay options.

**Connection Attempts**: ICE candidates are exchanged through the Signaling Server, and peers attempt to establish the most efficient connection possible.

**TURN Relay Fallback**: If direct connection fails due to firewall or NAT restrictions, communication is relayed through TURN (Traversal Using Relays around NAT) Servers, where media is sent from one peer to the TURN server which will forward it to another peer.

**Media Transmission**: Once connected, audio/video/data streams flow directly between peers (or through TURN if direct connection isn't possible).

## Key WebRTC APIs

- **`getUserMedia()`**: Captures audio and video from user's camera and microphone
- **`RTCPeerConnection`**: Manages the peer-to-peer connection, including ICE negotiation
- **`RTCDataChannel`**: Enables bidirectional data exchange between peers
- **`MediaRecorder`**: Records audio and video streams
- **`MediaStream`**: Represents synchronized audio and video tracks 
- **`RTCSessionDescription`**: Contains SDP data describing media session capabilities


## Troubleshooting

### Common Issues

1. **Camera or microphone not working**
   - Check browser permissions
   - Ensure no other application is using your camera/microphone

2. **Cannot connect to a room**
   - Verify the room ID is correct
   - Check that both users have allowed camera/microphone access
   - Ensure your network allows WebRTC connections (some corporate networks block it)

3. **Firebase configuration issues**
   - Double-check all environment variables
   - Ensure Firestore rules allow read/write operations

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
