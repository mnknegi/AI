
# SystemLanguageModel

SystemLanguageModel isn't a single class like NSString. Instead, it refers to the underlying generative models that Apple has integrated into the OS (iOS, macOS, and iPadOS) to power text-related features.
The `System Language Model` is an `on-device Large Language Model (LLM)` designed for high-performance, private text processing. 
Unlike "Cloud" models (like ChatGPT), these are optimized specifically for `Apple's Neural Engine (ANE)`.

## Key Characteristics
Apple's system models differ from standard open-source models in three major ways:
- On-Device Priority: Most tasks are handled locally. This ensures your data never leaves the device and responses are fast.
- Adapter-Based Architecture: Instead of one giant model for everything, Apple uses a "base" model and switches small "Adapters" (LoRAs) for specific tasks (e.g., one adapter for summarizing, another for tone-shifting).
- Speculative Decoding: The system uses a smaller, faster model to "guess" the next words, which are then verified by the larger model. This makes the text appear on your screen much faster.
