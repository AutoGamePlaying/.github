# AutoGamePlaying

**Let different AI models play games with the same self-written agent, under the same conditions, and compare the results.**

AGP (Auto Game Playing) is a Rust framework that:
- connects to mainstream LLM providers, each with a configurable endpoint;
- runs its own agent, which calls the tools provided by game modules;
- records every run in tamper-evident logs and signed results that can be used in competitions.

The framework itself contains no game logic; each game series is a separate module.

## Repositories

| Repository | Description |
| --- | --- |
| [agp](https://github.com/AutoGamePlaying/agp) | The framework (Rust): provider adapters, self-written agent loop, hash-chained logs, Ed25519-signed results, competitions, local web panel, Windows platform layer |
| [Final-Fantasy-Pixel-Remaster](https://github.com/AutoGamePlaying/Final-Fantasy-Pixel-Remaster) | FINAL FANTASY Pixel Remaster: the AI plans a whole chapter at once and code executes it; offline simulated game for pre-runs, real-machine executor |
| [Final-Fantasy-Resonance-Agent](https://github.com/AutoGamePlaying/Final-Fantasy-Resonance-Agent) | FINAL FANTASY RESONANCE: UE4SS mods for reading state and injecting input, Rust game module |

## Principles

- **Fair comparison**: every competing model gets the same tools, prompts, budget and retry policy. Information the game has not revealed yet stays hidden by default.
- **AI plans, code executes**: models make decisions; repeatable actions are done by tested code.
- **Game data as the source of truth**: plans and tool results refer to IDs from the game's own data and are checked against that data before submission.
- **Traceable and tamper-evident**: run logs and the provider-config journal are hash chains. Results and scoreboards are signed and record exactly which provider configuration was used.
- **Read-only plus input**: we read game state, and simulated input is the only write. We never modify game data or saves.

## Supported providers

DeepSeek, ChatGPT (OpenAI), Kimi, GLM, Claude, Gemini, Grok, MiniMax and Doubao, plus other OpenAI-compatible services and local models.

## Notice

The repositories in this organization **contain no game files, extracted game data or walkthrough text**. You need your own legitimate copy of each game. All game titles and trademarks belong to their respective owners. This project is not affiliated with SQUARE ENIX or any other rights holder.
