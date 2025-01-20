<h1 align="center">
  <br>
    DiscoSpeech
<br>
</h1>

<p align="center">
<a href="https://github.com/ajr-dev/discospeech/fork" target="blank">
<img src="https://img.shields.io/github/forks/ajr-dev/discospeech?style=for-the-badge" alt="discospeech forks"/>
</a>
<a href="https://github.com/ajr-dev/discospeech/stargazers" target="blank">
<img src="https://img.shields.io/github/stars/ajr-dev/discospeech?style=for-the-badge" alt="discospeech stars"/>
</a>
<a href="https://github.com/ajr-dev/discospeech/pulls" target="blank">
<img src="https://img.shields.io/github/issues-pr/ajr-dev/discospeech?style=for-the-badge" alt="discospeech pull-requests"/>
</a>
</p>

A Discord bot that listens to voice chat, transcribes speech using Whisper, generates responses using Ollama, and speaks back using ElevenLabs or Bark TTS.

## 🚀 Features

- Real-time voice transcription using OpenAI's Whisper
- AI-powered responses using Ollama (local LLM)
- Text-to-speech responses using ElevenLabs (cloud) or Bark (local)
- Automatic audio cleanup and management
- Configurable logging system

## Limits

- Currently not group chat friendly
- Not scalable to more servers at once
- No local tts model option

## Prerequisites

- Python 3.8+
- FFmpeg (for audio processing)
- Ollama installed and running locally
- Discord Bot Token
- ElevenLabs API Key and Voice ID
- CUDA-compatible GPU recommended (for faster transcription)

## Installation

1. Clone the repository
2. Install the required Python packages:

```sh
pip install -r requirements.txt
```

3. Copy `config.example.json` to `config.json` and fill in your credentials:

```json
{
    "discord_token": "YOUR_DISCORD_BOT_TOKEN",
    "elevenlabs_api_key": "YOUR_ELEVENLABS_API_KEY",
    "voice_id": "YOUR_ELEVENLABS_VOICE_ID",
    "ollama_host": "http://localhost:11434",
    "ollama_model": "llama3.1:latest",
    "cleanup_responses": false,
    "tts_service": "bark" 
}
```

You can either set `tts_service` to:
- `bark`
- `elevenlabs`

`elevenlabs_api_key` may be left as is if `tts_service` is not set to `elevenlabs`.

## Configuration

### Discord Bot Setup
1. Go to the [Discord Developer Portal](https://discord.com/developers/applications)
2. Create a new application
3. Add a bot to your application
4. Enable Voice State and Message Intent permissions
5. Copy the bot token to your `config.json`

### ElevenLabs Setup
1. Create an account at [ElevenLabs](https://elevenlabs.io)
2. Get your API key from the profile settings
3. Choose a voice and copy its ID
4. Add both to your `config.json`

### Ollama Setup
1. Install Ollama from [ollama.ai](https://ollama.ai)
2. Pull your preferred model:
```sh
ollama pull mistral
```

## Commands
- `!join` - Bot joins your current voice channel
- `!leave` - Bot leaves the voice channel

## 💻 Usage

1. Start the Ollama service
2. Run the bot:
```sh
python main.py
```

3. Invite the bot to your Discord server
4. Join a voice channel
5. Use `!join` to make the bot join
6. The bot will:
   - Listen to voice chat
   - Transcribe speech in real-time
   - Generate responses using Ollama
   - Speak responses using `ElevenLabs TTS` or a local `bark tts` model

## Project Structure

- `bot/` - Main bot module
  - `services/` - Core services (audio, TTS, LLM)
  - `voice/` - Voice processing components
  - `utils/` - Utility functions
- `temp/` - Temporary audio files
- `responses/` - Generated audio responses
- `logs/` - Application logs

## Logging

Logs are stored in `logs/bot.log` with automatic rotation at 10MB and keeping 5 backups.

## Citation

If you utilize this repository, data in a downstream project, please consider citing it with:

```
@misc{discospeech,
  author = {AJR},
  title = {DiscoSpeech: Realistic discord voice chat AI},
  year = {2025},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished = {\url{https://github.com/ajr-dev/discospeech}},
```

## 🌟 Star history

[![DiscoSpeech Star history Chart](https://api.star-history.com/svg?repos=ajr-dev/discospeech&type=Date)](https://star-history.com/#ajr-dev/discospeech&Date)

## License

[MIT License](LICENSE)

## 🙇 Acknowledgements

DiscoSpeech couldn't have been built without the help of great software already available. Thank you!

- [ollama](https://github.com/ollama/ollama)
- [whisper](https://github.com/openai/whisper)
- https://github.com/imayhaveborkedit/discord-ext-voice-recv
- [elevenlabs](https://github.com/elevenlabs/elevenlabs-python)
- [bark](https://github.com/suno-ai/bark)

## 🤗 Contributors

This is a community project, a special thanks to our contributors! 🤗

<a href="https://github.com/ajr-dev/discospeech/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=ajr-dev/discospeech" />
</a>