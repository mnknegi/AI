# AI

## Foundation Models in Apple iOS
Foundation Models is a new framework Apple introduced that allows developers to run Apple's on-device AI models directly within their apps on iOS, iPadOS, and macOS.

## Key Concepts

### On-Device Inference
Foundation Models runs Apple Intelligence models locally on the device — no internet connection or cloud calls required. This means faster responses, better privacy, and offline capability.

### The Framework
Introduced at WWDC 2025 (iOS 18/macOS 15 era), the FoundationModels framework gives developers Swift APIs to interact with the same language models that power Apple Intelligence features like Writing Tools and Siri enhancements.

## What You Can Do With It

Text generation — generate summaries, rewrites, creative content
Structured output — generate JSON or typed Swift objects via the @Generable macro
Guided generation — constrain the model's output to specific formats or schemas
Sessions — maintain multi-turn conversational context
Tool calling — let the model invoke Swift functions you define

```
import FoundationModels

// Create a session
let session = LanguageModelSession()

// Generate a response
let response = try await session.respond(to: "Summarize this text: ...")
print(response.content)
```

## Limitations

Only available on devices with Apple Intelligence support (A17 Pro / M1+)
The model is general-purpose but smaller than cloud models (GPT-4, Claude, etc.)
Not suitable for highly complex reasoning tasks
English-first (as of initial release)

## Why It Matters
It's Apple's answer to allowing private, fast, on-device AI without forcing developers to integrate third-party LLM APIs — keeping user data on the device while still enabling intelligent app features.
