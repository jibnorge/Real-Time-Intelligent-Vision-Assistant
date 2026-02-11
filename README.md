# RIVA: Real-time Intelligent Vision Assistant 


**RIVA** is an innovative AI-powered assistant designed to empower individuals with visual impairments by providing real-time audio descriptions of their surroundings. Originally conceptualized for the <a href=https://www.stclaircollege.ca/ford-innovation-showcase/2024-gallery target="_blank">**Ford Innovation Showcase 2024**</a>, RIVA secured a **Top 10** position, highlighting the power of accessible AI technology.

The system uses a proposed wearable camera (envisioned as a locket-style device) to capture the environment continuously. Through a chain of open-source AI models, it transcribes user voice commands, interprets visual scenes, refines descriptions, and speaks helpful information back to the user — all in near real-time.

## Features

- Voice-activated interaction (ask questions like "What's in front of me?" or "Describe the room")
- Real-time scene understanding and detailed audio descriptions
- Object detection, spatial grounding, and natural language scene narration
- Fully built with **open-source** pre-trained models from Hugging Face
- Modular pipeline — easy to swap or upgrade individual components
- Designed with accessibility and independence in mind

## Achievement

Top 10 finalist in the <a href=https://www.stclaircollege.ca/ford-innovation-showcase/2024-gallery target="_blank">**Ford Innovation Showcase 2024**</a> — celebrating transformative AI for accessibility.

## How It Works

RIVA processes input in a sequential multimodal pipeline:

```mermaid
flowchart TD
    A[User speaks command e.g. What's in front of me?] --> B[Microphone captures audio]
    B --> C[Speech-to-Text: Whisper large-v3]
    C --> D{General scene or specific question?}
    
    D -->|General| E[Default prompt: Describe image in detail]
    D -->|Specific| F[Use user's question as prompt]
    
    E --> G
    F --> G

    subgraph Camera Input
    Cam[Wearable camera captures frame] --> Img[Image]
    end

    Img --> G[Vision-Language Model: Kosmos-2 → grounded description]

    G --> Raw[Raw output: objects + locations]
    Raw --> Post[Post-processing: clean & condense]
    Post --> Final[Final natural description]
    
    Final --> TTS[Text-to-Speech: Parler-TTS]
    TTS --> Speak[Audio spoken to user]

    %% Dark-mode friendly colors
    style A fill:#1a1a40,stroke:#00D4FF,stroke-width:2px,color:#E0E0FF
    style B fill:#0d1a26,stroke:#A0A0FF,color:#E0E0FF
    style C fill:#0d1a26,stroke:#00D4FF,color:#E0E0FF
    style D fill:#2a1a40,stroke:#FF6BDB,stroke-width:3px,color:#FFFFFF
    style E fill:#1a2a40,stroke:#00FF9D,color:#E0E0FF
    style F fill:#1a2a40,stroke:#00FF9D,color:#E0E0FF
    style G fill:#2a1a2a,stroke:#C68CFF,stroke-width:3px,color:#FFFFFF
    style Cam fill:#0f1a2a,stroke:#FFAA00,color:#E0E0FF
    style Speak fill:#0d2a1a,stroke:#00FF9D,stroke-width:3px,color:#FFFFFF
```


## Model Results & Demonstrations

Here are real-world examples of how **RIVA** performs in practical scenarios. The system listens to voice commands, processes the visual input using Kosmos-2 for grounded understanding, refines the description, and speaks back clearly and helpfully.

### 1. General Environment Description
**User prompt:** "Hey RIVA! Describe the environment."

This shows RIVA providing a natural, detailed spoken description of the surroundings (e.g., room layout, objects, people, etc.).

![alt text](images/test_1.png)

**RIVA's spoken output (transcribed):**  
"The environment features a large open space with two students sitting on the steps of a staircase. One student is sitting on the left side of the stairs, while the other is on the right side. They are both working, with one student holding a book and the other holding a laptop. There are multiple chairs scattered around the space, with some placed near the stairs and others further away. In the background, there is a TV mounted on the wall, on the far left side."

**Full video demo:**
videos/Video 1.mp4

### 2. Safety-Critical Query: Road Crossing Assistance
**User prompt:** "Hey RIVA! Can I cross the road now?"

This demonstrates RIVA's ability to interpret safety-related questions, detect relevant elements (vehicles, traffic lights, pedestrians, road conditions), and give a cautious, actionable spoken response.

![alt text](images/test_2.png)

**RIVA's spoken output (transcribed):**  
"No, the traffic light is red, which means you should wait for now. Do you want me to tell you once it becomes green?"

**Full video demo:**
videos/Video 2.mp4

### 3. Object Detection on Canadian Banknotes
RIVA can also identify and describe specific objects like Canadian currency — useful for tasks such as shopping assistance, bill verification, or finding dropped money.

Below is an example of object detection results (bounding boxes + labels) on various Canadian notes ($5, $10, $20, etc.):

![Object Detection on Canadian Banknotes](runs/detect/predict4/test.jpg)

These demos highlight RIVA's multimodal capabilities: combining speech understanding, real-time vision, and natural audio feedback to support independence for people with visual impairments.