
# SystemLanguageModel

`SystemLanguageModel` is the `on-device large language model(LLM)` capable of text generation tasks — it's essentially the entry point to Apple's on-device LLM in the Foundation Models framework.

## What it is
SystemLanguageModel is the primary access point to Apple's built-in LLM. We use it to get a reference to the model before creating a session.

```
import FoundationModels

// Default general-purpose model
let model = SystemLanguageModel.default

// Specialized use case (e.g., content tagging)
let taggingModel = SystemLanguageModel(useCase: .contentTagging)
```

## Checking Availability
Before creating a session, one should check for `availability`, since the model can only run on Apple Intelligence-enabled devices in supported regions. availability is a two-case enum — either `.available` or `.unavailable`. If unavailable, you also receive a reason so you can adjust your UI accordingly.

```
let model = SystemLanguageModel.default

switch model.availability {
case .available:
    // Proceed to create a session
case .unavailable(let reason):
    switch reason {
    case .appleIntelligenceNotEnabled:
        // Prompt user to enable Apple Intelligence
    case .deviceNotEligible:
        // Device doesn't support Apple Intelligence
    case .modelNotReady:
        // Model is still downloading
    }
}
```

The `isAvailable` property is an all-encompassing convenience check — if it returns true, we're all set. 

## Default vs. Specialized Use Cases
Beyond the default model, Apple also provides additional built-in specialized use cases backed by adapters. You can pass these to SystemLanguageModel's initializer. One notable specialized adapter is the `content tagging adapter`, which provides first-class support for tag generation, entity extraction, and topic detection.

## Using It in a Session
By default, LanguageModelSession uses SystemLanguageModel.default automatically. One can also pass it explicitly:

> let session = LanguageModelSession(model: SystemLanguageModel.default)

