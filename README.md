import discord
from discord.ext import commands
import random
import string
import os

intents = discord.Intents.default()
intents.message_content = True
bot = commands.Bot(command_prefix="!", intents=intents)

@bot.event
async def on_ready():
    print(f"Connecté en tant que {bot.user}")

@bot.command()
async def key(ctx):
    key = ''.join(random.choices(string.ascii_uppercase + string.digits, k=15))
    await ctx.author.send(f"Voici ta clé ZAMASU : `{key}`")

bot.run(os.environ['DISCORD_TOKEN'])
