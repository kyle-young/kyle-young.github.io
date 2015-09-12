---
layout: page
title: Twitch.tv Chat Analysis 
---

<p class="message">
  Source code can be found at <a href="https://github.com/kyle-young/twitchtvchatanalysis" target="_blank" title="twitchtvanalysislink">github.com/kyle-young/twitchtvchatanalysis</a>.  The link that helped me create the bot is <a href="http://www.sevadus.tv/forums/index.php?/topic/774-simple-python-irc-bot/" target="_blank" title="help1">here</a>
</p>

This project ingests twitch.tv irc chat, stores it in SQLite, graphs using matplotlib. 

How to use (after you get all the required credentials):

1. Put the SQLite database name you want in the settings file   
2. Run createdb.py by typing in "python3 createdb.py"   
3. Get all of the IRC connection info   
    -For oauth key: www.twitchapps.com/tmi/   
    -For IRC connection info: https://api.twitch.tv/api/channels/CHANNEL_NAME/chat_properties   
4. When you want go get twitch.tv chat type in "python3 twitchingest.py", ctrl+c to stop   
5. To graph, type in "python3 graph.py"

---

<h4>Tidbit #1</h4>
The channels I wanted to get chat logs from are on Twitch's event servers so they have different IPs than regular channels.  These IPs can be found at [https://api.twitch.tv/api/channels/"channel name"/chat_properties](https://api.twitch.tv/api/channels/"channel name"/chat_properties).  For this project in particular I used Riot Game's channel so I used  [https://api.twitch.tv/api/channels/riotgames/chat_properties](https://api.twitch.tv/api/channels/riotgames/chat_properties)

<h4>Tidbit #2</h4>
For SQLite, INSERT speeds couldn't keep up with the velocity of twitch.tv's chat so I had to change two settings.   

1. The first one was setting "synchronous" to "off" which causes SQLite to continue without syncing as it hands data off to the OS.  Dangers of this is corruption if the OS crashes before the data is written.   
2. The second change was setting "journal_mode" to "memory" which causes SQLite to store the rollback journal to volatile RAM instead of disk.

