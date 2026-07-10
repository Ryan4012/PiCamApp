# Mobile Surveillance & Control System (Swift + Raspberry Pi)

## Overview
This project is a mobile-controlled surveillance and motion-detection system built using a Swift iOS app and a Raspberry Pi 5 backend. The Raspberry Pi hosts a Python Flask application that runs continuously and provides authenticated API endpoints for camera control, servo movement, and motion detection.

The system integrates hardware sensors and peripherals—including a USB camera, MG90S servo, and LD1020 radar sensor—allowing real-time video streaming and physical device control from a mobile device. Secure remote access is enabled using a Tailscale VPN mesh.

This project was built primarily for learning, experimentation, and real-world embedded systems experience, combining mobile development, backend services, networking, and hardware control.

## Motivation & Goals
**Why This Project**

I wanted to gain hands-on experience building a full-stack system that bridges mobile development and physical hardware. This project allowed me to explore real-time communication, device control, and secure remote access in a practical, production-like environment.

**Goals**
- Learn Swift and iOS app development using Xcode
- Build a persistent backend service using Python and Flask
- Integrate hardware peripherals with software control
- Implement secure authentication between mobile and backend services
- Stream live video over the network with low latency
- Design a system that works remotely via VPN

# App Images
<table>
  <tr>
    <th>VPN Check</th>
    <th>Home Page</th>
    <th>Camera Page</th>
    
  </tr>
  <tr>
    <td><img src="./App Images/AppStartUpPrompt.png" alt="Architecture Diagram" width="200" /></td>
    <td><img src="./App Images/AppHomePage.png" alt="Network Diagram" width="200" /></td>
    <td><img src="./App Images/AppCameraPage.png" alt="Network Diagram" width="200" /></td>
  </tr>

  <th>Motion Log</th>
  <th>Stats Loading</th>
  <th>Stats Page</th>

  <tr>
    <td><img src="./App Images/AppMotionLogSection.png" alt="Network Diagram" width="200" /></td>
    <td><img src="./App Images/AppStatsLoading.png" alt="Network Diagram" width="200" /></td>
    <td><img src="./App Images/AppStatsPage.png" alt="Network Diagram" width="200" /></td>
  </tr>
  
</table>

# Technology Stack
**Hardware** -
- Raspberry Pi 5
- USB Camera
- MG90S Servo Motor
- LD1020 Radar Motion Sensor

**Mobile Application** - 
- Swift
- Xcode
- iOS
- Backend
- Python
- Flask (REST API)
- Shell scripts (.sh) for stream control

**Video Streaming** - 
- MJPEG video stream
- USB camera interface

**Networking & Security** -
- Tailscale VPN
- Token-based authentication between Swift app and Flask backend

## Architecture Overview
**High-Level Architecture**
- The Raspberry Pi runs a Flask server 24/7, exposing authenticated API endpoints
- The Swift iOS app communicates with the Flask backend over HTTPS via Tailscale
- Hardware components (camera, servo, radar sensor) are controlled by backend functions
- MJPEG provides a live video feed to the mobile app
- Shell scripts are used to start and stop video streaming services

**Component Breakdown**
- Swift App: User interface, authentication, control commands, video display
- Flask API: Central control layer for hardware and streaming
- Shell Scripts: Start/stop MJPEG video streams
- Hardware Layer: Camera capture, servo positioning, motion detection

## Networking Overview
**Network Flow**
- Raspberry Pi and iPhone are connected via Tailscale VPN
- The Flask backend is only accessible within the VPN
- Video stream and API requests are routed securely over the mesh
- No direct public internet exposure is required

**Benefits**
- Secure remote access
- No port forwarding
- Encrypted device-to-device communication

## Services & Functionality
Component	Purpose	Deployment
Flask App	Backend API and hardware control	Raspberry Pi
MJPEG Stream	Live camera feed	Raspberry Pi
Shell Scripts	Control video stream lifecycle	Raspberry Pi
Swift App	Mobile UI and controls	iPhone
Tailscale	Secure networking	Pi & Phone

## Services & Functionality

| Component       | Purpose                               | Deployment        |
|-----------------|---------------------------------------|-------------------|
| Flask App       | Backend API and hardware control       | Raspberry Pi      |
| MJPEG Stream    | Live camera feed                       | Raspberry Pi      |
| Shell Scripts   | Control video stream lifecycle         | Raspberry Pi      |
| Swift App       | Mobile UI and controls                 | iPhone            |
| Tailscale       | Secure networking                      | Pi & iPhone       |


## Security Considerations
- Authentication: Shared authentication logic between Swift app and Flask backend
- Network Isolation: Backend accessible only via Tailscale VPN
- API Protection: Auth checks on all control endpoints
- Service Hardening: Flask app runs continuously with limited exposed services

## Setup & Deployment
1. Raspberry Pi boots and starts Flask backend as a persistent service
2. Flask app initializes hardware interfaces and API routes
3. MJPEG streaming is controlled via shell scripts
4. Swift app authenticates and communicates with Flask API
5. User can view live video and control hardware remotely

## What I Learned
- Swift UI development and mobile networking
- REST API design using Flask
- Secure authentication between mobile and backend services
- Hardware integration with Python
- Real-time video streaming using MJPEG
- Remote access using VPN-based networking

## Challenges & Lessons Learned
- Managing real-time video streaming latency
- Coordinating hardware control with backend API calls
- Ensuring secure communication between mobile and backend
- Debugging hardware behavior remotely
- Designing a backend that runs reliably 24/7
