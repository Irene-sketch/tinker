<p align="center">
  <img src="./img.png" alt="Project Banner" width="100%">
</p>

# [LUMINA] 🎯

## Basic Details
Lumina is an accessibility-focused web application designed to empower individuals with visual impairments or dyslexia. By leveraging "Edge AI," the app provides real-time auditory feedback, identifying household objects and reading text labels directly through the device's camera.

### Team Name: IRENE

### Team Members
- Member 1: Irene - TKM College of Engineering


### Hosted Project Link
https://lumina-blush-ten.vercel.app/

### Project Description
Lumina is an accessibility-focused web application designed to empower individuals with visual impairments or dyslexia. By leveraging "Edge AI," the app provides real-time auditory feedback, identifying household objects and reading text labels directly through the device's camera.

Our goal is to increase independence in daily tasks—such as identifying grocery items, navigating indoor spaces, or reading medication labels—without requiring expensive specialized hardware.

### The Problem statement
For the 285 million people worldwide with visual impairments and the millions more with severe dyslexia, simple daily tasks are constant hurdles. Identifying the difference between a can of soup and a can of pet food, or reading the dosage on a small medicine bottle, requires sighted assistance that isn't always available. Existing hardware solutions are often expensive, bulky, and have high learning curves, leaving a massive gap in accessible, independent living tools.

### The Solution
Lumina bridges this gap by turning any smartphone into an intelligent, talking pair of eyes. By using "Edge AI"—where the artificial intelligence runs directly in the user's web browser—we provide:

Instant Identification: Real-time object detection that tells the user what is in front of them without lag.

Text-to-Speech Clarity: High-speed OCR that converts printed labels into clear, spoken words.

Extreme Accessibility: A UI designed with high-contrast "Amber-on-Black" colors and massive touch targets, optimized for users with low vision or motor-control challenges.

Privacy & Speed: Because the AI processes images locally, no private camera data is ever sent to the cloud, and the app works even with weak internet connections.

---

## Technical Details

### Technologies/Components Used

**For Software:**
- Languages used: JavaScript (ES6+), HTML5, CSS3
- Frameworks used: React.js (Frontend UI), Vite (Build Tool), Express.js (Backend API)
- Libraries used: * TensorFlow.js: For browser-based machine learning inference.

COCO-SSD: Pre-trained object detection model.

Tesseract.js: For Optical Character Recognition (OCR).

Lucide-React: For accessible, scalable vector icons.

Framer Motion: For smooth, non-distracting UI transitions.

Axios: For communicating between the frontend and the Render backend.
- Tools used: VS Code, Git/GitHub (Version Control), Vercel (Frontend Hosting), Render (Backend Deployment), Chrome DevTools.



## Features

List the key features of your project:
- Feature 1: Real-Time Object Detection – Uses TensorFlow.js to identify 80+ household items (bottles, chairs, laptops) instantly with a high-confidence threshold.
- Feature 2: Advanced OCR (Text-to-Speech) – Integrates Tesseract.js to extract text from labels and medication bottles, converting it to clear audio feedback.
- Feature 3:Accessible "Amber-on-Black" UI – A specialized high-contrast interface designed specifically for users with low vision or light sensitivity.
- Feature 4: Local "Edge AI" Processing – All image recognition happens on the user's device, ensuring lightning-fast response times and total data privacy.

---

## Implementation

### For Software:

#### Installation
```bash
# Install dependencies for the Frontend
cd shelfscan-project/frontend
npm install

# Install dependencies for the Backend
cd ../backend
npm install


#### Run
```bash
# Start the Backend Server (Terminal 1)
cd shelfscan-project/backend
npm start

# Start the Frontend App (Terminal 2)
cd shelfscan-project/frontend
npm run dev


## Project Documentation

### For Software:

#### Screenshots (Add at least 3)

Screenshot1
https://drive.google.com/file/d/1SKuyhXruyIuqney3ao42vdEvCkQQrfhx/view?usp=sharing
-"Landing Page / User Onboarding: The initial interface where users launch the AI system. Designed with high contrast and clear typography to ensure ease of use for visually impaired individuals."


