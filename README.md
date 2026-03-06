# Hydra Guard — Remote Pattern Database

This repository hosts the remote scam detection patterns used by the [Hydra Guard Chrome Extension](https://github.com/dgarcia891/Scam-Alert).

## How It Works

The Hydra Guard extension periodically syncs patterns from `public/patterns.json` to augment its built-in detection rules. This allows new scam patterns to be deployed to all users without requiring an extension update.

## Pattern Format

```json
{
  "patterns": [
    {
      "phrase": "your account has been compromised",
      "category": "phrase|tld|domain",
      "severity_weight": 1-10,
      "source": "manual|ai_promoted|community"
    }
  ],
  "keywords": ["login", "verify", "urgent"],
  "version": "1.0.0",
  "last_updated": "2026-03-05T00:00:00Z"
}
```

### Categories
- **phrase** — Full scam phrases detected in page content
- **tld** — Suspicious top-level domains
- **domain** — Known malicious domains
- **keyword** — Individual suspicious keywords for URL/content scanning

### Severity Weight (1-10)
- **1-3**: Low confidence indicator
- **4-6**: Medium confidence indicator  
- **7-8**: High confidence indicator
- **9-10**: Critical — very strong scam signal

## Feedback Loop

Patterns are continuously refined through:
1. User-reported false positives/negatives from the extension
2. AI-powered review (Gemini 2.5 Flash) of correction batches
3. Admin approval with weight adjustments via the Hydra Guard admin panel

## License

Proprietary — Acme Zone. All rights reserved.
