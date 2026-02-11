# RIVA: Real-time Intelligent Vision Assistant

![RIVA Logo](https://via.placeholder.com/800x400.png?text=RIVA+-+Real-time+Intelligent+Vision+Assistant)  


**RIVA** is an innovative AI-powered assistant designed to empower individuals with visual impairments by providing real-time audio descriptions of their surroundings. Originally conceptualized for the **Ford Innovation Showcase 2024**, RIVA secured a **Top 10** position, highlighting the power of accessible AI technology.

The system uses a proposed wearable camera (envisioned as a locket-style device) to capture the environment continuously. Through a chain of open-source AI models, it transcribes user voice commands, interprets visual scenes, refines descriptions, and speaks helpful information back to the user — all in near real-time.

## ✨ Features

- Voice-activated interaction (ask questions like "What's in front of me?" or "Describe the room")
- Real-time scene understanding and detailed audio descriptions
- Object detection, spatial grounding, and natural language scene narration
- Fully built with **open-source** pre-trained models from Hugging Face
- Modular pipeline — easy to swap or upgrade individual components
- Designed with accessibility and independence in mind

## 🏆 Achievement

Top 10 finalist in the **Ford Innovation Showcase 2024** — celebrating transformative AI for accessibility.

## How It Works

RIVA processes input in a sequential multimodal pipeline:

```mermaid
flowchart TD
    A[User speaks command\n(e.g. 'Describe what you see')] --> B[Microphone captures audio]
    B --> C[Speech-to-Text\n(Whisper large-v3)]
    C --> D[Generate prompt\n(e.g. 'Describe this image in detail')]
    D --> E[Camera captures image]
    E --> F[Vision-Language Model\n(Microsoft Kosmos-2)]
    F --> G[Raw grounded description output]
    G --> H[NLP / Text Refinement\n(summarization or cleaning)]
    H --> I[Final natural description]
    I --> J[Text-to-Speech\n(e.g. Parler-TTS or SpeechT5)]
    J --> K[Audio spoken to user]
    
    style A fill:#f9f,stroke:#333
    style K fill:#bbf,stroke:#333