# translator

A Windows system-tray tool that intercepts selected text and rewrites it using OpenAI. Press a hotkey in any application to improve, translate, deformalise, or answer text in-place.

## Features

- **Text improvement** — fixes grammar, tightens wording, preserves tone and intentional formatting quirks
- **Translation** — 14 languages via simple suffixes (`-en`, `-es`, `-ja`, …)
- **Deformalise** — rewrites stiff text into casual, human language
- **Answer** — replaces a question with its answer
- **Chaining** — stack multiple suffixes (e.g. `hello -df-en` deformalises then translates)
- **System tray** — minimises to tray, configurable hotkey, persists settings across sessions
- **Secure key storage** — API key stored via Windows Credential Manager (`keyring`), not plaintext

## Requirements

- Windows 10/11
- Python 3.9+
- An [OpenAI API key](https://platform.openai.com/api-keys)

## Installation

```bash
git clone https://github.com/ozashub/translator.git
cd translator
pip install -r requirements.txt
```

Missing dependencies are also auto-installed on first run.

## Usage

```bash
python translator.py
```

On first launch you'll be prompted for:
1. Your OpenAI API key (stored securely via Windows Credential Manager)
2. A hotkey (press any key combo, then Enter to confirm)

After setup, the tool runs in the background. Type text in any application, press your hotkey, and the text is replaced with the AI result.

### Suffixes

Append a suffix to your text before pressing the hotkey to control the operation:

| Suffix | Operation |
|--------|-----------|
| *(none)* | Improve text |
| `-r` | Answer a question |
| `-df` | Deformalise |
| `-en` | Translate to English |
| `-es` | Translate to Spanish |
| `-fr` | Translate to French |
| `-de` | Translate to German |
| `-it` | Translate to Italian |
| `-pt` | Translate to Portuguese |
| `-ru` | Translate to Russian |
| `-ja` | Translate to Japanese |
| `-ko` | Translate to Korean |
| `-zh` | Translate to Chinese |
| `-nl` | Translate to Dutch |
| `-sv` | Translate to Swedish |
| `-no` | Translate to Norwegian |
| `-jam` | Translate to Jamaican Patois |

Suffixes can be chained: `some formal text -df-en` will deformalise first, then translate to English.

### Controls

| Key | Action |
|-----|--------|
| Configured hotkey | Process selected text |
| F12 | Reconfigure hotkey |
| Ctrl+C (in console) | Quit |

## Configuration

- **API key** — stored in Windows Credential Manager (managed by `keyring`). To reset, delete the `translator` entry in Credential Manager and restart.
- **Hotkey** — stored in the Windows Registry at `HKCU\Software\Translator`. Press F12 at any time to reconfigure.

## License

[MIT](LICENSE)
