# How Community Poke works

This is a high-level overview of how Community Poke is put together. It is not an official description of [Poke](https://poke.com) and it is not endorsed by The Interaction Company of California or Cognition.

## The short version

Community Poke is a Poke instance that a community bridges into the Poke Community Discord server. People in Discord talk to it through a Discord bot, and the bot relays their messages to Poke and Poke's replies back to Discord.

## The pieces

1. **A Poke account on Telegram.** The shared Poke instance runs under its own Poke account. Poke is reached through Telegram, so the account is the entry point for everything the bot does.

2. **A linked Telegram account.** A separate Telegram account is linked to the Poke account and receives the Discord traffic. Discord messages are forwarded into this linked account.

3. **TDLib for forwarding.** The forwarding is handled with TDLib, the Telegram Database Library, which lets a program act as a full Telegram client. Each forwarded Discord message arrives with a metadata header containing:
   - the Discord user ID
   - the Discord username
   - the display name
   - pronouns, where the user has set them
   - the user's roles in the server

   The header gives Poke enough context to know who it is talking to without relying on the message text alone.

4. **Poke's responses go back to Discord.** Poke replies in the Telegram chat, and those replies are picked up and posted back to the Discord channel they came from.

## Integrations

Poke can use connected tools (MCP integrations) to do work on behalf of the community. Integrations that are currently active include:

- **petrol-baby**: fuel price lookups, including current prices, price summaries, and price history.
- **Devin**: creating and managing Devin coding sessions, and the knowledge and playbooks Devin uses.
- **GitHub**: searching and reading repositories, issues, and pull requests, and making commits and pull requests in the CommunityPokeOrg repositories.

The set of integrations changes over time, so treat this list as a snapshot rather than a complete inventory.

## Things to keep in mind

- Anything Poke does through an integration runs with the permissions that integration was given.
- Discord messages are forwarded with the metadata header described above. Do not share personal details in the server that you would not want passed along.
- Questions about how a specific project works belong in that project's own repository README.

## Questions

Come say hi at [poke.com/discord](https://poke.com/discord) and ask about the setup.
