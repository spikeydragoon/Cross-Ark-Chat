# Cross-Ark-Chat

Cross Ark Chat connects all of your Ark Survival Evolved Servers chat together allowing you to talk to anyone from anywhere on your servers/clusters. I have added support to link in a discord channel so you can talk with your players from discord.
You can also enable tribe logs to be sent to your discord channel.

This program uses pure Rcon so it can be ran from anywhere however for best performance i would run it from the same pc that is hosting your Ark servers.

Since this program uses Rcon i did add in some rcon commands in the discord version.

This is what chat looks like depending on your settings.
```
Discord: (spikeydragoon): Hello all!
Island: (spikeydragoon): Hello all!
Center: (spikeydragoon): Hello all!
```

Read the [CONTRIBUTING.md](https://github.com/spikeydragoon/Cross-Ark-Chat/blob/master/CONTRIBUTING.md) file before submitting a issue.

Join us on [Discord](https://discord.gg/HAk4BmN)

If your looking to play on a server with this here is link to my [servers](arkservermanager.freeforums.net/thread/4716/dinoroars-cross-ark-servers-cluster)

## Getting Started

These instructions will get you a copy of Cross Ark Chat up and running.


### Prerequisites

This is for both linux and windows.

For linux you must download libunwind8 for CrossArkChat to work. 

For Ubuntu/Debian
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libunwind8
```
For RedHat/CentOS
```
sudo yum update
sudo yum install libunwind libicu
```

For Linux set the CrossArkChat folder/files permissions to 755 to allow w/r/execute

You must have rcon enabled in the Ark Server Settings.

For tribe logs you must have log tribe logs to rcon enabled in the Ark Server Settings.


### Installation

1:Download the version of Cross Ark Chat that you want to use.

2:Extract the CrossArkChat.zip to where ever you want the program to run from.

3:Open the folder you extracted and configure the programs settings in `_configuration.json`.

3a:Optionally if you want to setup a badword list then configure settings in `_wordfilter.json`.
If you dont plan to use badword filters then can just ignore this file. Do not delete this file as program wont run if its missing.

3b: Optionally if you want to use rcon commands from discord you must set up the role names in `_discordroles.json`.
Role names must be exzactly how they are listed in your discord server settings / role tab. This is case sensitive.

4:Launch the program.exe and enjoy. 

4a:For linux/redhat use `./CrossArkChat` or `./CrossDiscordArkChat` to start the bot. You must start the bot from the folder the bot is in.
If you want the bot to run in background so you dont have to stay logged in you can run `nohup ./CrossArkChat &` or `nohup ./CrossDiscordArkChat &` Note the & is very important and it will not work if thats not there.
To find the pid run `pc -ef | grep CrossArkChat` or `pc -ef | grep CrossDiscordArkChat`.
Once you have the pid run `kill 1234 1234` to end program nicely or `kill -9 1234 1234` to force close it. Replace the 1234 1234 with the pid you find from the above command.


## Configuration

Formating for the config files is important so make sure to keep all formating or you will have problems.
At the bottom it will show examples for the versions with and without discord as they have different configs.


### Configuration for _configuration.json

Basic formating for the config should look like this.

For version checker.
Do not change anything in this part. This is used by the bot to check to see if a new version is avaiable at startup.
```json
"ApplicationSettings": {
    "VersionCheckUrl": "https://raw.githubusercontent.com/spikeydragoon/Cross-Ark-Chat/master/version.txt"
  },
```
For Server Settings
* `Map`: is the name of your map. This should not contain spaces or special characters as it will cause the program to not work properly. This is also used for the chat prefix for the server if you have it enabled.

* `Ip`: is either your local ip if your running bot from your own computer example `192.168.1.2` or if your trying to connect to a server on a hosting provider then you will use the hosting providers public ip address example `75.75.75.75`
You should not use your own public ip as this will cause problems.

* `RconPort`: is the rcon port on the Ark Server. Again you must have rcon enabled.

* `QueryPort`: is the query port on the Ark Server.

* `Password`: is the Admin password on the Ark Server. This should not contain spaces or special characters as it will cause the program to not work properly.

* `Prefix`: is the prefix used to send chat to that server when UsePrefixToSendChat is set to `true`.

* `Active`: is used to tell the bot if the server should be used or not. `true` means bot will load it `false` means bot will ignore it.

* `ServerChannelId`: is the discord channel id that the server should send messages to if SendServerChatToOwnChannel is enabled.

For Non Discord Version of settings.
* `ShowAdminCommands` tells the bot to either show or hide admin commands. `true` is to show commands and `false` is to hide them.

* `AdminCommandLogging` tells the bot to log admin commands. `true` is to log admin commands to its own log file. `false` is to not log admin commands.

* `ShowTribeLogsInChat` tells the bot to either show or hide tribe logs in chat. `true` is to show tribe logs in chat `false` is to hide them. This only matters if you have show Tribe logs in Rcon enabled in your Ark Server Settings. This settings is mostly for people that wanted to have tribe logs in rcon however dont want it showing up in the bot.

* `UsePrefixToSendChat` tells the bot to use the PrefixToSendChat or not. If true you have to type the prefix first before your message will be sent. Example /cc hello

* `PrefixToSendChat` is the prefix that will be used if UsePrefixToSendChat is true. This prefix must be typed before the message to send chat. Example /cc hello

* `LogErrors` tells the bot to log errors.

* `LogChat` tells the bot to log chat.

* `LogAdminCommands` tells the bot to log admin commands if `showadmincommands` is set to `true`

* `LogTribeChat` tells the bot to log tribe chat if `showtribelogsinchat` is set to `true`

* `UseGameCommands` tells the bot to enable the CustomGame Commands opition.

For Discord Version of Settings

For Tribe settings.
* `TribeId`: is the in-game tribe id.

* `Active`: is used to tell the bot if the server should be used or not. `true` means bot will load it `false` means bot will ignore it.

* `TribeDiscordId` is the discord channel id that the server should send messages to if SendTribeLogsToOwnChannel is enabled.

For Game Command Settings.

* `Command` is the in-game prefix used to run the command reply.

* `Commandreply` is the reply the bot gives when running the Above command.

* `Active` tells the bot to use the command or not if the UseGameCommands is set to `true`

For Discord Settings.
* `DiscordChannelID` is the id of the channel you want the bot to send all the chat messages to and from.

* `TribeLogsDiscordChannelID` is the id of the channel you want the bot to send tribe logs to if you have them enabled. Note this can be the same as the DiscordChannelID if you want both to show in same chat.

* `AdminCommandsDiscordChannelID` is the id of the channel you want the bot to send admin commands to if you have them enabled.

* `SupportChannelID` is the id of the channel you want the bot to send support tickets to if enabled.

* `prefix` is the tag you use in discord when sending commands.

* `DiscordChatPrefix` is the chat prefix used in-game when sending messages from discord.

* `DiscordToken` is the Discord Bot Token required for the bot to connect to your server.

* `ShowAdminCommands` tells the bot to either show or hide admin commands. `true` is to show commands and `false` is to hide them.

* `SendAdminCommandsToOWnChannel` tells the bot to send admin commands to its own channel. `true` is to give admin commands its own discord channe. `false` is to keep them going to the same channel if showadmincommands is enabled.

* `ShowChatPrefixInDiscord` tells the bot to either show or hide the chat prefix in discord. This is mainly for people who only have one server. `true` shows the chat prefix(MapName) in discord `false` hides the prefix.

* `ShowTribeLogsInChat` tells the bot to either show or hide tribe logs in discord. This only matters if you have show Tribe logs in Rcon enabled in your Ark Server Settings.

* `SendTribeLogsToOwnChannel` tells the bot to send tribe logs to their own discord channels. ShowTribeLogsInChat must be enabled.

* `SendServerChatToOwnChannel` tells the bot to send server chat to their own discord channels.

* `UsePrefixToSendChat` tells the bot to use the PrefixToSendChat or not. If true you have to type the prefix set in server config first before your message will be sent. Example /all hello will send to all servers. /island hello will send just to the island.

* `UseSupportPrefix` tells the bot to use the SupportPrefix or not. If `true` when you type the supportprefix before your message it will send a message to a set discord channel. Example /help my dinoes are stuck.

* `PingRoleName` tells the bot to ping the set rolename in the support channel or not. `true` it will ping the discord role when it sends a message. `false` it will only send the message it will not ping anyone.

* `ReplyToSupportPing` tells the bot to send a reply message when someone uses the SupportPrefix.

* `SendChatToDiscord` tells the bot to send messages to discord or not. If `true` messages will send as normal. if `false` you will have to use the `PrefixToSendToDiscord` to send messages to discord.

* `LogErrors` tells the bot to log errors.

* `LogChat` tells the bot to log chat.

* `LogAdminCommands` tells the bot to log admin commands if `showadmincommands` is set to `true`

* `LogTribeChat` tells the bot to log tribe chat if `showtribelogsinchat` is set to `true`

* `UseGameCommands` tells the bot to enable the CustomGame Commands opition.

* `PrefixToSendAllServers` is the prefix that will be used if UsePrefixToSendChat is true. This prefix must be typed before the message to send chat. Example /all hello

* `SupportPrefix` is the prefix that will be used if UseSupportPrefix is true. This prefix must be typed before the messaage to send the message to the support channel. Example /help my dinos are stuck.

* `PrefixToSendToDiscord` is the prefix that will be used if `SendChatToDiscord` is `false`. Example /discord hello.

* `SupportRoleToPing` tell the bot which discord rolename to ping if pingrolename is true. Discord role must match the role name exzactly as its listed in your discord server roles tab. This is case sensitive.

* `SupportPingReply` Is the message that will be sent when someone uses the SupportPrefix if `ReplyToSupportPing` is `true`.

Example of adding more than one server to the bot. 
Notice the , is required for each additional server however the last one doesnt have one. This is important as if you dont put the , where needed the bot will not work.
```json
"Servers": [
    {
      "Map": "MapName",
      "IP": "0.0.0.0",
      "RconPort": 0,
      "QueryPort": 0,
      "Password": "Password",
      "Prefix": "/map",
      "Active": false,
      "ServerChannelId": 0
    },
    {
      "Map": "MapName",
      "IP": "0.0.0.0",
      "RconPort": 0,
      "QueryPort": 0,
      "Password": "Password",
      "Prefix": "/map",
      "Active": false,
      "ServerChannelId": 0
    }
  ],
```

Example of adding more than one tribe to the bot.
Notice the , is required for each additional tribe however the last one doesnt have one. This is important as if you dont put the , where needed the bot will not work.
```json
"TribeIDs":[
    {
      "TribeId": "00000",
      "Active": false,
      "TribeDiscordId": 0
    },
    {
      "TribeId": "00000",
      "Active": false,
      "TribeDiscordId": 0
    }
  ],
```

Example of adding more than one Game Command to the bot.

```json
"GameCommands": [
    {
      "Command": "!discord",
      "CommandReply": "https://discord.gg/",
      "Active": false
    },
    {
      "Command": "rules",
      "CommandReply": "These are the rules.",
      "Active": false
    },
    {
      "Command": "/ping",
      "CommandReply": "Pong!",
      "Active": false
    }
  ],
```

Example config for version without discord.
```json
{
  "Servers": [
    {
      "Map": "map",
      "IP": "0.0.0.0",
      "RconPort": 0,
      "Password": "password",
      "Prefix": "/map",
      "Active": false
    }
  ],
  
  "GameCommands": [
    {
      "Command": "!discord",
      "CommandReply": "https://discord.gg/",
      "Active": false
    },
    {
      "Command": "rules",
      "CommandReply": "These are the rules.",
      "Active": false
    },
    {
      "Command": "/ping",
      "CommandReply": "Pong!",
      "Active": false
    }
  ],
  
  "CrossChatSettings":{
    "ShowAdminCommands": false,
    "AdminCommandLogging": false,
    "ShowTribeLogsInChat": false,
    "UsePrefixToSendChat": false,
    "LogErrors": true,
    "LogChat": true,
    "LogAdminCommands": true,
    "LogTribeChat": true,
    "UseGameCommands": false,
    "PrefixToSendAllServers": "/all"
    }
}
```

Example config for version with discord.
```json
{
  "Servers": [
    {
      "Map": "Map",
      "IP": "0.0.0.0",
      "RconPort": 0,
      "QueryPort": 0,
      "Password": "Password",
      "Prefix": "/map",
      "Active": false,
      "ServerChannelId": 0
    }
  ],
  
  "TribeIDs":[
    {
      "TribeId": "00000",
      "Active": false,
      "TribeDiscordId": 0
    },
    {
      "TribeId": "00000",
      "Active": false,
      "TribeDiscordId": 0
    }
  ],
  
  "GameCommands": [
    {
      "Command": "!discord",
      "CommandReply": "https://discord.gg/",
      "Active": false
    },
    {
      "Command": "rules",
      "CommandReply": "These are the rules.",
      "Active": false
    },
    {
      "Command": "/ping",
      "CommandReply": "Pong!",
      "Active": false
    }
  ],
 
  "DiscordSettings": {
    "DiscordChannelID": 0,
    "TribeLogsDiscordChannelID": 0,
    "AdminCommandsDiscordChannelID": 0,
    "SupportChannelID": 0,
    "prefix": "d!",
    "DiscordChatPrefix": "Discord",
    "DiscordToken": "00000",
    "ShowAdminCommands": false,
    "SendAdminCommandsToOwnChannel": false,
    "ShowChatPrefixInDiscord": true,
    "ShowTribelogsInChat": false,
    "SendTribeLogsToOwnChannel": false,
    "SendServerChatToOwnChannel": false,
    "UsePrefixToSendChat": false,
    "UseSupportPrefix": false,
    "PingRoleName": true,
    "ReplyToSupportPing": false,
    "SendChatToDiscord": true,
    "LogErrors": true,
    "LogChat": true,
    "LogAdminCommands": true,
    "LogTribeChat": true,
    "UseGameCommands": false,
    "PrefixToSendAllServers": "/all",
    "SupportPrefix": "/help",
    "PrefixToSendToDiscord": "/discord",
    "SupportRoleToPing": "rolename",
    "SupportPingReply": "Your support ticket has been sent."
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

### Configuration for _discordroles.json

Basic formating for the config should look like this. If your not using the rcon commands in discord you can skip this.

Just change rolename to what ever role you want to use that rcon command. Note they must be typed exzactly like its listed in the discord settings role tab. These are case sensitive. So if the role is listed as AdMinRole your would type it just like that caps and all in the config.

You can also only have one role name per command so if you want multi roles to be able to run the command you must also give them that role in discord as well. So as an admin you will need all roles listed in the config to run all commands. This is how discord roles should be set up anyways meaning admins have all roles mods have mod role and lower esc.

Example _discordroles.json
```json
{
  "DiscordRoles": {
    "Rconcommand": "rolename",
    "AllowPlayerToJoinNoCheck": "rolename",
    "BanPlayer": "rolename",
    "Broadcast": "rolename",
    "DestroyAll": "rolename",
    "DestroyAllEnemies": "rolename",
    "DestroyStructures": "rolename",
    "DestroyWildDinos": "rolename",
    "DisallowPlayerToJoinNoCheck": "rolename",
    "DoExit": "rolename",
    "GetChat": "rolename",
    "GiveItemNumToPlayer": "rolename",
    "GiveExpToPlayer": "rolename",
    "KickPlayer": "rolename",
    "KillPlayer": "rolename",
    "ListPlayers": "rolename",
    "PlayersOnly": "rolename",
    "RenamePlayer": "rolename",
    "RenameTribe": "rolename",
    "SaveWorld": "rolename",
    "ServerChat": "rolename",
    "ServerChatTo": "rolename",
    "ServerChatToPlayer": "rolename",
    "SetMessageOfTheDay": "rolename",
    "SetTimeOfDay": "rolename",
    "ShowMessageOfTheDay": "rolename",
    "Slomo": "rolename",
    "UnBanPlayer": "rolename",
    "PurgeMessage": "rolename",
    "StartChat": "rolename",
    "StopChat": "rolename",
    "RestartChat": "rolename",
    "ClearChat": "rolename",
    "ServerList": "rolename",
    "ServerInfo": "rolename"
  }
}
```

### Configuration for _timedcommands.json

Basic formating for the config should look like this. If your not using the rcon command timers you can skip this.

Below are three exzamples of how you can configure your timers.

* `Name`: Name of the timer should be different than the other timers.

* `Server`: Name of the server to run it on. This should match the map name. You can also say all to run it on all active servers.

* `Commands`: List of all commands for the timer to run.

* `Command`: Name of the command to run OR type message to send. For list of commands see the discord role config above.

* `Type`: You have two types Command for rcon commands and Broadcast for sending messages. The type depends on what you have in command.

* `Active`: Set to `true` to active it or `false` for bot to ignore it.

* `Frequency`: You have three options here minute, hour, day for how often it happens.

* `Timespan`: The interval you want it to run based on the Frequency.

* `TimeOffset`: 24 hour format of when time of day you want the timer to start from. So instead of just every random hour you can tell it to do every hour after 4am.

```json
{
  "TimedCommands": [
    {
      "Name": "Test 1",
      "Server": "",
      "Commands": [
        {
          "Command": "messageoftheday",
          "Type": "Command"
        }
      ],
      "Active": "false",
      "Frequency": "minute",
      "Timespan": "30",
      "TimeOffset": "00:00:00"
    },
    {
      "Name": "Test 2",
      "Server": "",
      "Commands": [
        {
          "Command": "About to save the world",
          "Type": "Broadcast"
        },
        {
          "Command": "saveworld",
          "Type": "Command"
        }
      ],
      "Active": "false",
      "Frequency": "hour",
      "Timespan": "1",
      "TimeOffset": "00:00:00"
    },
    {
      "Name": "Test 3",
      "Server": "",
      "Commands": [
        {
          "Command": "About to wipe all wild dinos",
          "Type": "Broadcast"
        },
        {
          "Command": "wilddinowipe",
          "Type": "Command"
        }
      ],
      "Active": "false",
      "Frequency": "day",
      "Timespan": "1",
      "TimeOffset": "00:00:00"
    }
  ]
}
```

## Discord set up

Steps on how to get your discord tokens and channel ids.


### Creating your discord bot user

You have to create a discord bot user to get the token and to be able to add the bot to your discord server.

* You need to go to the Discord Developers section [here](https://discordapp.com/developers/applications) and click `Create an Application`
* Now name your bot then hit `Save Changes`. If you want you can provide a picture and you can give your bot a discription that will show up in the bots profile however this is not needed. The name given and picture is what will show up in your discord channel when the bot is online.
* On the left Click `Bot` then click `Add bot`. Confirm by clicking `Yes, do it~`
* Now you can get your bot's token by using the `click to reveal token` button. Note this is special and shouldnt be shared with anyone. Anyone that has this token can use it to mess with your discord server and bot. If you already gave your token to someone then go back to where it says click to reveal and click `Regenerate`.
* Paste the bot token in the `_configuration.json` file where it says `DiscordToken`


### Adding the CrossArk program to discord

You now have to add the bot to your discord server and give it permissions.

* You need to go to the Discord Developers section [here](https://discordapp.com/developers/applications) and click on the bot you created in the steps above.
* Under General Information copy the Client ID.
* In your browser type in `https://discordapp.com/oauth2/authorize?&client_id=YOUR_CLIENT_ID_HERE&scope=bot&permissions=0` Replace where it says You_Client_Id_Here with the Bot Client ID that you copyed above. Example `https://discordapp.com/oauth2/authorize?&client_id=123456789&scope=bot&permissions=0`
* Once this page loads up select the server you want to add the bot to. Note you must have the Manage Server permission on the server you are tring to invite the bot to.
* Click `Authorize`

Thats it your bot is now added to your discord server and once your done setting up the config turn the program on and enjoy.


## FAQ

* Q: Can you change the font, color, or size of the in-game chat to something besides the bold yellow?
* A: Sadly no this is a limitation of Rcons `sendchat` command and is hard coded into Arks Rcon. Until they make an option to be able to change this we are stuck with the yellow :(

* Q: Are you open to ideas and code changes?
* A: Yes i am all for adding new ideas and optimizing the code. If you want to contribute by making better guides, correcting my many typos, or giving ideas read the Contributing section then hit me up.

* Q: Do you plan to charge for this program?
* A: No i like "moneys" however this project was for fun and for the community to enjoy so if you paid for this then you have been scammed. If you want to help me you can feed me new ideas, help with making better guides, or fixing typos. Im to lazy to set up a paypal for donations but i may in the future since a free dr pepper would be nice.

* Q: Do you plan to add more features or is this it?
* A: I plan to keep updating the program for a good while mostly for the experience and to see what all we can do with it. Check my to-do list for my planned updates. Due to working full time i dont give etas since work might get busy depending on the season but i plan to at the bare min make sure the bot at least runs. If this ever changes i will let everyone know and look for someone to take it over.

Thats all i can think of for now :)


## To-Do List

* For a updated list check [here](https://github.com/spikeydragoon/Cross-Ark-Chat/projects/1)


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

* Shout out to [Bletch1971](https://github.com/Bletch1971) looking over your rcon code helped a lot and the ASM program you and your team developed is amazing.
