## Criminals
### Version: 1.0

![Example of the script in action](https://i.imgur.com/9wvbkro.png)

![Another example of the script in action](https://i.imgur.com/RKjTDpf.png)

The script enhances the bounty system by adding global messages when people reach certain tresholds of bounty (500, 1000 and 5000) or when they manage to clear their name. It also adds the ability to award the bounty to players who kill the criminals. Finally, it is possible to append prefixes to the chat messages sent by criminals, to let others know they indeed broke the law.


## INSTALLING INSTRUCTIONS

1) Put `criminals.lua` file in `...\tes3mp\mp-stuff\scripts\` folder.

2) Open `serverCore.lua` and add `criminals = require("criminals")` at the top along with other `require` lines.

3) Save `server.lua`, open `eventHandler.lua`.

4) Find `Players[pid]:Message("You have successfully logged in.\n")` and below it add `criminals.OnLogin(pid)`.

5) Find `Players[pid]:SaveBounty()` and add `criminals.UpdateBounty(pid)` below it.

6) (OPTIONAL) Find `message = config.rankColors.moderator .. "[Mod] " .. message`. Below the `end` line add:
```
            local prefix = criminals.IsCriminal(pid)
            message = prefix .. message
```
to add prefixes to in-game chat messages.

7) Save `eventHandler.lua` and open `\player\base.lua`.

8) Find `local killerPid = tes3mp.GetPlayerKillerPid(self.pid)` and below it add `criminals.ProcessBountyReward(self.pid, logicHandler.GetChatName(killerPid))`.

9) Save `base.lua` and start the server. Try committing a crime to gain a bounty of 500 or more and see if a message is displayed in the chat.

## SETTINGS
displayGlobalWanted = true -- whether or not to display the global messages in chat when a player's wanted status changes
displayGlobalClearedBounty = true -- whether or not to display a global message when a player clears their bounty
displayGlobalBountyClaim = true -- whether or not to display a global message when another player claims a bounty
bountyItem = "gold_001" -- item used as bounty, in case you use a custom currency
### Changes you can make in the script
|Variable|Description|
|:----|:-----|
|displayGlobalWanted|Whether or not to display a message when a player becomes wanted.|
|displayGlobalClearedBounty|Whether or not to display a message when a player clears their name.|
|displayGlobalBountyClaim|Whether or not to display a message when a player claims a bounty by killing another player.|
|bountyItem|Item used as bounty (normally gold).|

## KNOWN ISSUES

The chat prefixes, although completely optional, can interfere with other scripts that add prefixes. Consult `#scripting_help` channel on TES3MP discord server if you happen to use another script which adds prefixes for a solution.

## CHANGELOG:
### 1.0:
Script updated for 0.7.x.