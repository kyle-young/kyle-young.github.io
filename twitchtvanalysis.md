---
layout: page
title: Twitch.tv Chat Analysis 
---

<p class="message">
  Source code can be found at <a href="https://github.com/kyle-young/twitchtvchatanalysis" target="_blank" title="twitchtvanalysislink">github.com/kyle-young/twitchtvchatanalysis</a>.  The link that helped me create the bot is <a href="http://www.sevadus.tv/forums/index.php?/topic/774-simple-python-irc-bot/" target="_blank" title="help1">here</a>
</p>

<p class="message">
  The source code is self explanatory and I explain how to use it in the github repository, so I'll use this page to outline some of the gotchas I ran into while doing this project. 
</p>

><p class="message">
  The channels I wanted to get chat logs from are on Twitch's event servers so they have different IPs than regular channels.  These IPs can be found at https://api.twitch.tv/api/channels/"channel name"/chat_properties.  For this project in particular I used Riot Game's channel so I used  <a href="https://api.twitch.tv/api/channels/riotgames/chat_properties" target="_blank" title="riotgameschatserver">https://api.twitch.tv/api/channels/riotgames/chat_properties</a>
</p>

><p class="message">
  For SQLite, INSERT speeds couldn't keep up with the velocity of twitch.tv's chat so I had to change some settings.  The first one was setting "synchronous" to "off" which causes SQLite to continue without syncing as it hands data off to the OS.  Dangers of this is corruption if the OS crashes before the data is written.  The second change was setting "journal_mode" to "memory" which causes SQLite to store the rollback journal to volatile RAM instead of disk.
</p>
