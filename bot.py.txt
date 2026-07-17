import os
from telethon import TelegramClient, events

# These will be pulled from the Variables you set in Railway later
api_id = os.environ.get("API_ID")
api_hash = os.environ.get("API_HASH")

client = TelegramClient('session_name', int(api_id), api_hash)

@client.on(events.NewMessage(incoming=True, func=lambda e: e.is_private))
async def handler(event):
    await event.respond(
        "Thank you for your message. Starting July 17th, I am no longer employed at Uni Trans LLC. "
        "Please contact either Charlie Smith or Bryan Winston for more information."
    )

client.start()
client.run_until_disconnected()