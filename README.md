# Code Project Ideas

## Automated Hypixel Advertising Detection

* Description: Create a machine learning model that is trained to recognize typical advertising messages found on Hypixel, such as Twitch, housing, and guild advertising, as well as SkyBlock auctions, trading, and island advertising, and filters them so that the user doesn't see them.
* Language:
  * Python (No experience)
  * Java (No experience)
* Environment:
  * Azure Machine Learning
  * Forge (Minecraft Modding API)
* Features:
  * Several options, such as the types of messages to filter, the aggressiveness of the filter (like a confidence value), and the option to see what messages are filtered for the purpose of troubleshooting and feedback.
  * Selecting a message in chat should allow you to report it as an advertising message, which would then be used to train the model further.
* Philosophy:
  * Advertisements in Hypixel lobbies is just generally annoying.
  * Filtering of SkyBlock messages like auctions and trading can be useful if you're on a poor profile or are on an Ironman profile where trading is useless.
  * Usage of /myfilter to filter words like "Twitch, guild, auction" can accidentally filter genuine messages.
* Obstacles:
  * No experience with any of the languages or environments that would have to be used.
    * Python is practically a requirement for most machine learning
    * Java is absolutely required since Minecraft and Forge are Java.
    * Azure Machine Learning isn't *really* required, but I'd like experience with Azure's platforms.
    * Forge is unknown to me, although it may be easy to work with.
  * How should the model be trained, and how should the messages be tested against the model?
    * Should the model be trained and stored entirely on the client?
      * Pros: No need to worry about delivery method, zero network usage, consequences of falsely training the model are only experienced on the client that falsely trained it in the first place.
      * Cons: Processing intensive, large usage of disk space, can't be shared with other users.
    * Should the model be trained via Azure/External server, and then the latest version is uploaded to the client on launch?
      * Pros: Not processing intensive for the user, model is stored online, model is higher quality since it can be trained with everyone's messages.
      * Cons: High network usage, requires payment for the servers hosting it, training it against false advertising messages can be damaging.
      * Additional obstacles: Should a human filter submitted advertising messages to ensure that they are valid? Would the delivery of the model be slowed if multiple users are trying to download it at the same time? How will uploaded messages be handled? (Creating an API? What language should it be in? PHP? Ruby? What other languages would I have to learn?)
    * Should the model be trained via Azure/External server, and every message received by the client is uploaded to the server to be tested against the model, and then returned back to the client with a confidence value?
      * Pros: Not processing intensive for the user, no disk usage, model is stored online, model is higher quality since it can be trained with everyone's messages.
      * Cons: The time it takes between the message being sent to the client and the message then being filtered/shown to the user can be very large, high network usage, requires payment for the servers hosting it, training it against false advertising messages can be damaging.
      * Additional obstacles: Should a human filter submitted advertising messages to ensure that they are valid? Would the delivery of the model be slowed if multiple users are trying to download it at the same time? How will uploaded messages be handled? (Creating an API? What language should it be in? PHP? Ruby? What other languages would I have to learn?)
  * Does the uploading and storage of messages sent on Hypixel violate the privacy policy of Hypixel or privacy laws? After all, no consent is provided by the users sending messages, which are tested against the model or possibly even train the model.

## Dolphin In-Game Rich Presence

* Description: A fork of the Dolphin Emulator that incorporates Discord Rich Presence for specific games that includes information such as the level of the player, the world that the player is in, etc..
* Languages:
  * C++ (No experience)
* Environments:
  * Windows
* Features:
  * A wide array of supported games.
  * Options to toggle which games to display Rich Presence for, or to simply use the default Dolphin Rich Presence options.
* How to Accomplish:
  * RAM watching specific values that store information about the details being displayed in the Rich Presence. JSON files used in the event that the specific value needs to be interpreted into another value, like the ID of a world being translated into the actual world name.
* Philosophy:
  * Discord Rich Presence is just a cool feature in general.
  * Having information about the state of the game being played rather than just the name of the game itself would be useful.
* Obstacles:
  * No experience in C++ or the packages I'd likely have to use.
    * I'd probably be able to use the existing code for Dolphin as a reference.
  * It's pretty useless. There's no chance of it being included in a pull request to the main Dolphin repository because of how niche it is, and would become outdated quickly with the addition of new commits and updates to the main Dolphin repository.
  * There's a huge amount of games that can be played on Dolphin, how do I decide what games to incorporate support for?
  * What's the best way to watch the RAM values?