Screenshot2
https://drive.google.com/file/d/1QuccmzMO6l_Ba8zjKBIwBcRZHEu9aIjO/view?usp=sharing
-"AI Vision Interface: This view demonstrates the real-time object detection capabilities of Lumina. Using TensorFlow.js, the system identifies the user ('Person') and provides immediate visual and auditory feedback. The large, high-contrast buttons allow for easy switching between Live Detection and OCR Label Reading modes."


Screenshot3
https://drive.google.com/file/d/1mSUVoFYVLpyaqXt-npnjZr4XeMstvr-W/view?usp=sharing
- Smart Text Recognition (OCR)
Description: This interface demonstrates the Read Label feature powered by Tesseract.js. By capturing a snapshot of physical text—in this case, "TinkerHub"—the app extracts and converts it into a digital format that can be read aloud. This feature is essential for tasks like identifying medicine dosages, reading food labels, or navigating indoor signage.

#### Diagrams

**System Architecture:**

Architecture diagram:
graph LR
    User((User)) -->|Camera Stream| React[React Frontend - Vercel]
    subgraph Browser_Intelligence
        React --> TF[TensorFlow.js - Object Detection]
        React --> Tess[Tesseract.js - OCR]
    end
    TF --> Voice[Web Speech API - Audio]
    Tess --> Voice
    TF -->|Metadata| API[Node.js API - Render]
    API --> DB[(JSON/Database)]

Explanation:

Lumina follows a Client-Side AI (Edge Computing) architecture. This approach ensures that the application remains fast and private.

The Frontend (Vite + React): Acts as the primary engine. It captures the camera stream and passes it through the TensorFlow.js and Tesseract.js libraries for local inference.

Data Flow: Unlike traditional apps, the "heavy lifting" (image processing) stays on the user's phone. Only the metadata—the name of the object identified and the timestamp—is sent to the backend.

Tech Stack Interaction: React manages the UI state; Tailwind CSS provides the high-contrast accessibility layer; and the Web Speech API translates AI results into audio. The backend (Node.js/Express) serves as a persistent record-keeper.



**Application Workflow:**

Diagram:
sequenceDiagram
    autonumber
    actor User
    participant Browser as React Frontend (Vite)
    participant AI as Local AI (TF.js / Tesseract)
    participant Voice as Web Speech API
    participant Server as Node.js Backend (Render)

    User->>Browser: Opens App & Clicks "Launch System"
    Browser->>User: Request Camera Permission
    User-->>Browser: Permission Granted
    
    loop Real-time Detection
        Browser->>AI: Send Video Frame
        AI->>AI: Analyze Image
        Note over AI: Confidence > 70%
        AI-->>Browser: Return Object Label ("Bottle")
        Browser->>Voice: Trigger Text-to-Speech
        Voice-->>User: [Audio] "Bottle"
        Browser->>Server: POST /api/scans { item: "Bottle" }
    end
---

The Lumina workflow is a 4-step cycle designed for real-time accessibility. First, the User initializes the system by granting camera permissions. The Frontend then enters a high-speed loop, capturing frames and passing them to the local AI Engines (TensorFlow.js/Tesseract.js). When an object is identified with high confidence, the app triggers the Web Speech API for immediate audio feedback. Simultaneously, the detection metadata is sent via an asynchronous POST request to the Node.js Backend to update the user's scan history.



## Additional Documentation

### For Web Projects with Backend:

#### API Documentation

**Base URL:** https://lumina-yx5m.onrender.com

##### Endpoints

GET /api/scans

Description: Retrieves the chronological history of all objects and text identified by the AI. This is used to populate the "History" tab in the app.

Parameters:

limit (integer): Optional - Number of recent scans to return (default: 20).

Response:
{
  "status": "success",
  "count": 2,
  "data": [
    {
      "id": "65df...123",
      "label": "Bottle",
      "type": "object",
      "timestamp": "2026-02-28T09:45:00Z"
    },
    {
      "id": "65df...124",
      "label": "TINKERHUB",
      "type": "text",
      "timestamp": "2026-02-28T09:40:00Z"
    }
  ]
}

POST /api/scans

Description: Saves a newly identified object or text snippet to the database after a successful AI inference.

Request Body:
{
  "label": "Person",
  "type": "object",
  "confidence": 0.94
}
Response:
{
  "status": "success",
  "message": "Scan saved successfully",
  "insertedId": "65df...125"
}

