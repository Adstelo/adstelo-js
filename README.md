# @adstelo/sdk

Adstelo JS SDK for Telegram bots monetization. Supports Telegraf and grammY.  To use it, you must obtain keys from adstelo platform. Each bot gets a unique secret key. Dont mix them up!

## Install

```bash
npm install @adstelo/sdk
```

## Quick Start (One-liner)

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
```

## Telegraf

```js
import { Telegraf } from "telegraf";
import { adstelo } from "@adstelo/sdk";

const bot = new Telegraf(process.env.BOT_TOKEN);

bot.use(
  adstelo.telegraf({
    botSecret: process.env.ADSTELO_BOT_SECRET,
    apiKey: process.env.ADSTELO_API_KEY
  })
);
```

## API

- `adstelo.telegraf(options?)`
- `adstelo.grammy(options?)`
