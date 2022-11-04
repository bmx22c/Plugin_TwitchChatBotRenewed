# Twitch Chat Bot Renewed

Twitch Chat Bot Renewed is a plugin that will send information regarding maps, server, link to the map, personal best times and checkpoints to a database that you can access from your Stream Platform (Streamlabs, Streamelements or anything else).  
You can also configure every field with custom messages.

## Installation

Put the files in your OpenPlanet directory which is located here:  
```
C:\Users\<username>\OpenplanetNext\Plugins\TwitchChatBot
```

So that it looks like this:  
```
Plugins/
├─ TwitchChatBot.op
```

## Dependency
This plugin now uses the Checkpoint Counter plugin as a dependency, thanks to Phlarx.  
If you don't have this plugin, any checkpoint related commands will be disabled.  

You can download the plugin [here](https://openplanet.dev/plugin/checkpointcounter).

## Settings
### Parameters
You will need to register with your Ubisoft account (the same as your Trackmania account otherwise it won't work) by clicking on:  
`Scripts` > `Twitch Chat Bot` > `Authenticate`

This will open a new browser window where you will need to log into your Ubisoft account.  
Once connected, you will land on a page that will display **your key**.  
**⚠ Make sure to not lose your key!**

Once you got your key, you'll need to input it on the Twitch Chat Bot Renewed settings page:  
`Openplanet` > `Settings` > `Twitch Chat Bot Renewed` > `General` > `Key`

If everything worked, you'll see a notification telling you that you are connected. You can double-check by going into:  
`Scripts` > `Twitch Chat Bot` > `Active` (if `Active` is checked then it's good)

You can change the `Formatting` to either `Fixed` or `Custom`.  
**⚠ You can only select `Custom` if you have filled in all the fields in the `Strings` tab.**

List of all `Fixed` strings:
- On a map: `⏩ I am currently playing {name} by {author}.`
- Not on a map: `⚠ I am currently not in a map.`
- On a server: `⏩ I am currently playing on {name} ({nbr_player}/{max_player}).`
- Not on a server: `⚠ I am currently not on a server.`
- Personal best: `⏩ My current pb is {pb}s.`
- No personal best: `⚠ I don't have a pb on that map.`
- TMX URL: `⏩ Map URL: {url}`
- Map not found on TMX: `⚠ Map not found on TMX.`
- Checkpoint: `⏩ Current CP: {crt_cp}/{max_cp}.`

### Commands
You can enable or disable specific commands. Disabling a command means that the relevant information will not be sent to the server anymore.

### Strings
You can configure every string that will be posted in the chat.

You will have variables available for every command:
- Map:
    - `{name}` - map name
    - `{author}` - map author
    - `{author_time}` - map author time
- Server:
    - `{name}` - server name
    - `{nbr_player}` - current player count
    - `{max_player}` - number of slots of the current server
- Personal best time:
    - `{pb}` - personal best time
- URL:
    - `{TMXurl}` - map URL on [Trackmania Exchange](https://trackmania.exchange/)
    - `{TMIOurl}` - map URL on [trackmania.io](https://trackmania.io/)
- Checkpoint:
    - `{crt_cp}` - current CP
    - `{max_cp}` - number of CPs on the map

You can place these variables wherever you want inside the String fields.

_Note: You can paste emojis from outside Openplanet. They will be displayed as `?` but will be interpreted correctly in chat._

## Usage
Once properly configured, just launch Trackmania and it should connect to the server automatically.

You become inactive once you close Trackmania **or** you manually uncheck the `Active` button.  
Once you are inactive, the API will answer with either your predefined message or a fixed one:  
`⚠ I am not active.`

## Stream Platform
To use this plugin on your preferred stream platform, add a new command with the prefix that you want and add an API request to:  
**Nightbot:**  
`$(urlfetch https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>)`

**Streamlabs Chatbot:**  
`$readapi(https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>)`

**Streamlabs Cloudbot:**  
`{readapi.https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>}`

**Streamelements:**  
`${customapi.https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>}`

**Fossabot:**  
`$(customapi https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>)`

**Deepbot:**  
`@customapi@[https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>]`

**PhantomBot:**  
`(customapi https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>)`

**Ohbot:**  
`[customapi https://tm-info.digit-egifts.fr/read.php?type=<type>&username=<TM_username>&key=<private_key>]`

*Parameters:*
- Type
    - `map`
    - `server`
    - `pb`
    - `url`
    - `cp`
- Username: Your Trackmania username
- Private key: Your private key that has been given to you while authenticating

## What's different between this plugin and my old plugin "Twitch Chat Bot"
[Twitch Chat Bot](https://openplanet.nl/files/113) was using [Nsgr Twitch Base](https://openplanet.nl/files/93) as a dependency, so it was still using the old plugin format. It was also working in a completely different way. It was connecting to the chat and was listening to any new messages, and answered as the streamer (ex: `bmx22c`) in the chat, instead of going through Streamlabs or something similar.  
This **Twitch Chat Bot Renewed** is more of a bridge between a database and Streamlabs than a bot in itself.

## Legal Notice
While logging in with your Ubisoft account, I will only get your Ubisoft username and account ID.  
All stored keys are hashed.  
If you want me to remove your data from the database, just send me a message on Discord with your Trackmania username: `bmx22c#0001`.

## Special thanks
Thanks to **PHLARX** for the [CP counter](https://openplanet.nl/files/79)  
Thanks to **tooInfinite** for the help on the Trackmania API  
Thanks to **Miss** and the **Openplanet Discord** for the server information help  


## Contributing
Pull requests are welcome on [this repo](https://github.com/bmx22c/Plugin_TwitchChatBotRenewed). For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)