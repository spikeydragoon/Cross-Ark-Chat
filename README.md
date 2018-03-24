# Cross-Ark-Chat

Cross Ark Chat connects all of your Ark Survival Evolved Servers chat together allowing you to talk to anyone from anywhere on your servers/clusters. I have added support to link in a discord channel so you can talk with your players from discord.

This program uses pure Rcon so it can be ran from anywhere however for best proformance i would run it from the same pc that is hosting your Ark servers.

Since this program uses Rcon i did add in some rcon commands in the discord version however some are buggy and i am working to get those resolved.

This is what chat looks like depending on your settings.
```
Discord: (spikeydragoon): Hello all!
Island: (spikeydragoon): Hello all!
Center: (spikeydragoon): Hello all!
```

Read the [CONTRIBUTING.md](https://github.com/spikeydragoon/Cross-Ark-Chat/blob/master/CONTRIBUTING.md) file before submitting a issue.
Join us on [Discord](https://discord.gg/HAk4BmN)

## Getting Started

These instructions will get you a copy of Cross Ark Chat up and running.


### Prerequisites

This is for Windows OS only however if anyone wants to contribute and make a version for linux then shoot me a message.

You must have rcon enabled in the Ark Server settings.


### Installation

1:Download the version of Cross Ark Chat that you want to use.

2:Extract the CrossArkChat.zip to where ever you want the program to run from.

3:Open the folder you extracted and configure the programs settings in `_configuration.json`.

3a:Optionally if you want to setup a badword list then configure settings in `_wordfilter.json`.
If you dont plan to use badword filters then can just ignore this file. Do not delete this file as program wont run if its missing.

4:Launch the program and enjoy. For discord version only you must type `d!startchat` in your discord server to start Cross Chat.
If you changed the prefix in the config then use that instead of `d!` with `startchat`. Example `dt!startchat`.


## Configuration

Formating for the config files is important so make sure to keep all formating or you will have problems.
At the bottom it will show examples for the versions with and without discord as they have different configs.


### Configuration for _configuration.json

Basic formating for the config should look like this.

For Server Settings
* `Map`: is the name of your map. This should not contain spaces or special characters as it will cause the program to not work properly. This is also used for the chat prefix for the server if you have it enabled.

* `Ip`: is either your local ip if your running bot from your own computer example `192.168.1.2` or if your trying to connect to a server on a hosting provider then you will use the hosting providers public ip address example `75.75.75.75`
You should not use your own public ip as this will cause problems.

* `Port`: is the rcon port on the Ark Server. Again you must have rcon enabled.

* `Password`: is the Admin password on the Ark Server. This should not contain spaces or special characters as it will cause the program to not work properly.

For Non Discord Version of settings.
* `ShowAdminCommands` tells the bot to either show or hide admin commands. `true` is to show commands and `false` is to hide them.
* `ShowTribeLogsInChat` tells the bot to either show or hide tribe logs in chat. `true` is to show tribe logs in chat `false is to hide them. This only matters if you have show Tribe logs in Rcon enabled in your Ark Server Settings. This settings is mostly for people that wanted to have tribe logs in rcon however dont want it showing up in the bot. 

For Discord Version of Settings
* `DiscordChannelID` is the id of the channel you want the bot to send all the chat messages to and from.
* `TribeLogsDiscordChannelID` is the id of the channel you want the bot to send tribe logs to if you have them enabled. Note this can be the same as the DiscordChannelID if you want both to show in same chat.
* `prefix` is the tag you use in discord when sending commands. Example `d!` is used like `d!startchat`
* `DiscordToken` is the Discord Bot Token required for the bot to connect to your server.
* `ShowAdminCommands` tells the bot to either show or hide admin commands. `true` is to show commands and `false` is to hide them.
* `ShowChatPrefixInDiscord` tells the bot to either show or hide the chat prefix in discord. This is mainly for people who only have one server. `true` shows the chat prefix(MapName) in discord `false` hides the prefix.
* `ShowTribeLogsInChat` tells the bot to either show or hide tribe logs in discord. This only matters if you have show Tribe logs in Rcon enabled in your Ark Server Settings.

Example of adding more than one server to the bot. 
Notice the , is required for each additional server however the last one doesnt have one. This is important as if you dont put the , where needed the bot will not work.
```json
"Servers": [
    {
      "Map": "MapName",
      "IP": "0.0.0.0",
      "Port": 00000,
      "Password": "Password"
    },
    {
      "Map": "MapName",
      "IP": "0.0.0.0",
      "Port": 00000,
      "Password": "Password"
    }
  ],
```

Example config for version without discord.
```json
{
  "Servers": [
    {
      "Map": "MapNameNoSpace",
      "IP": "0.0.0.0",
      "Port": 00000,
      "Password": "Password"
    }
  ],
  
  "CrossChatSettings":{
    "ShowAdminCommands": false,
    "ShowTribeLogsInChat": false
    }
}
```

Example config for version with discord.
```json
{
  "Servers": [
    {
      "Map": "MapNameNoSpace",
      "IP": "0.0.0.0",
      "Port": 00000,
      "Password": "Password"
    }
  ],
 
  "DiscordSettings": {
    "DiscordChannelID": 0000000,
    "TribeLogsDiscordChannelID": 0000000,
    "prefix": "d!",
    "DiscordToken": "DiscordBotToken",
    "ShowAdminCommands": false,
    "ShowChatPrefixInDiscord": true,
    "ShowTribelogsInChat": false
  }
}
```


### Configuration for _wordfilter.json

Basic formating for the config should look like this. Only note as before the , is important you only need the , when adding more words. Important thing to notice is the , shouldnt go on the last word. Failure to put the , where it belongs will cause the program to not run.

Make sure if you dont use this list then keep the example words in there as if it is left blank the server will not work. However you can change the words to what ever you want.

Last thing to note is this only deletes the words when the bots sends it to all servers it does not change what the player types in game.

Example _WordFilter.json
```json
{
  "WordFilterList": [
  "ExampleWord",
  "ExampleWords"
  ]

}
```


## Discord set up

Steps on how to get your discord tokens and channel ids.


### Creating your discord bot user

You have to create a discord bot user to get the token and to be able to add the bot to your discord server.

* You need to go to the Discord Developers section [here](https://discordapp.com/developers/applications/me) and click `New Application`
* Now name your bot and if wanted provide a picture and opitionaly you can give your bot a discription that will show up in the bots profile however this is not needed. The name given and picture is what will show up in your discord channel when the bot is online.
* Click `Create Application` and on the next page scroll down until you see `Create a bot user` and click the button. Confirm by clicking `Yes, do it~`
* Now you can get your bot's token by using the `click to reveal` button in the App Bot User section. Note this is special and shouldnt be shared with anyone. Anyone that has this token can use it to mess with your discord server and bot. If you already have your token to someone then go back to where it says click to reveal and click generate new token.
* Paste the bot token in the `_configuration.json` file where it says `DiscordToken`


### Adding the CrossArk program to discord

You now have to add the bot to your discord server and give it permissions.

* You need to go to the Discord Developers section [here](https://discordapp.com/developers/applications/me) and click on the bot you created in the steps above.
* Under App Details copy the Client ID.
* In your browser type in `https://discordapp.com/oauth2/authorize?&client_id=YOUR_CLIENT_ID_HERE&scope=bot&permissions=0` Replace where it says You_Client_Id_Here with the Bot Client ID that you copyed above. Example `https://discordapp.com/oauth2/authorize?&client_id=123456789&scope=bot&permissions=0`
* Once this page loads up select the server you want to add the bot to. Note you must have the Manage Server permission on the server you are tring to invite the bot to.
* Click `Authorize`

Thats it your bot is now added to your discord server and once your done setting up the config turn the program on and enjoy.


## FAQ

* Q: Can you change the font, color, or size of the in-game chat to something besides the bold yellow?
* A: Sadly no this is a limitation of Rcons `sendchat` command and is hard coded into Arks Rcon. Until they make an option to be able to change this we are stuck with the yellow :(

* Q: Are you open to ideas and code changes?
* A: Yes i am all for adding new ideas and optimizing the code. If you want to contribute by helping with codeing, making better guids, correcting my many typos, or giving ideas read the Contributing section then hit me up.

* Q: Do you plan to charge for this program?
* A: No i like "moneys" however this project was for fun and for the community to enjoy so if you paid for this then you have been scammed. If you want to help me you can feed me new ideas, help with making better guides, fixing typos, or help with code. Im to lazy to set up a paypal for donations but i may in the future since a free dr pepper would be nice.

* Q: Why does your code look like a noob did it?
* A: I code as a hobby and never fully learned one langue only entry level stuff. Between side projects and work i use a little of everything.  c, c#, c++, html, python, php and java are what i dabbled in so far with the Cs and java being the main ones.

* Q: Do you plan to add more features or is this it?
* A: I plan to keep updating the program for a good while mostly for the experience and to see what all we can do with it. Check my to-do list for my planned updates. Due to working full time i dont give etas since work might get busy depending on the season but i plan to at the bare min make sure the bot at least runs. If this ever changes i will let everyone know and look for someone to take it over.

Thats all i can think of for now :)


## To-Do List

* Fix the Rcon commands that are buggy.
* Optimize code.


## Built With

* [QueryMaster](https://archive.codeplex.com/?p=querymaster) - Lib used to handle all steam and rcon connections.
* [Discord.net](https://github.com/RogueException/Discord.Net/tree/dev) - Lib used to handle all discord connections.
* [C# .Net](https://github.com/dotnet) - Codeing langue and project used to run the program.


## Contributing

Please read [CONTRIBUTING.md](https://github.com/spikeydragoon/Cross-Ark-Chat/blob/master/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.


## Authors

* **Spikeydragoon** - *Initial work* - [Spikeydragoon](https://github.com/spikeydragoon)

See also the list of [contributors](https://github.com/spikeydragoon/Cross-Ark-Chat/graphs/contributors) who participated in this project.


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details


## Acknowledgments

* Shout out to [Bletch1971](https://github.com/Bletch1971) looking over your rcon code helped alot and the ASM program you and your team developed is amazing.
