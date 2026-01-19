# **Laboratory Activity #7 – Web-Controlled IoT System with FastAPI**

## Project Overview
This activity demonstrates a **full-stack IoT system**, combining **web technologies**, **Python backend**, and **Arduino hardware control**.  
Unlike previous labs that relied on direct Serial or Python CLI control, this project allows users to **control LEDs via a web interface**, simulating the architecture behind modern smart home devices.

---

## System Features
- **Web-Based Interface:** Styled HTML page with buttons to toggle **Red, Green, and Blue LEDs**, as well as **All On/All Off** switches.  
- **Python FastAPI Backend:** Receives HTTP requests from the frontend and translates them into Arduino commands.  
- **Instant Hardware Response:** Arduino toggles LEDs connected to pins **5, 6, and 7** in real-time.  
- **Asynchronous Communication:** Web page remains responsive while commands are sent in the background.  

---

## Hardware Setup
- **Arduino Pins:**  
  - Red → Pin 7  
  - Green → Pin 6  
  - Blue → Pin 5  
- **USB Connection:** Arduino connected to the computer running Python FastAPI.  
- **LEDs:** Wired to pins with appropriate resistors.  

---

## How It Works

### **1️⃣ Three-Tier Architecture**
1. **Presentation Layer (Frontend):**  
   - `web.html` displays buttons for LED control.  
   - JavaScript `fetch()` API sends HTTP requests to the backend asynchronously.  

2. **Application Layer (Backend):**  
   - Python FastAPI server receives requests (e.g., `/led/red`) and sends corresponding commands (e.g., `'1'`) to Arduino via Serial port.  
   - Includes **CORS middleware** to allow secure browser-server communication.  

3. **Physical Layer (Hardware):**  
   - Arduino sketch listens on the Serial port.  
   - Switch statement parses incoming characters:
     - `'1'`, `'2'`, `'3'` → toggle individual LEDs  
     - `'9'` / `'0'` → turn all LEDs on/off  

---

### **2️⃣ Modular Code Structure**
- **Frontend (`web.html`):**  
  - Provides responsive UI with **Dark Mode styling**.  
  - Uses JavaScript `fetch()` for asynchronous commands.  

- **Backend (`main.py`):**  
  - FastAPI routes translate HTTP requests into Serial commands.  
  - Automatically connects to Arduino on startup.  

- **Arduino Firmware (`LabAct7.ino` & `Lab_Act7.h`):**  
  - Header file stores **pin definitions and setup logic**.  
  - Main sketch parses Serial input and controls LEDs.  

---

## IoT Concepts Demonstrated
- **REST API:** Standardized endpoints for hardware control over a network.  
- **HTTP Protocol:** Uses GET requests to trigger actions.  
- **Asynchronous JavaScript:** Ensures responsive web interface while communicating with the server.  
- **Middleware Concept:** Python acts as a bridge between high-level web requests and low-level Serial commands.  

---

## Summary
This lab demonstrates a **modern, web-controlled IoT system**, integrating frontend, backend, and hardware layers.  
It teaches **full-stack IoT design**, including **REST APIs, asynchronous web communication**, and **Serial hardware control**, providing a blueprint for real-world smart home and IoT applications.