DELETE /api/scans/:id

Description: Removes a specific entry from the user's scan history.

Parameters:

id (string): The unique ID of the scan record.

Response:
{
  "status": "success",
  "message": "Record deleted"
}




Installation & Run Guide
For Users (Mobile/PWA):
Lumina is a Progressive Web App. You don't need to download an APK or use a terminal to run it.

Visit the Live Site: https://lumina-sight.vercel.app (Replace with your actual link).

Add to Home Screen: - Android: Tap the three dots (⋮) in Chrome and select "Install App".

iOS: Tap the "Share" icon in Safari and select "Add to Home Screen".

For Developers (Running Locally):
If you want to run the source code on your own machine:
1. Clone the Repository:
git clone https://github.com/your-username/lumina-sight.git
cd lumina-sight

2. Setup the Backend:
cd backend
npm install
npm start

3. Setup the Frontend:
cd ../frontend
npm install
npm run dev








#### Demo Output


Demo Interaction Output
This section demonstrates how the Lumina AI processes real-world visual data and translates it into accessible output for the user.

Scenario 1: Environmental Navigation (Vision Mode)
Input: The user points the camera towards a living room area containing a chair and a laptop.

Process:

Model Inference: TensorFlow.js identifies objects in the video stream.

Threshold Check: Objects identified with >70% confidence are selected.

Speech Synthesis: The app triggers the Web Speech API.

Output:

Visual: Amber bounding boxes appear around the detected objects.

Audio: "Chair detected (92%). Laptop detected (85%)."

System Log: POST /api/scans sent to record the detection.

Scenario 2: Reading a Label (OCR Mode)
Input: A physical object with text, such as a "TinkerHub" sticker or a medicine bottle.

Process:

Image Capture: User taps the "Read Label" button.

Preprocessing: The app converts the frame to grayscale for better Tesseract accuracy.

OCR Extraction: Tesseract.js parses the image into a string.

Output:

Visual: The extracted text is displayed in large, bold font on the screen.

Audio: "Text identified: TINKERHUB"

Status: Success - Scan saved to history.



## Project Demo

### Video
Lumina is an accessibility-focused web application designed to empower individuals with visual impairments or dyslexia. By leveraging "Edge AI," the app provides real-time auditory feedback, identifying household objects and reading text labels directly through the device's camera.
https://drive.google.com/file/d/1qSzCz1Y1YZ0CHHA5eUqlwfeISaExDopL/view?usp=sharing



## AI Tools Used (Optional - For Transparency Bonus)

Tool Used: Gemini 3 Flash (Google), ChatGPT (OpenAI), Copilot(agent)

Purpose:

Architectural Planning: Designing the data flow between the local AI engines (TensorFlow/Tesseract) and the remote Node.js backend.

Documentation & Diagrams: Generating Mermaid.js code for system architecture, application workflows, and accessibility-focused documentation.

Debugging: Resolving integration issues between the Web Speech API and the React state lifecycle.

UI/UX Refinement: Guidance on high-contrast color palettes and accessible typography for visually impaired users.

Key Prompts Used:
"Design a system architecture where TensorFlow.js runs in the browser but syncs metadata to a Node.js backend."

"Generate a Mermaid sequence diagram for a mobile app identifying an object and speaking the result."

"Write API documentation for a POST endpoint that saves scan history with labels and timestamps."

"Explain the difference between a CLI tool and a Mobile Web App for a project documentation template."

Percentage of AI-generated code: Approximately 35%
(Most of the AI assistance was focused on boilerplate structure, configuration, and documentation, while the core logic and integration remained human-led.)

Human Contributions:
Core AI Integration: Manually tuning the confidence thresholds and frame-rate optimization for the camera feed.

Accessibility Implementation: Selecting specific high-contrast color values (Amber/Black) based on accessibility standards.

Backend Infrastructure: Setting up the Render server and connecting it to the database.

System Testing: Real-world testing of the object detection loop on physical household items to ensure accuracy.



## Team Contributions
- Irene Treessa Raj: sole contributor.



## License
This project is licensed under the MIT License


Made with ❤️ at TinkerHub
