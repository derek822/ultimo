import discord

# La variable intents almacena los privilegios del bot
intents = discord.Intents.default()
# Activar el privilegio de lectura de mensajes
intents.message_content = True
# Crear un bot en la variable cliente y transferirle los privilegios
client = discord.Client(intents=intents)

@client.event
async def on_ready():
    print(f'Hemos iniciado sesión como {client.user}')

@client.event
async def on_message(message):
    if message.author == client.user:
        return
    if message.content.startswith('$hello'):
        await message.channel.send("Hi!")
    elif message.content.startswith('$¿Qué es el reciclaje?'):
        await message.channel.send("trata de convertir residuos plásticos, la basura que consumimos diariamente, en nuevos productos o en materia prima para su posterior utilización,")
    elif message.content.startswith('$¿Cuál es la importancia del reciclaje?'):
        await message.channel.send("La importancia del reciclaje radica en el cuidado del medio ambiente, su proteccion y preserbacion")
    elif message.content.startswith('$¿que puedo reciclar?'):
        await message.channel.send("puedes resiclar reutilizando plasticos, cartones, hierro, etc...")
    elif message.content.startswith('$¿como puedo reciclar y reutilizar?'):
        await message.channel.send("utilizando materiales resiclavles para maquetas, proyectos, jugetes, arte, muebles, ect...")
    else:
        await message.channel.send(message.content)

@client.command()
async def helpme(ctx):
    commands_list = """
    *Lista de Comandos:*
    - !hello: Saluda al bot.
    - !genpass: Genera una contraseña aleatoria.
    - !roll: Tira un dado de 6 caras.
    - !guess: Juego de adivinanza de número.
    - !joke: Cuenta un chiste.
    - !trivia: Te da una trivia interesante.
    - !play [url]: Reproduce música de YouTube en tu canal de voz.
    - !leave: Desconecta al bot del canal de voz.
    """
    await ctx.send(commands_list)

client.run("MTI5NTAzMjIxOTE2MDY3NDMwNA.GG_5xY.RyVewDAp3XidV6Eluto1bFJ6nK8I505xD4guYM")
