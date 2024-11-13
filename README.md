# Orion

<img src="./docs/static/img/1500x500.png" alt="Orion Banner" width="100%" />

## Features

-   🛠 Full-featured Discord, Twitter and Telegram connectors
-   👥 Multi-agent and room support
-   📚 Easily ingest and interact with your documents
-   💾 Retrievable memory and document store
-   🚀 Highly extensible - create your own actions and clients to extend capabilities
-   ☁️ Supports many models, including local Llama, OpenAI, Anthropic, Groq, and more
-   📦 Just works!

## What can I use it for?

-   🤖 Chatbots
-   🕵️ Autonomous Agents
-   📈 Business process handling
-   🎮 Video game NPCs

# Getting Started

**Prerequisites (MUST):**
    
-   [Python 2.7+](https://www.python.org/downloads/)
-   [Node.js 22+](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)
-   [pnpm](https://pnpm.io/installation)

### Edit the .env file

-   Copy .env.example to .env and fill in the appropriate values
-   Edit the TWITTER environment variables to add your bot's username and password

### Edit the character file

-   Check out the file `src/core/defaultCharacter.ts` - you can modify this
-   You can also load characters with the `pnpm start --characters="path/to/your/character.json"` and run multiple bots at the same time.

After setting up the .env file and character file, you can start the bot with the following command:

```
pnpm i
pnpm start
```

# Customising Orion

### Adding custom actions

To avoid git clashes in the core directory, we recommend adding custom actions to a `custom_actions` directory and then adding them to the `orionConfig.yaml` file. See the `orionConfig.example.yaml` file for an example.

## Running with Orion

You can run Orion's model by setting the `AI_MODEL` environment variable to 'orion_ai16z_v1'

## Additional Requirements

You may need to install Sharp. If you see an error when starting up, try installing it with the following command:

```
pnpm install --include=optional sharp
```

# Environment Setup

You will need to add environment variables to your .env file to connect to various platforms:

```
# Required environment variables
DISCORD_APPLICATION_ID=
DISCORD_API_TOKEN= # Bot token
ORION_API_KEY=or-* # Orion API key
ELEVENLABS_XI_API_KEY= # API key from elevenlabs

# ELEVENLABS SETTINGS
ELEVENLABS_MODEL_ID=eleven_multilingual_v2
ELEVENLABS_VOICE_ID=21m00Tcm4TlvDq8ikWAM
ELEVENLABS_VOICE_STABILITY=0.5
ELEVENLABS_VOICE_SIMILARITY_BOOST=0.9
ELEVENLABS_VOICE_STYLE=0.66
ELEVENLABS_VOICE_USE_SPEAKER_BOOST=false
ELEVENLABS_OPTIMIZE_STREAMING_LATENCY=4
ELEVENLABS_OUTPUT_FORMAT=pcm_16000

TWITTER_DRY_RUN=false
TWITTER_USERNAME= # Account username
TWITTER_PASSWORD= # Account password
TWITTER_EMAIL= # Account email
TWITTER_COOKIES= # Account cookies

X_SERVER_URL=
ORION_MODEL=

WALLET_PRIVATE_KEY=EXAMPLE_WALLET_PRIVATE_KEY
WALLET_PUBLIC_KEY=EXAMPLE_WALLET_PUBLIC_KEY

BIRDEYE_API_KEY=

SOL_ADDRESS=So11111111111111111111111111111111111111112
SLIPPAGE=1
RPC_URL=https://api.mainnet-beta.solana.com
HELIUS_API_KEY=


## Telegram
TELEGRAM_BOT_TOKEN=

TOGETHER_API_KEY=
```

# Local Inference Setup

### CUDA Setup

If you have an NVIDIA GPU, you can install CUDA to speed up local inference dramatically.

```
pnpm install
npx --no node-llama-cpp source download --gpu cuda
```

Make sure that you've installed the CUDA Toolkit, including cuDNN and cuBLAS.

# Clients

## Discord Bot

For help with setting up your Discord Bot, check out here: https://discordjs.guide/preparations/setting-up-a-bot-application.html

# Development

## Testing

To run the test suite:

```bash
pnpm test           # Run tests once
pnpm test:watch    # Run tests in watch mode
```

For database-specific tests:

```bash
pnpm test:sqlite   # Run tests with SQLite
pnpm test:sqljs    # Run tests with SQL.js
```

Tests are written using Jest and can be found in `src/**/*.test.ts` files. The test environment is configured to:

-   Load environment variables from `.env.test`
-   Use a 2-minute timeout for long-running tests
-   Support ESM modules
-   Run tests in sequence (--runInBand)

To create new tests, add a `.test.ts` file adjacent to the code you're testing.
