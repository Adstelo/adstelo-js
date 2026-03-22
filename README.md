# @adstelo/sdk

Adstelo JS SDK for Telegram bots built on **grammY** and **Telegraf**. You dont need to edit your entire bot logic. just use the middleware in the app.use() and thats all!

## Requirements

- Node.js 18+
- A Telegram bot token
- Adstelo bot secret + API key (from your Adstelo bot registration)

## Install

```bash
npm install @adstelo/sdk
```

## Quick Start (grammY)

```js
import { Bot } from "grammy";
import { adstelo } from "@adstelo/sdk";

const bot = new Bot(process.env.BOT_TOKEN);

bot.use(
  adstelo.grammy({
    botSecret: process.env.ADSTELO_BOT_SECRET,
    apiKey: process.env.ADSTELO_API_KEY,
    cooldownSeconds: 2
  })
);

bot.command("start", (ctx) => ctx.reply("Hello from Adstelo"));

bot.start();
```

## Quick Start (Telegraf)

```js
import { Telegraf } from "telegraf";
import { adstelo } from "@adstelo/sdk";

const bot = new Telegraf(process.env.BOT_TOKEN);

bot.use(
  adstelo.telegraf({
    botSecret: process.env.ADSTELO_BOT_SECRET,
    apiKey: process.env.ADSTELO_API_KEY,
    cooldownSeconds: 2
  })
);

bot.start((ctx) => ctx.reply("Hello from Adstelo"));

bot.launch();
```

## What this SDK doesn't do:

- The sdk does not in any way broadcast any private information about the user conversations and the environment credentials over the network.  We only require you to pass your bot_secret and adstelo_api_key that you obtain from our official website. 

 
## Configuration

```ts
adstelo.grammy({
  botSecret: string,
  apiKey: string,
  cooldownSeconds?: number,
  baseUrl?: string
})
```

- `cooldownSeconds` default: `2` 

## Troubleshooting

**It exits immediately with code 1**
- Your `botSecret` or `apiKey` is invalid.
- Double-check the values in Adstelo dashboard.

**No events arriving**
- Confirm the middleware is registered before other handlers.
- Ensure your bot actually receives updates (polling/webhook is working).

**Rate limiting feels too aggressive**
- Increase `cooldownSeconds` in the middleware config.

## API

- `adstelo.grammy(options)`
- `adstelo.telegraf(options)`

## License

MIT
