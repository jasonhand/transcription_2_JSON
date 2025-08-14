# Transcript to JSON Converter

A lightweight, client-side web app that converts any transcript into valid JSON with a single field named `question`. The app prepends a fixed prompt to your transcript and outputs a ready-to-use JSON payload for summarization workflows.

## Why it's important
- **Consistency**: Every request uses the same prompt format for reliable summaries.
- **Validity**: Automatically escapes quotes, backslashes, and newlines to produce valid JSON.
- **Privacy**: Runs entirely in your browser—no servers, no network calls.
- **Speed**: Paste → Convert → Copy. No manual escaping or regex hacks.

## How it works
- The output JSON contains only one field: `question`.
- The value of `question` is the fixed prompt followed immediately by your transcript.
- Formatting uses `JSON.stringify(..., null, 2)` for readable, standards-compliant JSON.
- One-click copy uses the Clipboard API with a safe fallback for older browsers.

## Usage
1. Open `index.html` in your web browser (Chrome, Edge, Safari, Firefox).
2. Paste your transcript into the input box.
3. Click "Convert to JSON".
4. Click "Copy" to copy the JSON to your clipboard.

Tip: Press `Ctrl + Enter` inside the transcript box to convert.

## Output format
The app produces JSON with a single key:

```json
{
  "question": "Please provide a 200-word summary of the following transcription: <your transcript here>"
}
```

Example:
```json
{
  "question": "Please provide a 200-word summary of the following transcription: Yesterday we discussed the Q3 roadmap..."
}
```

## Features
- **Single `question` field** containing prompt + transcript
- **Error messages** for empty input and copy attempts with no content
- **Keyboard shortcut**: `Ctrl + Enter` to convert
- **Responsive UI** for desktop and mobile
- **No build step**: just open the file

## Development notes
- All logic is contained in `index.html`.
- Core function: `convertToJSON()` builds the single-field JSON and writes it to the output area.
- Copy behavior uses the native Clipboard API with a fallback for older browsers.

## Recent changes
- 2025-08-14: JSON output now uses a single field `question` that concatenates the fixed prompt and your transcript (previously used separate `question` and `transcript` fields).
- 2025-08-14: Updated on-page tips to reflect the single-field output structure.

## License
See `LICENSE` for details.
